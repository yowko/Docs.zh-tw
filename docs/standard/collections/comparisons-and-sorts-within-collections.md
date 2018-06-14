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
ms.openlocfilehash: 11393f4013a1b5ed9dc90154f289466432102a38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573116"
---
# <a name="comparisons-and-sorts-within-collections"></a>在集合內比較和排序
<xref:System.Collections> 類別幾乎會在管理集合內的所有處理序中執行比較，包含搜尋要移除的項目，或傳回成對的索引鍵與值。  
  
 集合通常會利用等號比較子和 (或) 排序比較子。 比較會使用兩個建構。  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a>檢查相等  
 例如， `Contains`、 <xref:System.Collections.IList.IndexOf%2A>、 <xref:System.Collections.Generic.List%601.LastIndexOf%2A>和 `Remove` 方法會為集合元素使用相等比較子。 如果集合為泛型，則會根據下列方針，比較項目是否相等：  
  
-   如果類型 T 實作了 <xref:System.IEquatable%601> 泛型介面，則相等比較子會是該介面的 <xref:System.IEquatable%601.Equals%2A> 方法。  
  
-   如果類型 T 未實作 <xref:System.IEquatable%601>，則會使用 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 。  
  
 此外，有些字典集合的建構函式多載，能接受 <xref:System.Collections.Generic.IEqualityComparer%601> 實作，其可用以比較索引鍵是否相等。 如需範例，請參閱 <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> 。  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a>決定排序順序  
 例如，方法 `BinarySearch` 和 `Sort` 會為集合元素使用排序比較子。 比較可以在集合的元素之間進行，或在元素和指定的值之間進行。 若為比較物件，會有 `default comparer` 和 `explicit comparer`的概念。  
  
 預設比較子會依賴至少一個所比較的物件，實作 **IComparable** 介面。 最好的作法是在所有用做為清單集合中的值或是用做為字典集合中索引鍵的類別上，實作 **IComparable** 。 若為泛型集合，會根據下列項目來決定相等比較：  
  
-   如果類型 T 實作 <xref:System.IComparable%601?displayProperty=nameWithType> 泛型介面，則預設比較子會是該介面的 <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> 方法。  
  
-   如果類型 T 實作非泛型 <xref:System.IComparable?displayProperty=nameWithType> 介面，則預設比較子會是該介面的 <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> 方法。  
  
-   如果類型 T 沒有實作其中一個介面，則不會有預設比較子，且必須明確地提供比較子或比較委派。  
  
 若要提供明確比較，某些方法接受以 **IComparer** 實作做為參數。 例如， <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 方法接受 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 實作。  
  
 系統目前的文化特性設定，會影響集合內的比較和排序。 依預設， **Collections** 類別中的比較和排序會區分文化特性。 若要略過文化特性設定，並因而取得一致的比較和排序結果，請使用 <xref:System.Globalization.CultureInfo.InvariantCulture%2A> 搭配接受 <xref:System.Globalization.CultureInfo>的成員多載。 如需詳細資訊，請參閱 [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) 與 [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)。  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a>相等和排序範例  
 下列程式碼示範簡單商務物件上的 <xref:System.IEquatable%601> 和 <xref:System.IComparable%601> 實作。 此外，當物件儲存在清單中且經過排序時，您會發現呼叫 <xref:System.Collections.Generic.List%601.Sort> 方法時，會為 `Part` 類型使用預設比較子，並使用匿名方法實作 <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> 方法。  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Collections.IComparer>  
 <xref:System.IEquatable%601>  
 <xref:System.Collections.Generic.IComparer%601>  
 <xref:System.IComparable>  
 <xref:System.IComparable%601>
