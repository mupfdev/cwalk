---
title: cwk_path_get_previous_segment
description: Moves to the previous segment.
---

_(since v1.0.0)_  
Moves to the previous segment.

## Description
```c
bool cwk_path_get_previous_segment(struct cwk_segment *segment);
```

This function moves the current segment to the previous segment. If the current segment is the first one, the submitted segment structure will stay unchanged and false is returned. The segment should be either initialized using **[[cwk_path_get_first_segment]]** or **[[cwk_path_get_last_segment]]**.

## Parameters
 * **segment**: The current segment which will be moved to the previous one.

## Return Vaue
Returns ``true`` if there is a segment before this one or ``false`` otherwise.

## Example
```c
#include <cwalk.h>
#include <stdio.h>
#include <stddef.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
  struct cwk_segment segment;

  if(!cwk_path_get_last_segment("/my/funny/test/path.txt", &segment)) {
    printf("Path doesn't have any segments.");
    return EXIT_FAILURE;
  }
  
  do {
    printf("Current segment is '%.*s'.\n", segment.size, segment.begin);
  } while(cwk_path_get_previous_segment(&segment));
  
  return EXIT_SUCCESS;
}
```

Ouput:
```
Current segment is 'path'.
Current segment is 'test'.
Current segment is 'funny'.
Current segment is 'my'.
```

## Changelog

| Version    | Description                                            |
|------------|--------------------------------------------------------|
| **v1.0.0** | The function is introduced.                            |