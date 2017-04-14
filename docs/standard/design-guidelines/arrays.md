---
title: "陣列 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "類別庫設計方針 [.NET Framework] 陣列"
  - "陣列 [.NET Framework] 使用指導方針"
  - "空的陣列"
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# 陣列
**✓ 執行** 偏好使用公用 Api 中的陣列上的集合。[集合](../../../docs/standard/design-guidelines/guidelines-for-collections.md) 節提供有關如何選擇集合和陣列的詳細資料。  
  
 **X 不** 使用唯讀陣列欄位。 欄位本身是唯讀的而且無法變更，但可變更陣列中的項目。  
  
 **✓ 考慮** 使用不規則的陣列取代多維陣列。  
  
 不規則的陣列是也是陣列的元素的陣列。 組成元素的陣列可以是不同的大小，相較於多維陣列的某些資料 （例如，疏鬆矩陣） 集而言較不浪費的空間。 此外，CLR 會最佳化索引作業不規則陣列，因此它們可能會表現出更好的執行階段效能，在某些情況下。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 <xref:System.Array>   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)