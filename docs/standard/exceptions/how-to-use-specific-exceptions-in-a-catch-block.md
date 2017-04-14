---
title: "如何：使用 Catch 區塊中的特定例外狀況 | Microsoft Docs"
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
  - "catch 區塊"
  - "例外狀況, try/catch 區塊"
  - "try/catch 區塊"
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用 Catch 區塊中的特定例外狀況
當例外狀況發生時，它會在堆疊中向上傳遞，而讓各個 Catch 區塊都有機會來處理它。  Catch 陳述式的順序很重要。  請針對特定例外狀況將 Catch 區塊放在一般例外狀況 Catch 區塊之前，否則編譯器 \(Compiler\) 可能會發出錯誤。  適當的 Catch 區塊會藉著將 Catch 區塊中指定的例外狀況名稱與例外狀況類型作比對來決定。  如果沒有特定的 Catch 區塊，例外狀況由一般 Catch 區塊 \(若有一個的話\) 來攔截。  
  
 下列程式碼範例使用 Try\/Catch 區塊來攔截 <xref:System.InvalidCastException>。  範例建立稱為 `Employee` 的類別，它具有單一屬性「員工職等」\(`Emlevel`\)。  方法 `, PromoteEmployee` 會接受物件並增加員工職等。  當 <xref:System.DateTime> 執行個體傳遞至 `PromoteEmployee` 方法時，就會發生 **InvalidCastException**。  
  
## 範例  
 [!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
 [!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
 [!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]  
  
 Common Language Runtime 會攔截未被 Catch 區塊攔截的例外狀況。  取決於執行階段如何被設定，不是偵錯對話方塊出現，就是程式停止執行而出現帶有例外狀況資訊的對話方塊。  如需偵錯的詳細資訊，請參閱[偵錯和分析應用程式](../../../docs/framework/debug-trace-profile/index.md)。  
  
## 請參閱  
 [如何：使用 Try\/Catch 區塊攔截例外狀況](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [如何：明確擲回例外狀況](../../../docs/standard/exceptions/how-to-explicitly-throw-exceptions.md)   
 [如何：建立使用者定義的例外狀況](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)   
 [如何：使用 Finally 區塊](../../../docs/standard/exceptions/how-to-use-finally-blocks.md)   
 [Exception 類別和屬性](../../../docs/standard/exceptions/exception-class-and-properties.md)   
 [例外狀況處理基礎觀念](../../../docs/standard/exceptions/exception-handling-fundamentals.md)