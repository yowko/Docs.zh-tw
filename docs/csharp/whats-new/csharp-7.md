# C# 7 中的新增功能

在 C# 7 ，提供以下功能：
* [ Out 參數修飾詞 ( Out variables )](#out參數修飾詞)
    - You can declare `out` values inline as arguments to the method where they are used.
* [ Tuple 方法 ( Tuples )](#tuple方法)
    - You can create lightweight, unnamed types that contain multiple public fields. Compilers and IDE tools understand the semantics of these types.
* [ Discard 暫存變數 ( Discards )](#暫存變數)
    - Discards are temporary, write-only variables used in assignments when you don't care about the value assigned. They are particularly useful when deconstructing tuples and user-defined types, as well as when calling methods with `out` parameters.
* [模式比對 ( Pattern Matching )](#模式比對)
    - You can create branching logic based on arbitrary types and values of the members of those types.
* [Ref 擲回傳址參數修飾詞 ( ref locals and returns )](#ref擲回傳址參數修飾詞)
    - Method arguments and local variables can be references to other storage.
* [區域函式 ( Local functions )](#區域函式)
    - You can nest functions inside other functions to limit their scope and visibility.
* [表示式本體成員 ( More expression-bodied members )](#表示式本體成員)
    - The list of members that can be authored using expressions has grown.
* [Throw 例外運算子參數修飾詞 ( throw Expressions )](#Throw例外運算子參數修飾詞)
    - You can throw exceptions in code constructs that previously were not allowed because `throw` was a statement. 
* [非同步方法的傳回型別 ( Generalized async return types )](#非同步方法的傳回型別) 
    - Methods declared with the `async` modifier can return other types in addition to `Task` and `Task<T>`.
* [小數位數語法 ( Numeric literal syntax improvements )](#小數位數語法)
    - New tokens improve readability for numeric constants.

The remainder of this topic discusses each of the features. For each feature,
you'll learn the reasoning behind it. You'll learn the syntax. You'll see
some sample scenarios where using the new feature will make you more 
productive as a developer. 

## out參數修飾詞

本方法提供 `out` 參數修飾詞改進。

過往進行變數初始化，需要使用 `out` 參數修飾詞定義變數性質時，您必須個別定義變數及執行方法 ( method ) 中 `out` 參數修飾詞：

```csharp
int numericResult;
if (int.TryParse(input, out numericResult))
    WriteLine(numericResult);
else
    WriteLine("Could not parse input");
```

現在您可以直接於執行方法當中的變數使用 `out` 參數修飾詞：

```csharp
if (int.TryParse(input, out int result))
    WriteLine(result);
else
    WriteLine("Could not parse input");
```

或許您可能希望如上述明確指名使用 `out` 參數修飾詞變數類型，然而語法亦可支援使用 `var` 隱含類型區域變數定義的變數：

```csharp
if (int.TryParse(input, out var answer))
    WriteLine(answer);
else
    WriteLine("Could not parse input");
```

使用 `out` 參數修飾詞的變數命名將可以獲得以下便利之處：

* 程式碼將可以更容易閱讀理解。
    - 當下使用 `out` 參數修飾詞時候，您不需要將變數個別獨立出來定義屬性。
* 無需為區域變數指定初始值。
    - 過往使用 `out` 參數修飾詞時候，無法指定選用性，您必需明確指定區域變數值 ( Value ) 。
    
本方法最常見使用情境為 `Try` 陳述式 ( try-catch-finally )  ，在使用此陳述式時，一個方法將擲回執行成功或執行失敗狀態，
若使用 `out` 參數修飾詞修飾擲回狀態，將可確保擲回狀態正確輸出。

When using the `out` variable declaration, the declared variable "leaks" into the outer scope of the if statement. This allows you to use the variable afterwards:

```csharp
if (!int.TryParse(input, out int result))
{    
    return null;
}

return result;
```

## Tuples

> [!NOTE]
> The new tuples features require the <xref:System.ValueTuple> types.
> You must add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) in order to use it
> on platforms that do not include the types.
>
> This is similar to other language features that rely on types
> delivered in the framework. Example include `async` and `await`
> relying on the `INotifyCompletion` interface, and LINQ relying
> on `IEnumerable<T>`. However, the delivery mechanism is changing
> as .NET is becoming more platform independent. The .NET Framework
> may not always ship on the same cadence as the language compiler. When new language
> features rely on new types, those types will be available as NuGet packages when
> the language features ship. As these new types get added to the .NET Standard
> API and delivered as part of the framework, the NuGet package requirement will
> be removed.

本方法提供組件 <xref:System.ValueTuple> 改進。

C# 提供許多解釋結構 ( structure ) 方法可以應用在您所設計程式結構上，然而在許多時候您可能需要以最小成本花費來設計程式
並能同時包括個別元素結構，因此 C# 為了能提供更好的解釋結構，提供了 *tuple* 類別能以更輕便的方式來表示多個個別元素結構。

需要注意本方法所解釋的個別元素結構並未經過驗證，您無法為個別定義定義方法 ( methods ) 。

> [!NOTE]
> Tuple 僅止於 C# 7， 因為效率不佳原因已經沒有語言支援。 
> 換句話說 Tuple 僅能被命名為`Item1`、`Item2` 等無效益之命名方式，
> 對此 C# 7 引進新的支援方式，可讓語意的 tuple 使用新的、更有效率的 *tuple* 類型的欄位名稱。

您可以建立一個 *tuple* 類別來描述個別元素結構。

```csharp
var letters = ("a", "b");
```

*tuple* 類別將會建立其成員 tuple `Item1` 和 `Item2` ，您可以使用相同Tuple建立方式變更變數建立
tuple，當中提供語意到每個 tuple 的成員名稱的語法：

```csharp
(string Alpha, string Beta) namedLetters = ("a", "b");
```

`namedLetters` 的 *tuple* 類別包含稱 Alpha 和 Beta 欄位。這些名稱僅止於編譯階段存在，
並且不會保留例如時檢查在執行階段使用反映的 tuple。

在 Tuple 指派中，您可以在指派的右邊，指定欄位的名稱︰

```csharp
var alphabetStart = (Alpha: "a", Beta: "b");
```

您也可以為指派的變數左側和右側指定欄位名稱：

```csharp
(string First, string Second) firstLetters = (Alpha: "a", Beta: "b");
```

> [!NOTE]
> 前述列會產生警告 `CS8123`，告訴您指派右邊的名稱 `Alpha` 和 `Beta` 會被忽略，因為它們與左邊的
> 名稱 `First` 和 `Second` 發生衝突。

上述範例說明宣告 Tuple 的基本語法。 Tuple 適合使用於 `private` 和 `internal` 方法的傳回型別
。 Tuple 提供簡易的語法可讓方法傳回多個離散值︰可以節省了撰寫定義傳回型別之 `class` 或 `struct` 
的工作。 不需要建立新的類型。

建立 Tuple 更有效率且更具生產力。 它是一個更簡單的輕量語法，可定義複數個值的資料結構。 下列範例
方法會傳回在一個整數序列中找到的最小和最大值︰

```csharp
private static (int Max, int Min) Range(IEnumerable<int> numbers)
{
    int min = int.MaxValue;
    int max = int.MinValue;
    foreach(var n in numbers)
    {
        min = (n < min) ? n : min;
        max = (n > max) ? n : max;
    }
    return (max, min);
}
```

使用 Tuple 可提供以下數個優點︰

* 能節省撰寫定義傳回型別之 `class` 或 `struct` 的工作。
* 無需要建立新的類型。
* 語言增強功能讓您無需呼叫  <xref:System.Tuple.Create``1(``0)> 方法。

方法的宣告提供所傳回 *tuple*  類別的名稱。 當您呼叫的方法時，傳回值是一個 Tuple，其欄位為 `Max` 和`Min`：

```csharp
var range = Range(numbers);
```

有時候您可能會需要使用移除封裝方式從方法傳回 Tuple 成員。 您可以藉由為 Tuple 中的每個值宣告不同
變數來完成。 而此移除封裝過程稱為「解構」Tuple：

```csharp
(int max, int min) = Range(numbers);
```

您也可以在 .NET 中為任何類型提供類似的解構。 這是藉由新增一個名稱為 `Deconstruct` 方法作為類別的成員而達成。
`Deconstruct` 方法將會為您想要擷取的每個屬性提供一組 `out` 引數。 請參考以下 `Point` 類別範例，它會提供
deconstructor 方法來擷取 `X` 和 `Y` 座標︰

```csharp
public class Point
{
    public Point(double x, double y)
    {
        this.X = x;
        this.Y = y;
    }

    public double X { get; }
    public double Y { get; }

    public void Deconstruct(out double x, out double y)
    {
        x = this.X;
        y = this.Y;
    }
}
```

您可以藉由指派 *tuples* 類別至 `Point` 方式來擷取個別的欄位：

```csharp
var p = new Point(3.14, 2.71);
(double X, double Y) = p;
```

您不受限於 `Deconstruct` 方法中所定義的名稱。 您可以在指派過程中擷取變數為其重新命名︰

```csharp
(double horizontalDistance, double verticalDistance) = p;
```

您可以在 [tuples topic](../tuples.md)主題中深入了解 Tuple。

## Discards

Often when deconstructing a tuple or calling a method with `out` parameters, you're forced to define a variable whose value you don't care about and don't intend to use. C# adds support for *discards* to handle this scenario. A discard is a write-only variable whose name is `_` (the underscore character); you can assign all of the values that you intend to discard to the single variable. A discard is like an unassigned variable; apart from the assignment statement, the discard can't be used in code.

Discards are supported in the following scenarios:

* When deconstructing tuples or user-defined types.

* When calling methods with [out](../language-reference/keywords/out.md) parameters.

* In a pattern matching operation with the [is](../language-reference/keywords/is.md) and [switch](../language-reference/keywords/switch.md) statements.

* As a standalone identifier when you want to explicitly identify the value of an assignment as a discard.

The following example defines a `QueryCityDataForYears` method that returns a 6-tuple that contains a data for a city for two different years. The method call in the example is concerned only with the two population values returned by the method and so treats the remaining values in the tuple as discards when it deconstructs the tuple.

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

For more information, see [Discards](../discards.md).
 
## Pattern matching

*Pattern matching* is a feature that allows you to implement method dispatch on
properties other than the type of an object. You're probably already familiar
with method dispatch based on the type of an object. In Object Oriented programming,
virtual and override methods provide language syntax to implement method dispatching
based on an object's type. Base and Derived classes provide different implementations. 
Pattern matching expressions extend this concept so that you can easily
implement similar dispatch patterns for types and data elements that are
not related through an inheritance hierarchy. 

Pattern matching supports `is` expressions and `switch` expressions. Each
enables inspecting an object and its properties to determine if that object
satisfies the sought pattern. You use the `when` keyword to specify additional
rules to the pattern.

### `is` expression

The `is` pattern expression extends the familiar `is` operator to query an object beyond its type.

Let's start with a simple scenario. We'll add capabilities to this scenario
that demonstrate how pattern matching expressions make algorithms that work
with unrelated types easy. We'll start with a method that computes the sum
of a number of die rolls:

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

You might quickly find that you need to find the sum of die rolls where
some of the rolls are made with more than one die. Part of the input
sequence may be multiple results instead of a single number:

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

The `is` pattern expression works quite well in this scenario. As part of
checking the type, you write a variable initialization. This creates
a new variable of the validated runtime type.

As you keep extending these scenarios, you may find that you build more
`if` and `else if` statements. Once that becomes unwieldy, you'll likely
want to switch to `switch` pattern expressions.

### `switch` statement updates

The *match expression* has a familiar syntax, based on the `switch`
statement already part of the C# language. Let's translate the existing code
to use a match expression before adding new cases: 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

The match expressions have a slightly different syntax than the `is` expressions, where
you declare the type and variable at the beginning of the `case` expression.

The match expressions also support constants. This can save time by
factoring out simple cases:

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

The code above adds cases for `0` as a special case of `int`, and `null`
as a special case when there is no input. This demonstrates one important
new feature in switch pattern expressions: the order of the `case`
expressions now matters. The `0` case must appear before the general `int`
case. Otherwise, the first pattern to match would be the `int` case,
even when the value is `0`. If you accidentally order match expressions such
that a later case has already been handled, the compiler will flag that
and generate an error.

This same behavior enables the special case for an empty input sequence.
You can see that the case for an `IEnumerable` item that has elements
must appear before the general `IEnumerable` case.

This version has also added a `default` case. The `default` case is always
evaluated last, regardless of the order it appears in the source. For that
reason, convention is to put the `default` case last.

Finally, let's add one last `case` for a new style of die. Some games
use percentile dice to represent larger ranges of numbers. 

> [!NOTE]
> Two 10-sided percentile dice can represent every number from 0
> through 99. One die has sides labelled `00`, `10`, `20`, ... `90`. The other
> die has sides labeled `0`, `1`, `2`, ... `9`. Add the two die values
> together and you can get every number from 0 through 99.

To add this kind of die to your collection, first define a type to represent
the percentile die:

[!code-csharp[18_PercentileDie](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDie "Percentile Die type")]

Then, add a `case` match expression for the new type:

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

The new syntax for pattern matching expressions makes it easier to create
dispatch algorithms based on an object's type, or other properties, using
a clear and concise syntax. Pattern matching expressions enable these
constructs on data types that are unrelated by inheritance.

You can learn more about pattern matching in the topic
dedicated to [pattern matching in C#](../pattern-matching.md).

## Ref locals and returns

This feature enables algorithms that use and return references
to variables defined elsewhere. One example is working with
large matrices, and finding a single location with certain
characteristics. One method would return the two indices for
a single location in the matrix:

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

There are many issues with this code. First of all, it's a public
method that's returning a tuple. The language supports this, but
user defined types (either classes or structs) are preferred
for public APIs.

Second, this method is returning the indices to the item in the matrix.
That leads callers to write code that uses those indices to dereference
the matrix and modify a single element:

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

You'd rather write a method that returns a *reference*
to the element of the matrix that you want to change. You could only accomplish
this by using unsafe code and returning a pointer to an `int` in previous versions.

Let's walk through a series of changes to demonstrate the ref local feature
and show how to create a method that returns a reference to internal storage.
Along the way, you'll learn the rules of the ref return and ref local feature that
protects you from accidentally misusing it.

Start by modifying the `Find` method declaration so that it returns a `ref int`
instead of a tuple. Then, modify the return statement so it returns the value
stored in the matrix instead of the two indices:

```csharp
// Note that this won't compile. 
// Method declaration indicates ref return,
// but return statement specifies a value return.
public static ref int Find2(int[,] matrix, Func<int, bool> predicate)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
        for (int j = 0; j < matrix.GetLength(1); j++)
            if (predicate(matrix[i, j]))
                return matrix[i, j];
    throw new InvalidOperationException("Not found");
}
```

When you declare that a method returns a `ref` variable, you must also
add the `ref` keyword to each return statement. That indicates return
by reference, and helps developers reading the code later remember that
the method returns by reference:

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

Now that the method returns a reference to the integer value in the
matrix, you need to modify where it's called.  The `var` declaration
means that `valItem` is now an `int` rather than a tuple:

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

The second `WriteLine` statement in the example above prints out the value `42`,
not `24`. The variable `valItem` is an `int`, not a `ref int`. The `var`
keyword enables the compiler to specify the type, but will not implicitly
add the `ref` modifier. Instead, the value referred to by the `ref return`
is *copied* to the variable on the left-hand side of the assignment. The
variable is not a `ref` local.

In order to get the result you want, you need to add the `ref` modifier
to the local variable declaration to make the variable a reference when
the return value is a reference:

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

Now, the second `WriteLine` statement in the example above will print 
out the value `24`, indicating that the storage in the matrix has been
modified. The local variable has been declared with the `ref` modifier,
and it will take a `ref` return. You must initialize a `ref` variable when
it is declared, you cannot split the declaration and the initialization.

The C# language has three other rules that protect you from misusing
the `ref` locals and returns:

* You cannot assign a standard method return value to a `ref` local variable.
    - That disallows statements like `ref int i = sequence.Count();`
* You cannot return a `ref` to a variable whose lifetime does not extend beyond the execution of the method.
    - That means you cannot return a reference to a local variable or a variable with a similar scope.
* `ref` locals and returns can't be used with async methods.
    - The compiler can't know if the referenced variable has been set to its final value when the async method returns.

The addition of ref locals and ref returns enable algorithms that are more
efficient by avoiding copying values, or performing dereferencing operations
multiple times. 

## Local functions

Many designs for classes include methods that are called from only
one location. These additional private methods keep each method small
and focused. However, they can make it harder to understand a class
when reading it the first time. These methods must be understood
outside of the context of the single calling location.

For those designs, *local functions* enable you to declare methods
inside the context of another method. This makes it easier for readers
of the class to see that the local method is only called from the context
in which is it declared.

There are two very common use cases for local functions: public iterator
methods and public async methods. Both types of methods generate
code that reports errors later than programmers might expect. In
the case of iterator methods, any exceptions are observed only
when calling code that enumerates the returned sequence. In the case
of async methods, any exceptions are only observed when the returned
`Task` is awaited.

Let's start with an iterator method:

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

Examine the code below that calls the iterator method incorrectly:

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

The exception is thrown when `resultSet` is iterated, not when `resultSet` is created.
In this contained example, most developers could quickly diagnose the
problem. However, in larger codebases, the code that creates an iterator
often isn't as close to the code that enumerates the result. You can
refactor the code so that the public method validates all arguments,
and a private method generates the enumeration:

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

This refactored version will throw exceptions immediately because the public
method is not an iterator method; only the private method uses the
`yield return` syntax. However, there are potential problems with this
refactoring. The private method should only be called from the public
interface method, because otherwise all argument validation is skipped.
Readers of the class must discover this fact by reading the entire class
and searching for any other references to the `alphabetSubsetImplementation` 
method.

You can make that design intent more clear by declaring the 
`alphabetSubsetImplementation` as a local function inside the public
API method:

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

The version above makes it clear that the local method is referenced
only in the context of the outer method. The rules for local functions
also ensure that a developer can't accidentally call the local function
from another location in the class and bypass the argument validation.

The same technique can be employed with `async` methods to ensure that
exceptions arising from argument validation are thrown before the asynchronous
work begins:

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> Some of the designs that are supported by local functions
> could also be accomplished using *lambda expressions*. Those
> interested can [read more about the differences](../local-functions-vs-lambdas.md)

## More expression-bodied members

C# 6 introduced [expression-bodied members](csharp-6.md#expression-bodied-function-members)
for member functions, and read-only properties. C# 7 expands the allowed
members that can be implemented as expressions. In C# 7, you can implement
*constructors*, *finalizers*, and `get` and `set` accessors on *properties*
and *indexers*. The following code shows examples of each:

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> This example does not need a finalizer, but it is shown
> to demonstrate the syntax. You should not implement a
> finalizer in your class unless it is necessary to  release
> unmanaged resources. You should also consider using the
> <xref:System.Runtime.InteropServices.SafeHandle> class instead
> of managing unmanaged resources directly.

These new locations for expression-bodied members represent
an important milestone for the C# language: These features
were implemented by community members working on the open-source
[Roslyn](https://github.com/dotnet/Roslyn) project.

## Throw expressions

In C#, `throw` has always been a statement. Because `throw` is a statement,
not an expression, there were C# constructs where you could not use it. These
included conditional expressions, null coalescing expressions, and some lambda
expressions. The addition of expression-bodied members adds more locations
where `throw` expressions would be useful. So that you can write any of these
constructs, C# 7 introduces *throw expressions*.

The syntax is the same as you've always used for `throw` statements. The only difference
is that now you can place them in new locations, such as in a conditional expression:

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

This features enables using throw expressions in initialization expressions:

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

Previously, those initializations would need to be in a constructor, with the
throw statements in the body of the constructor:


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> Both of the preceding constructs will cause exceptions to be thrown during
> the construction of an object. Those are often difficult to recover from.
> For that reason, designs that throw exceptions during construction are
> discouraged.

## Generalized async return types

Returning a `Task` object from async methods can introduce
performance bottlenecks in certain paths. `Task` is a reference
type, so using it means allocating an object. In cases where a
method declared with the `async` modifier returns a cached result, or
completes synchronously, the extra allocations can become a significant
time cost in performance critical sections of code. It can become
very costly if those allocations occur in tight loops.

The new language feature means that async methods may return other
types in addition to `Task`, `Task<T>` and `void`. The returned type
must still satisfy the async pattern, meaning a `GetAwaiter` method
must be accessible. As one concrete example, the `ValueTask` type
has been added to the .NET framework to make use of this new language
feature: 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> You need to add the NuGet package [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/)
> in order to use the <xref:System.Threading.Tasks.ValueTask%601> type.

A simple optimization would be to use `ValueTask` in places where
`Task` would be used before. However, if you want to perform extra
optimizations by hand, you can cache results from async work and
reuse the result in subsequent calls. The `ValueTask` struct has a constructor
with a `Task` parameter so that you can construct a `ValueTask` from the
return value of any existing async method:

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]
 
As with all performance recommendations, you should benchmark
both versions before making large scale changes to your code.

## Numeric literal syntax improvements

Misreading numeric constants can make it harder to understand
code when reading it for the first time. This often
occurs when those numbers are used as bit masks or other symbolic
rather than numeric values. C# 7 includes two new features to
make it easier to write numbers in the most readable fashion
for the intended use: *binary literals*, and *digit separators*.

For those times when you are creating bit masks, or whenever a
binary representation of a number makes the most readable code,
write that number in binary:

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

The `0b` at the beginning of the constant indicates that the
number is written as a binary number.

Binary numbers can get very long, so it's often easier to see
the bit patterns by introducing the `_` as a digit separator:

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

The digit separator can appear anywhere in the constant. For base 10
numbers, it would be common to use it as a thousands separator:

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

The digit separator can be used with `decimal`, `float` and `double`
types as well:

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

Taken together, you can declare numeric constants with much more
readability.
