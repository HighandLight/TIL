# 1장. OT

## Dart란?

### Dart 언어의 특징

1. 객체 지향 언어(Object-Oriented-Language)
2. User-Interface를 만드는 데에 아주 최적화되어있음
3. 빠르고 많은 플랫폼에 컴파일 가능
    
    > Dart가 가진 두 개의 컴파일러 : `Dart Native`, `Dart Web`
    > 
    > 
    
    > 
    > `1. Dart Native`
    > : Dart로 작성한 코드를 여러 CPU의 아키텍쳐에 맞게 변환해주는 컴파일러
    > 
    > <aside>
    > 💡 JIT vs AOT
    > `JIT(Just In Time)`
    > 
    > : 브라우저에서 파일들을 다운로드 한 뒤에 한번 컴파일해서 브라우저 엔진이 실행할 수 있는 저수준 언어로 바꾸어준 후에, 화면을 렌더하는 방식
    > → dart VM을 사용하여, 사용자가 쓴 코드의 결과를 바로 화면에 보여줌
    > → 사용자의 코드가 가상 머신에서 작동하고 있는 것이라 조금 느림
    > → 하지만 오직 개발중일 때에만 쓰임 배포 시는 AOT 사용
    > 
    > `AOT (Ahead Of Time)`
    > 
    > : 소스코드를 미리 컴파일하는 방식
    > 
    > ⇒ 결국, 개발 중일 때에는 VM 상에서 코드를 실행시키고, VM은 그 코드를 JIT으로 컴파일함. 
    > 따라서, 조금 느리더라도 사용자가 쓴 코드를 화면에서 바로 피드백할 수 있음.
    > 
    > 배포 시에는 코드를 AOT으로 컴파일하여, 실제 기계어로 변환, 더 빠르게 처리 가능.
    > 
    > https://yeoulcoding.me/124
    > 
    > 
    > 💡 Dart 공식 문서
    > https://dart.dev/overview
    > 
    > ### Dart Native (machine code JIT and AOT)
    > 
    > During development, a fast developer cycle is critical for iteration. The Dart VM offers a just-in-time compiler (JIT) with incremental recompilation (enabling hot reload), live metrics collections (powering [DevTools](https://dart.dev/tools/dart-devtools)), and rich debugging support.
    > 
    > When apps are ready to be deployed to production—whether you’re publishing to an app store or deploying to a production backend—the Dart ahead-of-time (AOT) compiler can compile to native ARM or x64 machine code. Your AOT-compiled app launches with consistent, short startup time.
    > 
    > The AOT-compiled code runs inside an efficient Dart runtime that enforces the sound Dart type system and manages memory using fast object allocation and a [generational garbage collector](https://medium.com/flutter-io/flutter-dont-fear-the-garbage-collector-d69b3ff1ca30).
    > 
 
    > 
    > `Dart Web`
    > : Dart로 작성한 코드들을 JavaScript로 변환해주는 컴파일러
    > 

### Flutter 은 왜 Dart언어를 선택했는가?

1. JIT컴파일과 AOT컴파일이 둘 다 있다. 
→ 정확한 개발, 빠른 배포 가능.
2. flutter, Dart는 모두 Google이 만듦.
    
    → 구글은 flutter를 위해서 Dart를 최적화할 수 있음.
    → 다른 프레임워크에서는 볼 수 없는 flutter-dart만의 장점.
    

---