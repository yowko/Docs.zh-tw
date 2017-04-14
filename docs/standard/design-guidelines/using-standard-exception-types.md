---
title: "使用標準的例外狀況類型 | Microsoft Docs"
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
  - "擲回例外狀況，標準類型"
  - "攔截例外狀況"
  - "例外狀況攔截"
  - "例外狀況，擲回"
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# 使用標準的例外狀況類型
本章節描述架構和其使用方式的詳細資料所提供的標準例外狀況。 清單是不是完整清單。 請參閱.NET Framework 參考文件的使用方式的其他 Framework 例外狀況型別。  
  
## 例外狀況和 SystemException  
 **X 不** 擲回 <xref:System.Exception?displayProperty=fullName> 或 <xref:System.SystemException?displayProperty=fullName>。  
  
 **X 不** 攔截 `System.Exception` 或 `System.SystemException` framework 程式碼中，除非您想要重新擲回。  
  
 **X 避免** 攔截 `System.Exception` 或 `System.SystemException`, ，除非在最上層例外狀況處理常式。  
  
## ApplicationException  
 **X 不** 擲回或衍生自 <xref:System.ApplicationException>。  
  
## InvalidOperationException  
 **✓ 執行** 擲回 <xref:System.InvalidOperationException> 的物件是否處於不適當的狀態。  
  
## ArgumentException、 ArgumentNullException 和 ArgumentOutOfRangeException  
 **✓ 執行** 擲回 <xref:System.ArgumentException> 或如果不正確的引數傳遞至成員及其子型別之一。 適用於想最具衍生性的例外狀況類型。  
  
 **✓ 執行** 設定 `ParamName` 屬性時擲回的子類別的其中一個 `ArgumentException`。  
  
 這個屬性代表造成例外狀況的參數名稱。 請注意，這個屬性可以設定使用其中一個建構函式多載。  
  
 **✓ 執行** 使用 `value` 屬性 setter 的隱含值參數的名稱。  
  
## NullReferenceException、 IndexOutOfRangeException 和 AccessViolationException  
 **X 不** 允許公開呼叫的 Api 以明確或隱含擲回 <xref:System.NullReferenceException>, ，<xref:System.AccessViolationException>, ，或 <xref:System.IndexOutOfRangeException>。 這些例外狀況會保留並擲回的執行引擎在大部分情況下表示 bug。  
  
 執行檢查，以避免擲回這些例外狀況的引數。 擲回這些例外狀況會公開您可能會隨著時間變更的方法的實作詳細資料。  
  
## StackOverflowException  
 **X 不** 明確擲回 <xref:System.StackOverflowException>。 應該在只能由 CLR 明確擲回例外狀況。  
  
 **X 不** 攔截 `StackOverflowException`。  
  
 就幾乎不可能撰寫 managed 程式碼都保持一致任意堆疊溢位時。 Unmanaged 的 CLR 組件會使用探查移動堆疊溢位定義完善的地方而非從任意堆疊溢位退出保持一致。  
  
## OutOfMemoryException  
 **X 不** 明確擲回 <xref:System.OutOfMemoryException>。 是僅由 CLR 基礎結構會擲回這個例外狀況。  
  
## ComException、 SEHException 和 ExecutionEngineException  
 **X 不** 明確擲回 <xref:System.Runtime.InteropServices.COMException>,  ，<xref:System.ExecutionEngineException>, ，和 <xref:System.Runtime.InteropServices.SEHException>。 這些例外狀況是由 CLR 基礎結構只擲回。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [例外狀況的設計指導方針](../../../docs/standard/design-guidelines/exceptions.md)