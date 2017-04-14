---
title: "擴充性設計 | Microsoft Docs"
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
  - "擴充類別庫"
  - "使用.NET Framework 中的類別程式庫的擴充性"
  - "類別庫設計方針 [.NET Framework] 擴充性"
  - "類別庫擴充性 [.NET Framework]"
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 擴充性設計
設計一套架構的重要面向之一確定已仔細考慮架構的擴充性。 這需要您已了解各種擴充性機制相關聯的優點與成本。 本章節可協助您決定哪一個擴充性機制，子類別化、 事件、 虛擬成員、 回呼 \(callback\) 等等 — 可以最符合您的架構需求。  
  
 有許多方法可允許擴充性架構中。 這些範圍權力較小，但成本更低但昂貴的功能非常強大。 任何指定的擴充性需求，您應該選擇符合需求的最高擴充性機制。 請記住，通常可以稍後新增更多的擴充性，但您可以永遠不會更立即且不會造成重大變更。  
  
## 在本節中  
 [非密封的類別](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [受保護的成員](../../../docs/standard/design-guidelines/protected-members.md)  
 [事件和回呼](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)  
 [抽象 （抽象型別和介面）](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [實作抽象的基底類別](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [密封](../../../docs/standard/design-guidelines/sealing.md)  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)