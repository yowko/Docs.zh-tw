---
title: 執行不區分文化特性的字串作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9500550fe415d77bacb44011622ddd83ffc8a9ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575371"
---
# <a name="performing-culture-insensitive-string-operations"></a>執行不區分文化特性的字串作業
執行區分文化特性字串作業的大部分 .NET Framework 方法預設會提供方法多載，讓您藉由傳遞 <xref:System.Globalization.CultureInfo> 參數，明確地指定要使用的文化特性。 這些多載可讓您消除大小寫對應和排序規則中的文化特性變化，保證您可以得到不區分文化特性的結果。  
  
 本節提供下列主題，以示範如何使用預設會區分文化特性的 .NET Framework 方法來執行不區分文化特性的字串作業。  
  
## <a name="in-this-section"></a>本節內容  
 [執行不區分文化特性的字串比較](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 描述如何使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 和 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法執行不區分文化特性的字串比較。  
  
 [執行不區分文化特性的大小寫變更](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 描述如何使用 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>、<xref:System.String.ToLower%2A?displayProperty=nameWithType>、<xref:System.Char.ToUpper%2A?displayProperty=nameWithType> 和 <xref:System.Char.ToLower%2A?displayProperty=nameWithType> 方法執行不區分文化特性的大小寫變更。  
  
 [在集合中執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 描述如何使用 <xref:System.Collections.CaseInsensitiveComparer>、<xref:System.Collections.CaseInsensitiveHashCodeProvider> 類別、<xref:System.Collections.SortedList>、<xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> 和 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>，在集合中執行不區分文化特性的作業。  
  
 [在陣列中執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 描述如何使用 <xref:System.Array.Sort%2A?displayProperty=nameWithType> 和 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> 方法，在陣列中執行不區分文化特性的作業。  
  
## <a name="related-sections"></a>相關章節  
 [不區分文化特性的字串之作業](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 描述為何您應該注意對字串執行作業時的文化特性，並提供指導方針來指出何時該執行區分文化特性的作業，何時該執行不區分文化特性的作業。
