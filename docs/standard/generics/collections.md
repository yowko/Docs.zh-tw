---
title: ".NET Framework 中的泛型集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d7e7d11446c14cffbef1e5cade5f082874187636
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="62697-102">.NET Framework 中的泛型集合</span><span class="sxs-lookup"><span data-stu-id="62697-102">Generic Collections in the .NET Framework</span></span>
<span data-ttu-id="62697-103">本主題提供 .NET Framework 中泛型集合類別和其他泛型類型的概觀。</span><span class="sxs-lookup"><span data-stu-id="62697-103">This topic provides an overview of the generic collection classes and other generic types in the .NET Framework.</span></span>  
  
## <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="62697-104">.NET Framework 中的泛型集合</span><span class="sxs-lookup"><span data-stu-id="62697-104">Generic Collections in the .NET Framework</span></span>  
 <span data-ttu-id="62697-105">.NET Framework 類別庫提供 <xref:System.Collections.Generic> 和 <xref:System.Collections.ObjectModel> 命名空間中的一些泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="62697-105">The .NET Framework class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="62697-106">如需這些類別的詳細資訊，請參閱[常用的集合類型](../../../docs/standard/collections/commonly-used-collection-types.md)。</span><span class="sxs-lookup"><span data-stu-id="62697-106">For more information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="62697-107">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="62697-107">System.Collections.Generic</span></span>  
 <span data-ttu-id="62697-108">許多泛型集合類型是非泛型類型的直接模擬。</span><span class="sxs-lookup"><span data-stu-id="62697-108">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="62697-109"><xref:System.Collections.Generic.Dictionary%602> 是 <xref:System.Collections.Hashtable> 的泛型版本，使用泛型結構 <xref:System.Collections.Generic.KeyValuePair%602> (而不是 <xref:System.Collections.DictionaryEntry>) 來進行列舉。</span><span class="sxs-lookup"><span data-stu-id="62697-109"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="62697-110"><xref:System.Collections.Generic.List%601> 是 <xref:System.Collections.ArrayList> 的泛型版本。</span><span class="sxs-lookup"><span data-stu-id="62697-110"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="62697-111">泛型 <xref:System.Collections.Generic.Queue%601> 和 <xref:System.Collections.Generic.Stack%601> 類別有對應的非泛型版本。</span><span class="sxs-lookup"><span data-stu-id="62697-111">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="62697-112"><xref:System.Collections.Generic.SortedList%602> 有泛型和非泛型版本。</span><span class="sxs-lookup"><span data-stu-id="62697-112">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="62697-113">這兩種版本是字典和清單的混合。</span><span class="sxs-lookup"><span data-stu-id="62697-113">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="62697-114"><xref:System.Collections.Generic.SortedDictionary%602> 泛型類別是純字典，沒有對應的非泛型版本。</span><span class="sxs-lookup"><span data-stu-id="62697-114">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="62697-115"><xref:System.Collections.Generic.LinkedList%601> 泛型類別是純連結清單，</span><span class="sxs-lookup"><span data-stu-id="62697-115">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="62697-116">沒有對應的非泛型版本。</span><span class="sxs-lookup"><span data-stu-id="62697-116">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="62697-117">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="62697-117">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="62697-118"><xref:System.Collections.ObjectModel.Collection%601> 泛型類別提供基底類別，可用於衍生您自己的泛型集合類型。</span><span class="sxs-lookup"><span data-stu-id="62697-118">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="62697-119"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 類別提供一個簡單的方法，從任何實作 <xref:System.Collections.Generic.IList%601> 泛型介面的類型中產生唯讀集合。</span><span class="sxs-lookup"><span data-stu-id="62697-119">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="62697-120"><xref:System.Collections.ObjectModel.KeyedCollection%602> 泛型類別提供一個方法來儲存物件 (其中包含物件的索引鍵)。</span><span class="sxs-lookup"><span data-stu-id="62697-120">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="62697-121">其他泛型類型</span><span class="sxs-lookup"><span data-stu-id="62697-121">Other Generic Types</span></span>  
 <span data-ttu-id="62697-122"><xref:System.Nullable%601> 泛型結構可讓您使用可指派 `null` 的實值類型。</span><span class="sxs-lookup"><span data-stu-id="62697-122">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="62697-123">這在使用資料庫查詢時會很有用，因為包含實值類型的欄位可能遺漏。</span><span class="sxs-lookup"><span data-stu-id="62697-123">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="62697-124">泛型類型參數可以是任何實值類型。</span><span class="sxs-lookup"><span data-stu-id="62697-124">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62697-125">在 C# 中，不需要明確使用 <xref:System.Nullable%601>，因為這個語言具有可為 null 類型的語法。</span><span class="sxs-lookup"><span data-stu-id="62697-125">In C# it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span>  
  
 <span data-ttu-id="62697-126"><xref:System.ArraySegment%601> 泛型結構提供一個方法，將項目範圍限定在任何類型之以零為起始的一維陣列中。</span><span class="sxs-lookup"><span data-stu-id="62697-126">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="62697-127">泛型類型參數是陣列的項目類型。</span><span class="sxs-lookup"><span data-stu-id="62697-127">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="62697-128">如果您的事件遵循 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 所使用的事件處理模式，則 <xref:System.EventHandler%601> 泛型委派不需要宣告委派類型來處理事件。</span><span class="sxs-lookup"><span data-stu-id="62697-128">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="62697-129">例如，假設您已建立衍生自 <xref:System.EventArgs> 的 `MyEventArgs` 類別來保存事件的資料。</span><span class="sxs-lookup"><span data-stu-id="62697-129">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="62697-130">您可以接著依照下列方式來宣告事件：</span><span class="sxs-lookup"><span data-stu-id="62697-130">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="62697-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="62697-131">See Also</span></span>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [<span data-ttu-id="62697-132">泛型</span><span class="sxs-lookup"><span data-stu-id="62697-132">Generics</span></span>](../../../docs/standard/generics/index.md)  
 [<span data-ttu-id="62697-133">管理陣列和清單的泛型委派</span><span class="sxs-lookup"><span data-stu-id="62697-133">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [<span data-ttu-id="62697-134">泛型介面</span><span class="sxs-lookup"><span data-stu-id="62697-134">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
