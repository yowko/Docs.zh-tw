---
title: 委派和 Lambda
description: 了解委派如何定義指定特定方法簽章的類型，可直接呼叫，或傳遞至另一個方法，再進行呼叫。
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: e392f6b2e57bebf1ab916bc6142aebbc8f341db2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615302"
---
# <a name="delegates-and-lambdas"></a>委派和 Lambda

委派可定義指定特定方法簽章的類型。 符合此簽章的方法 (靜態或執行個體) 可指派給該類型的變數，然後直接呼叫 (使用適當的引數)，或當做引數本身傳遞至另一個方法，再進行呼叫。 下列範例示範委派的用法。

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

為了簡化開發程序，.NET 包含一組委派類型，程式設計人員可重複使用這些類型，而不需要建立新的類型。 這些類型包括 `Func<>`、`Action<>` 和 `Predicate<>`，可用於 .NET API 中的不同位置，而不需要定義新的委派類型。 當然，這三種類型彼此有些不同，如您在其簽章中所見，大部分與其預定使用方式相關：

* 使用委派的引數時如需執行動作，會使用 `Action<>`。
* `Func<>` 通常會在需要轉換時使用，亦即您必須將委派的引數轉換成其他結果。 預測就是一個主要範例。
* `Predicate<>` 會在需要判斷引數是否符合委派的條件時使用。 它也可以寫成 `Func<T, bool>`。

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

在這個簡單的範例中，在 `Main` 方法外定義方法似乎有點多餘。 因此，.NET Framework 2.0 引入**匿名委派**的概念。 在此支援下，您可以建立「內嵌」委派，而不需要指定任何其他類型或方法。 只要在需要的地方內嵌委派的定義即可。

例如，我們將切換設定，並使用匿名委派篩選出只有偶數的清單，然後列印至主控台。

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

如您所見，委派的主體只是一組運算式，與任何其他委派相同。 但這並不是不同的定義，而是當作「臨機操作」引入 <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> 方法呼叫。

不過，即使使用此方法，還是有許多程式碼可以捨棄。 此時就需要 **Lambda 運算式**。

Lambda 運算式 (簡稱 "Lambda") 最先是在 C# 3.0 中，當作 Language Integrated Query (LINQ) 的其中一個核心建置組塊所引入。 這是更方便使用委派的語法。 這些運算式可宣告簽章和方法主體，但除非指派給委派，否則並沒有自己的正式身分識別。 不同於委派，這些運算式可在事件註冊左邊，或在各種 LINQ 子句和方法中直接指派。

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

在上述範例中，使用的 Lambda 運算式為 `i => i % 2 == 0`。 同樣地，它只是對於使用委派**非常**方便的語法，因此實際上的使用狀況會類似於使用匿名委派的狀況。

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

在此內容中使用 `+=` 運算子來訂閱[事件](../../docs/csharp/language-reference/keywords/event.md)。 如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。

## <a name="further-reading-and-resources"></a>延伸閱讀和資源

* [委派](../../docs/csharp/programming-guide/delegates/index.md)
* [匿名函式](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [Lambda 運算式](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
