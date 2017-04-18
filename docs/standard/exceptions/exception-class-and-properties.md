---
title: "Exception 類別和屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exception 類別"
  - "例外狀況, Exception 類別"
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Exception 類別和屬性
<xref:System.Exception> 類別為例外狀況所繼承的基底類別 \(Base Class\)。  大部分的例外狀況物件都是 **Exception** 衍生類別的執行個體，但您可以將所有由 <xref:System.Object> 類別衍生出來的物件當做是例外狀況擲回。  注意，並非所有語言都支援擲回和攔截不是衍生自 **Exception** 的物件。  在幾乎所有的情形中，建議您只需擲回並攔截 **Exception** 物件。  
  
 **Exception** 類別具有數個屬性，使得對例外狀況的了解更簡單。  這些屬性包括：  
  
-   <xref:System.Exception.StackTrace%2A> 屬性。  
  
     這個屬性包含堆疊追蹤，可以用來確定何處錯誤發生。  堆疊追蹤包括來源檔名稱和程式行號 \(若有偵錯資訊的話\)。  
  
-   <xref:System.Exception.InnerException%2A> 屬性。  
  
     這個屬性可以用來在例外處理期間建立和保留例外狀況的系列。  您可以使用這個屬性建立含有先前攔截的例外狀況的新例外狀況。  原始例外狀況在 **InnerException** 屬性中可以被第二個例外狀況擷取，並讓處理第二個例外狀況的程式碼得以檢查額外資訊。  
  
     例如，假定您有讀取檔案及格式化讀取資料的方法。  程式碼嘗試從檔案讀取，但有 FileException 被擲回。  方法攔截 FileException 並擲回 BadFormatException。  在這個情形中，FileException 可以儲存於 BadFormatException 的 **InnerException** 屬性。  
  
     若要改善呼叫端的能力以確定例外狀況被擲回的理由，則需要方法攔截 Helper 常式擲回的例外狀況，並接著擲回更能表明已發生錯誤的例外狀況。  您可以建立新的和較有意義的例外狀況，其中內部例外狀況參考可設定為原始例外狀況。  然後，這個更有意義的例外狀況可以擲回給呼叫端。  注意，有了這個功能，您就可以建立連結的例外狀況系列，這系列以最先擲回的例外狀況做為結尾。  
  
-   <xref:System.Exception.Message%2A> 屬性。  
  
     這個屬性提供例外狀況起因的詳細資訊。  **Message** 是以擲回例外狀況之執行緒的 <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=fullName> 屬性指定的語言顯示。  
  
-   <xref:System.Exception.HelpLink%2A> 屬性。  
  
     這個屬性可以儲存說明檔 \(提供大量例外狀況起因的資訊\) 的 URL \(或 URN\)。  
  
-   <xref:System.Exception.Data%2A> 屬性  
  
     此屬性為 IDictionary，能夠在機碼值組中保留任意資料。  
  
 繼承自 **Exception** 的大部分類別並不實作額外成員或提供額外功能；它們僅是繼承自 **Exception**。  因此，例外狀況的最重要資訊可能存在於例外狀況的階層架構、例外狀況名稱和包含於例外狀況中的資訊。  
  
## 請參閱  
 [例外狀況階層架構](../../../docs/standard/exceptions/exception-hierarchy.md)   
 [例外狀況處理基礎觀念](../../../docs/standard/exceptions/exception-handling-fundamentals.md)   
 [例外狀況的最佳作法](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [例外狀況](../../../docs/standard/exceptions/index.md)