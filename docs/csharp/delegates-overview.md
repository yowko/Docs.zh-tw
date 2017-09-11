---
title: "委派簡介"
description: "委派簡介"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f68742a02ebf12e222b2fa6827352a3684de5648
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---

# <a name="introduction-to-delegates"></a><span data-ttu-id="9f8cb-104">委派簡介</span><span class="sxs-lookup"><span data-stu-id="9f8cb-104">Introduction to Delegates</span></span>

[<span data-ttu-id="9f8cb-105">上一個</span><span class="sxs-lookup"><span data-stu-id="9f8cb-105">Previous</span></span>](delegates-events.md)

<span data-ttu-id="9f8cb-106">委派提供 .NET 中的「晚期繫結」**機制。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-106">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="9f8cb-107">「晚期繫結」表示您建立演算法，在其中，呼叫端也會提供至少一個方法來實作演算法的一部分。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-107">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="9f8cb-108">例如，請考慮排序天文學應用程式中的星星清單。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-108">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="9f8cb-109">您可以選擇排序這些星星與地球的距離、星星的亮度，或其可察覺的亮度。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-109">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="9f8cb-110">在所有這些情況下，Sort() 方法的做法基本上相同︰根據某個比較來排列清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-110">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="9f8cb-111">針對每個排序順序，比較兩顆星的程式碼會不同。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-111">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="9f8cb-112">這類解決方案已用於軟體達中半世紀之久。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-112">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="9f8cb-113">C# 語言委派概念提供一流的語言支援，以及這類概念的型別安全。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-113">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="9f8cb-114">如您將在本系列稍後所見，您為這類演算法所撰寫的 C# 程式碼為型別安全，並利用語言和編譯器確保引數和傳回型別的類型相符。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-114">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="9f8cb-115">委派的語言設計目標</span><span class="sxs-lookup"><span data-stu-id="9f8cb-115">Language Design Goals for Delegates</span></span>

<span data-ttu-id="9f8cb-116">語言設計人員會針對最後成為委派的功能列舉數個目標。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-116">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="9f8cb-117">小組想要將通用語言建構用於任何晚期繫結演算法。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-117">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="9f8cb-118">這可讓開發人員了解一個概念，並將這個相同的概念用於許多不同的軟體問題。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-118">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="9f8cb-119">其次，小組想要同時支援單一和多點傳送方法呼叫</span><span class="sxs-lookup"><span data-stu-id="9f8cb-119">Second, the team wanted to support both single and multi-cast method calls.</span></span> <span data-ttu-id="9f8cb-120">(多點傳送委派是已將多個方法鏈結在一起的委派)。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-120">(Multicast delegates are delegates where multiple methods have been chained together.</span></span> <span data-ttu-id="9f8cb-121">您將在[本系列稍後](delegate-class.md)看到範例。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-121">You'll see examples [later in this series](delegate-class.md).</span></span> 

<span data-ttu-id="9f8cb-122">小組想要委派支援開發人員期待所有 C# 建構的相同型別安全。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-122">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="9f8cb-123">最後，小組已辨識事件模式是委派或任何晚期繫結演算法十分有用的一種特定模式。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-123">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm) is very useful.</span></span> <span data-ttu-id="9f8cb-124">小組想要確保委派的程式碼可以提供 .NET 事件模式的基礎。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-124">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="9f8cb-125">該工作的結果已是 C# 和 .NET 中的委派和事件支援。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-125">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="9f8cb-126">本節的其餘文章將涵蓋語言功能、程式庫支援，以及使用委派時所使用的一般慣用語。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-126">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="9f8cb-127">您將了解 `delegate` 關鍵字和其所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-127">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="9f8cb-128">您將了解 `System.Delegate` 類別的功能，以及如何使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-128">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="9f8cb-129">您將了解如何建立型別安全委派，以及如何建立可透過委派叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-129">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="9f8cb-130">您也將了解如何使用 Lambda 運算式來使用委派和事件。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-130">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="9f8cb-131">您將看到委派成為一個 LINQ 之建置區塊的位置。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-131">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="9f8cb-132">您將了解委派如何是 .NET 事件模式的基礎和其差異。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-132">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="9f8cb-133">整體來說，您將看到委派如何在 .NET 中進行程式設計以及使用架構 API 時成為不可或缺部分。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-133">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="9f8cb-134">我們現在就開始吧。</span><span class="sxs-lookup"><span data-stu-id="9f8cb-134">Let's get started.</span></span>

[<span data-ttu-id="9f8cb-135">下一個</span><span class="sxs-lookup"><span data-stu-id="9f8cb-135">Next</span></span>](delegate-class.md)

