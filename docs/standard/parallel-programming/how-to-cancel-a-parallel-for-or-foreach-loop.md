---
title: "如何：取消 Parallel.For 或 ForEach 迴圈"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f82c5758e02b4beebf035fe8f43f856447855a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>如何：取消 Parallel.For 或 ForEach 迴圈
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>和<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>方法使用支援取消作業取消語彙基元。 如需有關取消一般情況下，請參閱[取消](../../../docs/standard/threading/cancellation-in-managed-threads.md)。 在平行迴圈中，您提供<xref:System.Threading.CancellationToken>中方法<xref:System.Threading.Tasks.ParallelOptions>參數並再將平行呼叫括在 try catch 區塊。  
  
## <a name="example"></a>範例  
 下列範例示範如何取消呼叫<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>。 您可以套用至相同的方法<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>呼叫。  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 如果通知取消語彙基元相同語彙基元中指定<xref:System.Threading.Tasks.ParallelOptions>執行個體，則平行迴圈，將會擲回單一<xref:System.OperationCanceledException>上取消作業。 如果其他語彙基元會導致取消，迴圈將會擲回<xref:System.AggregateException>與<xref:System.OperationCanceledException>為 InnerException。  
  
## <a name="see-also"></a>另請參閱  
 [資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
