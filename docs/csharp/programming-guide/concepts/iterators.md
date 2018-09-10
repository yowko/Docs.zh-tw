---
title: 在 C# 中逐一查看集合
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: d8a39569df517dffa8ff4b2f638f089f420e44c7
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253541"
---
# <a name="iterators-c"></a>迭代器 (C#)

「迭代器」可用來逐步執行集合，例如清單和陣列。

迭代器方法或 `get` 存取子會對集合執行自訂反覆運算。 迭代器方法使用 [yield return](../../../csharp/language-reference/keywords/yield.md) 陳述式，一次傳回一個項目。 當到達 `yield return` 陳述式時，系統會記住程式碼中的目前位置。 下次呼叫迭代器函式時，便會從這個位置重新開始執行。

您會使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式或使用 LINQ 查詢，透過用戶端程式碼取用迭代器。

在下列範例中，第一次反覆運算 `foreach` 迴圈會使 `SomeNumbers` 迭代器方法中的執行繼續，直到到達第一個 `yield return` 陳述式為止。 此反覆運算會傳回值 3，並保留迭代器方法中的目前位置。 下次反覆運算迴圈時，迭代器方法中的執行會從上次停止的位置繼續，並且在到達 `yield return` 陳述式時再次停止。 此反覆運算會傳回值 5，並再次保留迭代器方法中的目前位置。 當到達迭代器方法結尾時，迴圈便完成。

```csharp
static void Main()
{
    foreach (int number in SomeNumbers())
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 3 5 8
    Console.ReadKey();
}

public static System.Collections.IEnumerable SomeNumbers()
{
    yield return 3;
    yield return 5;
    yield return 8;
}
```

迭代器方法或 `get` 存取子的傳回型別可以是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。

您可以使用 `yield break` 陳述式結束反覆項目。

> [!NOTE]
> 如需本主題中除簡易迭代器範例以外的其他所有範例，請加入 `System.Collections` 和 `System.Collections.Generic` 命名空間的 [using](../../../csharp/language-reference/keywords/using-directive.md) 指示詞。

## <a name="simple-iterator"></a>簡單的 Iterator

下列範例在 [for](../../../csharp/language-reference/keywords/for.md) 迴圈內有一行 `yield return` 陳述式。 在 `Main` 中，每次反覆運算 `foreach` 陳述式主體都會建立迭代器函式的呼叫，以繼續進行下一個 `yield return` 陳述式。

```csharp
static void Main()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 6 8 10 12 14 16 18
    Console.ReadKey();
}

public static System.Collections.Generic.IEnumerable<int>
    EvenSequence(int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (int number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="creating-a-collection-class"></a>建立集合類別

在以下範例中，`DaysOfTheWeek` 類別會實作 <xref:System.Collections.IEnumerable> 介面，而這個介面需使用 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。 編譯器會隱含呼叫 `GetEnumerator` 方法，以傳回 <xref:System.Collections.IEnumerator>。

`GetEnumerator` 方法使用 `yield return` 陳述式，一次傳回一個字串。

```csharp
static void Main()
{
    DaysOfTheWeek days = new DaysOfTheWeek();

    foreach (string day in days)
    {
        Console.Write(day + " ");
    }
    // Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey();
}

public class DaysOfTheWeek : IEnumerable
{
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };

    public IEnumerator GetEnumerator()
    {
        for (int index = 0; index < days.Length; index++)
        {
            // Yield each day of the week.
            yield return days[index];
        }
    }
}
```

下列範例會建立 `Zoo` 類別，其中包含動物的集合。

參考類別執行個體 (`theZoo`) 的 `foreach` 陳述式會隱含呼叫 `GetEnumerator` 方法。 參考 `Birds` 和 `Mammals` 屬性的 `foreach` 陳述式會使用 `AnimalsForType` 具名迭代器方法。

```csharp
static void Main()
{
    Zoo theZoo = new Zoo();

    theZoo.AddMammal("Whale");
    theZoo.AddMammal("Rhinoceros");
    theZoo.AddBird("Penguin");
    theZoo.AddBird("Warbler");

    foreach (string name in theZoo)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros Penguin Warbler

    foreach (string name in theZoo.Birds)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Penguin Warbler

    foreach (string name in theZoo.Mammals)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros

    Console.ReadKey();
}

public class Zoo : IEnumerable
{
    // Private members.
    private List<Animal> animals = new List<Animal>();

    // Public methods.
    public void AddMammal(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });
    }

    public void AddBird(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });
    }

    public IEnumerator GetEnumerator()
    {
        foreach (Animal theAnimal in animals)
        {
            yield return theAnimal.Name;
        }
    }

    // Public members.
    public IEnumerable Mammals
    {
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }
    }

    public IEnumerable Birds
    {
        get { return AnimalsForType(Animal.TypeEnum.Bird); }
    }

    // Private methods.
    private IEnumerable AnimalsForType(Animal.TypeEnum type)
    {
        foreach (Animal theAnimal in animals)
        {
            if (theAnimal.Type == type)
            {
                yield return theAnimal.Name;
            }
        }
    }

    // Private class.
    private class Animal
    {
        public enum TypeEnum { Bird, Mammal }

        public string Name { get; set; }
        public TypeEnum Type { get; set; }
    }
}
```

## <a name="using-iterators-with-a-generic-list"></a>搭配泛型清單使用迭代器

在以下範例中，<xref:System.Collections.Generic.Stack%601> 泛型類別會實作 <xref:System.Collections.Generic.IEnumerable%601> 泛型介面。 <xref:System.Collections.Generic.Stack%601.Push%2A> 方法會將值指派給 `T` 類型的陣列。 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法會使用 `yield return` 陳述式以傳回陣列值。

除了泛型 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法，您也必須實作非泛型 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。 這是因為 <xref:System.Collections.Generic.IEnumerable%601> 繼承自 <xref:System.Collections.IEnumerable>。 非泛型實作會延後到泛型實作。

此範例使用具名迭代器來支援逐一查看相同資料集合的各種方法。 這些具名迭代器是 `TopToBottom` 和 `BottomToTop` 屬性，以及 `TopN` 方法。

`BottomToTop` 屬性會在 `get` 存取子中使用迭代器。

```csharp
static void Main()
{
    Stack<int> theStack = new Stack<int>();

    //  Add items to the stack.
    for (int number = 0; number <= 9; number++)
    {
        theStack.Push(number);
    }

    // Retrieve items from the stack.
    // foreach is allowed because theStack implements IEnumerable<int>.
    foreach (int number in theStack)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    // foreach is allowed, because theStack.TopToBottom returns IEnumerable(Of Integer).
    foreach (int number in theStack.TopToBottom)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    foreach (int number in theStack.BottomToTop)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 0 1 2 3 4 5 6 7 8 9

    foreach (int number in theStack.TopN(7))
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3

    Console.ReadKey();
}

public class Stack<T> : IEnumerable<T>
{
    private T[] values = new T[100];
    private int top = 0;

    public void Push(T t)
    {
        values[top] = t;
        top++;
    }
    public T Pop()
    {
        top--;
        return values[top];
    }

    // This method implements the GetEnumerator method. It allows
    // an instance of the class to be used in a foreach statement.
    public IEnumerator<T> GetEnumerator()
    {
        for (int index = top - 1; index >= 0; index--)
        {
            yield return values[index];
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }

    public IEnumerable<T> TopToBottom
    {
        get { return this; }
    }

    public IEnumerable<T> BottomToTop
    {
        get
        {
            for (int index = 0; index <= top - 1; index++)
            {
                yield return values[index];
            }
        }
    }

    public IEnumerable<T> TopN(int itemsFromTop)
    {
        // Return less than itemsFromTop if necessary.
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;

        for (int index = top - 1; index >= startIndex; index--)
        {
            yield return values[index];
        }
    }

}
```

## <a name="syntax-information"></a>語法資訊

出現的迭代器可以是方法或 `get` 存取子。 迭代器不能出現在事件、執行個體建構函式、靜態建構函式或靜態完成項中。

從 `yield return` 陳述式中的運算式類型到迭代器傳回的 IEnumerable<T> 型別引數，必須有隱含轉換。

在 C# 中，迭代器方法不可有任何 `in`、`ref` 或 `out` 參數。

在 C# 中，"yield" 不是保留字，只有在 `return` 或 `break` 關鍵字前面使用時才具有特殊意義。

## <a name="technical-implementation"></a>技術實作

雖然您將迭代器撰寫成方法，但編譯器會將其轉譯成巢狀類別，其實也就是狀態機器。 此類別會在用戶端程式碼中的 `foreach` 迴圈繼續期間追蹤迭代器的位置。

若要查看編譯器的功能，您可以使用 Ildasm.exe 工具，檢視為迭代器方法產生的 Microsoft 中繼語言程式碼。

當您建立 [class](../../../csharp/language-reference/keywords/class.md) 或 [struct](../../../csharp/language-reference/keywords/struct.md) 的迭代器時，您不需要實作整個 <xref:System.Collections.IEnumerator> 介面。 當編譯器偵測到迭代器時，它會自動產生 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> 介面的 `Current`、`MoveNext` 和 `Dispose` 方法。

之後每次反覆運算 `foreach` 迴圈 (或直接呼叫 `IEnumerator.MoveNext`)，下一個迭代器程式碼主體都會在上一個 `yield return` 陳述式之後繼續。 然後繼續執行至下一個 `yield return` 陳述式，直到達到迭代器主體結尾，或遇到 `yield break` 陳述式為止。

迭代器不支援 <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> 方法。 若要從頭開始逐一查看，您必須取得新的迭代器。 對迭代器方法傳回的迭代器呼叫 <xref:System.Collections.IEnumerator.Reset%2A> 會擲回 <xref:System.NotSupportedException>。

如需其他資訊，請參閱 [C# 語言規格](../../../csharp/language-reference/language-specification/index.md)。

## <a name="use-of-iterators"></a>迭代器的使用

當您需要使用複雜的程式碼來填入清單序列時，迭代器可讓您維持 `foreach` 迴圈的簡潔性。 當您想要執行下列作業時，這會很有用：

- 在第一次反覆運算 `foreach` 迴圈之後修改清單序列。

- 避免在第一次反覆運算 `foreach` 迴圈之前完整載入大型清單。 分頁擷取以分批載入資料表資料列即為一例。 另一個範例是 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> 方法，它會在 .NET Framework 中實作迭代器。

- 在迭代器中封裝建立清單。 在迭代器方法中，您可以建立清單，然後在迴圈中產生每個結果。

## <a name="see-also"></a>請參閱

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)
- [yield](../../../csharp/language-reference/keywords/yield.md)
- [搭配陣列使用 foreach](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)
- [泛型](../../../csharp/programming-guide/generics/index.md)