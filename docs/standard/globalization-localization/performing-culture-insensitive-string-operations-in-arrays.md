---
title: "在陣列中執行不區分文化特性的字串作業"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b4e040ed379cdbf43fbe8b2c4379fdd4dc781f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="e26ef-102">在陣列中執行不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="e26ef-102">Performing Culture-Insensitive String Operations in Arrays</span></span>
<span data-ttu-id="e26ef-103">多載<xref:System.Array.Sort%2A?displayProperty=nameWithType>和<xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>方法執行區分文化特性的排序，預設使用<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="e26ef-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e26ef-104">這些方法所傳回的區分文化特性的結果可能會因文化特性，因為排序順序的差異。</span><span class="sxs-lookup"><span data-stu-id="e26ef-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="e26ef-105">若要消除區分文化特性的行為，請使用其中一個可接受這個方法的多載`comparer`參數。</span><span class="sxs-lookup"><span data-stu-id="e26ef-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="e26ef-106">`comparer`參數會指定<xref:System.Collections.IComparer>比較陣列中的項目時要使用的實作。</span><span class="sxs-lookup"><span data-stu-id="e26ef-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="e26ef-107">參數，請指定 使用自訂而異的比較子類別<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e26ef-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e26ef-108">自訂而異的比較子類別的範例中的 < 使用 SortedList 類別 > 子主題提供[集合中執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)主題。</span><span class="sxs-lookup"><span data-stu-id="e26ef-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>  
  
 <span data-ttu-id="e26ef-109">**請注意**傳遞**CultureInfo.InvariantCulture**比較方法並執行不區分文化特性的比較。</span><span class="sxs-lookup"><span data-stu-id="e26ef-109">**Note** Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="e26ef-110">不過，它不會讓某些項目進行非語言比較，例如檔案路徑、登錄機碼和環境變數。</span><span class="sxs-lookup"><span data-stu-id="e26ef-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="e26ef-111">它也不支援根據比較結果所做出的安全性決策。</span><span class="sxs-lookup"><span data-stu-id="e26ef-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="e26ef-112">對於非語言比較或支援，結果為基礎的安全性決策，應用程式應該使用的比較方法可接受<xref:System.StringComparison>值。</span><span class="sxs-lookup"><span data-stu-id="e26ef-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="e26ef-113">然後將應用程式應該<xref:System.StringComparison.Ordinal>。</span><span class="sxs-lookup"><span data-stu-id="e26ef-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e26ef-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e26ef-114">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="e26ef-115">執行不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="e26ef-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
