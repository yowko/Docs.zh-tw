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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d273fbaa792092f5ea56bfa59392794b6728ed67
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="8ec19-102">在陣列中執行不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="8ec19-102">Performing Culture-Insensitive String Operations in Arrays</span></span>
<span data-ttu-id="8ec19-103"><xref:System.Array.Sort%2A?displayProperty=nameWithType> 和 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> 方法的多載預設會使用 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 屬性執行區分文化特性的排序。</span><span class="sxs-lookup"><span data-stu-id="8ec19-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8ec19-104">這些方法所傳回的區分文化特性的結果可能會因為文化特性排序順序上的差異而有所不同。</span><span class="sxs-lookup"><span data-stu-id="8ec19-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="8ec19-105">若要消除區分文化特性的行為，請使用此方法中可接受 `comparer` 參數的其中一個多載。</span><span class="sxs-lookup"><span data-stu-id="8ec19-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="8ec19-106">`comparer` 參數會指定要在比較陣列中元素時使用的 <xref:System.Collections.IComparer> 實作。</span><span class="sxs-lookup"><span data-stu-id="8ec19-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="8ec19-107">為參數指定一個使用 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 的自訂非變異值比較子類別。</span><span class="sxs-lookup"><span data-stu-id="8ec19-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ec19-108">如需自訂非變異值比較子類別的範例，請參閱[在集合中執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)主題中的「使用 SortedList 類別」子主題。</span><span class="sxs-lookup"><span data-stu-id="8ec19-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>  
  
 <span data-ttu-id="8ec19-109">**注意：**將 **CultureInfo.InvariantCulture** 傳遞給比較方法的確會執行不區分文化特性的比較。</span><span class="sxs-lookup"><span data-stu-id="8ec19-109">**Note** Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="8ec19-110">不過，它不會讓某些項目進行非語言比較，例如檔案路徑、登錄機碼和環境變數。</span><span class="sxs-lookup"><span data-stu-id="8ec19-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="8ec19-111">它也不支援根據比較結果所做出的安全性決策。</span><span class="sxs-lookup"><span data-stu-id="8ec19-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="8ec19-112">若要進行非語言比較或需要支援根據結果的安全性決策，應用程式應該使用可接受 <xref:System.StringComparison> 值的比較方法。</span><span class="sxs-lookup"><span data-stu-id="8ec19-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="8ec19-113">接著，應用程式應該會傳遞 <xref:System.StringComparison.Ordinal>。</span><span class="sxs-lookup"><span data-stu-id="8ec19-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec19-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8ec19-114">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="8ec19-115">執行不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="8ec19-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
