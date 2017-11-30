---
title: "強類型委派"
description: "了解如何在建立需要委派的功能時，使用泛型委派類型來宣告自訂類型。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 467ba18f8e032b9b3b8f480d4b10c92d0d7ba3b9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="4b22e-104">強類型委派</span><span class="sxs-lookup"><span data-stu-id="4b22e-104">Strongly Typed Delegates</span></span>

[<span data-ttu-id="4b22e-105">上一個</span><span class="sxs-lookup"><span data-stu-id="4b22e-105">Previous</span></span>](delegate-class.md)

<span data-ttu-id="4b22e-106">在前一篇文章中，您看到您使用 `delegate` 關鍵字來建立特定委派類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-106">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="4b22e-107">抽象委派類別提供進行鬆散結合和叫用的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="4b22e-107">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="4b22e-108">具體委派類型會變得更為好用，原因是採行和強制新增至委派物件的引動過程清單之方法的型別安全。</span><span class="sxs-lookup"><span data-stu-id="4b22e-108">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="4b22e-109">當您使用 `delegate` 關鍵字並定義具體委派類型時，編譯器會產生這些方法。</span><span class="sxs-lookup"><span data-stu-id="4b22e-109">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="4b22e-110">實際上，只要您需要不同的方法簽章，這就會建立新的委派類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-110">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="4b22e-111">這項工作在一段時間之後會十分繁瑣。</span><span class="sxs-lookup"><span data-stu-id="4b22e-111">This work could get tedious after a time.</span></span> <span data-ttu-id="4b22e-112">每項新功能都需要新的委派類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-112">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="4b22e-113">還好，這不是必要的。</span><span class="sxs-lookup"><span data-stu-id="4b22e-113">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="4b22e-114">.NET 核心架構包含您只要需要委派類型即可重複使用的數個類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-114">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="4b22e-115">這些是[泛型](programming-guide/generics/index.md)定義，因此當您需要新的方法宣告時，可以宣告自訂項目。</span><span class="sxs-lookup"><span data-stu-id="4b22e-115">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="4b22e-116">這些類型的第一個是 <xref:System.Action> 類型和數個變化：</span><span class="sxs-lookup"><span data-stu-id="4b22e-116">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="4b22e-117">有關共變數的文章涵蓋泛型型別引數上的 `in` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="4b22e-117">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="4b22e-118">有多種變化`Action`委派，其中包含最多 16 個引數，例如<xref:System.Action%6016>。</span><span class="sxs-lookup"><span data-stu-id="4b22e-118">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="4b22e-119">這些定義一定要為每個委派引數使用不同的泛型引數：這讓您擁有最大的彈性。</span><span class="sxs-lookup"><span data-stu-id="4b22e-119">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="4b22e-120">方法引數不需要但可以是相同的類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-120">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="4b22e-121">針對任何具有 void 傳回型別的委派類型，使用其中一個 `Action` 類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-121">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="4b22e-122">此架構也包含數個泛型委派類型，可用於傳回值的委派類型︰</span><span class="sxs-lookup"><span data-stu-id="4b22e-122">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="4b22e-123">有關共變數的文章涵蓋結果泛型型別引數上的 `out` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="4b22e-123">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="4b22e-124">有多種變化`Func`這類最多 16 個輸入引數與委派<xref:System.Func%6017>。</span><span class="sxs-lookup"><span data-stu-id="4b22e-124">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="4b22e-125">依照慣例，結果的類型一律是所有 `Func` 宣告中的最後一個型別參數。</span><span class="sxs-lookup"><span data-stu-id="4b22e-125">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="4b22e-126">針對任何傳回值的委派類型，使用其中一個 `Func` 類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-126">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="4b22e-127">沒有也特殊<xref:System.Predicate%601>委派，會傳回單一值的測試類型：</span><span class="sxs-lookup"><span data-stu-id="4b22e-127">There's also a specialized <xref:System.Predicate%601> type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="4b22e-128">您可能會注意到，針對任何 `Predicate` 類型，會有結構上相等的 `Func` 類型。例如︰</span><span class="sxs-lookup"><span data-stu-id="4b22e-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="4b22e-129">您可能會將這兩個類型視為相等。</span><span class="sxs-lookup"><span data-stu-id="4b22e-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="4b22e-130">但它們並不相等。</span><span class="sxs-lookup"><span data-stu-id="4b22e-130">They are not.</span></span>
<span data-ttu-id="4b22e-131">這兩個變數不能交換使用。</span><span class="sxs-lookup"><span data-stu-id="4b22e-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="4b22e-132">某個類型的變數無法獲指派另一個類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="4b22e-133">C# 型別系統會使用所定義類型的名稱，而不是結構。</span><span class="sxs-lookup"><span data-stu-id="4b22e-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="4b22e-134">.NET 核心程式庫中的所有這些委派類型定義都應該表示，您不需要針對任何您所建立且需要委派的新功能定義新的委派類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="4b22e-135">這些泛型定義應該提供您在大部分情況下所需要的所有委派類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="4b22e-136">您可以只具現化具有必要型別參數的其中一個類型。</span><span class="sxs-lookup"><span data-stu-id="4b22e-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="4b22e-137">如果是可以設為泛型的演算法，則可以將這些委派用作泛型型別。</span><span class="sxs-lookup"><span data-stu-id="4b22e-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="4b22e-138">這應該會節省時間，並將您建立來使用委派所需的新類型數目減到最少。</span><span class="sxs-lookup"><span data-stu-id="4b22e-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="4b22e-139">在下一篇文章中，您將看到實際使用委派的數個常見模式。</span><span class="sxs-lookup"><span data-stu-id="4b22e-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="4b22e-140">下一個</span><span class="sxs-lookup"><span data-stu-id="4b22e-140">Next</span></span>](delegates-patterns.md)
