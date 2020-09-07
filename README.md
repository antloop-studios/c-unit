<h1 align=center>UNIT</h1>

Trivial C unit testing library

## Usage

Input:

```c
// main.c

#include "unit.h"

// all tests must have signature:
//   void name();

void test1() {
     test_assert(1 == 1);
     test_ok();
}

void test2() {
     test_assert(2 == 1);
     test_ok();
}

int main() {
     test_run_all(
         &test1,
         &test2,
     );
}
```

Output:

```
 OK  test1
 KO  test2[14]: 2 == 1
DONE
```

## Methods

```c
#define test_assert(condition)
```

Assert a condition that must be valid, or return from test. If assertion fails, a message is printed with test name, the location of the assert and the failed condition.

```c
#define test_ok()
```

Prints a success message containing the test name and returns.

```c
#define test_run_all(...)
```

Runs all given tests, takes a list of `void (*test)()` function pointers to tests.
