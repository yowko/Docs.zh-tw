---
title: "如何：建立使用者定義的例外狀況 | Microsoft Docs"
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
  - "例外狀況, 範例"
  - "例外狀況, 使用者定義"
  - "使用者定義的例外狀況"
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立使用者定義的例外狀況
如果您想要使用者能夠利用程式設計方式來區別某些錯誤情況，您可以建立自己的使用者定義的例外狀況。  .NET Framework 提供最終衍生自基底類別 <xref:System.Exception> 的例外狀況類別的階層架構。  這些類別的每一個都會定義特定例外狀況，所以在許多情形中您只需攔截例外狀況即可。  您也可以藉著從 <xref:System.Exception> 類別衍生，建立自己的 Exception 類別。  
  
 在建立您自己的例外狀況時，以文字 "Exception" 當做使用者定義的例外狀況的類別名稱結尾，是比較好的程式撰寫作法。 實作三個如下列範例所示範的建議的通用建構函式 \(Constructor\)，也是不錯的作法。  
  
> [!NOTE]
>  在使用遠端處理的情形中，您必須確定伺服器 \(被呼叫端\) 上具有任何使用者定義的例外狀況中繼資料 \(Metadata\) 可供用戶端 \(Proxy 物件或呼叫端\) 使用。  例如，呼叫不同應用程式定義域方法的程式碼必須能夠尋找含有遠端呼叫擲回的例外狀況的組件。  如需詳細資訊，請參閱[處理例外狀況的最佳作法](../../../docs/standard/exceptions/best-practices-for-exceptions.md)。  
  
 在下列範例中，新的 Exception 類別 `EmployeeListNotFoundException` 衍生自 <xref:System.Exception>。  這些建構函式是在類別中定義的，每個建構函式都採用不同的參數。  
  
## 範例  
 [!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
 [!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
 [!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  
  
## 請參閱  
 [如何：使用 Try\/Catch 區塊攔截例外狀況](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [如何：使用 Catch 區塊中的特定例外狀況](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)   
 [例外狀況的最佳作法](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [例外狀況處理基礎觀念](../../../docs/standard/exceptions/exception-handling-fundamentals.md)