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
	
> [!NOTE] Title
>  
