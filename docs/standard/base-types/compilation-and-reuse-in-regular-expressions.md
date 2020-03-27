---
title: 規則運算式中的編譯和重複使用
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET Framework regular expressions, engines
- .NET Framework regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
ms.openlocfilehash: b89f7f88233ecdab25ba2a74647aafeb4d8b74af
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344183"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a><span data-ttu-id="e68e5-102">規則運算式中的編譯和重複使用</span><span class="sxs-lookup"><span data-stu-id="e68e5-102">Compilation and Reuse in Regular Expressions</span></span>
<span data-ttu-id="e68e5-103">只要了解規則運算式引擎如何編譯運算式，以及了解如何快取規則運算式，您就可以使大量使用規則運算式的應用程式達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="e68e5-103">You can optimize the performance of applications that make extensive use of regular expressions by understanding how the regular expression engine compiles expressions and by understanding how regular expressions are cached.</span></span> <span data-ttu-id="e68e5-104">本主題討論編譯及快取。</span><span class="sxs-lookup"><span data-stu-id="e68e5-104">This topic discusses both compilation and caching.</span></span>  
  
## <a name="compiled-regular-expressions"></a><span data-ttu-id="e68e5-105">編譯的規則運算式</span><span class="sxs-lookup"><span data-stu-id="e68e5-105">Compiled Regular Expressions</span></span>  
 <span data-ttu-id="e68e5-106">根據預設，規則運算式引擎會將規則運算式編譯為內部指令的序列 (這些是不同於 Microsoft Intermediate Language (MSIL) 的高階程式碼)。</span><span class="sxs-lookup"><span data-stu-id="e68e5-106">By default, the regular expression engine compiles a regular expression to a sequence of internal instructions (these are high-level codes that are different from Microsoft intermediate language, or MSIL).</span></span> <span data-ttu-id="e68e5-107">當引擎執行規則運算式時，它將會解譯內部程式碼。</span><span class="sxs-lookup"><span data-stu-id="e68e5-107">When the engine executes a regular expression, it interprets the internal codes.</span></span>  
  
 <span data-ttu-id="e68e5-108">如果 <xref:System.Text.RegularExpressions.Regex> 物件是以 <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> 選項所建構，它會將規則運算式明確地編譯為 MSIL 程式碼，而非高階規則運算式的內部指令。</span><span class="sxs-lookup"><span data-stu-id="e68e5-108">If a <xref:System.Text.RegularExpressions.Regex> object is constructed with the <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> option, it compiles the regular expression to explicit MSIL code instead of high-level regular expression internal instructions.</span></span> <span data-ttu-id="e68e5-109">這允許 .NET 的 Just-in-Time (JIT) 編譯器將運算式轉換為原生機器碼以達到較高效能。</span><span class="sxs-lookup"><span data-stu-id="e68e5-109">This allows .NET's just-in-time (JIT) compiler to convert the expression to native machine code for higher performance.</span></span>  <span data-ttu-id="e68e5-110">構造<xref:System.Text.RegularExpressions.Regex>物件的成本可能更高，但與物件執行匹配的成本可能要小得多。</span><span class="sxs-lookup"><span data-stu-id="e68e5-110">The cost of constructing the <xref:System.Text.RegularExpressions.Regex> object may be higher, but the cost of performing matches with it is likely to be much smaller.</span></span>

 <span data-ttu-id="e68e5-111">替代方法是使用先行編譯的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="e68e5-111">An alternative is to use precompiled regular expressions.</span></span> <span data-ttu-id="e68e5-112">您可以使用 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> 方法，將您的所有運算式編譯為一個可重複使用的 DLL。</span><span class="sxs-lookup"><span data-stu-id="e68e5-112">You can compile all of your expressions into a reusable DLL by using the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> method.</span></span> <span data-ttu-id="e68e5-113">這樣可避免需要在執行階段進行編譯，同時仍能從已編譯之規則運算式的速度中獲益。</span><span class="sxs-lookup"><span data-stu-id="e68e5-113">This avoids the need to compile at runtime while still benefiting from the speed of compiled regular expressions.</span></span>  
  
## <a name="the-regular-expressions-cache"></a><span data-ttu-id="e68e5-114">規則運算式快取</span><span class="sxs-lookup"><span data-stu-id="e68e5-114">The Regular Expressions Cache</span></span>  
 <span data-ttu-id="e68e5-115">為了提升效能，規則運算式引擎會維護整個應用程式的已編譯規則運算式之快取。</span><span class="sxs-lookup"><span data-stu-id="e68e5-115">To improve performance, the regular expression engine maintains an application-wide cache of compiled regular expressions.</span></span> <span data-ttu-id="e68e5-116">這個快取會儲存只有在靜態方法呼叫中使用的規則運算式模式</span><span class="sxs-lookup"><span data-stu-id="e68e5-116">The cache stores regular expression patterns that are used only in static method calls.</span></span> <span data-ttu-id="e68e5-117">（不緩存提供給實例方法的正則運算式模式。這樣可以避免每次使用運算式時都需要將運算式重新解析為高級位元組代碼。</span><span class="sxs-lookup"><span data-stu-id="e68e5-117">(Regular expression patterns supplied to instance methods are not cached.) This avoids the need to reparse an expression into high-level byte code each time it is used.</span></span>  
  
 <span data-ttu-id="e68e5-118">快取的規則運算式數目上限取決於 `static` (在 Visual Basic 中為 `Shared`) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="e68e5-118">The maximum number of cached regular expressions is determined by the value of the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e68e5-119">根據預設，規則運算式引擎最多可快取 15 個已編譯的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="e68e5-119">By default, the regular expression engine caches up to 15 compiled regular expressions.</span></span> <span data-ttu-id="e68e5-120">如果編譯的規則運算式數目超出快取大小，就會捨棄最近最少使用的規則運算式，並快取新的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="e68e5-120">If the number of compiled regular expressions exceeds the cache size, the least recently used regular expression is discarded and the new regular expression is cached.</span></span>  
  
 <span data-ttu-id="e68e5-121">應用程式可以通過以下兩種方式之一重用正則運算式：</span><span class="sxs-lookup"><span data-stu-id="e68e5-121">Your application can reuse regular expressions in one of the following two ways:</span></span>  
  
- <span data-ttu-id="e68e5-122">使用 <xref:System.Text.RegularExpressions.Regex> 物件的靜態方法來定義規則運算式。</span><span class="sxs-lookup"><span data-stu-id="e68e5-122">By using a static method of the <xref:System.Text.RegularExpressions.Regex> object to define the regular expression.</span></span> <span data-ttu-id="e68e5-123">如果您使用的是已由另一個靜態方法調用定義的正則運算式模式，則正則運算式引擎將嘗試從緩存中檢索它。</span><span class="sxs-lookup"><span data-stu-id="e68e5-123">If you're using a regular expression pattern that has already been defined by another static method call, the regular expression engine will try to retrieve it from the cache.</span></span> <span data-ttu-id="e68e5-124">如果緩存中不可用，引擎將編譯正則運算式並將其添加到緩存中。</span><span class="sxs-lookup"><span data-stu-id="e68e5-124">If it's not available in the cache, the engine will compile the regular expression and add it to the cache.</span></span>
  
- <span data-ttu-id="e68e5-125">在需要現有 <xref:System.Text.RegularExpressions.Regex> 物件的規則運算式模式時重複使用該物件。</span><span class="sxs-lookup"><span data-stu-id="e68e5-125">By reusing an existing <xref:System.Text.RegularExpressions.Regex> object as long as its regular expression pattern is needed.</span></span>  
  
 <span data-ttu-id="e68e5-126">由於物件具現化和規則運算式編譯會造成額外負荷，因此建立及快速終結多個 <xref:System.Text.RegularExpressions.Regex> 物件是個非常耗費資源的處理序。</span><span class="sxs-lookup"><span data-stu-id="e68e5-126">Because of the overhead of object instantiation and regular expression compilation, creating and rapidly destroying numerous <xref:System.Text.RegularExpressions.Regex> objects is a very expensive process.</span></span> <span data-ttu-id="e68e5-127">對於使用大量不同規則運算式的應用程式，您可以使用靜態 `Regex` 方法的呼叫，或增加規則運算式快取的大小，以達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="e68e5-127">For applications that use a large number of different regular expressions, you can optimize performance by using calls to static `Regex` methods and possibly by increasing the size of the regular expression cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e68e5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e68e5-128">See also</span></span>

- [<span data-ttu-id="e68e5-129">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="e68e5-129">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
