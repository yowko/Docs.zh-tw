---
title: Hashtable 和 Dictionary 集合類型
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Hashtable class, grouping data in collections
- Hashtable collection type
- hash tables
- grouping data in collections, Hashtable collection type
- hash function
- collections [.NET Framework], Hashtable collection type
ms.assetid: bfc20837-3d02-4fc7-8a8f-c5215b6b7913
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4dde57e03e26085d19099e749afd50ba14874a5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195370"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Hashtable 和 Dictionary 集合類型
<xref:System.Collections.Hashtable?displayProperty=nameWithType> 類別以及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> 泛型類別會實作 <xref:System.Collections.IDictionary?displayProperty=nameWithType> 介面。 <xref:System.Collections.Generic.Dictionary%602> 泛型類別還會實作 <xref:System.Collections.Generic.IDictionary%602> 泛型介面。 因此，這些集合中的每個項目是索引鍵-值組。  
  
 <xref:System.Collections.Hashtable> 物件是由包含集合項目的值區所組成。 值區是 <xref:System.Collections.Hashtable> 中項目的虛擬子群組，比大多數集合的搜尋和擷取更容易且更快速。 每個值區會與一個雜湊碼相關聯，這個雜湊碼是使用雜湊函式並根據項目的索引鍵所產生。  
  
 泛型 <xref:System.Collections.Generic.HashSet%601> 類別是包含唯一項目的未排序集合。  
  
 雜湊函式是根據索引鍵傳回數值雜湊碼的演算法。 索引鍵是所儲存之物件的特定屬性值。 雜湊函式一律必須針對同一個索引鍵傳回相同的雜湊碼。 雜湊函式可以為兩個不同的索引鍵產生相同的雜湊碼，但是當雜湊函式為每個唯一的索引鍵產生唯一的雜湊碼時，可以提升從雜湊資料表擷取項目的效能。  
  
 當做 <xref:System.Collections.Hashtable> 中項目使用的每個物件必須能夠使用 <xref:System.Object.GetHashCode%2A> 方法的實作，為自己產生雜湊碼。 不過，您也可以使用接受 <xref:System.Collections.IHashCodeProvider> 實作做為其中一個參數的 <xref:System.Collections.Hashtable> 建構函式，為 <xref:System.Collections.Hashtable> 中的所有項目指定雜湊函式。  
  
 將物件加入 <xref:System.Collections.Hashtable> 之後，該物件會儲存在與符合物件雜湊碼的雜湊碼關聯的值區中。 當搜尋 <xref:System.Collections.Hashtable> 中的值時，系統會針對該值產生雜湊碼，並搜尋與該雜湊碼關聯的值區。  
  
 例如，字串的雜湊函式可能會接受字串中每個字元的 ASCII 碼，並全部加入以產生雜湊碼。 字串 "picnic" 的雜湊碼與字串 "basket" 的雜湊碼不同；因此，字串 "picnic" 和 "basket" 會在不同的值區。 相反地，"stressed" 和 "desserts" 有相同的雜湊碼，因此會在相同的值區。  
  
 <xref:System.Collections.Generic.Dictionary%602> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 類別的功能與 <xref:System.Collections.Hashtable> 類別相同。 特定類型 (<xref:System.Object> 以外的類型) 的 <xref:System.Collections.Generic.Dictionary%602> 提供比實值類型的 <xref:System.Collections.Hashtable> 更佳的效能。 這是因為 <xref:System.Collections.Hashtable> 的項目屬於 <xref:System.Object> 類型；因此，當您儲存或擷取實值類型時，通常會發生 Boxing 和 Unboxing。 當多個執行緒可能同時存取集合時，應該使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 類別。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Hashtable>  
- <xref:System.Collections.IDictionary>  
- <xref:System.Collections.IHashCodeProvider>  
- <xref:System.Collections.Generic.Dictionary%602>  
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>  
- [常用的集合類型](../../../docs/standard/collections/commonly-used-collection-types.md)
