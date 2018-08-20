# Yaml

## Lint Configuration

The following configuration [for the tool `yamllint`](https://github.com/adrienverge/yamllint) will pick up the required styleguide:

```yaml
---
extends: default

rules:
  line-length:
    max: 120
  comments-indentation: disable
  braces:
    max-spaces-inside: 1
```

## Rules

### Braces

Braces should have a max of 1 space delimiting operators. For example, 

```yaml
object: { key1: 4, key2: 8 }
```

### File declaration

Files should start with the yaml file declaration:

```yaml
---
```

For example,

```yaml
---
foo: "bar"
```

This allows easy concatenation of multiple files together.

### Line Length

Lines should not exceed 120 characters where possible.

### Value quotation

String values should be quoted, but numeric or boolean values should not. For example,

```yaml
---
string: "bar"
number: 15

boolean: true
```

This allows being clear in the edge cases where content could be either a number or a string:

```yaml
---
string: "0438123456"
```

Or in cases where the content may include special characters:

```yaml
---
string: "string: string"
string: "true"
```
