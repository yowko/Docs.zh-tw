---
title: "受保護的成員 | Microsoft Docs"
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
  - "受保護的成員 [.NET Framework]"
  - "受保護的成員"
  - "未密封的類別 [.NET Framework]"
  - "類別 [.NET Framework]，受保護的成員"
  - "非密封的類別"
  - "自訂類別行為"
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 受保護的成員
受保護的成員，本身並不提供任何擴充性，但是它們可以讓透過子類別化的擴充性功能更強大。 它們可以用於公開不必要複雜化，主要的公用介面的進階的自訂選項。  
  
 架構設計人員必須小心使用受保護的成員，是因為 「 受保護 」 的名稱可以讓感應的安全性。 任何人都可以子類別的未密封的類別和存取受保護的成員，和公用成員所用的防禦性編碼方式完全相同，套用至受保護的成員。  
  
 **✓ 考慮** 使用受保護的進階自訂的成員。  
  
 **✓ 執行** 為用於安全性、 文件及相容性分析公用未密封的類別以處理受保護的成員。  
  
 任何人都可以繼承自的類別，並存取受保護的成員。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)