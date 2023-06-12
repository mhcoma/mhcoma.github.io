---
layout: post
tags: [c]
---

```c
#include <stdio.h>

typedef enum tu_foo_type_enum tu_foo_type;
typedef struct tu_foo_struct tu_foo;

enum tu_foo_type_enum {
	TU_FOO_INT,
	TU_FOO_STR
};

struct tu_foo_struct {
	tu_foo_type type;
	union {
		int i;
		char* str;
	};
};

void print_tu_foo(tu_foo tf) {
	switch (tf.type) {
		case TU_FOO_INT:
			printf("%d\n", tf.i);
		break;
		case TU_FOO_STR:
			printf("%s\n", tf.str);
		break;
	}
}

int main(void) {
	tu_foo a = {0, };
	tu_foo b = {0, };

	a.type = TU_FOO_INT;
	a.i = 100;

	b.type = TU_FOO_STR;
	b.str = "asdf";

	print_tu_foo(a);
	print_tu_foo(b);

	return 0;
}
```

타입을 구분할 `tu_foo_type`은 정수이므로 `char` 등의 1바이트 정수를 사용해도 좋다. 