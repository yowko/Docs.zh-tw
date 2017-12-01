---
title: "如何：取消工作及其子系"
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
helpviewer_keywords: tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 374068694a3aa9724905964717dc5e77c09fc0ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-task-and-its-children"></a>如何：取消工作及其子系
這些範例會示範如何執行下列工作：  
  
1.  建立及啟動可取消的工作。  
  
2.  將取消語彙基元傳遞至您的使用者委派和選擇性工作執行個體。  
  
3.  請注意並回應取消要求，在您的使用者委派。  
  
4.  （選擇性） 請注意在呼叫執行緒上已取消工作。  
  
 呼叫的執行緒並不會強制結束工作。它只會通知已要求取消。 如果工作已在執行中，會決定要注意要求與回應適當的使用者委派。 如果工作執行前要求取消，則永遠不會執行的使用者委派，然後工作物件轉換至 Canceled 狀態。  
  
## <a name="example"></a>範例  
 此範例顯示如何結束<xref:System.Threading.Tasks.Task>及其子系，以回應取消要求。 這個範例也會說明在使用者委派藉由擲回 <xref:System.Threading.Tasks.TaskCanceledException> 結束時，呼叫端執行緒可以選擇性地使用 <xref:System.Threading.Tasks.Task.Wait%2A> 方法或 <xref:System.Threading.Tasks.Task.WaitAll%2A> 方法等候工作完成。 在這種情況下，您必須使用 `try/catch` 區塊來處理呼叫端執行緒上的例外狀況。  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>類別完全整合在一起的取消模型為基礎的<xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>和<xref:System.Threading.CancellationToken?displayProperty=nameWithType>型別。 如需詳細資訊，請參閱[Managed 執行緒中的取消](../../../docs/standard/threading/cancellation-in-managed-threads.md)和[工作取消](../../../docs/standard/parallel-programming/task-cancellation.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>  
 <xref:System.Threading.CancellationToken?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
 [以工作為基礎的非同步程式設計](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [附加與中斷連結的子工作](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)  
 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
