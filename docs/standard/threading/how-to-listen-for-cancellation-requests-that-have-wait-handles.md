---
title: "How to: Listen for Cancellation Requests That Have Wait Handles | Microsoft Docs"
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
  - "cancellation, waiting with wait handles"
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Listen for Cancellation Requests That Have Wait Handles
如果方法在等候事件接收信號時遭到封鎖，就無法檢查取消語彙基元的值並且即時回應。  在第一個範例中，會示範如何在您使用並非原生支援統一取消架構的事件 \(例如 <xref:System.Threading.ManualResetEvent?displayProperty=fullName>\) 時解決這個問題。  第二個範例顯示更多使用 <xref:System.Threading.ManualResetEventSlim?displayProperty=fullName> 的精簡方法，此方式支援統一取消。  
  
> [!NOTE]
>  啟用 "Just My Code" 時，Visual Studio 有時候會在擲回例外狀況的程式碼行處中斷，並顯示「使用者程式碼未處理的例外狀況」之類的錯誤訊息。這是良性的錯誤。  您可以按 F5 從中斷的地方繼續，並看到下面範例所示的例外狀況處理行為。  若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消選取 \[工具\]、\[選項\]、\[偵錯\]、\[一般\] 下的 \[Just My Code\] 核取方塊即可。  
  
## 範例  
 下列範例會使用 <xref:System.Threading.ManualResetEvent>，示範如何對不支援統一取消的等候控制代碼解除封鎖。  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## 範例  
 下列範例會使用 <xref:System.Threading.ManualResetEventSlim>，示範如何對不支援統一取消的統整式基本項目解除封鎖。  相同的方法可以用於其他輕量型的統整式基本項目，例如 <xref:System.Threading.Semaphore>`Slim` 與 <xref:System.Threading.CountdownEvent>。  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## 請參閱  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)