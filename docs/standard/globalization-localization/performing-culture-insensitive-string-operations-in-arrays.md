---
title: "在陣列中執行不區分文化特性的字串作業 | Microsoft Docs"
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
  - "陣列 [.NET Framework], 不區分文化特性的字串之作業"
  - "比較子參數"
  - "不區分文化特性的字串之作業, 在陣列中"
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 在陣列中執行不區分文化特性的字串作業
預設情況下，<xref:System.Array.Sort%2A?displayProperty=fullName> 和 <xref:System.Array.BinarySearch%2A?displayProperty=fullName> 方法的多載會使用 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=fullName> 屬性執行區分文化特性排序。  因排序次序的不同，這些方法傳回的區分文化特性結果可以因文化特性而有所不同。  若要排除區分文化特性的行為，請使用接受 `comparer` 參數之這種方法的其中一個多載。  `comparer` 參數會指定在比較陣列中元素時所使用的 <xref:System.Collections.IComparer> 實作。  對於參數，請指定會使用 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> 的自訂非變異比較子類別。  自訂不因比較子而異的類別的範例在[在集合中執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)主題的＜使用 SortedList 類別＞副標題中有提供。  
  
 **注意**：將 **CultureInfo.InvariantCulture** 傳遞給比較方法，的確會執行不區分文化特性的比較。  然而，這並不會進行非語言比較，例如檔案路徑、登錄機碼和環境變數。  同時也不會支援依據比較結果進行的安全性決策。  對於非語言比較或以結果為基礎之安全性決策的支援，應用程式應該使用接受 <xref:System.StringComparison> 值的比較方法。  然後應用程式應該傳遞 <xref:System.StringComparison>。  
  
## 請參閱  
 <xref:System.Array.Sort%2A?displayProperty=fullName>   
 <xref:System.Array.BinarySearch%2A?displayProperty=fullName>   
 <xref:System.Collections.IComparer>   
 [執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)