# eslint-plugin-import-order-all

This is a fork of [eslint-plugin-import](https://www.npmjs.com/package/eslint-plugin-import).

**For all rule documentation and funding options please see that original package.**

This fork enables auto-fix sorting of imports even when there is an unassigned import in the midst. This change fails lots of tests and I haven't bothered to fix them all, so **be warned**. If you have issues, just use the original package linked above.

# What this changes

The following code

```
import 'internal/module';
import 'module'; // completely ignored, even though it is external
import 'internal/module';
```

will now be auto-fixed into this:

```
import 'internal/module';
import 'internal/module';
import 'module';
```

(The relative ordering between `internal/module` and `module` may differ depending on your `order` rule settings.)

To use this you must add the `import-order-all` plugin to your eslintrc instead of `import`. Also, all rules must use the `import-order-all/` path instead of `import/`.