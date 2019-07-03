---
title: 在集合內比較和排序
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d9124c90d09e2fa94a0eaa2ff8cd4e4ab15206f
ms.sourcegitcommit: ced0cccf15adfd492f8196cb739f01dde52c9252
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/14/2019
ms.locfileid: "67135677"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="52a84-102">在集合內比較和排序</span><span class="sxs-lookup"><span data-stu-id="52a84-102">Comparisons and Sorts Within Collections</span></span>
<span data-ttu-id="52a84-103"><xref:System.Collections> 類別幾乎會在管理集合內的所有處理序中執行比較，包含搜尋要移除的項目，或傳回成對的索引鍵與值。</span><span class="sxs-lookup"><span data-stu-id="52a84-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>  
  
 <span data-ttu-id="52a84-104">集合通常會利用等號比較子和 (或) 排序比較子。</span><span class="sxs-lookup"><span data-stu-id="52a84-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="52a84-105">比較會使用兩個建構。</span><span class="sxs-lookup"><span data-stu-id="52a84-105">Two constructs are used for comparisons.</span></span>  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a><span data-ttu-id="52a84-106">檢查相等</span><span class="sxs-lookup"><span data-stu-id="52a84-106">Checking for equality</span></span>  
 <span data-ttu-id="52a84-107">例如， `Contains`、 <xref:System.Collections.IList.IndexOf%2A>、 <xref:System.Collections.Generic.List%601.LastIndexOf%2A>和 `Remove` 方法會為集合元素使用相等比較子。</span><span class="sxs-lookup"><span data-stu-id="52a84-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="52a84-108">如果集合為泛型，則會根據下列方針，比較項目是否相等：</span><span class="sxs-lookup"><span data-stu-id="52a84-108">If the collection is generic, than items are compared for equality according to the following guidelines:</span></span>  
  
- <span data-ttu-id="52a84-109">如果類型 T 實作了 <xref:System.IEquatable%601> 泛型介面，則相等比較子會是該介面的 <xref:System.IEquatable%601.Equals%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="52a84-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>  
  
- <span data-ttu-id="52a84-110">如果類型 T 未實作 <xref:System.IEquatable%601>，則會使用 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="52a84-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>  
  
 <span data-ttu-id="52a84-111">此外，有些字典集合的建構函式多載可接受用來比較索引鍵是否相等的 <xref:System.Collections.Generic.IEqualityComparer%601> 實作。</span><span class="sxs-lookup"><span data-stu-id="52a84-111">In addition, some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="52a84-112">如需範例，請參閱 <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="52a84-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> constructor.</span></span>  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a><span data-ttu-id="52a84-113">決定排序順序</span><span class="sxs-lookup"><span data-stu-id="52a84-113">Determining sort order</span></span>  
 <span data-ttu-id="52a84-114">例如，方法 `BinarySearch` 和 `Sort` 會為集合元素使用排序比較子。</span><span class="sxs-lookup"><span data-stu-id="52a84-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="52a84-115">比較可以在集合的元素之間進行，或在元素和指定的值之間進行。</span><span class="sxs-lookup"><span data-stu-id="52a84-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="52a84-116">若為比較物件，會有 `default comparer` 和 `explicit comparer`的概念。</span><span class="sxs-lookup"><span data-stu-id="52a84-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>  
  
 <span data-ttu-id="52a84-117">預設比較子會依賴至少一個所比較的物件，實作 **IComparable** 介面。</span><span class="sxs-lookup"><span data-stu-id="52a84-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="52a84-118">最好的作法是在所有用做為清單集合中的值或是用做為字典集合中索引鍵的類別上，實作 **IComparable** 。</span><span class="sxs-lookup"><span data-stu-id="52a84-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="52a84-119">若為泛型集合，會根據下列項目來決定相等比較：</span><span class="sxs-lookup"><span data-stu-id="52a84-119">For a generic collection, equality comparison is determined according to the following:</span></span>  
  
- <span data-ttu-id="52a84-120">如果類型 T 實作 <xref:System.IComparable%601?displayProperty=nameWithType> 泛型介面，則預設比較子會是該介面的 <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="52a84-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>  
  
- <span data-ttu-id="52a84-121">如果類型 T 實作非泛型 <xref:System.IComparable?displayProperty=nameWithType> 介面，則預設比較子會是該介面的 <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="52a84-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>  
  
- <span data-ttu-id="52a84-122">如果類型 T 沒有實作其中一個介面，則不會有預設比較子，且必須明確地提供比較子或比較委派。</span><span class="sxs-lookup"><span data-stu-id="52a84-122">If type T doesn’t implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>  
  
 <span data-ttu-id="52a84-123">若要提供明確比較，某些方法接受以 **IComparer** 實作做為參數。</span><span class="sxs-lookup"><span data-stu-id="52a84-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="52a84-124">例如， <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 方法接受 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 實作。</span><span class="sxs-lookup"><span data-stu-id="52a84-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>  
  
 <span data-ttu-id="52a84-125">系統目前的文化特性設定，會影響集合內的比較和排序。</span><span class="sxs-lookup"><span data-stu-id="52a84-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="52a84-126">依預設， **Collections** 類別中的比較和排序會區分文化特性。</span><span class="sxs-lookup"><span data-stu-id="52a84-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="52a84-127">若要略過文化特性設定，並因而取得一致的比較和排序結果，請使用 <xref:System.Globalization.CultureInfo.InvariantCulture%2A> 搭配接受 <xref:System.Globalization.CultureInfo>的成員多載。</span><span class="sxs-lookup"><span data-stu-id="52a84-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="52a84-128">如需詳細資訊，請參閱 [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) 與 [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="52a84-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a><span data-ttu-id="52a84-129">相等和排序範例</span><span class="sxs-lookup"><span data-stu-id="52a84-129">Equality and sort example</span></span>  
 <span data-ttu-id="52a84-130">下列程式碼示範簡單商務物件上的 <xref:System.IEquatable%601> 和 <xref:System.IComparable%601> 實作。</span><span class="sxs-lookup"><span data-stu-id="52a84-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="52a84-131">此外，當物件儲存在清單中且經過排序時，您會發現呼叫 <xref:System.Collections.Generic.List%601.Sort> 方法時，會為 `Part` 類型使用預設比較子，並使用匿名方法實作 <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="52a84-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="52a84-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52a84-132">See also</span></span>

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
