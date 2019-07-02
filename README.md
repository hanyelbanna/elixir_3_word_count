word_count.exs

```elixir
# in exs file you no need a module and no compilation
# the file will execute line by line like Ruby

filename =
  IO.gets("File to count the words from: ")
  |> String.trim()

# "!" to throw error if can not read the file
words =
  File.read!(filename)
  # String.split with one arrgument will split on space
  # ~r{\w} regular expression for one Word
  # ~r{\n} regular expression for new line
  # ~r{\\n} regular expression for "\n" -> first \ for scape second one
  # ~r{\w+} regular expression for one Word or more
  # ~r{[^\w]} regular expression for Not a Word
  # ~r{[^\w']} regular expression for Not a Word and not a apostrof
  # ~r{[^\w]+} regular expression for Not a Word (one or more)
  # ~r{(\n|\w)} regular expression for one Word OR one new line
  # ~r{(\n|\w)+} regular expression for (one Word OR one new line) or more
  |> String.split(~r{(\\n|[^\w'])+})
  # return new list with filter condition # to remove "" from the list
  |> Enum.filter(fn x -> x != "" end)

words
# return number of items in the list
|> Enum.count()
|> IO.puts()

```



```
To run exs file:

from terminal:
$ elixir word_count.exs

from iex:
iex> Code.load_file "word_count.exs"

```



vsc note:

```
Command + 1  -> switch cursore to code screen

Command + d  -> select the same word again in the file
```

