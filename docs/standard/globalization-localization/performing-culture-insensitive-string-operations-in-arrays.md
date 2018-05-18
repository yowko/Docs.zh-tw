---
title: 在陣列中執行不區分文化特性的字串作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4d732d64eecff72403c455c14b68c3aec1b5407
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>在陣列中執行不區分文化特性的字串作業
<xref:System.Array.Sort%2A?displayProperty=nameWithType> 和 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> 方法的多載預設會使用 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 屬性執行區分文化特性的排序。 這些方法所傳回的區分文化特性的結果可能會因為文化特性排序順序上的差異而有所不同。 若要消除區分文化特性的行為，請使用此方法中可接受 `comparer` 參數的其中一個多載。 `comparer` 參數會指定要在比較陣列中元素時使用的 <xref:System.Collections.IComparer> 實作。 為參數指定一個使用 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 的自訂非變異值比較子類別。 如需自訂非變異值比較子類別的範例，請參閱[在集合中執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)主題中的「使用 SortedList 類別」子主題。  
  
 **注意：** 將 **CultureInfo.InvariantCulture** 傳遞給比較方法的確會執行不區分文化特性的比較。 不過，它不會讓某些項目進行非語言比較，例如檔案路徑、登錄機碼和環境變數。 它也不支援根據比較結果所做出的安全性決策。 若要進行非語言比較或需要支援根據結果的安全性決策，應用程式應該使用可接受 <xref:System.StringComparison> 值的比較方法。 接著，應用程式應該會傳遞 <xref:System.StringComparison.Ordinal>。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
