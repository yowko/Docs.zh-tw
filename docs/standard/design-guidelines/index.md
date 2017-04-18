---
title: "Framework 設計方針 | Microsoft Docs"
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
  - "程式庫，.NET Framework 類別庫"
  - "有關類別庫設計方針 [.NET Framework]"
  - "類別庫設計方針 [.NET Framework]"
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Framework 設計方針
本節提供設計擴充和.NET Framework 進行互動的程式庫的指導方針。 目標是要協助確保藉由提供用於開發的程式設計語言無關的統一程式設計模型的 API 一致性和方便使用的程式庫設計人員。 我們建議開發可擴充.NET Framework 的類別和元件時，請遵循這些設計指導方針。 不一致的程式庫設計造成負面影響開發人員產能，並不建議採用。  
  
 指導方針會按照加上文字的簡單建議 `Do`, ，`Consider`, ，`Avoid`, ，和 `Do not`。 這些指導方針旨在協助類別庫設計人員了解不同方案之間的取捨。 可能有一些情況良好的程式庫設計需要您違反這些設計指導方針。 這種情況下應該很少見，而且，您必須清除且引人注目的原因，對您的決策。  
  
 這些指導方針摘錄自 *Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式*, ，Krzysztof Cwalina 與 Brad Abrams。  
  
## 在本節中  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 提供的指導方針命名組件、 命名空間、 類型和類別庫中的成員。  
  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)  
 提供使用靜態和抽象類別、 介面、 列舉、 結構和其他類型的方針。  
  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
 提供設計和使用屬性、 方法、 建構函式、 欄位、 事件、 運算子和參數的指導方針。  
  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 討論擴充性機制，例如子類別化，使用事件、 虛擬成員和回呼，並說明如何選擇最符合您的架構需求的機制。  
  
 [例外狀況的設計指導方針](../../../docs/standard/design-guidelines/exceptions.md)  
 說明設計、 擲回和攔截例外狀況的設計指導方針。  
  
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 描述使用常見的類型，例如陣列、 屬性和集合、 支援序列化，以及多載等號比較運算子的方針。  
  
 [常見的設計模式](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 提供指導方針選擇並實作相依性屬性和處置模式。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [概觀](../../../docs/framework/get-started/overview.md)   
 [.NET Framework 藍圖](http://msdn.microsoft.com/zh-tw/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)   
 [開發指南](../../../docs/framework/development-guide.md)