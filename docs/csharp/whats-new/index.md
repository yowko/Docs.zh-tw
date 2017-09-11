---
title: "C# 的新功能 - C# 指南"
description: "C# 語言的進化方式"
keywords: "C#, 最新功能, 新功能, Roslyn"
author: BillWagner
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.translationtype: HT
ms.sourcegitcommit: 195b2206eec0a8f070454aed1ddefe56ee92adc9
ms.openlocfilehash: 7b7cb235e2ba5bc3c9a21603058eb20475766ea7
ms.contentlocale: zh-tw
ms.lasthandoff: 08/15/2017

---

# <a name="whats-new-in-c"></a><span data-ttu-id="2c79c-104">C# 的新功能</span><span class="sxs-lookup"><span data-stu-id="2c79c-104">What's new in C#</span></span> #

<span data-ttu-id="2c79c-105">此頁面提供 C# 語言每個主要版本的新功能藍圖。</span><span class="sxs-lookup"><span data-stu-id="2c79c-105">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="2c79c-106">下列連結提供每個版本中新增主要功能的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2c79c-106">The links below provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c79c-107">C# 語言中的部分功能仰賴「標準程式庫」中的型別和方法。</span><span class="sxs-lookup"><span data-stu-id="2c79c-107">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="2c79c-108">例外狀況處理便是其中一個例子。</span><span class="sxs-lookup"><span data-stu-id="2c79c-108">One example is exception processing.</span></span> <span data-ttu-id="2c79c-109">每個 `throw` 陳述式或運算式都會受到檢查，以確保擲回衍生自 @System.Exception 的物件。</span><span class="sxs-lookup"><span data-stu-id="2c79c-109">Every `throw` statement or expression is checked to ensure the object being thrown is derived from @System.Exception.</span></span> <span data-ttu-id="2c79c-110">每個 `catch` 也一樣會受到檢查，以確保攔截到衍生自 @System.Exception 的型別。</span><span class="sxs-lookup"><span data-stu-id="2c79c-110">Similarly, every `catch` is checked to ensure that the type being caught is derived from @System.Exception.</span></span> <span data-ttu-id="2c79c-111">每個版本都可能會加入新的需求。</span><span class="sxs-lookup"><span data-stu-id="2c79c-111">Each version may add new requirements.</span></span> <span data-ttu-id="2c79c-112">若要在較舊的環境中使用最新的語言功能，可能需要安裝特定的程式庫。</span><span class="sxs-lookup"><span data-stu-id="2c79c-112">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="2c79c-113">相關說明請見每個特定版本的頁面。</span><span class="sxs-lookup"><span data-stu-id="2c79c-113">These are documented in the page for each specific version.</span></span> <span data-ttu-id="2c79c-114">若要知道此相依性的背景，可深入了解[語言和程式庫之間的關係](relationships-between-language-and-library.md)。</span><span class="sxs-lookup"><span data-stu-id="2c79c-114">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 

* <span data-ttu-id="2c79c-115">[C# 7](csharp-7.md)：</span><span class="sxs-lookup"><span data-stu-id="2c79c-115">[C# 7](csharp-7.md):</span></span>
    - <span data-ttu-id="2c79c-116">此頁面說明 C# 語言中的最新功能。</span><span class="sxs-lookup"><span data-stu-id="2c79c-116">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="2c79c-117">這涵蓋目前於 [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) 中提供使用的 C# 7。</span><span class="sxs-lookup"><span data-stu-id="2c79c-117">This covers C# 7, currently available in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/).</span></span>

* <span data-ttu-id="2c79c-118">[C# 6](csharp-6.md)：</span><span class="sxs-lookup"><span data-stu-id="2c79c-118">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="2c79c-119">此頁面說明 C# 6 中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="2c79c-119">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="2c79c-120">若是 Windows 開發人員，這些功能可在 Visual Studio 2015 中使用。若是在 macOS 和 Linux 上探索 C# 的開發人員，則可在 .NET Core 1.0 中使用。</span><span class="sxs-lookup"><span data-stu-id="2c79c-120">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="2c79c-121">[跨平台支援](../../core/index.md)：</span><span class="sxs-lookup"><span data-stu-id="2c79c-121">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="2c79c-122">透過 .NET Core 支援，C# 可在多種平台上執行。</span><span class="sxs-lookup"><span data-stu-id="2c79c-122">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="2c79c-123">如果您有興趣在 macOS 或是其中一個支援的 Linux 發行版本上嘗試 C#，請深入了解 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="2c79c-123">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="2c79c-124">舊版本</span><span class="sxs-lookup"><span data-stu-id="2c79c-124">Previous Versions</span></span>
<span data-ttu-id="2c79c-125">以下列出舊版 C# 語言及 Visual Studio .NET 中引入的重要功能。</span><span class="sxs-lookup"><span data-stu-id="2c79c-125">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="2c79c-126">Visual Studio .NET 2013：</span><span class="sxs-lookup"><span data-stu-id="2c79c-126">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="2c79c-127">此版 Visual Studio 包括 Bug 修正、效能改進，以及 .NET 編譯器平台 (“Roslyn”) (後來成為 .NET 編譯器平台 SDK<!--Link to ../roslyn/index.md-->) 的技術預覽。</span><span class="sxs-lookup"><span data-stu-id="2c79c-127">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="2c79c-128">C# 5 / Visual Studio .NET 2012：</span><span class="sxs-lookup"><span data-stu-id="2c79c-128">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="2c79c-129">`Async` / `await`，及[呼叫者資訊](../programming-guide/concepts/caller-information.md)屬性。</span><span class="sxs-lookup"><span data-stu-id="2c79c-129">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="2c79c-130">C# 4 / Visual Studio .NET 2010：</span><span class="sxs-lookup"><span data-stu-id="2c79c-130">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="2c79c-131">`Dynamic`、[具名引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)、選擇性參數及泛型[共變數/反變數](../programming-guide/concepts/covariance-contravariance/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2c79c-131">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="2c79c-132">C# 3 / Visual Studio .NET 2008：</span><span class="sxs-lookup"><span data-stu-id="2c79c-132">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="2c79c-133">物件和集合初始設定式、Lambda 運算式、擴充方法、匿名類型、自動屬性、區域`var`型別推斷、及 [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2c79c-133">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="2c79c-134">C# 2 / Visual Studio .NET 2005：</span><span class="sxs-lookup"><span data-stu-id="2c79c-134">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="2c79c-135">匿名方法、泛型、可為 Null 的型別、迭代器/yield、`static` 類別，以及委派的共變數/反變數。</span><span class="sxs-lookup"><span data-stu-id="2c79c-135">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="2c79c-136">C# 1.1 / Visual Studio .NET 2003：</span><span class="sxs-lookup"><span data-stu-id="2c79c-136">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="2c79c-137">`#line` pragma 和 XML 文件註解。</span><span class="sxs-lookup"><span data-stu-id="2c79c-137">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="2c79c-138">C# 1 / Visual Studio .NET 2002：</span><span class="sxs-lookup"><span data-stu-id="2c79c-138">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="2c79c-139">[C#](../csharp.md) 的初次發行。</span><span class="sxs-lookup"><span data-stu-id="2c79c-139">The first release of [C#](../csharp.md).</span></span>   

