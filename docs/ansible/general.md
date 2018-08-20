# General Styleguide

## Verifying style

A `.yamllint` file has been added to the git repository to allow easy linting. It can be consumed with the
[yamllint tool](https://github.com/adrienverge/yamllint), found in most OS package repositories.

Additionally, an `.arclint`  file has been created to aggregate the lints in a pre-commit hook as defined
in a [post written by Andrew Howden](https://medium.com/@andrewhowdencom/i-successfully-fake-being-a-tidy-developer-with-this-one-weird-trick-okay-git-hooks-733573b1c679).

## Yaml files

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

### Value quotation.

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

