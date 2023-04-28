---
layout: post
tags: [c]
---

```c
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
```