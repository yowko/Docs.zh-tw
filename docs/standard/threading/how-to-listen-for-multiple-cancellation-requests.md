---
title: "How to: Listen for Multiple Cancellation Requests | Microsoft Docs"
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
  - "cancellation tokens, joining"
  - "LinkedTokenSource, how to"
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Listen for Multiple Cancellation Requests
這個範例示範如何同時接聽兩個取消語彙基元，如此任一語彙基元要求取消作業時，您便可以取消作業。  
  
> [!NOTE]
>  啟用 "Just My Code" 時，Visual Studio 有時候會在擲回例外狀況的程式碼行處中斷，並顯示「使用者程式碼未處理的例外狀況」之類的錯誤訊息。這是良性的錯誤。  您可以按 F5 從中斷的地方繼續，並看到下面範例所示的例外狀況處理行為。  若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消選取 \[工具\]、\[選項\]、\[偵錯\]、\[一般\] 下的 \[Just My Code\] 核取方塊即可。  
  
## 範例  
 在下列範例中，<xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> 方法會用於將兩個語彙基元聯結成為一個。  這可以讓語彙基元傳遞給只接受一個取消語彙基元做為引數的方法。  這個範例示範常見的使用案例，其中方法必須觀察從類別外部傳入的語彙基元以及類別內部所產生的語彙基元。  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 當連結後的語彙基元擲回 <xref:System.OperationCanceledException> 時，傳遞給例外狀況的語彙基元為連結後的語彙基元，而不是前置項語彙基元。  若要判斷取消的是哪個語彙基元，請直接檢查前置項語彙基元的狀態。  
  
 在這個範例中，絕對不可擲回 <xref:System.AggregateException>，但在此處卻攔截到，原因是在現實情況中，除了 <xref:System.OperationCanceledException> 以外，從工作委派中擲回的任何其他例外狀況，都是包裝在 <xref:System.OperationCanceledException>。  
  
## 請參閱  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)