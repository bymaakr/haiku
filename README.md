# Haiku

Generates memorable names similar to Xaddress or Heroku. Supports custom
words, custom delimiters, and custom reducer functions.

## Installation

Add `haiku` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [{:haiku, "~> 0.3.0"}]
end
```

## Usage

```elixir
iex> Haiku.build
"quiet-morning-5933"

iex> Haiku.build(delimiter: '.')
"quiet.morning.5933"

iex> Haiku.build(range: 99)
"quiet-morning-45"

iex> Haiku.build(delimiter: '.', range: 99)
"quiet.morning.45"
```

## Configuration

In your `config.exs`:

```
config :haiku,
        delimiter: '.',
        range: 9999,
        adjectives: ~w(autumn hidden bitter misty),
        nouns: ~w(meadow sun glade bird)
        reducer_module: MyModule
        reducer_function: :custom_reduce
```

> Note that `reducer_function/4` must be public and has 4-arity, receiving a list of `args` with the following order: `[delimiter, adjective, noun, number]`, and must return a string.
> For example:
>
>
> ```
> def custom_reduce(delimiter, adjective, noun, number) do
>  "Poop"
> end
> ```

## Thanks

**haiku** © 2016+, Yos Riady. Released under the [MIT] License.<br>
Authored and maintained by Yos Riady with help from contributors ([list][contributors]).

> [yos.io](http://yos.io) &nbsp;&middot;&nbsp;
> GitHub [@yosriady](https://github.com/yosriady)

[MIT]: http://mit-license.org/
[contributors]: http://github.com/yosriady/haiku/contributors
