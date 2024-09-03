# Migrate pydantic

A few grit patterns that are being used to migrate from pydantic 1 to pydantic

**ATTENTION** the migrations are not guranateed to be error free. Feel free
to use, but it's your responsibility to check that your code works correctly.


## Usage

1. Follow instructions to install grit https://docs.grit.io/cli/quickstart

2. gh repo clone eyurtsev/migrate-pydantic

3. Use appropriate pattern for your code base:

```sh
grit apply [src]/.grit/patterns/extra_migrate.grit
```

```sh
grit apply [src]/.grit/patterns/to_pydantic_2.grit
```

```sh
grit apply [src]/.grit/patterns/model_before_rewrite.grit
```

```sh
grit apply [src]/.grit/patterns/model_after_rewrite.grit
```

Finally

```sh
grit apply --language python '`Self` where { add_import(source="typing_extensions", name="Self")}'
```


Some extra migrations can be done with bump-pydantic:

https://github.com/pydantic/bump-pydantic

```sh
bump-pydantic --disable BP007 .
```

This disables the root_validator → model_validator remapping which doesn’t work correctly in many cases.


