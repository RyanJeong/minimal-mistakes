---
title: "[WIP]A brief introduction to C++’s model for type- and resource-safety"
excerpt: ""

categories:
  - Computer
tags:
  - Programming
  - Cpp
  - WIP

use_math: true
toc: true 
toc_label: "Table of Contents" 
toc_icon: "cog"
toc_sticky: true 

last_modified_at: 2021-06-08 21:33:00 +0900
---

# Abstract
이 게시글은 모호한 포인터 사용을 제거해 메모리를 비롯한 자원을 안정적으로 사용할 수 있는 기법들에 대해 설명한다. 

# 0. Overview
이 게시글의 구성은 아래와 같다.

1. <i>The problem</i>: Resource leaks and memory corruption
2. <i>Constraints on any solution</i>: Generality, performance, and compatibility
3. <i>Memory safety</i>: Eliminate dangling pointers and access to deleted objects
4. <i>Resource safety</i>: Eliminate resource leaks
5. <i>Other problems</i>: Concurrency, casts, range errors, etc.
6. <i>Historical note</i>: Where did the solutions come from?

# 1. Introduction
아래 코드를 보자.
```c++
void use(FILE* p);

int some_code(int x)
{
    FILE* f = fopen("foo", "w");
    if (f==0) error("cannot open file");
    if (0<x) {
        use(f);
        // ... do a lot of work ...
    }
    else
        return -1;
    long pos = ftell(f);            // read through f
    // ...
    fprintf(f, "Die, die, die!\n"); // read and write through f
    fclose(f);
    return 0;
```
이 코드는 마치 아무런 문제가 없는 듯 하다. 그러나 함수 `use()`가 아래와 같다면 얘기는 달라진다. 
```c++
void use(FILE* p)
{
    // ...
    free(p);
    // ...
}
```
숙련된 C/C++ 개발자라면 이 간단한 예제의 문제점들을 빠르게 해결할 수 있을 것이다. 


# References
* [ISO,2014] <i>[Standard for Programming Language C++ (late draft 2014)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4296.pdf)</i>.
* [Hinnant,2002] H. Hinnant: <i>[A Proposal to Add Move Semantics Support to the C++ Language](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2002/n1377.htm)</i>. 
* [Stroustrup, 1982] B. Stroustrup: Classes: <i>[An Abstract Data Type Facility for the C Language](http://pascal-francis.inist.fr/vibad/index.php?action=getRecordDetail&idt=PASCAL83X0392703)</i>. Sigplan Notices, January, 1982. 
* [Stroustrup, 1994] B. Stroustrup: <i>[The Design and Evolution of C++](https://books.google.com/books?hl=ko&lr=&id=hS9mDwAAQBAJ&oi=fnd&pg=PT11&ots=xOie0n41Um&sig=oPFLDegNrReLn4NrG-jqMlUiOgc)</i>. Addison Wesley. ISBN 0-201-
54330-3. 1994.
* [Stroustrup,2015] B. Stroustrup and H. Sutter: <i>[C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines)</i>.
* [Sutter, 2015] H. Sutter and N. MacIntosh: <i>[Lifetime Safety: Preventing Leaks and Dangling](http://www.trucsazeb.re/CppCoreGuidelines/docs/Lifetimes%20I%20and%20II%20-%20v0.9.1.pdf)</i>.
* [Sutter, 2015] <i>[The Guideline Support Library](https://github.com/microsoft/gsl)</i>.


*** 

* References: 
    * Stroustrup, B., Sutter, H., & Dos Reis, G. (2015). <i>[A brief introduction to C++’s model for type-and resource-safety](https://stroustrup.com/resource-model.pdf)</i>.

