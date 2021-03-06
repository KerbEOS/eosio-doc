1.1 소개
========

이 문서는 개발자 관점에서 EOSIO의 상세한 부분들을 배우기 위한 완벽한 가이드이다.

.. rubric:: 이 가이드에서 배울 수 있는 것들

당신이 배울 수 있는 것들 중 몇 가지만을 나열해 보면 다음과 같다.

* 테스트 용 node를 빠르게 시작시키는 방법
* 지갑과 키를 사용하는 방법
* 계정을 생성하는 방법
* 컨트랙트를 작성하는 방법
* 컴파일하고 ABI를 생성하는 방법
* 컨트랙트를 배포하는 방법

.. rubric:: C/C++ 경험

EOSIO 기반 블록체인은 사용자가 개발한 웹 어셈블리(WASM, WebAssembly) 애플리케이션과 코드를 실행한다. WASM은 Google, Microsoft, Apple을 포함하여 업계의 선두 기업들에 의해 폭넓은 지원을 받고 있는 새롭게 등장한 표준이다.

현 시점에서 WASM으로 컴파일하는 가장 성숙한 툴체인(toolchain)은 clang/llvm의 C/C++ 컴파일러이다. 가장 높은 호환성을 보장받기 위해 EOSIO가 제공하는 C++ 툴체인을 사용할 것을 권장한다.

서드 파티(3rd party)들에 의해 개발 중인 다른 툴체인으로는 Rust, Python, Solidity 등이 있다. 이들 언어들은 C/C++에 비해 보다 단순해 보일 지는 모르지만 성능 측면에서 당신이 개발할 애플리케이션의 확장성을 제한할 가능성이 있다. 우리는 C++가 성능과 보안성이 우수한 스마트 컨트랙트를 개발하기 위한 최적의 언어라고 생각하며, 어느 정도 예측 가능한 미래까지는 C++를 사용할 계획이다.

.. rubric:: Linux/Mac OS 경험

EOSIO 소프트웨어는 다음과 같은 환경을 지원한다.

* Amazon 2017.09와 그 이후 버전
* Centos 7
* Fedora 25와 그 이후 버전 (Fedora 27 권장)
* Mint 18
* Ubuntu 16.04 (Ubuntu 16.10 권장)
* Ubuntu 18.04
* Mac OS Darwin 10.12와 그 이후 버전 (Mac OS 10.13.x 권장)

.. rubric:: 커맨드라인 인터페이스에 대한 지식

EOSIO에서 제공하는 다양한 툴들을 사용하기 위해서는 기본적인 커맨드라인 인터페이스 사용 방법을 알고 있어야 한다.

.. rubric:: C++ 개발 환경

C++ 문법 강조 기능을 제공하면 더 좋겠지만, 어떤 텍스트 편집기라도 사용할 수 있다. 많이 사용되는 에디터는 Sublime Text와 Atom이다. 다른 방법은 코드 자동 완성 기능과 통합된 개발 경험을 제공하는 IDE를 사용하는 것이다. 당신이 원하는 소프트웨어를 사용하기 바라며, 뭘 사용할지 정하지 못하겠다면 다음과 같은 것들을 사용해 볼 수 있을 것이다.

.. rubric:: 사용 가능한 에디터나 IDE

* `Sublime Text <https://www.sublimetext.com>`_
* `Atom <https://atom.io/>`_
* `CLion <https://www.jetbrains.com/clion/>`_
* `Eclipse <http://www.eclipse.org/downloads/packages/release/oxygen/1a/eclipse-ide-cc-developers>`_
* `Visual Studio Code <https://code.visualstudio.com/>`_

.. rubric:: 개발 환경을 위한 OS

Linux 계열의 OS를 사용하면 이 가이드를 따라 실습을 수행하는데 어려움이 없을 것이다. 다음 OS들만을 지원하는 것은 아니지만 기본적으로 다음의 OS들은 사용 가능하다.

* Mac OS
* Ubuntu
* Debian
* Fedora

.. rubric:: Windows의 경우

Windows를 사용하는 경우 아직 현재까지는 파워쉘로 포팅된 커맨드들이나 사용 지침을 제공하지 않고 있다. 향후 파워쉘 커맨드들을 추가로 제공할 수도 있다. 그동안은 VM 위에서 Ubuntu를 설치하고 개발 환경을 설정하는 것이 가장 좋은 방법일 것이다. 물론 Linux 명령들을 포팅하여 사용하는데 익숙한 Windows 개발자들은 거의 문제 없이 사용 가능할 것이다.
