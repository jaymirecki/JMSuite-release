# JMSuite

## What's in this repository?
This repository houses a collection of helpful C# libraries, available in individual modules or combinations.

## Table of Contents
* [Modules](#modules)
    * [Full Suite](#all)
    * [Testing](#testing)
* [How to interact with the project](#interacting)

<a name="modules"></a>
# Modules

<a name="all"></a>
## Full Suite
v1.0.0-beta.1 <br>
Filename: jmsuite.dll <br>
Contains all the JMSuite Modules wrapped in one neat little library.

<a name="testing"></a>
## Testing
v1.0.0-beta.1<br>
Filename: jmsuite-testing.dll<br>
[Development Repository](https://github.com/jaymirecki/JMSuite-Testing-Module)
### Documentation
<b>CheckExpect()</b><br>
Parameters: string testName, 
            string testInput(), 
            string expectedOutput <br>
Returns: void <br>
Runs testInput and compares the result with expectedOutput.

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
    JMSuite.Testing.ReportTestResults();
}
string ExampleTestFunction() {
    return "Foo";
}
```

### Change Log
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
