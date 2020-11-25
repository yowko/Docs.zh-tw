---
title: 規則運算式中的編譯和重複使用
ms.date: 03/30/2017
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET regular expressions, engines
- .NET regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
ms.openlocfilehash: b0d3ac619e8d9548fffcb41b23d2ebd6663915e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723203"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a><span data-ttu-id="5dd0a-102">規則運算式中的編譯和重複使用</span><span class="sxs-lookup"><span data-stu-id="5dd0a-102">Compilation and Reuse in Regular Expressions</span></span>

<span data-ttu-id="5dd0a-103">只要了解規則運算式引擎如何編譯運算式，以及了解如何快取規則運算式，您就可以使大量使用規則運算式的應用程式達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-103">You can optimize the performance of applications that make extensive use of regular expressions by understanding how the regular expression engine compiles expressions and by understanding how regular expressions are cached.</span></span> <span data-ttu-id="5dd0a-104">本主題討論編譯及快取。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-104">This topic discusses both compilation and caching.</span></span>  
  
## <a name="compiled-regular-expressions"></a><span data-ttu-id="5dd0a-105">編譯的規則運算式</span><span class="sxs-lookup"><span data-stu-id="5dd0a-105">Compiled Regular Expressions</span></span>  

 <span data-ttu-id="5dd0a-106">根據預設，規則運算式引擎會將規則運算式編譯為內部指令的序列 (這些是不同於 Microsoft Intermediate Language (MSIL) 的高階程式碼)。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-106">By default, the regular expression engine compiles a regular expression to a sequence of internal instructions (these are high-level codes that are different from Microsoft intermediate language, or MSIL).</span></span> <span data-ttu-id="5dd0a-107">當引擎執行規則運算式時，它將會解譯內部程式碼。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-107">When the engine executes a regular expression, it interprets the internal codes.</span></span>  
  
 <span data-ttu-id="5dd0a-108">如果 <xref:System.Text.RegularExpressions.Regex> 物件是以 <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> 選項所建構，它會將規則運算式明確地編譯為 MSIL 程式碼，而非高階規則運算式的內部指令。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-108">If a <xref:System.Text.RegularExpressions.Regex> object is constructed with the <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> option, it compiles the regular expression to explicit MSIL code instead of high-level regular expression internal instructions.</span></span> <span data-ttu-id="5dd0a-109">這允許 .NET 的 Just-in-Time (JIT) 編譯器將運算式轉換為原生機器碼以達到較高效能。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-109">This allows .NET's just-in-time (JIT) compiler to convert the expression to native machine code for higher performance.</span></span>  <span data-ttu-id="5dd0a-110">建立物件的成本 <xref:System.Text.RegularExpressions.Regex> 可能較高，但是執行相符專案的成本可能會很小。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-110">The cost of constructing the <xref:System.Text.RegularExpressions.Regex> object may be higher, but the cost of performing matches with it is likely to be much smaller.</span></span>

 <span data-ttu-id="5dd0a-111">替代方法是使用先行編譯的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-111">An alternative is to use precompiled regular expressions.</span></span> <span data-ttu-id="5dd0a-112">您可以使用 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> 方法，將您的所有運算式編譯為一個可重複使用的 DLL。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-112">You can compile all of your expressions into a reusable DLL by using the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> method.</span></span> <span data-ttu-id="5dd0a-113">這可避免在執行時間編譯的需求，但仍可從已編譯的正則運算式速度中獲益。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-113">This avoids the need to compile at run time while still benefiting from the speed of compiled regular expressions.</span></span>  
  
## <a name="the-regular-expressions-cache"></a><span data-ttu-id="5dd0a-114">規則運算式快取</span><span class="sxs-lookup"><span data-stu-id="5dd0a-114">The Regular Expressions Cache</span></span>  

 <span data-ttu-id="5dd0a-115">為了提升效能，規則運算式引擎會維護整個應用程式的已編譯規則運算式之快取。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-115">To improve performance, the regular expression engine maintains an application-wide cache of compiled regular expressions.</span></span> <span data-ttu-id="5dd0a-116">這個快取會儲存只有在靜態方法呼叫中使用的規則運算式模式</span><span class="sxs-lookup"><span data-stu-id="5dd0a-116">The cache stores regular expression patterns that are used only in static method calls.</span></span> <span data-ttu-id="5dd0a-117">不會快取提供給實例方法 (正則運算式模式。 ) 這可避免在每次使用時，都必須將運算式重新剖析為高階位元組程式碼。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-117">(Regular expression patterns supplied to instance methods are not cached.) This avoids the need to reparse an expression into high-level byte code each time it is used.</span></span>  
  
 <span data-ttu-id="5dd0a-118">快取的規則運算式數目上限取決於 `static` (在 Visual Basic 中為 `Shared`) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-118">The maximum number of cached regular expressions is determined by the value of the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5dd0a-119">根據預設，規則運算式引擎最多可快取 15 個已編譯的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-119">By default, the regular expression engine caches up to 15 compiled regular expressions.</span></span> <span data-ttu-id="5dd0a-120">如果編譯的規則運算式數目超出快取大小，就會捨棄最近最少使用的規則運算式，並快取新的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-120">If the number of compiled regular expressions exceeds the cache size, the least recently used regular expression is discarded and the new regular expression is cached.</span></span>  
  
 <span data-ttu-id="5dd0a-121">您的應用程式可以透過下列兩種方式之一重複使用正則運算式：</span><span class="sxs-lookup"><span data-stu-id="5dd0a-121">Your application can reuse regular expressions in one of the following two ways:</span></span>  
  
- <span data-ttu-id="5dd0a-122">使用 <xref:System.Text.RegularExpressions.Regex> 物件的靜態方法來定義規則運算式。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-122">By using a static method of the <xref:System.Text.RegularExpressions.Regex> object to define the regular expression.</span></span> <span data-ttu-id="5dd0a-123">如果您使用的正則運算式模式已由另一個靜態方法呼叫定義，則正則運算式引擎會嘗試從快取中取出。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-123">If you're using a regular expression pattern that has already been defined by another static method call, the regular expression engine will try to retrieve it from the cache.</span></span> <span data-ttu-id="5dd0a-124">如果快取中未提供，引擎將會編譯正則運算式，並將它新增至快取。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-124">If it's not available in the cache, the engine will compile the regular expression and add it to the cache.</span></span>
  
- <span data-ttu-id="5dd0a-125">在需要現有 <xref:System.Text.RegularExpressions.Regex> 物件的規則運算式模式時重複使用該物件。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-125">By reusing an existing <xref:System.Text.RegularExpressions.Regex> object as long as its regular expression pattern is needed.</span></span>  
  
 <span data-ttu-id="5dd0a-126">由於物件具現化和規則運算式編譯會造成額外負荷，因此建立及快速終結多個 <xref:System.Text.RegularExpressions.Regex> 物件是個非常耗費資源的處理序。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-126">Because of the overhead of object instantiation and regular expression compilation, creating and rapidly destroying numerous <xref:System.Text.RegularExpressions.Regex> objects is a very expensive process.</span></span> <span data-ttu-id="5dd0a-127">對於使用大量不同規則運算式的應用程式，您可以使用靜態 `Regex` 方法的呼叫，或增加規則運算式快取的大小，以達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="5dd0a-127">For applications that use a large number of different regular expressions, you can optimize performance by using calls to static `Regex` methods and possibly by increasing the size of the regular expression cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd0a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dd0a-128">See also</span></span>

- [<span data-ttu-id="5dd0a-129">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="5dd0a-129">.NET Regular Expressions</span></span>](regular-expressions.md)
