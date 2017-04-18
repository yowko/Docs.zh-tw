---
title: "虛擬成員 | Microsoft Docs"
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
  - "可覆寫成員"
  - "虛擬成員"
  - "成員 [.NET Framework] 虛擬"
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 虛擬成員
虛擬成員可以覆寫，因此變更子類別的行為。 他們是相當類似的回呼，以擴充性提供，但執行效能和記憶體耗用量方面更好。 此外，虛擬成員在需要建立一種特殊種類的現有型別 （特製化） 的情況下更自然習慣。  
  
 虛擬成員會優於回呼和事件，但不是執行效能優於非虛擬方法。  
  
 虛擬成員的主要缺點是虛擬成員的行為只修改在編譯時間。 回呼的行為可以在執行階段修改。  
  
 虛擬成員，例如回呼 （和可能有多個回呼），會使設計、 測試和維護，因為虛擬成員的任何呼叫非預期的方式可以覆寫，而且可以執行任意程式碼。 此外，清楚地定義合約的虛擬成員，因此設計和撰寫它們的成本較高者為通常需要更多的心力。  
  
 **X 不** 讓成員虛擬，除非您有正當的理由，若要這樣做，而且您了解所有設計、 測試和維護虛擬成員與相關的成本。  
  
 虛擬成員會較少能夠容許方面可以對它們而不會中斷相容性的變更。 此外，它們是低於非虛擬成員，主要是因為不是內嵌的虛擬成員的呼叫。  
  
 **✓ 考慮** 限制只在絕對必要的擴充性。  
  
 **✓ 執行** 偏好公用存取範圍之虛擬成員受保護的存取範圍。 公用成員應該提供擴充性 （如有必要） 藉由呼叫受保護的虛擬成員。  
  
 類別的 public 成員應該提供正確的功能集，該類別的直接取用者。 虛擬成員專為在類別中覆寫，而且受保護的存取範圍領域可以要使用的所有虛擬擴充功能的好方法。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)