---
title: "Canceling Threads Cooperatively | Microsoft Docs"
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
  - "threads, cancellation"
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Canceling Threads Cooperatively
在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 之前，.NET Framework 不會提供內建，以便在執行緒啟動後以合作方式加以取消。 不過，在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，您可以使用取消語彙基元來取消執行緒，就如同您可以使用它們來取消 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 物件或 PLINQ 查詢。 雖然 <xref:System.Threading.Thread?displayProperty=fullName> 類別不提供取消語彙基元的內建支援，您仍可透過使用採取 <xref:System.Threading.ParameterizedThreadStart> 委派的 <xref:System.Threading.Thread> 建構函式，將語彙基元傳遞至執行緒程序。 下列範例示範如何進行這項操作。  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## 請參閱  
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)