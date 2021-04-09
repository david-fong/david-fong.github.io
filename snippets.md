
# My Code Snippets


```sh
# Change indentation to use tabs for typescript files:
git ls-files | command grep -E '*.ts$' | awk '{print "unexpand --tabs=4 --first-only", $0, " > /tmp/e; mv /tmp/e ", $0}' | sh
```

```sh
# Make the TypeScript compiler use tabs for indentation.
# https://github.com/Microsoft/TypeScript/issues/4042
#sed -i 's/"    "/"\\t"/g' node_modules/typescript/lib/*.js
```

```sh
# get size of test folders in node_modules:
du -s $(find node_modules -type d -name test) | sort -n | vim -

# get packages in node_modules by size
du -s $(find node_modules/ -name 'package\.json' -printf "%h\n" | sort -u) | sort -n

# get direct subfolders of packages in node_modules that may not be source files
du -s $(find $(find node_modules/ -name 'package\.json' -printf "%h\n" | sort -u) -mindepth 1 -maxdepth 1 -type d | \grep -vE '(src|lib|dist|out|build|node_modules)$') | sort -n | vim -
```

```sh
# node args:
# --frozen-intrinsics \ # cjs >:(
# --experimental-policy='policy.json' \
# --disallow-code-generation-from-strings # >:( depd
```


```typescript
// fast large-json-serializable-object initialization
`JSON.parse('${jsonStr.replace(/[\\']/g, "\\$&")}')`
```
