---
title: 規則運算式中的執行緒安全
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0bcab0757bc48f6a8216dd5878f0289e49a275
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208162"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="bf442-102">規則運算式中的執行緒安全</span><span class="sxs-lookup"><span data-stu-id="bf442-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="bf442-103"><xref:System.Text.RegularExpressions.Regex> 類別本身為不變 (唯讀) 的安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="bf442-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="bf442-104">也就是說，您可以在任何執行緒上建立 **Regex** 物件，並在執行緒之間共用；您也可以從任何執行緒呼叫比對方法，而不會變更任何全域狀態。</span><span class="sxs-lookup"><span data-stu-id="bf442-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="bf442-105">不過，**Regex** 傳回的結果物件 (**Match** 和 **MatchCollection**) 只可在單一執行緒上使用。</span><span class="sxs-lookup"><span data-stu-id="bf442-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="bf442-106">雖然這當中有許多物件在邏輯上是不可變的，但它們的實作可能會延遲某些結果的計算來提升效能，因此，呼叫端必須進行序列化存取。</span><span class="sxs-lookup"><span data-stu-id="bf442-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="bf442-107">如果需要在多個執行緒上共用 **Regex** 結果物件，可透過呼叫這些物件的同步方法，將其轉換成安全執行緒的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bf442-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="bf442-108">所有的規則運算式類別 (除了列舉程式以外) 都是安全執行緒，或可利用同步處理方法轉換為安全執行緒物件。</span><span class="sxs-lookup"><span data-stu-id="bf442-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="bf442-109">列舉程式是唯一的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf442-109">Enumerators are the only exception.</span></span> <span data-ttu-id="bf442-110">應用程式必須將集合列舉程式的呼叫序列化。</span><span class="sxs-lookup"><span data-stu-id="bf442-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="bf442-111">規則是，如果某個集合可以在多個執行緒上同時列舉，您就應該在列舉程式所周遊之集合的根物件位置，同步處理列舉程式方法。</span><span class="sxs-lookup"><span data-stu-id="bf442-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf442-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf442-112">See also</span></span>

- [<span data-ttu-id="bf442-113">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="bf442-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
