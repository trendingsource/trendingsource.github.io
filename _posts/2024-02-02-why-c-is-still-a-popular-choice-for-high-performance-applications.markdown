---
layout: post
title: "Why C is Still a Popular Choice for High Performance Applications"
date:   2024-02-02 08:45:46 +0000
categories: "Redis"
excerpt_image: https://scanlibs.com/wp-content/uploads/high-performance-applications-c.jpg
image: https://scanlibs.com/wp-content/uploads/high-performance-applications-c.jpg
---

Redis, one of the most popular open source databases, is written in C instead of C++. But why would its creators choose C over C++? Let's take a deeper look at some key reasons.
### Simplicity and Minimalism
At around 2,000 lines of code, Redis is an impressively small yet powerful piece of software. This minimalism stems in large part from C's simplicity as a language. **Without object-oriented abstractions** or other higher-level features, C encourages writing code that does one thing and does it well. For performance-critical applications, simplicity allows the programmer greater control over memory, performance optimizations, and low-level system interactions. 
Complex features found in C++ like templates can also **increase build times and binary size**. With Redis needing to be highly portable, its creators valued the terse and straightforward nature of C. Overall C lends itself better than C++ to writing code with minimal complexity.

![](https://cdn.educba.com/academy/wp-content/uploads/2019/11/features-of-c.png)
### Portability 
Written in ANSI C99, Redis can compile on virtually any system with a C compiler. Its lack of external dependencies means building from source is straightforward. In contrast, C++ portability relies on standard libraries being available across platforms. By choosing C, Redis ensures maximum compatibility with different operating systems and processor architectures important for wide adoption.
### Faster Development
For performance-oriented projects like Redis where nanoseconds matter, optimizations require careful consideration. C supports this process through its raw access to memory layouts and processor instructions. Without C++'s abstractions, developers can more directly reason about how their code will execute. This facilitates rapid prototyping, experimentation, and refinement of algorithms **critical for high-performance computing**.
### Easier Refactoring 
Evolving C++ code over time can introduce unintended complexity, as class hierarchies evolve and refactoring breaks dependencies. Low-level C code is more self-contained and modular, avoiding these "knots." Refactoring C is simpler without worrying about breaking class relationships. For long-lived projects like Redis, this ease of upgrading and refining code over decades outweighs potential C++ performance benefits.
### Fewer Resources 
Written without advanced C++ features, Redis requires far less memory and processing power. For use cases like embedded or constrained systems where resources matter greatly, C provides an advantage. Its lack of abstractions also means Redis remains a small and lightweight database even after 20+ years of evolution and new features.
### Aversion to Complexity
As performance-oriented developers, Redis' creators favored pragmatic simplicity over theoretical benefits. After experimenting, they found C++ encouraged more complex designs that did little to improve performance but increased debugging headaches. C better suited their priority of achieving excellent speed through clear and direct implementation rather than abstraction.
Overall, while C++ can offer theoretical gains, for projects like Redis practical concerns of portability, minimalism, rapid iteration, and long-term maintenance outweigh these. By choosing C, its developers optimized for qualities like simplicity, self-containment, and minimizing complexity they valued most for their high-performance use case. Two decades later, Redis remains popular in large part due to these design decisions made early on.
 ![Why C is Still a Popular Choice for High Performance Applications](https://scanlibs.com/wp-content/uploads/high-performance-applications-c.jpg)