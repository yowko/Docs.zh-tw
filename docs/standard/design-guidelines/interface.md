---
title: "介面設計 | Microsoft Docs"
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
  - "介面 [.NET Framework] 設計指導方針"
  - "類型設計方針介面"
  - "類別庫設計方針 [.NET Framework] 介面"
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 介面設計
雖然大部分的 Api 最能模擬使用類別和結構，有介面比較適合的或是唯一的選項。  
  
 CLR 不支援多重繼承 （亦即，CLR 類別無法繼承多個基底類別），但允許實作除了繼承自基底類別的一個或多個介面的型別。 因此，介面會經常使用多重繼承的效果。 例如， <xref:System.IDisposable> 讓支援 disposability 他們要在其中加入任何其他繼承階層架構的獨立的型別是介面。  
  
 在定義的介面是適當的情況下是建立可由數種類型，包括一些實值型別支援的通用介面。 實值型別無法繼承類型以外的其他 <xref:System.ValueType>, ，但可以實作介面，因此會使用介面是唯一的選項，以便提供通用基底型別。  
  
 **✓ 執行** 定義介面，如果您需要一些通用的 API，以支援一組型別，其中包含實值型別。  
  
 **✓ 考慮** 定義介面，如果您需要支援它的功能已經繼承自其他類型的類型。  
  
 **X 避免** 使用標記介面 （但不含成員的介面）。  
  
 如果您需要將類別標示為具有特定特性 （標記），一般情況下，使用自訂屬性，而不是介面。  
  
 **✓ 執行** 提供至少一個型別是介面的實作。  
  
 此舉有助於驗證介面的設計。 例如， <xref:System.Collections.Generic.List%601> 是實作 <xref:System.Collections.Generic.IList%601> 介面。  
  
 **✓ 執行** 提供至少一個 API 來使用您定義每個介面 （做為介面型別採取介面做為參數或屬性的方法）。  
  
 此舉有助於驗證介面設計。 例如， <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=fullName> 取用 <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> 介面。  
  
 **X 不** 將成員加入至先前已發佈的介面。  
  
 這樣會中斷介面的實作。 您應該建立新的介面，以避免版本控制問題。  
  
 除了這些指導方針所述的情況下，您應，一般情況下，選擇類別而非介面設計的 managed 程式碼可重複使用程式庫。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)