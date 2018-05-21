---
title: 委派和 Lambda
description: 了解委派如何定義指定特定方法簽章的類型，可直接呼叫，或傳遞至另一個方法，再進行呼叫。
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: f8184b87fc62f378fe72138733f87de924da60f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="b85be-103">委派和 Lambda</span><span class="sxs-lookup"><span data-stu-id="b85be-103">Delegates and lambdas</span></span>

<span data-ttu-id="b85be-104">委派可定義指定特定方法簽章的類型。</span><span class="sxs-lookup"><span data-stu-id="b85be-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="b85be-105">符合此簽章的方法 (靜態或執行個體) 可指派給該類型的變數，然後直接呼叫 (使用適當的引數)，或當做引數本身傳遞至另一個方法，再進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="b85be-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="b85be-106">下列範例示範委派的用法。</span><span class="sxs-lookup"><span data-stu-id="b85be-106">The following example demonstrates delegate use.</span></span>

```csharp
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

*   <span data-ttu-id="b85be-107">在第 4 行，我們建立特定簽章的委派類型，在本例中是接受字串參數再傳回字串參數的方法。</span><span class="sxs-lookup"><span data-stu-id="b85be-107">On line 4 we create a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
*   <span data-ttu-id="b85be-108">在第 6 行，我們藉由提供具有完全相同之簽章的方法，來定義委派的實作。</span><span class="sxs-lookup"><span data-stu-id="b85be-108">On line 6, we define the implementation of the delegate by providing a method that has the exact same signature.</span></span>
*   <span data-ttu-id="b85be-109">在第 13 行，此方法會指派給符合 `Reverse` 委派的類型。</span><span class="sxs-lookup"><span data-stu-id="b85be-109">On line 13, the method is assigned to a type that conforms to the `Reverse` delegate.</span></span>
*   <span data-ttu-id="b85be-110">最後，在第 15 行，我們叫用此委派，以傳遞要反轉的字串。</span><span class="sxs-lookup"><span data-stu-id="b85be-110">Finally, on line 15 we invoke the delegate passing a string to be reversed.</span></span>

<span data-ttu-id="b85be-111">為了簡化開發程序，.NET 包含一組委派類型，程式設計人員可重複使用這些類型，而不需要建立新的類型。</span><span class="sxs-lookup"><span data-stu-id="b85be-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="b85be-112">這些類型包括 `Func<>`、`Action<>` 和 `Predicate<>`，可用於 .NET API 中的不同位置，而不需要定義新的委派類型。</span><span class="sxs-lookup"><span data-stu-id="b85be-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="b85be-113">當然，這三種類型彼此有些不同，如您在其簽章中所見，大部分與其預定使用方式相關：</span><span class="sxs-lookup"><span data-stu-id="b85be-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

*   <span data-ttu-id="b85be-114">使用委派的引數時如需執行動作，會使用 `Action<>`。</span><span class="sxs-lookup"><span data-stu-id="b85be-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
*   <span data-ttu-id="b85be-115">`Func<>` 通常會在需要轉換時使用，亦即您必須將委派的引數轉換成其他結果。</span><span class="sxs-lookup"><span data-stu-id="b85be-115">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="b85be-116">預測就是一個主要範例。</span><span class="sxs-lookup"><span data-stu-id="b85be-116">Projections are a prime example of this.</span></span>
*   <span data-ttu-id="b85be-117">`Predicate<>` 會在需要判斷引數是否符合委派的條件時使用。</span><span class="sxs-lookup"><span data-stu-id="b85be-117">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="b85be-118">它也可以寫成 `Func<T, bool>`。</span><span class="sxs-lookup"><span data-stu-id="b85be-118">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="b85be-119">我們現在可以使用 `Func<>` 委派取代自訂類型，針對上述範例進行重寫。</span><span class="sxs-lookup"><span data-stu-id="b85be-119">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="b85be-120">程式會以完全相同的方式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b85be-120">The program will continue running exactly the same.</span></span>

```csharp
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

<span data-ttu-id="b85be-121">在這個簡單的範例中，在 Main() 方法外定義方法似乎有點多餘。</span><span class="sxs-lookup"><span data-stu-id="b85be-121">For this simple example, having a method defined outside of the Main() method seems a bit superfluous.</span></span> <span data-ttu-id="b85be-122">因此，.NET Framework 2.0 引入**匿名委派**的概念。</span><span class="sxs-lookup"><span data-stu-id="b85be-122">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="b85be-123">在此支援下，您可以建立「內嵌」委派，而不需要指定任何其他類型或方法。</span><span class="sxs-lookup"><span data-stu-id="b85be-123">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="b85be-124">只要在需要的地方內嵌委派的定義即可。</span><span class="sxs-lookup"><span data-stu-id="b85be-124">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="b85be-125">例如，我們將切換設定，並使用匿名委派篩選出只有偶數的清單，然後列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="b85be-125">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
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
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

<span data-ttu-id="b85be-126">注意醒目提示的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="b85be-126">Notice the highlighted lines.</span></span> <span data-ttu-id="b85be-127">如您所見，委派的主體只是一組運算式，與任何其他委派相同。</span><span class="sxs-lookup"><span data-stu-id="b85be-127">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="b85be-128">但這並不是不同的定義，而是當做 _「臨機操作」_ 引入 `List<T>` 類型的 `FindAll()` 方法呼叫中。</span><span class="sxs-lookup"><span data-stu-id="b85be-128">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the `FindAll()` method of the `List<T>` type.</span></span>

<span data-ttu-id="b85be-129">不過，即使使用此方法，還是有許多程式碼可以捨棄。</span><span class="sxs-lookup"><span data-stu-id="b85be-129">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="b85be-130">此時就需要 **Lambda 運算式**。</span><span class="sxs-lookup"><span data-stu-id="b85be-130">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="b85be-131">Lambda 運算式 (簡稱 "Lambda") 最先是在 C# 3.0 中，當作 Language Integrated Query (LINQ) 的其中一個核心建置組塊所引入。</span><span class="sxs-lookup"><span data-stu-id="b85be-131">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="b85be-132">這是更方便使用委派的語法。</span><span class="sxs-lookup"><span data-stu-id="b85be-132">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="b85be-133">這些運算式可宣告簽章和方法主體，但除非指派給委派，否則並沒有自己的正式身分識別。</span><span class="sxs-lookup"><span data-stu-id="b85be-133">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="b85be-134">不同於委派，這些運算式可在事件註冊左邊，或在各種 LINQ 子句和方法中直接指派。</span><span class="sxs-lookup"><span data-stu-id="b85be-134">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various Linq clauses and methods.</span></span>

<span data-ttu-id="b85be-135">因為 Lambda 運算式不過是指定委派的另一種方式，所以我們應該能夠重寫上述範例，使用 Lambda 運算式取代匿名委派。</span><span class="sxs-lookup"><span data-stu-id="b85be-135">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
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

<span data-ttu-id="b85be-136">如果您看一下醒目提示的程式碼行，就能了解 Lambda 運算式看起來如何。</span><span class="sxs-lookup"><span data-stu-id="b85be-136">If you take a look at the highlighted lines, you can see how a lambda expression looks like.</span></span> <span data-ttu-id="b85be-137">同樣地，它只是對於使用委派**非常**方便的語法，因此實際上的使用狀況會類似於使用匿名委派的狀況。</span><span class="sxs-lookup"><span data-stu-id="b85be-137">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="b85be-138">同樣地，Lambda 就是委派，這表示它們可當做事件處理常式使用，而不會有任何問題，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="b85be-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

## <a name="further-reading-and-resources"></a><span data-ttu-id="b85be-139">延伸閱讀和資源</span><span class="sxs-lookup"><span data-stu-id="b85be-139">Further reading and resources</span></span>

*   [<span data-ttu-id="b85be-140">委派</span><span class="sxs-lookup"><span data-stu-id="b85be-140">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
*   [<span data-ttu-id="b85be-141">匿名函式</span><span class="sxs-lookup"><span data-stu-id="b85be-141">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [<span data-ttu-id="b85be-142">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="b85be-142">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
