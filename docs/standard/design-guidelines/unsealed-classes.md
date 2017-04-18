---
title: "非密封的類別 | Microsoft Docs"
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
  - "未密封的類別 [.NET Framework]"
  - "非密封的類別"
  - "繼承、 類別"
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 非密封的類別
密封的類別無法被繼承，並防止擴充性。 相反地，可以繼承自的類別則稱為非密封的類別。  
  
 **✓ 考慮** 使用非密封的類別不在提供低成本的妙招卻高價值為架構的擴充性，新增虛擬或受保護的成員。  
  
 開發人員通常會想要繼承自非密封類別，以便新增方便成員，例如自訂建構函式、 新的方法或方法多載。 例如，  `System.Messaging.MessageQueue` 未密封，因此可讓使用者建立自訂的佇列預設為特定的佇列路徑，或加入自訂方法，可簡化針對特定案例的 API。  
  
 根據預設，最程式設計語言中，未密封的類別會和這也是建議的預設值為大部分的架構中的類別。 更令人激賞的 framework 使用者而提供因為相對較低的測試與非密封類型相關聯的成本很便宜的非密封類型所提供的擴充。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)   
 [密封](../../../docs/standard/design-guidelines/sealing.md)