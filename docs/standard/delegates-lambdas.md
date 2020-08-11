---
title: 委派和 Lambda
description: 瞭解委派如何定義指定特定方法簽章的類型，可直接呼叫，或傳遞至另一個方法並呼叫。
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 1307599a3832be5f48cd62a7b8c1be7f76a3d4a5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063740"
---
# <a name="delegates-and-lambdas"></a>委派和 Lambda

委派會定義指定特定方法簽章的類型。 符合此簽章的方法 (靜態或執行個體) 可指派給該類型的變數，然後直接呼叫 (使用適當的引數)，或當做引數本身傳遞至另一個方法，再進行呼叫。 下列範例示範委派的用法。

```csharp
using System;
using System.Linq;

public class Program
{
    public delegate string Reverse(string s);

    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Reverse rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

* `public delegate string Reverse(string s);` 程式行會建立特定簽章的委派類型，在本例中是接受字串參數再傳回字串參數的方法。
* `static string ReverseString(string s)` 方法與定義的委派類型具有完全相同的簽章，會實作委派。
* `Reverse rev = ReverseString;` 程式行顯示您可將方法指派至對應委派類型的變數。
* `Console.WriteLine(rev("a string"));` 程式行示範如何使用委派類型的變數來叫用委派。

為了簡化開發程序，.NET 包含一組委派類型，程式設計人員可重複使用這些類型，而不需要建立新的類型。 這些類型是 `Func<>` 、 `Action<>` 和 `Predicate<>` ，而且不需要定義新的委派類型即可使用它們。 這三種類型之間有一些差異，必須使用它們的用途：

* 使用委派的引數時如需執行動作，會使用 `Action<>`。 它所封裝的方法不會傳回值。
* `Func<>` 通常會在需要轉換時使用，亦即您必須將委派的引數轉換成其他結果。 投影是一個很好的例子。 它所封裝的方法會傳回指定的值。
* `Predicate<>` 會在需要判斷引數是否符合委派的條件時使用。 它也可以撰寫為 `Func<T, bool>` ，這表示方法會傳回布林值。

我們現在可以使用 `Func<>` 委派取代自訂類型，針對上述範例進行重寫。 程式會以完全相同的方式繼續執行。

```csharp
using System;
using System.Linq;

public class Program
{
    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Func<string, string> rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

在這個簡單的範例中，在 `Main` 方法外定義方法似乎有點多餘。 .NET Framework 2.0 引進了*匿名委派*的概念，可讓您建立「內嵌」委派，而不需要指定任何其他類型或方法。

在下列範例中，匿名委派會將清單篩選為只是偶數，然後將其列印至主控台。

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(
          delegate (int no)
          {
              return (no % 2 == 0);
          }
        );

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

如您所見，委派的主體只是一組運算式，與任何其他委派相同。 但它不是個別的定義，而是在我們的方法_呼叫中特別_介紹 <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> 。

不過，即使使用此方法，還是有許多程式碼可以捨棄。 此時就需要 *Lambda 運算式*。 Lambda 運算式（簡稱 "lambda"）是以 c # 3.0 引進，做為語言整合式查詢 (LINQ) 的其中一個核心建立區塊。 這是更方便使用委派的語法。 它們會宣告簽章和方法主體，但除非指派給委派，否則不會有自己的正式身分識別。 不同于委派，它們可以直接指派為事件註冊的右手邊，或在各種 LINQ 子句和方法中。

因為 Lambda 運算式不過是指定委派的另一種方式，所以我們應該能夠重寫上述範例，使用 Lambda 運算式取代匿名委派。

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(i => i % 2 == 0);

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

在上述範例中，使用的 Lambda 運算式為 `i => i % 2 == 0`。 同樣地，這只是使用委派的一個便利語法。 這種情況下會發生什麼事，與匿名委派的情況類似。

同樣地，Lambda 就是委派，這表示它們可當做事件處理常式使用，而不會有任何問題，如下列程式碼片段所示。

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

在此內容中使用 `+=` 運算子來訂閱[事件](../csharp/language-reference/keywords/event.md)。 如需詳細資訊，請參閱[如何訂閱及取消訂閱事件](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。

## <a name="further-reading-and-resources"></a>延伸閱讀和資源

* [委派](../csharp/programming-guide/delegates/index.md)
* [匿名函式](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Lambda 運算式](../csharp/language-reference/operators/lambda-expressions.md)
