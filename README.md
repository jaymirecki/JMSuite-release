# JMSuite

## What's in this repository?
This repository houses a collection of helpful C# libraries, available in individual modules or combinations.

## Table of Contents
* [Modules](#modules)
    * [Full Suite](#all)
    * [Collections.Dictionary](#dictionary)
    * [Collections.Graph](#graph)
    * [Testing](#testing)
* [How to interact with the project](#interacting)

<a name="modules"></a>
# Modules

<a name="all"></a>
## Full Suite
v1.0.0-beta.2 <br>
Filename: jmsuite.dll <br>
Contains all the JMSuite Modules wrapped in one neat little library.

<a name="dictionary"></a>
## Collections.Dictionary
v1.0.0-beta.1<br>
Filename: JMSuite.Collections.Dictionary.dll<br>
<!-- [Development Repository](https://github.com/jaymirecki/JMSuite-Testing-Module) -->
The `Dictionary` class is identical to the built-in `System.Collections.Generic.Dictionary<TKey, TValue>`, except the JMSuite version implements `IXmlSerializable`. It has no additional methods other than those required for the interface.

### Documentation
<b>ReportTestResults()</b><br>
Parameters: none <br>
Returns: void <br>
Reports the results of all tests to the console.

### Change Log
v1.0.0-beta.1
* Untested build

<a name="graph"></a>
## Collections.Graph
v1.0.0-beta.1<br>
Filename: JMSuite.Collections.Dictionary.dll<br>
<!-- [Development Repository](https://github.com/jaymirecki/JMSuite-Testing-Module) -->
The `Graph<T>` class implements a weighted directed graph that supports distance and path finding. It implements `ICollection<T>` and `IEnumerable<T>`.

### Documentation
<b>Count</b><br>
Type: int<br>
An integer representing the number of vertices in the graph.

<b>Edges</b><br>
Type: List<Dictionary.Edge><br>
A list of all the edges.

<b>IsReadOnly</b><br>
Type: bool<br>
A value representing whether the graph is read only.

<b>Values</b><br>
Type: List<T><br>
A list of all the vertex values.

<b>Graph\<T\>()</b><br>
Parameters: none<br>
Returns: Graph\<T\><br>
Constructor for the class.

<b>Add(T value)</b><br>
Parameters: T value<br>
Returns: void<br>
Adds the provided value as a vertex to the graph. Will not add the value if it already exists in the graph. Functionally equivalent to `AddVertex`.

<b>Clear()</b><br>
Parameters: none<br>
Returns: void<br>
Clears the graph.

<b>Remove(T value)</b><br>
Parameters: T value<br>
Returns: bool<br>
Removes the provided value from the graph. Returns true if the value was found, false if the value did not exist in the graph.

<b>AddVertex(T value)</b><br>
Parameters: T value<br>
Returns: void<br>
Adds the provided value as a vertex to the graph. Will not add the value if it already exists in the graph. Functionally equivalent to `Add`.

<b>CopyTo(T[ ] array, int arrayIndex)</b><br>
Parameters: T[ ] array,
            int arrayIndex<br>
Returns: void<br>
Copies the vertex values to the provided array, starting at the provided index.

<b>AddEdge(T origin, T destination, int weight)</b><br>
Parameters: T origin,
            T destination,
            int weight<br>
Returns: void<br>
Adds an edge of the provided weight between the provided origin and destination. Raises an exception if either the origin or the destination is not in the graph. For a safe version, see `TryAddEdge`.

<b>AddEdge(T origin, T destination, int weight)</b><br>
Parameters: T origin,
            T destination,
            int weight<br>
Returns: bool<br>
Adds an edge of the provided weight between the provided origin and destination. Returns true if both the origin and the destination are in the graph, returns false otherwise.

<b>Contains(T value)</b><br>
Parameters: T value<br>
Returns: bool<br>
Returns true if the provided value is in the graph, false otherwise.

<b>TryDistanceTo(T start, T end, out int distance)</b><br>
Parameters: T start,
            T end,
            out int distance<br>
Returns: bool<br>
Finds the distance between the provided start and end values. Returns true if there exists a path between the start and end values, returns false otherwise.

<b>TryDistanceTo(T start, T end, out int distance, Func\<T, bool\> predicate)</b><br>
Parameters: T start,
            T end,
            out int distance,
            Func\<T, bool\> predicate<br>
Returns: bool<br>
Finds the distance between the provided start and end values, traversing only through values that satisfy the predicate. Returns true if there exists a path between the start and end values that satisfies the predicate, returns false otherwise.

<b>TryPathTo(T start, T end, out List\<T\> path)</b><br>
Parameters: T start,
            T end,
            out List\<T\> path<br>
Returns: bool<br>
Finds the shortest path between the provided start and end values. Returns true if there exists a path between the start and end values, returns false otherwise.

<b>TryPathTo(T start, T end, out List\<T\> path, Func\<T, bool\> predicate)</b><br>
Parameters: T start,
            T end,
            out List\<T\> path,
            Func\<T, bool\> predicate<br>
Returns: bool<br>
Finds the shortest path between the provided start and end values, traversing only through values that satisfy the predicate. Returns true if there exists a path between the start and end values that satisfies the predicate, returns false otherwise.

<b>DistanceTo(T start, T end)</b><br>
Parameters: T start,
            T end<br>
Returns: int<br>
Returns the distance between the provided start and end values. Raises and exception if there is not a path between the start and end vertices.

<b>TryConnectedVertices(T start, out Dictionary\<T, int\> connectedVertices)</b><br>
Parameters: T start,
            out Dictionary\<T, int\> connectedVertices<br>
Returns: bool<br>
Finds all the vertices reachable from the provided start value, and includes the distance of each vertex from the start vertex. Returns true if the start value is in the graph, returns false otherwise.

<b>TryConnectedVertices(T start, out Dictionary\<T, int\> connectedVertices, Func\<T, bool\> predicate)</b><br>
Parameters: T start,
            out Dictionary\<T, int\> connectedVertices,
            Func\<T, bool\> predicate<br>
Returns: bool<br>
Finds all the vertices reachable from the provided start value, traversing only through values that satisfy the predicate, and includes the distance of each vertex from the start vertex. Returns true if the start value is in the graph, returns false otherwise.

### Example Usage
```
using JMSuite.Collections.Graph;
...
void Foo() {
    Graph<int> g = new Graph<int>();
    g.Add(1);
    g.Add(2);
    g.Add(3);
    g.Add(4);

    g.AddEdge(1, 2, 2);
    g.AddEdge(1, 3, 2);
    g.AddEdge(1, 4, 3);
    g.AddEdge(2, 4, 2);
    g.AddEdge(3, 4, 2);

    int distance;
    g.TryDistanceTo(1, 4, out distance);
}
```

### Change Log
v1.0.0-beta.1
* First build

<a name="testing"></a>
## Testing
v1.0.0-beta.1<br>
Filename: JMSuite.Testing.dll<br>
[Development Repository](https://github.com/jaymirecki/JMSuite-Testing-Module)
### Documentation
<b>CheckExpect()</b><br>
Parameters: string testName, 
            string testInput(), 
            string expectedOutput <br>
Returns: void <br>
Runs testInput and compares the result with expectedOutput.

<b>CheckExpectTimed()</b><br>
Parameters: string testName, 
            string testInput(), 
            string expectedOutput <br>
Returns: void <br>
Runs testInput, compares the result with expectedOutput, and reports the time for the test to run.

<b>ReportTestResults()</b><br>
Parameters: none <br>
Returns: void <br>
Reports the results of all tests to the console.

### Example Usage
```
using JMSuite;
...
void Foo() {
    JMSuite.Testing.CheckExpect("Example Test", 
                                ExampleTestFunction,
                                "Foo");
    JMSuite.Testing.CheckExpectTimed("Example Test Timed", ExampleTestFunction, "Foo");
    JMSuite.Testing.ReportTestResults();
}
string ExampleTestFunction() {
    return "Foo";
}
```

### Change Log
v1.0.0-beta.2
* Ability to time a CheckExpect

v1.0.0-beta.1
* Ability to CheckExpect and report test results at then end of the testing program.

<a name="interacting"></a>
# How to interact with the project
## Getting Started

To compile your code with our libraries: 
```
csc.exe yourcode.cs -reference:ourlibrary.dll
```

### Prerequisites

Use the csc compiler, likely located here (if using the LSW for Ubuntu)

```
/mnt/c/Windows/Microsoft.NET/Framework/vX.X/csc.exe
```

## To contribute
Visit our development repositories (linked at each submodule)

## Built With

* [Microsoft .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework-runtime/net472) - To compile and run on Windows
* [Mono](https://www.mono-project.com/download/stable/) - To compile and run on Linux
* [Visual Studio Code](https://code.visualstudio.com/) - The editor used

## Authors

* Jarett (Jay) Mirecki
