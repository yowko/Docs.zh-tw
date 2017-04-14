---
title: "擲回例外狀況 | Microsoft Docs"
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
  - "例外狀況，擲回"
  - "明確擲回例外狀況"
  - "擲回例外狀況，設計方針"
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 擲回例外狀況
擲回例外狀況這一節中所述的指導方針需要良好定義的執行失敗的意義。 每當成員不是什麼，就會發生執行失敗設計 （其成員名稱一樣）。 例如，如果 `OpenFile` 方法無法傳回給呼叫端的開啟的檔案控制代碼，則會視為執行失敗。  
  
 大部分的開發人員已熟悉使用例如部門的使用方式錯誤由零或 null 參考例外狀況。 在架構中，例外狀況會用於所有的錯誤狀況，包括執行錯誤。  
  
 **X 不** 傳回錯誤碼。  
  
 例外狀況是報告錯誤的架構中的主要方法。  
  
 **✓ 執行** 報表執行失敗，所擲回例外狀況。  
  
 **✓ 考慮** 藉由呼叫終止處理序 `System.Environment.FailFast` （.NET Framework 2.0 的功能） 而非擲回例外狀況，如果您遇到的情況下是不安全的進一步執行。  
  
 **X 不** 盡可能使用一般流程控制、 例外狀況。  
  
 除了系統故障和作業可能發生競爭情形，架構設計人員應該設計 Api，讓使用者可以撰寫程式碼不會擲回例外狀況。 例如，您可以提供檢查先決條件之前呼叫成員，因此使用者可以撰寫程式碼不會擲回例外狀況的方法。  
  
 用來檢查先決條件的另一個成員的成員通常稱為軟體測試人員，並呼叫 doer 實際運作的成員。  
  
 Tester\-doer 模式可能無法接受的效能負荷一些情況。 在這種情況下，您應考慮所謂試剖析模式 \(請參閱 [例外狀況和效能](../../../docs/standard/design-guidelines/exceptions-and-performance.md) 如需詳細資訊\)。  
  
 **✓ 考慮** 擲回例外狀況的效能含意。 每秒 100 以上擲回率是有可能會明顯影響大部分的應用程式的效能。  
  
 **✓ 執行** 擲回的公開呼叫成員，因為發生違規之成員的所有例外狀況 （而非系統失敗） 合約，並將其視為您的合約的一部分的文件。  
  
 例外狀況合約的一部分，不應該變更從一個版本到下一個 （亦即，不應該變更例外狀況類型，和不應該加入新的例外狀況）。  
  
 **X 不** 或不可以是擲回的公用成員取決於一些選項。  
  
 **X 不** 擁有 public 成員例外狀況傳回為傳回值或 `out` 參數。  
  
 傳回從公開的 Api，而不是擲回的例外狀況就失去了許多優點例外狀況的錯誤報告。  
  
 **✓ 考慮** 使用例外狀況產生器方法。  
  
 通常會從不同的地方擲回相同的例外狀況。 若要避免程式碼，請使用 helper 方法，建立例外狀況，並初始化其屬性。  
  
 此外，成員擲回例外狀況不會進行內嵌。 移動產生器將 throw 陳述式可能會允許內嵌的成員。  
  
 **X 不** 擲回例外狀況的例外狀況篩選條件區塊。  
  
 當例外狀況篩選條件會引發例外狀況時，clr，攔截例外狀況，而且篩選條件會傳回 false。 這種行為是區別篩選執行及明確傳回 false，因此很難進行偵錯。  
  
 **X 避免** 明確擲回例外狀況的 finally 區塊。 隱含擲回的例外狀況呼叫擲回的方法產生的可接受的。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [例外狀況的設計指導方針](../../../docs/standard/design-guidelines/exceptions.md)