---
title: "How to: Listen for Cancellation Requests by Polling | Microsoft Docs"
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
  - "cancellation, how to poll for requests"
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# How to: Listen for Cancellation Requests by Polling
下列範例示範一種方式，讓使用者程式碼可以定期輪詢取消語彙基元，確認取消是否已透過呼叫執行緒提出。  這個範例會使用 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 型別，但是相同的模式適用直接由 <xref:System.Threading.ThreadPool?displayProperty=fullName> 型別或 <xref:System.Threading.Thread?displayProperty=fullName> 型別所建立的非同步作業。  
  
## 範例  
 輪詢需要使用某些迴圈或遞迴程式碼，因為這類程式碼可以定期讀取布林 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性的值。  如果您使用的是 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 型別並且要等候工作於呼叫執行緒上完成，那麼可以使用 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 方法檢查屬性並擲回例外狀況。  您可以使用這個方法，確保擲回正確的例外狀況來回應要求。  如果使用的是 <xref:System.Threading.Tasks.Task>，那麼呼叫這個方法要比手動擲回 <xref:System.OperationCanceledException> 來得理想。  如果您不需要擲回例外狀況，那麼可以只檢查屬性，並且在屬性為 `true` 時自方法傳回。  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 呼叫 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 相當快速，而且不會在迴圈中加入過多執行工作。  
  
 如果呼叫的是 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>，且如果除了擲回例外狀況，您還需要執行其他工作以便對取消做出回應，那麼只需要明確地檢查 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性。  在這個範例中，您可以看到程式碼實際存取該屬性兩次，一次是在明確存取中，第二次則在 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 方法中。  但是，由於每次存取時，讀取 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性的動作只需用到一次 Volatile 讀取指令，因此存取兩次對於效能而言並不會產生很大的影響。  所以呼叫此方法仍然比手動擲回 <xref:System.OperationCanceledException> 來得理想。  
  
## 請參閱  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)