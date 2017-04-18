---
title: "排序集合類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "集合 [.NET Framework], SortedList 集合類型"
  - "群組集合中的資料, SortedList 集合類型"
  - "SortedDictionary 集合類型"
  - "SortedList 類別, 群組集合中的資料"
  - "SortedList 集合類型"
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# 排序集合類型
<xref:System.Collections.SortedList?displayProperty=fullName> 類別、<xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> 泛型類別以及 <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> 泛型類別在會實作 <xref:System.Collections.IDictionary> 介面這方面全都類似於 <xref:System.Collections.Hashtable> 類別與 <xref:System.Collections.Generic.Dictionary%602> 泛型類別，但它們是依索引鍵以排序次序來維護它們的元素，並且不具有雜湊資料表的 O\(1\) 插入和擷取特性。  這三個類別具有幾個共通的功能：  
  
-   所有這三個類別都會實作 <xref:System.Collections.IDictionary?displayProperty=fullName> 介面。  此外，其中兩個泛型類別還會實作 <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName> 泛型介面  
  
-   每個元素都是一組用於列舉用途的索引鍵\/值組  
  
    > [!NOTE]
    >  被列舉時，非泛型 <xref:System.Collections.SortedList> 類別會傳回 <xref:System.Collections.DictionaryEntry> 物件，而這兩個泛型型別則會傳回 <xref:System.Collections.Generic.KeyValuePair%602> 物件。  
  
-   元素會依據 <xref:System.Collections.IComparer?displayProperty=fullName> 實作 \(如果是非泛型 <xref:System.Collections.SortedList>\) 或 <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> 實作 \(如果是這兩個泛型類別\) 排序。  
  
-   每個類別都會提供屬性，這些屬性會傳回只包含索引鍵或只包含值的集合  
  
 下表列出兩個排序的清單類別以及 <xref:System.Collections.Generic.SortedDictionary%602> 類別之間的一些差異。  
  
|<xref:System.Collections.SortedList> 非泛型類別和 <xref:System.Collections.Generic.SortedList%602> 泛型類別|<xref:System.Collections.Generic.SortedDictionary%602> 泛型類別|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|會製作那些傳回索引鍵和值的屬性的索引，以便進行有效率的索引式擷取|非索引式擷取|  
|擷取是 O\(log `n`\)|擷取是 O\(log `n`\)|  
|引入運算子和移除一般是 O\(`n`\)；不過，如果是已經處於排序次序的資料，引入運算子是 O\(1\)，這樣每個元素都會加入至清單結尾 \(這是假設不需要調整大小\)|引入運算子和移除是 O\(log `n`\)|  
|使用的記憶體比 <xref:System.Collections.Generic.SortedDictionary%602> 還少|使用的記憶體比 <xref:System.Collections.SortedList> 非泛型類別和 <xref:System.Collections.Generic.SortedList%602> 泛型類別多|  
  
 如需必須同時供多個執行緒存取的已排序清單或字典，您可以在衍生自 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 的類別中加入排序邏輯。  
  
> [!NOTE]
>  如果是本身包含索引鍵的值 \(例如，包含員工 ID 編號的員工資料錄\)，您可以經由衍生自 <xref:System.Collections.ObjectModel.KeyedCollection%602> 泛型類別來建立索引集合，此索引集合具有清單的某些特性以及目錄的某些特性。  
  
 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，<xref:System.Collections.Generic.SortedSet%601> 類別提供於插入、刪除與搜尋後維持資料排序順序的自我平衡樹狀結構。  這個類別和 <xref:System.Collections.Generic.HashSet%601> 類別會實作 <xref:System.Collections.Generic.ISet%601> 介面。  
  
## 請參閱  
 <xref:System.Collections.IDictionary?displayProperty=fullName>   
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>   
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>   
 [常用的集合類型](../../../docs/standard/collections/commonly-used-collection-types.md)