# Chronos

An Elixir library for handling dates. Chronos can be used in both production and testing to quickly
determine a date.

## Using

You can add Chronos as a dependency in your `mix.exs` file. Since it only requires Elixir and Erlang there are no other dependencies.

```
def deps do
  [ { :chronos, github: "nurugger07/chronos" } ]
end
```

Then run `mix deps.get` in the shell to fetch and compile the dependencies

To use the Chronos date features in your project you can import the Chronos module or call the functions directly.

```
defmodule YourModule do
  
  import Chronos

  def get_today do
    today
  end
end
```

or you can call functions without the import

```
defmodule YourModule do
  def get_today do
    Chronos.today
  end
end
```

There are a number of functions to help with dates including below are some of the current APIs:

```
# yesterday without a date assumes you want the day before the current date
# current date is {2012, 12, 21}
iex(1)> Chronos.yesterday
{2012, 12, 20}

iex(2)> Chronos.tomorrow
{2012, 12, 22}
```

You can find the date for days or weeks in the past or future:

```
iex(1)> Chronos.days_ago(3)
{2012, 12, 18}

iex(2)> Chronos.weeks_ago(5)
{2012, 11, 16}
```

## Use in Testing

Chronos is helpful in testing date based assertions because you can assign a default date or pass in a date to base the calculations on.

```
defmodule TestingModule do
  use Chronos, date: {2012, 12, 21}
end

```
If the date option is set the default date for all functions will be that date. 

## Coming Soon

* More date features like begining_of_week, end_of_week, 
* More Time features
* Time Date formatting options
