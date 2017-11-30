---
title: "如何：接聽具有等候控制代碼的取消要求"
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
helpviewer_keywords: cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1eaa84d924fde63e94c36fab50a809c7c03f075
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>如何：接聽具有等候控制代碼的取消要求
方法會封鎖並同時它正在等待事件發出信號，如果它無法檢查的取消語彙基元的值，並及時回應。 第一個範例示範如何解決這個問題，當您使用事件這類<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>原生不支援統一的取消架構。 第二個範例將示範以更有效率的方法使用<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>，支援整合取消。  
  
> [!NOTE]
>  啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。 這個錯誤是良性的。 您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。 若要防止 Visual Studio 的第一個錯誤的中斷，只要取消核取下的 [Just My Code] 核取方塊**工具、 選項、 偵錯、 一般**。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Threading.ManualResetEvent>示範如何解除封鎖等候控制代碼不支援統一的取消。  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Threading.ManualResetEventSlim>示範如何解除封鎖協調支援的基本型別統一的取消。 相同的方法可以搭配其他輕量型協調基本類型，例如<xref:System.Threading.Semaphore>`Slim`和<xref:System.Threading.CountdownEvent>。  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>另請參閱  
 [Managed 執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)
