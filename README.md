[![build status](https://secure.travis-ci.org/STRML/JSXHint.png)](http://travis-ci.org/STRML/JSXHint)

#JSXHint
A wrapper around JSHint to allow linting of files containing JSX syntax.

Accepts the same input and JSHint and emits the same output. Switches sent to jsxhint
are forwarded on to jshint.

Glob parsing, ignores, and jshintrc parsing are all performed by jshint. 

##Rationale

This module is intended for use as part of 
[SublimeLinter-jsxhint](https://github.com/SublimeLinter/SublimeLinter-jsxhint),
but it can be used separately as a smart replacement for JSHint. It will automatically convert any file with 
the `jsx` extension or the `/** @jsx React.DOM */` docblock into JS using `react-tools`, then present
the file to JSHint for validation. 

`JSXHint` is safe to use as a drop-in replacement for `JSHint`, even when
JSX files are not present in a project.

`JSXHint` offers a simple workflow that accepts JSX files without modification.
Additionally, `JSXHint` actually lints the object definitions generated by the JSX compiler, allowing you to catch 
mistakes in your templates (such as undefined variables, syntax errors, and missing modules).

##Examples

```
# Basic globbing
jsxhint -c ./other-directory/.jshintrc src/foo/*.jsx
# Accepts stdin with '-'
jsxhint - < src/file.jsx
# Exclude files
jsxhint --exclude excludeme.jsx src/foo/*.jsx 
```

##Installation
`npm install -g jsxhint`

##Usage
```
Usage:
  jsxhint [OPTIONS] [ARGS]

Options: 
  -c, --config STRING    Custom configuration file
      --reporter STRING  Custom reporter (<PATH>|jslint|checkstyle)
      --exclude STRING   Exclude files matching the given filename pattern 
                         (same as .jsxhintignore) 
      --verbose          Show message codes
      --show-non-errors  Show additional data generated by jsxhint
  -e, --extra-ext STRING Comma-separated list of file extensions to use 
                         (default is .js) 
      --jslint-reporter  Use a jslint compatible reporter (DEPRECATED, use 
                         --reporter=jslint instead) 
      --checkstyle-reporter Use a CheckStyle compatible XML reporter 
                            (DEPRECATED, use --reporter=checkstyle 
                            instead) 
  -v, --version          Display the current version
  -h, --help             Display help and usage details
```
