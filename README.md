# `callstack()` (legacy)
v1 version of [callstack](https://github.com/SALZKARTOFFEEEL/callstack).

I encourage you to **not** use this function if you can use [the v2 version](https://github.com/SALZKARTOFFEEEL/callstack).

## Definition
```autohotkey
stack := callstack(limit := -1)
```
* `limit` – _integer_: The amount of callstack entries to return.
  * If `limit` is positive or 0, `stack.length()` equals `limit`.
* `stack` – _array_ of _objects_: The current callstack (including the call to `callstack()` itself).
  * Each entry represents one entry in the callstack.
  * Each entry is an object. Each object has three keys:
    * `file` – _string_: The **full path of the file** the entry of the callstack points to.
    * `line` – _integer_: The **line number of the line** the entry of the callstack points to.
    * `func` – _string_: The **name of the function** the entry of the callstack points to.

## Example
```autohotkey
test1() {
  test2()
}
test2() {
  test3()
}
test3() {
  callstack()
}

strStack := ""
for _, entry in test1() {
  strStack .= "Line: " entry["line"] "`nFile: " entry["file"] "`nFunc: " entry["func"] "`n----`n"
}
msgbox, % strStack
```
