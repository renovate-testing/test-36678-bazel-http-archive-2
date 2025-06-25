# 36678

Reproduction for [Renovate issue 36678](https://github.com/renovatebot/renovate/issues/36678).

## Current behavior

Bazel dependencies are not being updated correctly when they are grouped.

Example group updated (incorrect): https://github.com/alan-agius4/renovate-bazel-update-repro/pull/4/files

Example of ungrouped update (correct): https://github.com/alan-agius4/renovate-bazel-update-repro/pull/1/files

```diff
http_archive(
    name = "io_bazel_rules_webtesting",
    sha256 = "e9abb7658b6a129740c0b3ef6f5a2370864e102a5ba5ffca2cea565829ed825a",
-   urls = ["https://github.com/bazelbuild/rules_webtesting/releases/download/0.3.5/rules_webtesting.tar.gz"],
+   urls = ["https://github.com/bazelbuild/rules_webtesting/releases/download/0.4.1/rules_webtesting.tar.gz"],
)

http_archive(
    name = "aspect_rules_js",
    sha256 = "83e5af4d17385d1c3268c31ae217dbfc8525aa7bcf52508dc6864baffc8b9501",
    strip_prefix = "rules_js-2.3.7",
-   url = "https://github.com/aspect-build/rules_js/releases/download/v2.3.7/rules_js-v2.3.7.tar.gz",
+   url = "https://github.com/aspect-build/rules_js/releases/download/v2.3.8/rules_js-v2.3.7.tar.gz",
)
```


**Problems**:
 - The `sha256` and `strip_prefix` are not updated
 - Only the first portion of the URL is updated.


## Expected behavior
The `sha256`, `strip_prefix` and the urls are updated correctly.

## Link to the Renovate issue or Discussion
https://github.com/renovatebot/renovate/discussions/36678
