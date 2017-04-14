---
title: "How to: Wrap EAP Patterns in a Task | Microsoft Docs"
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
  - "tasks, how to wrap EAP patterns"
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Wrap EAP Patterns in a Task
下列範例示範如何使用 <xref:System.Threading.Tasks.TaskCompletionSource%601>，將任意的可延伸驗證通訊協定主機 \(EAP\) 非同步作業序列以一項工作的形式公開。  這個範例也顯示如何使用 <xref:System.Threading.CancellationToken>，在 <xref:System.Net.WebClient> 物件上叫用內建的取消方法。  
  
## 範例  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## 請參閱  
 [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)