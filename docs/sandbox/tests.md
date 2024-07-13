# titre

## sub

```sh


```

## table

title | title | title
-|-|-
content | sub | sub
content | sub | sub
content | sub | sub

### git graph

```mermaid
gitGraph
  commit id: "One"
  commit id: "Two"
  commit id: "Three"
  branch develop
  checkout main
  commit id: "4" type: REVERSE tag: "RC_1"
  checkout develop
  commit id: "Four"
  commit id: "Five"
  checkout main
  commit id: "Six"
```

## code blocks

``` py title="bubble_sort.py" linenums="1"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```