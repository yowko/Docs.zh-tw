---
title: "如何：明確擲回例外狀況 | Microsoft Docs"
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
  - "例外狀況, 擲回"
  - "例外狀況, try/catch 區塊"
  - "FileNotFoundException 類別"
  - "隱含擲回例外狀況"
  - "try/catch 區塊"
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：明確擲回例外狀況
您可以使用 `throw` 陳述式，明確擲回例外狀況。  您也可以使用 `throw` 陳述式，再次將已攔截的例外狀況擲回。  加入資訊至例外狀況 \(在偵錯時被重新擲回以提供更多資訊\)，是良好的程式設計方式。  
  
 下列程式碼範例使用 Try\/Catch 區塊來攔截可能的 <xref:System.IO.FileNotFoundException>。  Try 區塊之後的是會攔截 <xref:System.IO.FileNotFoundException>，且如果沒找到資料檔案就將訊息寫入至主控台的 Catch 區塊。  下一個陳述式是 Throw 陳述式，它會擲回新的 <xref:System.IO.FileNotFoundException> 並加入文字資訊至例外狀況。  
  
## 範例  
 [!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
 [!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  
  
## 請參閱  
 [如何：使用 Try\/Catch 區塊攔截例外狀況](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [如何：使用 Catch 區塊中的特定例外狀況](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)   
 [如何：使用 Finally 區塊](../../../docs/standard/exceptions/how-to-use-finally-blocks.md)   
 [例外狀況處理基礎觀念](../../../docs/standard/exceptions/exception-handling-fundamentals.md)