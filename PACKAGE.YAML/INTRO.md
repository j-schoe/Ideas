# PACKAGE.YAML

```yaml
package.yaml: 1.0
using:
  some-plugin: ^1.1.0
scripts:
  print: echo "Hello"
dependencies:
  - link: https://example.com/some/package.yaml
    integrity: hl:123456789abcdefghi
artifacts:
  - name: some
    link: ./artifacts/something
    type: directory
```

```sh
$ package print
# Hello
```
