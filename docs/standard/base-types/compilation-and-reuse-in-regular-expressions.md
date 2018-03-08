---
title: "規則運算式中的編譯和重複使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 230a1b8b083362c149b5b7e64f708bd09ab21788
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="compilation-and-reuse-in-regular-expressions"></a><span data-ttu-id="66eb5-102">規則運算式中的編譯和重複使用</span><span class="sxs-lookup"><span data-stu-id="66eb5-102">Compilation and Reuse in Regular Expressions</span></span>
<span data-ttu-id="66eb5-103">只要了解規則運算式引擎如何編譯運算式，以及了解如何快取規則運算式，您就可以使大量使用規則運算式的應用程式達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="66eb5-103">You can optimize the performance of applications that make extensive use of regular expressions by understanding how the regular expression engine compiles expressions and by understanding how regular expressions are cached.</span></span> <span data-ttu-id="66eb5-104">本主題討論編譯及快取。</span><span class="sxs-lookup"><span data-stu-id="66eb5-104">This topic discusses both compilation and caching.</span></span>  
  
## <a name="compiled-regular-expressions"></a><span data-ttu-id="66eb5-105">編譯的規則運算式</span><span class="sxs-lookup"><span data-stu-id="66eb5-105">Compiled Regular Expressions</span></span>  
 <span data-ttu-id="66eb5-106">根據預設，規則運算式引擎會將規則運算式編譯為內部指令的序列 (這些是不同於 Microsoft Intermediate Language (MSIL) 的高階程式碼)。</span><span class="sxs-lookup"><span data-stu-id="66eb5-106">By default, the regular expression engine compiles a regular expression to a sequence of internal instructions (these are high-level codes that are different from Microsoft intermediate language, or MSIL).</span></span> <span data-ttu-id="66eb5-107">當引擎執行規則運算式時，它將會解譯內部程式碼。</span><span class="sxs-lookup"><span data-stu-id="66eb5-107">When the engine executes a regular expression, it interprets the internal codes.</span></span>  
  
 <span data-ttu-id="66eb5-108">如果 <xref:System.Text.RegularExpressions.Regex> 物件是以 <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> 選項所建構，它會將規則運算式明確地編譯為 MSIL 程式碼，而非高階規則運算式的內部指令。</span><span class="sxs-lookup"><span data-stu-id="66eb5-108">If a <xref:System.Text.RegularExpressions.Regex> object is constructed with the <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> option, it compiles the regular expression to explicit MSIL code instead of high-level regular expression internal instructions.</span></span> <span data-ttu-id="66eb5-109">這允許 .NET 的 Just-in-Time (JIT) 編譯器將運算式轉換為原生機器碼以達到較高效能。</span><span class="sxs-lookup"><span data-stu-id="66eb5-109">This allows .NET's just-in-time (JIT) compiler to convert the expression to native machine code for higher performance.</span></span>  
  
<span data-ttu-id="66eb5-110">不過，產生的 MSIL 無法卸載。</span><span class="sxs-lookup"><span data-stu-id="66eb5-110">However, generated MSIL cannot be unloaded.</span></span> <span data-ttu-id="66eb5-111">卸載程式碼的唯一方式就是要卸載整個應用程式定義域 (也就是卸載您應用程式的所有程式碼)。</span><span class="sxs-lookup"><span data-stu-id="66eb5-111">The only way to unload code is to unload an entire application domain (that is, to unload all of your application's code.).</span></span> <span data-ttu-id="66eb5-112">實際上，以 <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> 選項編譯規則運算式之後，絕對不會釋放已編譯運算式所使用的資源，即使規則運算式是由 <xref:System.Text.RegularExpressions.Regex> 物件所建立，而且物件本身會被釋放以回收記憶體亦然。</span><span class="sxs-lookup"><span data-stu-id="66eb5-112">Effectively, once a regular expression is compiled with the <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> option,   never releases the resources used by the compiled expression, even if the regular expression was created by a <xref:System.Text.RegularExpressions.Regex> object that is itself released to garbage collection.</span></span>  
  
 <span data-ttu-id="66eb5-113">您必須小心限制以 <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> 選項編譯的不同規則運算式數目，以避免消耗太多資源。</span><span class="sxs-lookup"><span data-stu-id="66eb5-113">You must be careful to limit the number of different regular expressions you compile with the <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> option to avoid consuming too many resources.</span></span> <span data-ttu-id="66eb5-114">如果應用程式必須使用大量或未限制數目的規則運算式，應該要解譯而不是編譯各個運算式。</span><span class="sxs-lookup"><span data-stu-id="66eb5-114">If an application must use a large or unbounded number of regular expressions, each expression should be interpreted, not compiled.</span></span> <span data-ttu-id="66eb5-115">不過，如果要重複使用少數規則運算式，應該使用 <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> 進行編譯以獲得較高效能。</span><span class="sxs-lookup"><span data-stu-id="66eb5-115">However, if a small number of regular expressions are used repeatedly, they should be compiled with <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> for better performance.</span></span> <span data-ttu-id="66eb5-116">替代方法是使用先行編譯的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="66eb5-116">An alternative is to use precompiled regular expressions.</span></span> <span data-ttu-id="66eb5-117">您可以使用 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> 方法，將您的所有運算式編譯為一個可重複使用的 DLL。</span><span class="sxs-lookup"><span data-stu-id="66eb5-117">You can compile all of your expressions into a reusable DLL by using the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> method.</span></span> <span data-ttu-id="66eb5-118">這樣可避免需要在執行階段進行編譯，同時仍能從已編譯之規則運算式的速度中獲益。</span><span class="sxs-lookup"><span data-stu-id="66eb5-118">This avoids the need to compile at runtime while still benefiting from the speed of compiled regular expressions.</span></span>  
  
## <a name="the-regular-expressions-cache"></a><span data-ttu-id="66eb5-119">規則運算式快取</span><span class="sxs-lookup"><span data-stu-id="66eb5-119">The Regular Expressions Cache</span></span>  
 <span data-ttu-id="66eb5-120">為了提升效能，規則運算式引擎會維護整個應用程式的已編譯規則運算式之快取。</span><span class="sxs-lookup"><span data-stu-id="66eb5-120">To improve performance, the regular expression engine maintains an application-wide cache of compiled regular expressions.</span></span> <span data-ttu-id="66eb5-121">這個快取會儲存只有在靜態方法呼叫中使用的規則運算式模式</span><span class="sxs-lookup"><span data-stu-id="66eb5-121">The cache stores regular expression patterns that are used only in static method calls.</span></span> <span data-ttu-id="66eb5-122">(不會快取提供給執行個體方法的規則運算式模式)。這可避免在每次使用運算式時，必須將其重新剖析為高階位元組程式碼。</span><span class="sxs-lookup"><span data-stu-id="66eb5-122">(Regular expression patterns supplied to instance methods are not cached.) This avoids the need to reparse an expression into high-level byte code each time it is used.</span></span>  
  
 <span data-ttu-id="66eb5-123">快取的規則運算式數目上限取決於 `static` (在 Visual Basic 中為 `Shared`) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="66eb5-123">The maximum number of cached regular expressions is determined by the value of the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="66eb5-124">根據預設，規則運算式引擎最多可快取 15 個已編譯的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="66eb5-124">By default, the regular expression engine caches up to 15 compiled regular expressions.</span></span> <span data-ttu-id="66eb5-125">如果編譯的規則運算式數目超出快取大小，就會捨棄最近最少使用的規則運算式，並快取新的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="66eb5-125">If the number of compiled regular expressions exceeds the cache size, the least recently used regular expression is discarded and the new regular expression is cached.</span></span>  
  
 <span data-ttu-id="66eb5-126">您的應用程式可以透過下列其中一種方式，來利用預先編譯的規則運算式：</span><span class="sxs-lookup"><span data-stu-id="66eb5-126">Your application can take advantage of precompiled regular expressions in one of the following two ways:</span></span>  
  
-   <span data-ttu-id="66eb5-127">使用 <xref:System.Text.RegularExpressions.Regex> 物件的靜態方法來定義規則運算式。</span><span class="sxs-lookup"><span data-stu-id="66eb5-127">By using a static method of the <xref:System.Text.RegularExpressions.Regex> object to define the regular expression.</span></span> <span data-ttu-id="66eb5-128">如果您使用其他靜態方法呼叫中已定義的規則運算式模式，規則運算式引擎就會從快取中擷取這個規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="66eb5-128">If you are using a regular expression pattern that has already been defined in another static method call, the regular expression engine will retrieve it from the cache.</span></span> <span data-ttu-id="66eb5-129">如果沒有，則引擎會編譯規則運算式並新增至快取。</span><span class="sxs-lookup"><span data-stu-id="66eb5-129">If not, the engine will compile the regular expression and add it to the cache.</span></span>  
  
-   <span data-ttu-id="66eb5-130">在需要現有 <xref:System.Text.RegularExpressions.Regex> 物件的規則運算式模式時重複使用該物件。</span><span class="sxs-lookup"><span data-stu-id="66eb5-130">By reusing an existing <xref:System.Text.RegularExpressions.Regex> object as long as its regular expression pattern is needed.</span></span>  
  
 <span data-ttu-id="66eb5-131">由於物件具現化和規則運算式編譯會造成額外負荷，因此建立及快速終結多個 <xref:System.Text.RegularExpressions.Regex> 物件是個非常耗費資源的處理序。</span><span class="sxs-lookup"><span data-stu-id="66eb5-131">Because of the overhead of object instantiation and regular expression compilation, creating and rapidly destroying numerous <xref:System.Text.RegularExpressions.Regex> objects is a very expensive process.</span></span> <span data-ttu-id="66eb5-132">對於使用大量不同規則運算式的應用程式，您可以使用靜態 `Regex` 方法的呼叫，或增加規則運算式快取的大小，以達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="66eb5-132">For applications that use a large number of different regular expressions, you can optimize performance by using calls to static `Regex` methods and possibly by increasing the size of the regular expression cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66eb5-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="66eb5-133">See Also</span></span>  
 [<span data-ttu-id="66eb5-134">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="66eb5-134">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
