---
title: C# 的新功能 - C# 指南
description: C# 語言的進化方式
ms.date: 11/13/2017
ms.assetid: 77deec51-a14d-46d4-9bb3-faf449477149
ms.openlocfilehash: 3fc42809943b10d09d59780576dd9768d9e16ec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c"></a><span data-ttu-id="887f5-103">C# 的新功能</span><span class="sxs-lookup"><span data-stu-id="887f5-103">What's new in C#</span></span> #

<span data-ttu-id="887f5-104">此頁面提供 C# 語言每個主要版本的新功能藍圖。</span><span class="sxs-lookup"><span data-stu-id="887f5-104">This page provides a roadmap of new features in each major release of the C# language.</span></span> <span data-ttu-id="887f5-105">下列連結提供每個版本中新增主要功能的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="887f5-105">The following links provide detailed information on the major features added in each release.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="887f5-106">C# 語言中的部分功能仰賴「標準程式庫」中的型別和方法。</span><span class="sxs-lookup"><span data-stu-id="887f5-106">The C# language relies on types and methods in a *standard library* for some of the features.</span></span> <span data-ttu-id="887f5-107">例外狀況處理便是其中一個例子。</span><span class="sxs-lookup"><span data-stu-id="887f5-107">One example is exception processing.</span></span> <span data-ttu-id="887f5-108">每個 `throw` 陳述式或運算式都會受到檢查，以確保擲回衍生自 <xref:System.Exception> 的物件。</span><span class="sxs-lookup"><span data-stu-id="887f5-108">Every `throw` statement or expression is checked to ensure the object being thrown is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="887f5-109">每個 `catch` 也一樣會受到檢查，以確保攔截到衍生自 <xref:System.Exception> 的型別。</span><span class="sxs-lookup"><span data-stu-id="887f5-109">Similarly, every `catch` is checked to ensure that the type being caught is derived from <xref:System.Exception>.</span></span> <span data-ttu-id="887f5-110">每個版本都可能會加入新的需求。</span><span class="sxs-lookup"><span data-stu-id="887f5-110">Each version may add new requirements.</span></span> <span data-ttu-id="887f5-111">若要在較舊的環境中使用最新的語言功能，可能需要安裝特定的程式庫。</span><span class="sxs-lookup"><span data-stu-id="887f5-111">To use the latest language features in older environments, you may need to install specific libraries.</span></span> <span data-ttu-id="887f5-112">每個特定版本的頁面中會記載這些相依性。</span><span class="sxs-lookup"><span data-stu-id="887f5-112">These dependencies are documented in the page for each specific version.</span></span> <span data-ttu-id="887f5-113">若要知道此相依性的背景，可深入了解[語言和程式庫之間的關係](relationships-between-language-and-library.md)。</span><span class="sxs-lookup"><span data-stu-id="887f5-113">You can learn more about the [relationships between language and library](relationships-between-language-and-library.md) for background on this dependency.</span></span> 


* <span data-ttu-id="887f5-114">[C# 7.2](csharp-7-2.md):</span><span class="sxs-lookup"><span data-stu-id="887f5-114">[C# 7.2](csharp-7-2.md):</span></span>
    - <span data-ttu-id="887f5-115">此頁面說明 C# 語言中的最新功能。</span><span class="sxs-lookup"><span data-stu-id="887f5-115">This page describes the latest features in the C# language.</span></span> <span data-ttu-id="887f5-116">[Visual Studio 2017 15.5 版](https://www.visualstudio.com/vs/whatsnew/)和 [.NET Core 2.0 SDK](../../core/whats-new/index.md) 目前提供 C# 7.2。</span><span class="sxs-lookup"><span data-stu-id="887f5-116">C# 7.2 is currently available in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="887f5-117">[C# 7.1](csharp-7-1.md)：</span><span class="sxs-lookup"><span data-stu-id="887f5-117">[C# 7.1](csharp-7-1.md):</span></span>
    - <span data-ttu-id="887f5-118">此頁面描述 C# 7.1 中的功能。</span><span class="sxs-lookup"><span data-stu-id="887f5-118">This page describes the features in C# 7.1.</span></span> <span data-ttu-id="887f5-119">[Visual Studio 2017 15.3 版](https://www.visualstudio.com/vs/whatsnew/)和 [.NET Core 2.0 SDK](../../core/whats-new/index.md) 已新增這些功能。</span><span class="sxs-lookup"><span data-stu-id="887f5-119">These features were added in [Visual Studio 2017 version 15.3](https://www.visualstudio.com/vs/whatsnew/), and in the [.NET Core 2.0 SDK](../../core/whats-new/index.md).</span></span>

* <span data-ttu-id="887f5-120">[C# 7.0](csharp-7.md)：</span><span class="sxs-lookup"><span data-stu-id="887f5-120">[C# 7.0](csharp-7.md):</span></span>
    - <span data-ttu-id="887f5-121">此頁面說明 C# 7.0 中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="887f5-121">This page describes the features added in C# 7.0.</span></span> <span data-ttu-id="887f5-122">[Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) 和 [.NET Core 1.0](../../core/whats-new/index.md) 及更新版本已新增這些功能</span><span class="sxs-lookup"><span data-stu-id="887f5-122">These features were added in [Visual Studio 2017](https://www.visualstudio.com/vs/whatsnew/) and [.NET Core 1.0](../../core/whats-new/index.md) and later</span></span>
     
* <span data-ttu-id="887f5-123">[C# 6](csharp-6.md)：</span><span class="sxs-lookup"><span data-stu-id="887f5-123">[C# 6](csharp-6.md):</span></span>
    - <span data-ttu-id="887f5-124">此頁面說明 C# 6 中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="887f5-124">This page describes the features that were added in C# 6.</span></span> <span data-ttu-id="887f5-125">若是 Windows 開發人員，這些功能可在 Visual Studio 2015 中使用。若是在 macOS 和 Linux 上探索 C# 的開發人員，則可在 .NET Core 1.0 中使用。</span><span class="sxs-lookup"><span data-stu-id="887f5-125">These features are available in Visual Studio 2015 for Windows developers, and on .NET Core 1.0 for developers exploring C# on macOS and Linux.</span></span>

<!--* [C# Interactive](../interactive/index.md): 
    - This page describes C# Interactive, an interactive Read Eval Print Loop (REPL) that you can use to explore the C# language. You can use it to write code interactively and see it execute immediately, without any compile or build step.
-->
* <span data-ttu-id="887f5-126">[跨平台支援](../../core/index.md)：</span><span class="sxs-lookup"><span data-stu-id="887f5-126">[Cross Platform Support](../../core/index.md):</span></span>
    - <span data-ttu-id="887f5-127">透過 .NET Core 支援，C# 可在多種平台上執行。</span><span class="sxs-lookup"><span data-stu-id="887f5-127">C#, through .NET Core support, runs on multiple platforms.</span></span> <span data-ttu-id="887f5-128">如果您有興趣在 macOS 或是其中一個支援的 Linux 發行版本上嘗試 C#，請深入了解 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="887f5-128">If you are interested in trying C# on macOS, or on one of the many supported Linux distributions, learn more about .NET Core.</span></span>

<!--
- [.NET Compiler Platform SDK](../roslyn/index.md):
    - The .NET Compiler Platform SDK enables you to write code that performs static analysis on C# code. You can use these APIs to find potential errors, or bad practices, suggest fixes, and even implement those fixes.
-->
  
## <a name="previous-versions"></a><span data-ttu-id="887f5-129">舊版本</span><span class="sxs-lookup"><span data-stu-id="887f5-129">Previous Versions</span></span>
<span data-ttu-id="887f5-130">以下列出舊版 C# 語言及 Visual Studio .NET 中引入的重要功能。</span><span class="sxs-lookup"><span data-stu-id="887f5-130">The following lists key features that were introduced in previous versions of the C# language and Visual Studio .NET.</span></span>  
  
 * <span data-ttu-id="887f5-131">Visual Studio .NET 2013：</span><span class="sxs-lookup"><span data-stu-id="887f5-131">Visual Studio .NET 2013:</span></span> 
     - <span data-ttu-id="887f5-132">此版 Visual Studio 包括 Bug 修正、效能改進，以及 .NET 編譯器平台 (“Roslyn”) (後來成為 .NET 編譯器平台 SDK<!--Link to ../roslyn/index.md-->) 的技術預覽。</span><span class="sxs-lookup"><span data-stu-id="887f5-132">This version of Visual Studio included bug fixes, performance improvements, and technology previews of .NET Compiler Platform ("Roslyn") which became the .NET Compiler Platform SDK<!--Link to ../roslyn/index.md-->.</span></span>

 * <span data-ttu-id="887f5-133">C# 5 / Visual Studio .NET 2012：</span><span class="sxs-lookup"><span data-stu-id="887f5-133">C# 5, Visual Studio .NET 2012:</span></span> 
     - <span data-ttu-id="887f5-134">`Async` / `await`，及[呼叫者資訊](../programming-guide/concepts/caller-information.md)屬性。</span><span class="sxs-lookup"><span data-stu-id="887f5-134">`Async` / `await`, and [caller information](../programming-guide/concepts/caller-information.md) attributes.</span></span>

 * <span data-ttu-id="887f5-135">C# 4 / Visual Studio .NET 2010：</span><span class="sxs-lookup"><span data-stu-id="887f5-135">C# 4, Visual Studio .NET 2010:</span></span> 
     - <span data-ttu-id="887f5-136">`Dynamic`、[具名引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)、選擇性參數及泛型[共變數/反變數](../programming-guide/concepts/covariance-contravariance/index.md)。</span><span class="sxs-lookup"><span data-stu-id="887f5-136">`Dynamic`, [named arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md), optional parameters, and generic [covariance and contra variance](../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

 * <span data-ttu-id="887f5-137">C# 3 / Visual Studio .NET 2008：</span><span class="sxs-lookup"><span data-stu-id="887f5-137">C# 3, Visual Studio .NET 2008:</span></span> 
     - <span data-ttu-id="887f5-138">物件和集合初始設定式、Lambda 運算式、擴充方法、匿名類型、自動屬性、區域`var`型別推斷、及 [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="887f5-138">Object and collection initializers, lambda expressions, extension methods, anonymous types, automatic properties, local `var` type inference, and [Language Integrated Query (LINQ)](../programming-guide/concepts/linq/index.md).</span></span>

 * <span data-ttu-id="887f5-139">C# 2 / Visual Studio .NET 2005：</span><span class="sxs-lookup"><span data-stu-id="887f5-139">C# 2, Visual Studio .NET 2005:</span></span> 
     - <span data-ttu-id="887f5-140">匿名方法、泛型、可為 Null 的型別、迭代器/yield、`static` 類別，以及委派的共變數/反變數。</span><span class="sxs-lookup"><span data-stu-id="887f5-140">Anonymous methods, generics, nullable types, iterators/yield, `static` classes, and covariance and contra variance for delegates.</span></span>

 * <span data-ttu-id="887f5-141">C# 1.1 / Visual Studio .NET 2003：</span><span class="sxs-lookup"><span data-stu-id="887f5-141">C# 1.1, Visual Studio .NET 2003:</span></span> 
     - <span data-ttu-id="887f5-142">`#line` pragma 和 XML 文件註解。</span><span class="sxs-lookup"><span data-stu-id="887f5-142">`#line` pragma and xml doc comments.</span></span>

 * <span data-ttu-id="887f5-143">C# 1 / Visual Studio .NET 2002：</span><span class="sxs-lookup"><span data-stu-id="887f5-143">C# 1, Visual Studio .NET 2002:</span></span> 
     - <span data-ttu-id="887f5-144">[C#](../csharp.md) 的初次發行。</span><span class="sxs-lookup"><span data-stu-id="887f5-144">The first release of [C#](../csharp.md).</span></span>   
