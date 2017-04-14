---
title: "密封 | Microsoft Docs"
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
  - "限制擴充性"
  - "密封類別 [.NET Framework]"
  - "防止自訂"
  - "密封類別"
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 密封
物件導向架構的功能之一是，開發人員可以擴充及自訂，架構設計人員所預期的方式。 這是設計的電源和可延伸的危險。 當您設計您的架構時，它，因此屬於時需要它，請仔細設計的擴充性，並限制擴充性，會有問題時很重要。  
  
 功能強大的機制，可防止擴充性密封。 您可以密封類別或個別成員。 密封類別，可防止使用者從類別繼承。 密封成員可防止使用者覆寫特定成員。  
  
 **X 不** 密封類別，而不需要這麼做的好理由。  
  
 密封類別，因為您無法將擴充性案例不充分的理由。 Framework 使用者想要從類別繼承，基於各種 nonobvious 原因的詳細資訊，例如新增方便成員。 請參閱 [非密封的類別](../../../docs/standard/design-guidelines/unsealed-classes.md) nonobvious 原因的範例使用者想要繼承自型別。  
  
 密封類別的原因包括︰  
  
-   類別是靜態類別。 請參閱 [靜態類別設計](../../../docs/standard/design-guidelines/static-class.md)。  
  
-   類別會將敏感的安全性密碼儲存在繼承的 protected 成員。  
  
-   此類別會繼承許多虛擬成員與密封它們個別的成本會超過優點的未密封的類別。  
  
-   此類別是需要非常快速的執行階段查詢的屬性。 密封的屬性會有較高的效能層級比未密封。 請參閱 [屬性](../../../docs/standard/design-guidelines/屬性.md)。  
  
 **X 不** 在密封類型上宣告受保護或虛擬的成員。  
  
 根據定義，密封的類型無法被繼承的。 這表示，無法呼叫密封類型上受保護的成員，而且不能覆寫虛擬方法，密封類型上。  
  
 **✓ 考慮** 密封您覆寫的成員。  
  
 可能是因為簡介虛擬成員的問題 \(所述 [虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)\) 雖然到稍微較低的程度套用，覆寫設定。 密封覆寫會幫助您從階層架構中該點開始這些問題。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)   
 [非密封的類別](../../../docs/standard/design-guidelines/unsealed-classes.md)