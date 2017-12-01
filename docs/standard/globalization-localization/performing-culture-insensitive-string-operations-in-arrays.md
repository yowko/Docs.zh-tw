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
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>在陣列中執行不區分文化特性的字串作業
多載<xref:System.Array.Sort%2A?displayProperty=nameWithType>和<xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>方法執行區分文化特性的排序，預設使用<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>屬性。 這些方法所傳回的區分文化特性的結果可能會因文化特性，因為排序順序的差異。 若要消除區分文化特性的行為，請使用其中一個可接受這個方法的多載`comparer`參數。 `comparer`參數會指定<xref:System.Collections.IComparer>比較陣列中的項目時要使用的實作。 參數，請指定 使用自訂而異的比較子類別<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。 自訂而異的比較子類別的範例中的 < 使用 SortedList 類別 > 子主題提供[集合中執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)主題。  
  
 **請注意**傳遞**CultureInfo.InvariantCulture**比較方法並執行不區分文化特性的比較。 不過，它不會讓某些項目進行非語言比較，例如檔案路徑、登錄機碼和環境變數。 它也不支援根據比較結果所做出的安全性決策。 對於非語言比較或支援，結果為基礎的安全性決策，應用程式應該使用的比較方法可接受<xref:System.StringComparison>值。 然後將應用程式應該<xref:System.StringComparison.Ordinal>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
