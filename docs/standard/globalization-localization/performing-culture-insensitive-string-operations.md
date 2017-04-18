---
title: "執行不區分文化特性的字串作業 | Microsoft Docs"
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
  - "大小寫對應"
  - "自訂大小寫對應"
  - "文化特性，自訂排序規則"
  - "自訂排序規則"
  - "不區分文化特性的字串作業，執行的選項"
  - "文化特性，自訂大小寫對應"
  - "不區分文化特性的字串作業，方法多載"
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 執行不區分文化特性的字串作業
執行區分文化特性字串作業的多數 .NET Framework 方法在預設情況下都會提供方法多載，可以讓您藉由傳遞 <xref:System.Globalization.CultureInfo> 參數來明確指定要使用的文化特性。  這些多載可以讓您排除文化特性在大小寫對應和排序規則中的差異，並確保結果不會區分文化特性。  
  
 本章節提供下列主題，示範如何使用預設為區分文化特性的 .NET Framework 方法來執行不區分文化特性的字串作業。  
  
## 在本節中  
 [執行不區分文化特性的字串比較](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 描述如何使用 <xref:System.String.Compare%2A?displayProperty=fullName> 和 <xref:System.String.CompareTo%2A?displayProperty=fullName> 方法來執行不區分文化特性的字串比較。  
  
 [執行不區分文化特性的大小寫變更](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 描述如何使用 <xref:System.String.ToUpper%2A?displayProperty=fullName>、<xref:System.String.ToLower%2A?displayProperty=fullName>、<xref:System.Char.ToUpper%2A?displayProperty=fullName> 和 <xref:System.Char.ToLower%2A?displayProperty=fullName> 方法來執行不區分文化特性的大小寫變更。  
  
 [在集合中執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 說明如何使用 [CaseInsensitiveComparer 類別](frlrfSystemCollectionsCaseInsensitiveComparerClassTopic)、<xref:System.Collections.CaseInsensitiveHashCodeProvider> 類別、[SortedList 類別](frlrfSystemCollectionsSortedListClassTopic)、[ArrayList.Sort 方法](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.sort.aspx)和 [CollectionsUtil.CreateCaseInsensitiveHashtable 方法](frlrfSystemCollectionsSpecializedCollectionsUtilClassCreateCaseInsensitiveHashtableTopic)在集合中執行不區分文化特性的作業。  
  
 [在陣列中執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 描述如何使用 <xref:System.Array.Sort%2A?displayProperty=fullName> 和 <xref:System.Array.BinarySearch%2A?displayProperty=fullName> 方法，在陣列中執行不區分文化特性的作業。  
  
## 相關章節  
 [不區分文化特性的字串作業](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 說明對字串執行作業時為何應該要知道文化特性，並提供方針做為何時要執行區分文化特性作業和何時要執行不區分文化特性作業的參考。