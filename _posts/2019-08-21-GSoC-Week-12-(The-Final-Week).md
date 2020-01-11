---
layout: post
title: 'GSoC 2019: Week 12 (The Final Week)'
comments: true
tags: [gsoc, sympy]
categories: [open-source]
seo:
  date_modified: 2020-01-11 18:06:59 +0530
---
The last week of coding period is officially over. A summary of the work done during this week is:

* [#17379](https://github.com/sympy/sympy/pull/17379) is now complete and currently under review. I will try to get it merged within this week.
* [#17392](https://github.com/sympy/sympy/pull/17392) still needs work. I will try to put a closure to this by the end of week.
* [#17440](https://github.com/sympy/sympy/pull/17440) was started. It attempts to add a powerful (but optional) SAT solving engine to SymPy ([pycosat](https://pypi.org/project/pycosat/)). The performance gain for SAT solver is also subtle here: Using this
```
from sympy import *
from sympy.abc import x
r = random_poly(x, 100, -100, 100)
ans = ask(Q.positive(r), Q.positive(x))
```
The performance is like
```
# In master
   |  `- 0.631 check_satisfiability  sympy/assumptions/satask.py:30
   |     `- 0.607 satisfiable  sympy/logic/inference.py:38
   |        `- 0.607 dpll_satisfiable  sympy/logic/algorithms/dpll2.py:21
# With pycosat
   |  `- 0.122 check_satisfiability  sympy/assumptions/satask.py:30
   |     `- 0.098 satisfiable  sympy/logic/inference.py:39
   |        `- 0.096 pycosat_satisfiable  sympy/logic/algorithms/pycosat_wrapper.py:11
```
It is finished and under review now.

Also, with the end of GSoC 2019, final evaluations have started. I will be writing a final report to the whole project by the end of this week.

So far it has been a great and enriching experience for me. It was my first attempt at GSoC and I am lucky to get such an exposure. I acknowledge that I started with an abstract idea of the project but I now understand both the need and the code of `New Assumptions` pretty well (thanks to [Aaron](https://github.com/asmeurer) who wrote the most of it). The system is still in its early phases and needs a lot more work. I am happy to be a part of it and I will be available to work on it.

This is the last weekly report but I will still be contributing to SymPy and open source in general. I will try to write more of such experiences through this portal. Till then, Good bye and thank you!
