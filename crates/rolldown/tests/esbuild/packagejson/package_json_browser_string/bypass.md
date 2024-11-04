# Reason
1. different fs
2. different naming style
# Diff
## /Users/user/project/out.js
### esbuild
```js
// Users/user/project/node_modules/demo-pkg/browser.js
var require_browser = __commonJS({
  "Users/user/project/node_modules/demo-pkg/browser.js"(exports, module) {
    module.exports = function() {
      return 123;
    };
  }
});

// Users/user/project/src/entry.js
var import_demo_pkg = __toESM(require_browser());
console.log((0, import_demo_pkg.default)());
```
### rolldown
```js
import assert from "node:assert";


//#region node_modules/demo-pkg/browser.js
var require_browser = __commonJS({ "node_modules/demo-pkg/browser.js"(exports, module) {
	module.exports = function() {
		return 123;
	};
} });

//#endregion
//#region src/entry.js
var import_browser = __toESM(require_browser());
assert.equal((0, import_browser.default)(), 123);

//#endregion
```
### diff
```diff
===================================================================
--- esbuild	/Users/user/project/out.js
+++ rolldown	entry.js
@@ -1,9 +1,9 @@
 var require_browser = __commonJS({
-    "Users/user/project/node_modules/demo-pkg/browser.js"(exports, module) {
+    "node_modules/demo-pkg/browser.js"(exports, module) {
         module.exports = function () {
             return 123;
         };
     }
 });
-var import_demo_pkg = __toESM(require_browser());
-console.log((0, import_demo_pkg.default)());
+var import_browser = __toESM(require_browser());
+console.log((0, import_browser.default)());

```