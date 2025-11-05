# Note about this readme

This is just temporary to show what I tried locally to test the new feature.
It might not work on any machinen because it relies on packages installed locally.

## Testing

When we provide only
```py
extra_enabled_features = [":foo"],
```
then
```py
bazel build //examples/inject_extra_features/...
```
should fail with 
```sh
error: unrecognized command-line option '-foo'
```
and pass with
```py
bazel build //examples/inject_extra_features/... --features=-foo
```

When we provide only
```py
extra_known_features = [":foo"],
```
then
```py
bazel build //examples/inject_extra_features/...
```
should pass but
```py
bazel build //examples/inject_extra_features/... --features=foo
```
fail with
```sh
error: unrecognized command-line option '-foo'
```

When we provide both
```py
extra_enabled_features = [":foo"],
extra_known_features = [":foo"],
```
then
```py
bazel build //examples/inject_extra_features/... --features=-foo
```
should pass but
```py
bazel build //examples/inject_extra_features/...
```
fail with
```sh
error: unrecognized command-line option '-foo'
```
