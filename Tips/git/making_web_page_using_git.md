# Github.io 개인 사이트 만들기

## 동기
같이 일하는 동료분의 개인 사이트가 멋있어서 탐이 났다!

간단하게 개인 사이트를 만들 수 있을 것 같은 (아마) 착각도 들고, 
github.io 라는 이름을 보건대 웹호스팅 없어도 만들 수 있을 것 같아 검색해보았다.

## 튜토리얼
https://pages.github.com 이 사이트에 기본적인 튜토리얼이 기술되어 있다.

해당 페이지에서 User or organization site / A terminal 을 선택하여 hello word 까지 수행해보았다.

## Jekyll
Hello world 보다 나은 페이지를 만들어볼까 하고 구글링해보니 상당수의 검색 결과가 jekyll 이라는 repository 를 이용하고 있었다.

https://github.com/barryclark/jekyll-now

https://jekyllrb-ko.github.io/ 한글 문서도 있다!

### Jekyll 설치

Mac 을 이용하고 있으므로, 아래와 같이 수행해보았다.

```sudo gem install jekyll```

gem 은 Ruby 의 패키지 매니저라고 한다. Xcode 가 깔려 있으면 ruby 도 같이 깔리는 모양이지만, 나같은 경우엔 다음과 같은 에러가 났다.

```
Building native extensions.  This could take a while...
ERROR:  Error installing jekyll:
	ERROR: Failed to build gem native extension.

    /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/bin/ruby extconf.rb
checking for ffi.h... *** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.  Check the mkmf.log file for more details.  You may
need configuration options.

Provided configuration options:
	--with-opt-dir
	--without-opt-dir
	--with-opt-include
	--without-opt-include=${opt-dir}/include
	--with-opt-lib
	--without-opt-lib=${opt-dir}/lib
	--with-make-prog
	--without-make-prog
	--srcdir=.
	--curdir
	--ruby=/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/bin/ruby
	--with-ffi_c-dir
	--without-ffi_c-dir
	--with-ffi_c-include
	--without-ffi_c-include=${ffi_c-dir}/include
	--with-ffi_c-lib
	--without-ffi_c-lib=${ffi_c-dir}/
	--with-libffi-config
	--without-libffi-config
	--with-pkg-config
	--without-pkg-config
/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:434:in `try_do': The compiler failed to generate an executable file. (RuntimeError)
You have to install development tools first.
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:549:in `block in try_compile'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:502:in `with_werror'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:549:in `try_compile'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:1038:in `block in have_header'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:889:in `block in checking_for'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:340:in `block (2 levels) in postpone'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:310:in `open'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:340:in `block in postpone'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:310:in `open'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:336:in `postpone'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:888:in `checking_for'
	from /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/mkmf.rb:1037:in `have_header'
	from extconf.rb:16:in `<main>'


Gem files will remain installed in /Library/Ruby/Gems/2.0.0/gems/ffi-1.9.18 for inspection.
Results logged to /Library/Ruby/Gems/2.0.0/gems/ffi-1.9.18/ext/ffi_c/gem_make.out
```

http://jekyllrb.com/docs/troubleshooting/#installation-problems 

OS 별로 Jekyll 의 install troubleshooting 정리된 위 사이트를 보고 다음과 같이 gem update 를 시도해보았다.

```sudo gem update --system```

그러나 여전히 install error 가 있었으므로 다음을 시도해본다.
Xcode 의 command line tool 을 설치하는 내용이라고 한다.

```xcode-select --install```

되는줄 알았더니 이번엔 이런 에러가 뜬다.

```
Building native extensions.  This could take a while...
Successfully installed ffi-1.9.18
Fetching: rb-inotify-0.9.8.gem (100%)
Successfully installed rb-inotify-0.9.8
Fetching: listen-3.0.8.gem (100%)
ERROR:  While executing gem ... (Errno::EPERM)
    Operation not permitted - /usr/bin/listen
```

찾아보니 [Stack overflow](http://stackoverflow.com/questions/32891965/error-while-executing-gem-errnoeperm-operation-not-permitted) 에서 다음을 시도해보라고 한다...

```sudo gem install -n /usr/local/bin jekyll```

링크에서 GEM_NAME_HERE 에 있는 부분이 ruby package name 을 적으라는 뜻인 것 같다.
그리고 드디어 실행이 잘 되었다.

### Theme 선택

http://jekyllthemes.org/

이 사이트에 들어가니 다양한 Theme 가 제공되고 있다!

다들 비슷한 모양들이라서 Theme 선택하기 어려운 줄 알았는데 딱히 그렇진 않은 모양이다. 먼저 예뻐보이는 Theme 을 선택해보기로 한다.

그 와중에 Pycon KR 등에서 자주 보이던 테마 발견.. https://jasonlong.github.io/cayman-theme/

그치만 이 Theme 이 왠지 마음에 들어서 설치해보기로 했다. http://jekyllthemes.org/themes/end2end/

### Theme 설치
마음에 드는 Theme 을 다운로드 받아 압축을 풀고, `_config.yml` 파일의 gems 를 참고하여 Theme 에서 사용하는 패키지들을 설치해주었다.

```sudo gem install jekyll-paginate```

내가 선택한 Theme 에서는 이 패키지만 적혀 있었지만, Theme 의 종류에 따라 다르다고 하니 확인해볼 것.

그 다음에 Theme directory 에 들어가서 아래와 같이 썼다.

```jekyll new eyshin05.github.io```

근데... 끊임없는 에러가 난다.

```
/Library/Ruby/Gems/2.0.0/gems/bundler-1.14.6/lib/bundler/spec_set.rb:87:in `block in materialize': Could not find jekyll-sass-converter-1.4.0 in any of the sources (Bundler::GemNotFound)
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.6/lib/bundler/spec_set.rb:80:in `map!'
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.6/lib/bundler/spec_set.rb:80:in `materialize'
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.6/lib/bundler/definition.rb:176:in `specs'
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.6/lib/bundler/definition.rb:235:in `specs_for'
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.6/lib/bundler/definition.rb:224:in `requested_specs'
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.6/lib/bundler/runtime.rb:118:in `block in definition_method'
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.6/lib/bundler/runtime.rb:19:in `setup'
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.6/lib/bundler.rb:100:in `setup'
	from /Library/Ruby/Gems/2.0.0/gems/jekyll-3.4.3/lib/jekyll/plugin_manager.rb:36:in `require_from_bundler'
	from /Library/Ruby/Gems/2.0.0/gems/jekyll-3.4.3/exe/jekyll:9:in `<top (required)>'
	from /usr/local/bin/jekyll:22:in `load'
	from /usr/local/bin/jekyll:22:in `<main>'

```
이런 식으로 에러가 나면 

```sudo gem install -n /usr/local/bin jekyll-sass-converter -v 1.4.0``` 

이런 식으로 Dependency 가 있는 package 들을 설치했다... 왜...

처음으로 루비와 관련된 일을 해보는건데 루비가 싫어지려고 하고 있다.
다른 theme 를 고를까... orz

### 더 좋은 참조 사이트를 찾았다
https://help.github.com/articles/about-github-pages-and-jekyll/

여기 보면...

1. 테마 선택: https://help.github.com/articles/creating-a-github-pages-site-with-the-jekyll-theme-chooser/#using-the-jekyll-theme-chooser-with-a-new-repository


## 결과물
https://eyshin05.github.io

## 참고한 사이트
1. 이 블로그에 mac 기반으로 친절하게 설명되어 있다! https://qkraudghgh.github.io/jekyll/2016/07/02/jekyll-blog-setup.html
2. https://help.github.com/articles/about-github-pages-and-jekyll/
