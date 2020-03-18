---
title: System.Delegate 和 `delegate` 關鍵字
description: 瞭解 .NET 中支援委託的類，以及這些類如何映射到"委託"關鍵字。
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 87fdf19c4ea810c5ac4409fe16c3cba9d5fc6574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146277"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="29eae-103">System.Delegate 和 `delegate` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="29eae-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="29eae-104">上一步</span><span class="sxs-lookup"><span data-stu-id="29eae-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="29eae-105">本文介紹 .NET 中支援委託的類，以及這些類如何映射到關鍵字`delegate`。</span><span class="sxs-lookup"><span data-stu-id="29eae-105">This article covers the classes in .NET that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="define-delegate-types"></a><span data-ttu-id="29eae-106">定義委託類型</span><span class="sxs-lookup"><span data-stu-id="29eae-106">Define delegate types</span></span>

<span data-ttu-id="29eae-107">首先讓我們說明 'delegate' 關鍵字，因為您在使用委派時主要會用到這個項目。</span><span class="sxs-lookup"><span data-stu-id="29eae-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="29eae-108">當您使用 `delegate` 關鍵字時，編譯器產生的程式碼會對應到叫用 <xref:System.Delegate> 和 <xref:System.MulticastDelegate> 類別成員的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="29eae-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span>

<span data-ttu-id="29eae-109">定義委派型別的語法與定義方法簽章的語法類似。</span><span class="sxs-lookup"><span data-stu-id="29eae-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="29eae-110">您只需要將 `delegate` 關鍵字加入定義中。</span><span class="sxs-lookup"><span data-stu-id="29eae-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="29eae-111">讓我們繼續使用 List.Sort() 方法作為範例。</span><span class="sxs-lookup"><span data-stu-id="29eae-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="29eae-112">第一個步驟是建立比較委派的型別：</span><span class="sxs-lookup"><span data-stu-id="29eae-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="29eae-113">編譯器會產生一個衍生自 `System.Delegate` 且符合所用簽章的類別 (在此情況下，其為一個會傳回整數且具有兩個引數的方法)。</span><span class="sxs-lookup"><span data-stu-id="29eae-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="29eae-114">該委派的型別為 `Comparison`。</span><span class="sxs-lookup"><span data-stu-id="29eae-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="29eae-115">`Comparison` 委派型別是泛型型別。</span><span class="sxs-lookup"><span data-stu-id="29eae-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="29eae-116">如需泛型的詳細資料，請參閱[這裡](programming-guide/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="29eae-116">For details on generics see [here](programming-guide/generics/index.md).</span></span>

<span data-ttu-id="29eae-117">請注意，此語法看似在宣告一個變數，但實際上是宣告「型別」\*\*。</span><span class="sxs-lookup"><span data-stu-id="29eae-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="29eae-118">您可以在類別中定義委派型別、直接在命名空間中定義，或甚至在全域命名空間中加以定義。</span><span class="sxs-lookup"><span data-stu-id="29eae-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="29eae-119">不過，我們並不建議您直接宣告全域命名空間中的委派型別 (或其他型別)。</span><span class="sxs-lookup"><span data-stu-id="29eae-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span>

<span data-ttu-id="29eae-120">編譯器也會產生這個新型別的加入處理常式和移除處理常式，該類別的用戶端即可在執行個體的引動過程清單中加入和移除方法。</span><span class="sxs-lookup"><span data-stu-id="29eae-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="29eae-121">編譯器會強制確保您要加入或移除的方法簽章符合宣告方法時所用的簽章。</span><span class="sxs-lookup"><span data-stu-id="29eae-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span>

## <a name="declare-instances-of-delegates"></a><span data-ttu-id="29eae-122">聲明委託實例</span><span class="sxs-lookup"><span data-stu-id="29eae-122">Declare instances of delegates</span></span>

<span data-ttu-id="29eae-123">定義委派之後，您可以建立該型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="29eae-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="29eae-124">如同 C# 中的所有變數一般，您無法直接宣告命名空間或全域命名空間中的委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="29eae-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="29eae-125">變數的型別為稍早定義的 `Comparison<T>` 委派型別。</span><span class="sxs-lookup"><span data-stu-id="29eae-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="29eae-126">變數的名稱為 `comparator`。</span><span class="sxs-lookup"><span data-stu-id="29eae-126">The name of the variable is `comparator`.</span></span>

 <span data-ttu-id="29eae-127">上述程式碼片段會宣告類別內的成員變數。</span><span class="sxs-lookup"><span data-stu-id="29eae-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="29eae-128">您也可以宣告本身為區域變數或方法引數的委派變數。</span><span class="sxs-lookup"><span data-stu-id="29eae-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoke-delegates"></a><span data-ttu-id="29eae-129">調用委託</span><span class="sxs-lookup"><span data-stu-id="29eae-129">Invoke delegates</span></span>

<span data-ttu-id="29eae-130">您可以呼叫委派，藉此叫用該委派引動過程清單中的方法。</span><span class="sxs-lookup"><span data-stu-id="29eae-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="29eae-131">在 `Sort()` 方法中，程式碼會呼叫比較方法以判斷物件的放置順序：</span><span class="sxs-lookup"><span data-stu-id="29eae-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="29eae-132">在上述該行中，程式碼會「叫用」\*\* 附加至委派的方法。</span><span class="sxs-lookup"><span data-stu-id="29eae-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="29eae-133">您可將變數視為方法名稱，並使用一般方法呼叫語法加以叫用。</span><span class="sxs-lookup"><span data-stu-id="29eae-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="29eae-134">該行程式碼會進行不安全的假設︰因此無法保證目標已新增至委派。</span><span class="sxs-lookup"><span data-stu-id="29eae-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="29eae-135">如果未附加任何目標，上述行會導致系統擲回 `NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="29eae-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="29eae-136">我們會在本[系列](delegates-patterns.md)稍後說明可用來解決這個問題的慣用語，這些慣用語比簡單的 null 檢查更複雜。</span><span class="sxs-lookup"><span data-stu-id="29eae-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assign-add-and-remove-invocation-targets"></a><span data-ttu-id="29eae-137">分配、添加和刪除調用目標</span><span class="sxs-lookup"><span data-stu-id="29eae-137">Assign, add, and remove invocation targets</span></span>

<span data-ttu-id="29eae-138">這涉及委派型別的定義方式，以及委派執行個體的宣告和叫用方式。</span><span class="sxs-lookup"><span data-stu-id="29eae-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="29eae-139">如果開發人員想要使用 `List.Sort()` 方法，則需要先定義一個方法，使其簽章符合委派型別的定義，並將它指派給排序方法所用的委派。</span><span class="sxs-lookup"><span data-stu-id="29eae-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="29eae-140">此指派會將這個方法新增至該委派物件的引動過程清單。</span><span class="sxs-lookup"><span data-stu-id="29eae-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="29eae-141">假設您想要依據字串長度來排序清單，</span><span class="sxs-lookup"><span data-stu-id="29eae-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="29eae-142">您的比較函式可能如下︰</span><span class="sxs-lookup"><span data-stu-id="29eae-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

<span data-ttu-id="29eae-143">此方法會以私用方法的形式宣告。</span><span class="sxs-lookup"><span data-stu-id="29eae-143">The method is declared as a private method.</span></span> <span data-ttu-id="29eae-144">沒關係，</span><span class="sxs-lookup"><span data-stu-id="29eae-144">That's fine.</span></span> <span data-ttu-id="29eae-145">您可能不希望這個方法成為公用介面的一部分。</span><span class="sxs-lookup"><span data-stu-id="29eae-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="29eae-146">它仍可以在附加至委派時作為比較方法來使用。</span><span class="sxs-lookup"><span data-stu-id="29eae-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="29eae-147">呼叫程式碼會將這個方法附加至委派物件的目標清單，並透過該委派進行存取。</span><span class="sxs-lookup"><span data-stu-id="29eae-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="29eae-148">您可以該方法傳遞給 `List.Sort()` 方法，以建立這種關聯性：</span><span class="sxs-lookup"><span data-stu-id="29eae-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="29eae-149">請注意，使用的方法名稱不含括弧。</span><span class="sxs-lookup"><span data-stu-id="29eae-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="29eae-150">將方法作為引數使用時，系統會指示編譯器將方法參考轉換成可作為委派引動過程的目標，並將該方法附加為叫用目標。</span><span class="sxs-lookup"><span data-stu-id="29eae-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="29eae-151">您可能也已宣告 `Comparison<string>` 型別的變數並進行指派，以便明確宣告：</span><span class="sxs-lookup"><span data-stu-id="29eae-151">You could also have been explicit by declaring a variable of type `Comparison<string>` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="29eae-152">適用於作為委派目標的方法是小型方法的情況，且通常會使用 [Lambda 運算式](./programming-guide/statements-expressions-operators/lambda-expressions.md)語法來執行指派：</span><span class="sxs-lookup"><span data-stu-id="29eae-152">In uses where the method being used as a delegate target is a small method, it's common to use [lambda expression](./programming-guide/statements-expressions-operators/lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="29eae-153">使用 lambda 運算式進行委託目標在後面的[一節中](delegates-patterns.md)將介紹更多內容。</span><span class="sxs-lookup"><span data-stu-id="29eae-153">Using lambda expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="29eae-154">Sort() 範例通常會將單一的目標方法附加至委派。</span><span class="sxs-lookup"><span data-stu-id="29eae-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="29eae-155">即便如此，委派物件仍支援具有多個目標方法 (附加至委派物件) 的引動過程清單。</span><span class="sxs-lookup"><span data-stu-id="29eae-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="29eae-156">Delegate 和 MulticastDelegate 類別</span><span class="sxs-lookup"><span data-stu-id="29eae-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="29eae-157">上述語言支援提供使用委派時通常需要的功能與支援。</span><span class="sxs-lookup"><span data-stu-id="29eae-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="29eae-158">這些功能都是建置在 .NET Core Framework 的 <xref:System.Delegate> 和 <xref:System.MulticastDelegate> 兩個類別之上。</span><span class="sxs-lookup"><span data-stu-id="29eae-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="29eae-159">類`System.Delegate`及其單個直接子類`System.MulticastDelegate`為創建委託、將方法註冊為委託目標以及調用註冊為委託目標的所有方法提供了框架支援。</span><span class="sxs-lookup"><span data-stu-id="29eae-159">The `System.Delegate` class and its single direct subclass, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span>

<span data-ttu-id="29eae-160">有趣的是，`System.Delegate` 和 `System.MulticastDelegate` 類別本身不是委派型別，</span><span class="sxs-lookup"><span data-stu-id="29eae-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="29eae-161">卻可提供所有特定委派型別的基礎。</span><span class="sxs-lookup"><span data-stu-id="29eae-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="29eae-162">這個相同的語言設計程序要求您不能宣告衍生自 `Delegate` 或 `MulticastDelegate` 的類別。</span><span class="sxs-lookup"><span data-stu-id="29eae-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="29eae-163">C# 語言規則禁止使用該類別。</span><span class="sxs-lookup"><span data-stu-id="29eae-163">The C# language rules prohibit it.</span></span>

<span data-ttu-id="29eae-164">相反地，當您使用 C# 語言關鍵字來宣告委派型別時，C# 編譯器會建立一個衍生自 `MulticastDelegate` 的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="29eae-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="29eae-165">這種設計起源於第一版的 C# 和 .NET。</span><span class="sxs-lookup"><span data-stu-id="29eae-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="29eae-166">設計團隊的其中一個目標是要確保使用委派時，語言能強制執行型別安全。</span><span class="sxs-lookup"><span data-stu-id="29eae-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="29eae-167">亦即，系統必須確保叫用委派時使用正確的引數型別和數目，</span><span class="sxs-lookup"><span data-stu-id="29eae-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="29eae-168">以及在編譯時間能正確表示任何傳回的型別。</span><span class="sxs-lookup"><span data-stu-id="29eae-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="29eae-169">委派是屬於 .NET 1.0 版本的一部分，也就是泛型之前的版本。</span><span class="sxs-lookup"><span data-stu-id="29eae-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="29eae-170">要強制執行此型別安全的最佳方式，是讓編譯器建立具象委派類別，以表示要使用的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="29eae-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="29eae-171">雖然您不能直接建立衍生的類別，但仍會用到這些類別上所定義的方法。</span><span class="sxs-lookup"><span data-stu-id="29eae-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="29eae-172">接著，我們將逐步解說使用委派時最常使用的方法。</span><span class="sxs-lookup"><span data-stu-id="29eae-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="29eae-173">首先，最重要的是記住您使用的每個委派皆衍生自 `MulticastDelegate`。</span><span class="sxs-lookup"><span data-stu-id="29eae-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="29eae-174">多點傳送委派是指，透過委派叫用時，可以叫用一個以上的方法目標。</span><span class="sxs-lookup"><span data-stu-id="29eae-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="29eae-175">原本的設計考量是要區隔只能附加並叫用一個目標方法的委派，以及可以附加並叫用多個目標方法的委派。</span><span class="sxs-lookup"><span data-stu-id="29eae-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="29eae-176">但經過證實，這種區隔的實務效果比原先設想的還要差。</span><span class="sxs-lookup"><span data-stu-id="29eae-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="29eae-177">不過這兩個不同的類別自其初始公開版本就已經建立，且在架構當中。</span><span class="sxs-lookup"><span data-stu-id="29eae-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="29eae-178">您最常搭配使用委派的方法是 `Invoke()` 和 `BeginInvoke()` / `EndInvoke()`。</span><span class="sxs-lookup"><span data-stu-id="29eae-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="29eae-179">`Invoke()` 會叫用已附加至特定委派執行個體的所有方法。</span><span class="sxs-lookup"><span data-stu-id="29eae-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="29eae-180">如上方所見，您通常會使用委派變數上的方法呼叫語法來叫用委派。</span><span class="sxs-lookup"><span data-stu-id="29eae-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="29eae-181">您可在[本系列中稍後](delegates-patterns.md)看到直接使用這些方法的模式。</span><span class="sxs-lookup"><span data-stu-id="29eae-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="29eae-182">現在，您已經看到語言語法和支援委託的類，讓我們來檢查如何使用、創建和調用鍵入的委託。</span><span class="sxs-lookup"><span data-stu-id="29eae-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created, and invoked.</span></span>

[<span data-ttu-id="29eae-183">下一步</span><span class="sxs-lookup"><span data-stu-id="29eae-183">Next</span></span>](delegates-strongly-typed.md)
