---
title: Homebrew로 java 설치하기
date: 2019-04-11
category: 설치기
header:
  image: /assets/images/jesus-kiteque-224069-unsplash.jpg
  caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
---

mac에다가 java를 설치하려고 블로그를 검색하는데 죄다 oracle 사이트 가서 다운로드를 받으라고 한다.

귀찮아서 Homebrew로 설치하는 방법을 검색했다.

java를 설치하기 위해서는 **Homebrew cask** 가 필요하다. cask는 GUI 기반의 어플리케이션을 설치할 수 있도록 해주는 도구이다. 우선 cask를 설치하자.

```sh
brew install cask
```

다음으로 Homebrew를 최신 버전으로 업데이트 한다.

```shell
brew update && brew upgrade cask && brew cleanup && brew cask cleanup
```

업데이트가 끝났으면 `brew cask info java` 를 실행하여 설치 가능한 java 의 정보를 확인한다.

```sh
dongjinpark@park-mac > brew cask info java
java: 12,33
https://jdk.java.net/
Not installed
From: https://github.com/Homebrew/homebrew-cask/blob/master/Casks/java.rb
==> Name
OpenJDK Java Development Kit
==> Artifacts
jdk-12.jdk -> /Library/Java/JavaVirtualMachines/openjdk-12.jdk (Generic Artifact)
```

별도의 설정이 없을 경우 최신버전을 안내하기 때문에 설치 가능한 버전이 12로 나온다. 내가 설치하고 싶은 버전은 8이기 때문에 약간의 추가 작업이 필요하다. `brew tap caskroom/versions` 를 실행하여 설치가능한 java version을 추가한다. (tap : third-party repository 추가)

```sh
brew tap caskroom/versions
```

`brew search java` 를 실행하면 다음과 같이 다른 버전의 java가 목록에 있는 것을 확인할 수 있다.

```sh
dongjinpark@park-mac > brew search java
==> Formulae
app-engine-java            javarepl                   libreadline-java
google-java-format         jslint4java

==> Casks
charles-applejava                        java8
eclipse-java                             netbeans-java-ee
eclipse-javascript                       netbeans-java-se
java                                     oracle-jdk-javadoc
java-beta                                yourkit-java-profiler
java11                                   homebrew/cask-versions/java-beta
java6
```

`brew cask install java8`를 실행하여 java8을 설치하면 끝.
