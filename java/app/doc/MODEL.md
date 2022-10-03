# CSV files with a single record kind

Suppose that we have a CSV file with a single record type such as:

```
The Deer Hunter,1978
"Good Morning, Vietnam",1087
```

and that we need to write another CSV file with another single record type:

```
17c988ef040c39534fb79cb0c50469f8f714d354,The Deer Hunter,1978
3428f2055415b92e79178c19b61f3cf6899d4883,"Good Morning, Vietnam",1087
```

Then we will define corresponding `record` types:

```java
record Model (
    String id,
    String name,
    Year release
) {}

record InputText (
    String name,
    String release
) {}

record OutputText (
    String id,
    String name,
    String release
) {}
```

## Pseudo code - Reading

Given a row of CSV text from a CSV file, create a JSON object instance fron the row of CSV text:

```java
interface Reading
{
    static <T> T json_object(final String row) { ... }
}
```

Create an `InputText` instance from the JSON object:

```java
interface Reading
{
    static <T> InputText text(final T json_object) { ... }
}
```

Then you will have a `Model` instance from the `InputText` instance:

```java
interface Reading
{
    static Model model(final Text text) { ... }
}
```

## Pseudo code - Writing

Given a `Model` instance, create an `OutputText` instance:

```java
interface Writing
{
    static OutputText text(final Model model) { ... }
}
```

Create a JSON object instance from the `OutputText` instance:

```java
interface Writing
{
    static <T> T jsone_object(final OutputText text) { ... }
}
```

Finally, create a row of CSV text from the JSON object instance, and write the row of CSV text into another CSV file.

