---
title: "抽象類別設計 | Microsoft Docs"
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
  - "類型設計方針，抽象類別"
  - "抽象類別，設計方針"
  - "類別庫設計方針 [.NET Framework] 類別"
  - "抽象類別 [.NET Framework]"
  - "類別 [.NET Framework] 設計指導方針"
  - "類型設計方針類別"
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 抽象類別設計
**X 不** 抽象型別中定義公用或受保護的內部建構函式。  
  
 應該只有當使用者將需要建立型別的執行個體的公用建構函式。 因為您無法建立抽象類型的執行個體，具有公用建構函式的抽象類型是不正確地設計、 誤導使用者。  
  
 **✓ 執行** 抽象類別中定義受保護或內部建構函式。  
  
 受保護的建構函式更常見原因，並只允許基底類別子型別建立時執行它自己的初始化。  
  
 內部建構函式可以用來限制組件定義類別的抽象類別的具體實作。  
  
 **✓ 執行** 提供至少一個從每個您在出貨的抽象類別繼承的具象型別。  
  
 此舉有助於驗證的抽象類別設計。 例如，  <xref:System.IO.FileStream?displayProperty=fullName> 是實作 <xref:System.IO.Stream?displayProperty=fullName> 抽象類別。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)