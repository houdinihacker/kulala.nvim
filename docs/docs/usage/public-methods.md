# Public methods

All public methods are available via the `kulala` module.

### run

`require('kulala').run()` runs the current request.

### replay

`require('kulala').replay()` replays the last run request.

### scratchpad

`require('kulala').scratchpad()` opens the scratchpad.

The scratchpad is a (throwaway) buffer where you can write your requests.

It is useful for quick testing. It is useful for requests that you don't want to save.

It's default contents can be configured via the
[`scratchpad_default_contents`][scratchpad_default_contents] setup option.

### copy

`require('kulala').copy()` copies the current request
(as cURL command) to the clipboard.

### close

`require('kulala').close()` closes the kulala window and also the current buffer.

> (it will not close the current buffer, if it is not a `.http` or `.rest` file)

### toggle_view

`require('kulala').toggle_view()` toggles between
the `body` and `headers` view of the last run request.

Persists across restarts.

### search

`require('kulala').search()` searches for all `.http` and `.rest` files
in the current working directory.

It tries to load up a telescope prompt to select a file or fallback to using `vim.ui.select`.

### jump_prev

`require('kulala').jump_prev()` jumps to the previous request.

### jump_next

`require('kulala').jump_next()` jumps to the next request.

### download_graphql_schema

You can download the schema of a GraphQL server with:

```
:lua require("kulala").download_graphql_schema()
```

You need to have your cursor on a line with a GraphQL request.

The file will be downloaded to the the directory where the current file is located.

The filename will be `[http-file-name-without-extension].graphql-schema.json`.

This file can be used in conjunction with
the [kulala-cmp-graphql][kulala-cmp-graphql] plugin to
provide autocompletion and type checking.

### set_selected_env

> If you are using a dotenv (`.env`) file,
> this function has no effect.
>
> It is only for setting the selected environment of
> a `http-client.env.json` file.

`require('kulala').set_selected_env(env_key)`
sets the selected environment.

See: https://learn.microsoft.com/en-us/aspnet/core/test/http-files?view=aspnetcore-8.0#environment-files

If you omit the `env_key`,
it will try to load up a telescope prompt to select an environment or fallback to using `vim.ui.select`.

[scratchpad_default_contents]: ../getting-started/setup-options#scratchpad_default_contents
[kulala-cmp-graphql]: https://github.com/mistweaverco/kulala-cmp-graphql.nvim
