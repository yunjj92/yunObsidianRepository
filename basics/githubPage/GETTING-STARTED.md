---
tags:
  - type/note
aliases: 
created: 2025-01-23, 15:28
modified: 2025-01-23, 15:28
template-type: Frontmatter
template-version: "1.3"
cc: CC BY-SA 4.0
source: https://github.com/groepl/Obsidian-Templates
---
## 필수 설치 항목
### 1) ruby, gem, gcc, make
### 2) Ruby101
```
jekyll는  Ruby로 작성되었습니다. jekyll 테마를 구성하기 전에 ruby가 뭔지 부터 알아가시죠!
```
- Gems
	- Gem은 특정 기능을 모아둔 것으로써, 여러 프로젝트를 오가며 쓸 수도 있고, 다른 사람들과 공유할 수도 있다. 대표적으로 다음과 같은 기능을 수행한다. 
		- Ruby 객체를 JSON으로 변환
		- Pagination
		- Github와 같은 Api와 통신
	- jekyll는 곧 한 개의 gem이라고 볼 수 있는데, 다수의 jekyll 플러그인 또한 gem이라고 할 수 있다. 예를 들면 jekyll-feed, jekyll-seo-tag, jekyll-archives
- Gemfile
	- Gemfile은 본인 사이트에서 사용되는 다수의 gem을 목록화 한 것으로, 모든 jekyll 사이트는 Gemfile을 main 폴더에 가지고 있다. 대충 아래와 비슷한 무언가를 가리킨다. 		

> [!NOTE] Gemfile 예시
> source "https://rubygems.org" 
> 
> gem "jekyll" 
> 
> group :jekyll_plugins do 
> 	gem "jekyll-feed" 
> 	gem "jekyll-seo-tag" 
> end

- Bundler
	 Bundler도 마찬가지로 하나의 gem으로 site안의 다른 gem을 설치하는 역할을 한다. 
	 'gem install bundler' 명령어를 수행하여 Bundler를 설치하면 된다. 이건 한 번만 설치하면 되고, jekyll Project를 만들 때마다 설치하지 않아도 된다. Bundler를 이용하여 Gemfile 목록에 있는 gem을 설치하기 위해선,  Gemfile이 있는 디렉토리에서 다음과 같은 명령어를 수행하면 된다. 

### 3) SCSS syntax

-  stylesheet 구조 
	 - Top Level Statements
			- Module loads @use
				다른 Sass stylesheet의 mixins, functions, variables를 로드. @use에 의해 로드되는 스타일시트는 "modules"라고 명명. 만약 한 번에 여러 개의 파일을 로드하고자 한다면 @foward를 사용
- Jekyll는 기본적으로 jekyll-sass-converter 플러그인이 포함되어 있다. 따라서  Sass 관련 모든 것들은 \_sass 디렉토리에서 찾게 되어있다. 만약에 VSCode에서 @import "main" 코드에 경고가 뜬다면 무시한다. sass 설정은 모두 본인 사이트의 source에서 상대경로를 가리킨다. \_config.yml 파일 위치를 기준으로한 상대경로는 아님.
	
> [!NOTE] e.g
> @use 'foundation/code';
> @use 'foundation/lists';
>  

- Style Rules
	- 중첩: 또 다른 스타일 안에 다른 스타일 규칙을 작성할 수 있으며, Sass가 자동으로 바깥 규칙의 선택자에 내부 규칙을 병합시켜준다. 
		
> [!NOTE] 
> ```
nav {
 ul {
   margin: 0;
   padding: 0;
   list-style: none;
 }
 li { display: inline-block; }
 a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
 }
}

```
* bundle : to push or put someone or sth somewhere quickly and roughly
  e.g) bundle sth into sth. He bundled his clothes into the washing machine. 
  e.g) The children were bundled off to school early that morning.
  : to include an extra computer program or other product with something that you sell: 
  e.g) The system came bundled with a word processor, spreadsheet, and graphics program.
```

- '@import' is  deprecated 
		2019년에 Sass module system을 발표했고, 이 때 @use @forward를 @import 대신하기 위해 추가했다. 이는 스타일시트를 더 유지가능한 형태로 관리하고 에러가 덜 발생하는 목적으로 도입되었다. @import는 공식적으로 Dart Sass 1.80.0 부터 쓰이지 않는다. 
		@import 사용에 대해 deprecation 경고가 발생할 때를 대비해서 최근에 '--silence-deprecation' 명령어 옵션을 추가했다. 만약에 @import를 사용하지 않고 새로운 모듈 시스템으로 옮길 예정이라면, 아래 명령어를 수행하면 된다. 
	```
	$ sass-migrator module --migrate-deps <path/to/style.scss>
	```

### 4) \_config.yml

> [!NOTE] Title
> Jekyll는 사이트를 꾸미는 데 있어서 굉장히 유연하게 사용 가능하다. 다음 설정 사항은 루트 디렉토리에 위치한 \_config.yml 혹은 \_config.toml 파일에 구체적으로 작성하면 된다.   

-  설정 가능 카테고리
	-  Configuration Options 
	-  Default Configuration
	-  Front Matter Defaults
	-  Environments
	-  Markdown Options
	-  Liquid OPtions
	-  Sass/SCSS Options
	-  Webrick Options 
	-  Incremental Regeneration

 -  Configuration Options
 ```
  source: DIR  -- jekyll가 파일을 읽을 위치를 변경
  destination:DIR  --  jekyll가 파일을 작성할 위치를 변경
  safe: BOOL -- 검증되지 않은 플러그인 비활성화, 캐싱, symbolic link 무시
  disable_disk_cache: BOOL
  ignore_theme_config: BOOL -- jekyll가 theme-config 전체를 사용하지 않도록 수정가능
  exclude: [DIR, FILE, ...] -- 변환할 때 이것만큼은 하지 말아줘
  include: [DIR, FILE, ...] -- 변환할 때 이것만큼은 꼭 포함해줘
  
  
 ```

- What is a cache?
	 무언가를 저장하는데 사용되는 하드웨어 혹은 소프트웨어를 일컫는다. 보통 적은 양이지만 더 빠르고 더 값비싼 메모리를 사용하여 최근에 접근한 데이터와 관련해 퍼포먼스를 향상시키기 위해 사용한다.
	 'Cached Data'는 일시적으로 저장매체에 저장되고, main storage와 분리된다. Cache는 일반적으로 CPU, applications, web browses, OS에서 사용된다. 
	 Cache는 bulk media 혹은 main storage 공간에서 지속적으로 클라이언트의 요구를 수용할 수 없기 때문에 사용된다. Cache는 데이터 접근 시간과 latency를 줄여주고, I/O를 더 빠르게 수행할 수 있도록 한다. 대부분의 모든 application 작업량이 I/O 작동에 의존하기 때문에 caching process는 application 성능을 향상시킨다. 

	 Q. 그렇다면 chache는 어떻게 작동하는가? 
	 A. 클라이언트가 데이터에 접근하려고 하면, 컴퓨터는 가장 먼저 cache를 체크한다. 참고로 'a cache hit'라는 것은 데이터가 cache에서 발견되었음을 의미한다. 이 cache hit가 나올 확률을 우리는 cache hit rate(ratio) 라고 부른다. 
	 만약에 요청된 데이터가 cache에 없다면(우리는 이걸 a cache miss라고 부른다), 해당 데이터를 메인 메모리에서 가져와서 Cache


## 5) liquid template 

- capture:
		문자열을 값으로 받는 변수를 새로 만든다. 
```
{% capture tempval  %}
    value
{% endcapture %}
```
-  Iteration 
	- for 
		- 최대 50번의 순환 가능하고 그 이상의 횟수가 수행되어야 한다면 여러 번에 나눠서 수행해야 하고 이때는  {% paginate %}를 사용한다. 
		- limit를 사용하여 순환의 횟수를 제한할 수 있다. 
		- offset을 이용하여 반대로 시작하는 숫자를 지정할 수 도 있다. 
		- 순환할 구체적인 범위를 지정할 수 있다.
```
 {% for variable in array %}
	 expression
 {% endfor %}

 {% for variable in array limit: number %}
	 expression
 {% endfor %}

 {% for variable in array offset: number %}
	 expression
 {% endfor %}

{% for variable in (number..number) %}
  expression
{% endfor %}
```

## 6) Node.js

 


출처: https://shopify.dev/docs/api/liquid/tags/for

```
[모르는 단어는 여기를 참고해주십쇼! ]
 * a storage medium(storage media) is a physical device that receives and retains electronic data for applications and users and makes the data available for retrieval
 e.g) USB Stick, DVD, 
 * Network latency is the delay in network communication. It shows the time that data takes to transfer across the network. 
 * eject : to push, throw, or force sth out of a place
  e.g) When X-rays are absorbed by matter, electrons are ejected from the atoms of which it tis composed. 
   : to come out of a machine when a button ins pressed, or to make sth do this
  e.g) How do you eject the tape? 
* conversion: the process of converting something from one thing to another
 : a process in which someone changes to a new relition or belief
* excerpt: a short part taken from a speech, book, film, etc.;
 e.g) An excerpt from her new thriller will appear in this weekend's magazine.
 * sooner rahter than later:  without too much delay
 * backsliding: to go back to doing sth bad when you have been doing something good, especially to stop working hard or to fail to do something that you had agreed to do
	 e.g) My diet was going well, but I've been backsliding a little recently 
* Migrate off of : to move away from a place or region
		
```

