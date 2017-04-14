---
title: "抽象 （抽象型別和介面） | Microsoft Docs"
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
  - "抽象介面 [.NET Framework]"
  - "抽象介面 [.NET Framework]"
  - "抽象型別 [.NET Framework]"
  - "抽象類型 [.NET Framework]"
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 抽象 （抽象型別和介面）
一個抽象概念是描述合約，但不提供完整的實作合約的型別。 抽象通常會實作為抽象類別或介面，和他們隨附一組妥善定義的參考文件，描述所需的語意的實作合約的型別。 最重要的抽象概念，.NET Framework 中的部分包括 <xref:System.IO.Stream>, ，<xref:System.Collections.Generic.IEnumerable%601>, ，和 <xref:System.Object>。  
  
 您可以透過實作支援抽象類別的合約的具象型別，並使用此具象型別與 framework Api 取用 （操作） 擴充架構的抽象概念。  
  
 有意義且實用的抽象概念，能夠承受的時間，測試就會非常難以設計的。 主要的困難取得適當的成員集合，沒有其他不較少。 如果抽象概念，具有太多的成員，會變得很困難或甚至根本不可能實作。 如果有太少成員的承諾的功能，它會變成無效許多有趣的案例中。  
  
 太多的抽象概念，架構也有負面影響架構的可用性。 通常是很難瞭解抽象概念，而不需要了解它如何融入相通的具象實作和抽象方法，在操作的 Api。 此外，抽象概念和其成員的名稱是抽象的因此通常是一相當隱密，而且親近不含第一次的了解其使用方式的更廣泛的內容。  
  
 不過，抽象提供的功能極為強大的擴充性機制無法通常會比對的擴充性。 也就是許多架構模式的詳細資訊，例如外掛程式，核心逆轉控制 \(IoC\)、 管線、 等等。 它們也是非常重要的可測試性的架構。 良好的抽象概念讓清除大量用於單元測試的相依性。 在 \[摘要\] 抽象負責大快人心的豐富功能的現代的物件導向架構。  
  
 **X 不** 提供抽象，除非它們由開發數個具象實作和使用抽象的 Api 進行測試。  
  
 **✓ 執行** 之間的抽象類別和介面設計抽象時謹慎選擇。  
  
 **✓ 考慮** 提供參考測試的具象實作的抽象概念。 這類測試應該允許使用者來測試是否正確地實作它們的實作的合約。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)