---
title: "靜態類別設計 | Microsoft Docs"
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
  - "類型設計方針，靜態類別"
  - "類別庫設計方針 [.NET Framework] 類別"
  - "類別 [.NET Framework] 靜態"
  - "靜態類別 [.NET Framework]"
  - "類別 [.NET Framework] 設計指導方針"
  - "類型設計方針類別"
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 靜態類別設計
靜態類別會定義為只包含靜態成員的類別 \(當然除了繼承自的執行個體成員 <xref:System.Object?displayProperty=fullName> 和可能的私用建構函式\)。 有些語言提供靜態類別內建支援。 在 C\# 2.0 版及更新版本中，當類別會宣告為靜態，它是密封的抽象，而且可以覆寫或宣告沒有任何執行個體成員。  
  
 靜態類別是純粹物件導向設計和簡化之間取得折衷。 它們通常用來提供其他作業的捷徑 \(例如 <xref:System.IO.File?displayProperty=fullName>\)，擴充方法或功能的完整物件導向包裝函式是未經授權的持有者 \(例如 <xref:System.Environment?displayProperty=fullName>\)。  
  
 **✓ 執行** 謹慎使用靜態類別。  
  
 靜態類別應只做為支援物件導向的核心架構的類別。  
  
 **X 不** 視為其他的值區的靜態類別。  
  
 **X 不** 宣告或覆寫在靜態類別的執行個體成員。  
  
 **✓ 執行** 宣告為密封，抽象的並新增私用執行個體建構函式，如果您的程式語言沒有內建支援靜態類別。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)