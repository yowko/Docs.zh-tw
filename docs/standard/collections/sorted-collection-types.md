---
title: "排序集合類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
caps.latest.revision: 16
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 210582c6cf31b59f7f6c4b577c0e8a2c2f25ddd6
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="sorted-collection-types"></a>排序集合類型
<xref:System.Collections.SortedList?displayProperty=fullName> 類別、<xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> 泛型類別和 <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> 泛型類別，類似於實作 <xref:System.Collections.IDictionary> 介面的 <xref:System.Collections.Hashtable> 類別和 <xref:System.Collections.Generic.Dictionary%602> 泛型類別，但它們會依索引鍵的排序次序維持其項目，沒有 O(1) 插入和雜湊資料表的擷取特性。 三個類別有數個共用功能︰  
  
-   所有三個類別都會實作 <xref:System.Collections.IDictionary?displayProperty=fullName> 介面。 兩個泛型類別也會實作 <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName> 泛型介面。  
  
-   每個元素都是進行列舉的索引鍵/值組。  
  
    > [!NOTE]
    >  雖然兩個泛型類型會傳回 <xref:System.Collections.Generic.KeyValuePair%602> 物件，但是非泛型 <xref:System.Collections.SortedList> 類別會在列舉時傳回 <xref:System.Collections.DictionaryEntry> 物件。  
  
-   元素的排序根據是 <xref:System.Collections.IComparer?displayProperty=fullName> 實作 (適用於非泛型 <xref:System.Collections.SortedList>) 或 <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> 實作 (適用於兩種泛型類別)。  
  
-   每個類別都會提供傳回集合的屬性，而這個集合僅包含索引鍵或僅包含值。  
  
 下表列出兩個已排序清單類別與 <xref:System.Collections.Generic.SortedDictionary%602> 類別之間的部分差異。  
  
|<xref:System.Collections.SortedList> 泛型類別與 <xref:System.Collections.Generic.SortedList%602> 泛型類別|<xref:System.Collections.Generic.SortedDictionary%602> 泛型類別|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|對傳回索引鍵和值的屬性進行編製索引，以進行有效率的索引擷取。|無索引擷取。|  
|擷取是 O(log `n`)。|擷取是 O(log `n`)。|  
|插入和移除一般是 O(`n`)；不過，對於已處於排序順序的資料，插入是 O(1)，因此每個元素都會新增至清單的結尾。 (這假設不需要調整大小)。|插入和移除是 O(log `n`)。|  
|使用的記憶體少於 <xref:System.Collections.Generic.SortedDictionary%602>。|使用的記憶體多於 <xref:System.Collections.SortedList> 非泛型類別和 <xref:System.Collections.Generic.SortedList%602> 泛型類別。|  
  
 針對必須可以從多個執行緒同時存取的已排序清單或字典，您可以將排序邏輯新增至衍生自 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 的類別。  
  
> [!NOTE]
>  針對包含專屬索引鍵的值 (例如，包含員工識別碼的員工記錄)，您可以建立索引鍵集合，而索引鍵集合透過衍生自 <xref:System.Collections.ObjectModel.KeyedCollection%602> 泛型類別而具有部分清單特性和部分字典特性。  
  
 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，<xref:System.Collections.Generic.SortedSet%601> 類別會提供自我平衡樹狀目錄，以在插入、刪除和搜尋之後依排序順序維護資料。 這個類別和 <xref:System.Collections.Generic.HashSet%601> 類別會實作 <xref:System.Collections.Generic.ISet%601> 介面。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.IDictionary?displayProperty=fullName>   
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>   
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>   
 [常用的集合類型](../../../docs/standard/collections/commonly-used-collection-types.md)
