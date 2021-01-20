# Style Guides

##### Table of Contents
* [Service Naming Rules](#service-naming-rules)
    - [Repository](#repository)
    - [C# Solutions](#c-sharp-solutions)
* [C# Code Style Guide](#c-sharp-code-style-guide)
    - [Class Structure](#class-structure)
    - [General](#general)
    - [Behavior](#behavior)
        + [C# Functional Extensions](c-sharp-functional-extensions)
    - [Statements](#statements)


<a name="service-naming-rules"/>

## 1. Service Naming Rules


<a name="repository"/>

### 1.1 Repository 

1.1.1 Web services _must_ be named after castles from [this article](https://en.wikipedia.org/wiki/Japan's_Top_100_Castles).\
_Example:_ [kanazawa](https://github.com/happy-travel/kanazawa)

1.1.2 Libraries _may_ be named after their role.\
_Examples:_ [data-formatters](https://github.com/happy-travel/data-formatters), or [diplomat](https://github.com/happy-travel/diplomat)

1.1.3 Connector implementation names _must_ start with supplier name and end with `-connector` postfix. 
_Examples:_ [netstorming-connector](https://github.com/happy-travel/netstorming-connector)


<a name="c-sharp-solutions"/>

### 1.2 C# Solutions

1.2.1 Keep following rules when name

- Assemblies:
```
HappyTravel.<SolutionName>.<ProjectName>
```
_Example:_ `HappyTravel.Edo.Api`

- Projects:
```
<SolutionName>.<ProjectName>
```

- Namespaces:
```
<SolutionName>.<ProjectName>
```

1.2.2 A project _must_ end on `Api`, if it contains API endpoints

1.2.3 A project _must_ end on `Client`, if if it contains an implementation of any API (i.e. a supplier one)

1.2.4 If a project contains separate DB-related logic, it usually calls `Data`


<a name="c-sharp-code-style-guide"/>

## 2. C# Code Style Guide


<a name="class-structure"/>

### 2.1 Class Structure

2.1.1 You _must_ keep elements of a class in order from public, to internal, to protected, and to private

2.1.2 Elements within the scope (methods, properties etc..) _should_ be sorted in alphabetical order

2.1.3 Scope modifiers _must_ be specified
```csharp
// bad
bool Method() {}

// good
private Method() {}
```

2.1.4 Local functions _may_ be placed at an execution order

2.1.5 Local functions _must_ be placed at the end of a method

2.1.6 Class structure:
| Class |
| ------------- |
| Constructors |
| Delegates |
| Methods and properties |
| Constants |
| Static fields and properties |
| Instance-level fields and properties |

\
_Example:_
```csharp
public class Class
{
    public Class(object dependency)
    {
        _dependency = dependency;
    }

    
    public object MethodA()
    {
        var result = BuildObject();
        return result;
    }

    
    public string MethodB()
        => Constant;


    private object BuildObject()
    {
        DoB();
        DoA();

        return new();


        bool DoB() {}

        bool DoA() {}
    }


    public const string Constant = "Constant";


    private readonly object _dependency;
}
```


<a name="general"/>

### 2.2 General

2.2.1 You _should_ call a returning value as `result`

2.2.2 Use nullable refs where possible

2.2.3 Use one blank line to separate method logical parts

2.2.4 Use two blank lines to separate methods from each other

2.2.5 Use 160 characters or less per line

2.2.6 Try to keep a class no more than 250–300 lines 

2.2.7 Use one method per line for fulent-style code
```csharp
// bad
_context.Entities.Where(_ => true)
    .Select(e => e).ToList();
  
// ok
_context.Entities.Where(_ => true)
    .Select(e => e)
    .ToList();

// good
_context.Entities   
    .Where(_ => true)
    .Select(e => e)
    .ToList();
```

2.2.8 Place an arrow at a new line when using expression syntax
```csharp
public static int GetValue() 
    => DoSomeCalculation();
```

2.2.9 Prefer expression syntax over statement body where possible

2.2.10 You _may_ use shorter names for small scopes, but keep readability first

2.2.11 Do not use `Async` postfix by default in method names, because most of our methods are asynchronous and the prefix adds extra visual noise


<a name="behavior"/>

### 2.3 Behavior

2.3.1 Methods _must not_ affect on variables from an outer scope (except local functions)
```csharp
// bad
bool value;

void SomeFunc() 
{ 
    value = true 
}
```


<a name="c-sharp-functional-extensions"/>

#### 2.3.2 C# Functional Extensions

2.3.2.1 Return a result instead of `Result.Success(result)` where possible
```csharp
// bad
Result<MoneyAmount> GetServicePrice(string referenceCode)
{
    var booking = GetBookings());
    if (booking is default)
        return Result.Failure<MoneyAmount>("Could not find booking");

    return Result.Success(new MoneyAmount(booking.TotalPrice, booking.Currency));
}

// good
Result<MoneyAmount> GetServicePrice(string referenceCode)
{
    var booking = GetBookings());
    if (booking is default)
        return Result.Failure<MoneyAmount>("Could not find booking");

    return new MoneyAmount(booking.TotalPrice, booking.Currency);
}
```


<a name="statements"/>

### 2.4 Statements

2.4.1 Use `is` and `is not` in conditional statements

2.4.2 Do not use braces over one line statements if code block contains one short line
```csharp
// bad
if (condition is true)
{
    DoAction();
}

// good
if (condition is true)
    DoAction();
```

2.4.3 Use braces for all, either for zero branches of a statement
```csharp
// bad
if (condition is true)
    DoAction();
else
{
    DoAnother();
}

// good
if (condition is true)
    DoAction();
else
    DoAnother();
```

2.4.4 Always use braces if a branch contains more than one line

2.4.5 Split conditions by _three_ lines when use ternary operator
```csharp
// bad
return x != y ? Result.Failure("Variable missmatch") : Result.Success();

// good
return x != y
    ? Result.Failure("Variable missmatch")
    : Result.Success();
```
