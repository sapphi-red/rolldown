## /out.js
### esbuild
```js
class Foo {
}
class Bar extends Foo {
  constructor() {
    super();
  }
}
```
### rolldown
```js


```
### diff
```diff
===================================================================
--- esbuild	/out.js
+++ rolldown	entry_js.mjs
@@ -1,6 +0,0 @@
-class Foo {}
-class Bar extends Foo {
-    constructor() {
-        super();
-    }
-}

```