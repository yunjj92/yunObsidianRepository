---
tags: type/structure structure/bujo
# --- Learn more about "How to use tags": https://forum.obsidian.md/t/how-to-use-tags/
aliases: 
created: 2025-02-19, 13:25
modified: 2025-02-19, 13:25
# --- Install plugin: https://github.com/beaussan/update-time-on-edit-obsidian
template-type: BuJo Daily
template-version: "1.3"
# --- Find latest updates: https://github.com/groepl/Obsidian-Templates
---

#weekly-planner 
## 2월 19일(수요일) ~ 2월 21일(금요일)
##### [2월 19일 (수요일) ]

> [!NOTE] TO-DO LIST
> 1. 추가 API 개발 
> 2. 수정 API 개발 
> 3. 유지보수

###### 추가 API 개발 MEMO
	@RequestMapping("set/new_prgs_stat_cd.action")
- Service Logic todo 
	- ip 가져오기 -> id 가져오기 -> parameter VO 객체 생성 -> 서비스 메서드 호출// Controller 끝
	-  일괄 유효성 체크 
		- parameter로 들어온 judg_seq tb_si_judg_info 조회하여 데이터 있는지부터 체크 
		- 접수 전인 '작성 중', '보완요청'  상태인지 체크
			- tb_si_judg_info.judg_dips_stat_cd == '5' 혹은 '10' 인 경우 -> 각 '전송완료', '접수'
	-  대리인 정보 (tb_ext_depy -> tb_si_ownr_intr)
		- 유효성 체크
			- 
	-  재결요약(tb_ext_rept_summary -> tb_si_rept_summary)
	-  협의평가(tb_ext_cslt_amt_tot -> tb_si_cslt_amt_tot)
	-  사업시행담당자(tb_ext_biz_oprt_ichr -> tb_si_biz_oprt_ichr)
	-  첨부파일(tb_ext_)

###### 유지보수
- 조서금액합계(사업정보의 '금액')와 직접 작성한 '종전금액합계' 5% 차이 남
	- 직접 작성한 '종전금액합계'
```
SELECT judg_seq , biz_oprt_prce FROM tb_ext_judg_info teji where teji.judg_seq = ? 
```
	- 일단 '조서금액합계' 연계 EXT 테이블 기준으로 내는 쿼리 아래와 같음 
```
SELECT
(SELECT COUNT(*) AS OBJ FROM TB_EXT_REPT_INFO WHERE LAND_OBST_KIND_CD != 'L' AND LAND_OBST_KIND_CD != 'D'
AND COALESCE(DEL_YN,'N') = 'N' AND JUDG_SEQ = ? AND COALESCE(DEL_YN,'N') = 'N') obj,
(SELECT COUNT(*) AS LND
   FROM ( SELECT DISTINCT
               SIDO_GUNGU_CD||DOMYRI_CD||MONT_DIV_CD||MAIN_STRT_NO||COALESCE(fn_cast_varchar2int(SUB_STRT_NO),'0')
     FROM TB_EXT_REPT_INFO
    WHERE JUDG_SEQ = ? AND LAND_OBST_KIND_CD = 'L' AND COALESCE(DEL_YN,'N') = 'N' ) SUB
   ) as "lnd",
(SELECT COUNT(DISTINCT OWNR_SEQ) OWN2 FROM TB_EXT_REPT_INFO OWN LEFT OUTER JOIN TB_EXT_REPT_OWNR_INTR B ON OWN.REPT_SEQ = B.REPT_SEQ
WHERE OWN.JUDG_SEQ = ? AND B.JUDG_SEQ = ? AND OWN.DEL_YN = 'N'	AND B.OWNR_INTR_YN = 'O') as "own",
(SELECT COUNT(DISTINCT INTR_SEQ) RPS2 FROM TB_EXT_REPT_INFO INR
LEFT OUTER JOIN TB_EXT_REPT_OWNR_INTR B ON INR.REPT_SEQ = B.REPT_SEQ
WHERE INR.JUDG_SEQ = ?	AND B.JUDG_SEQ = ?	AND INR.DEL_YN = 'N'	AND B.OWNR_INTR_YN = 'R') rps,
(SELECT SUM(COALESCE(AREA_AMOT,0)) AS "area"  FROM TB_EXT_REPT_INFO WHERE JUDG_SEQ = ? AND LAND_OBST_KIND_CD = 'L'AND COALESCE(DEL_YN,'N') = 'N') area,
(SELECT SUM(COALESCE(BEF_AMT,0)) AS bizoprtprcesum
   FROM TB_EXT_REPT_OWNR_INTR A
   INNER JOIN TB_EXT_REPT_INFO B ON A.REPT_SEQ = B.REPT_SEQ
  WHERE A.JUDG_SEQ = ?
    AND A.OWNR_INTR_YN = 'O'
AND COALESCE(B.DEL_YN,'N') = 'N'
) as "bizOprtPrceSum"
```
- 구분 지상권 ? 
- 합유? 
