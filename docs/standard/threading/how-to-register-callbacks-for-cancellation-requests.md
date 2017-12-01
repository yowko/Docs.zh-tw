---
title: "如何：註冊取消要求的回呼"
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
helpviewer_keywords: cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85b15ed610d80958ac9d7e3762ac8ea7b781b8d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>如何：註冊取消要求的回呼
下列範例示範如何註冊委派，會叫用時<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>屬性變成 true 由於呼叫<xref:System.Threading.CancellationTokenSource.Cancel%2A>上建立權杖的物件。 您可以使用這個技巧來取消原本不支援整合取消架構的非同步作業，以及解除封鎖可能會等候非同步作業完成的方法。  
  
> [!NOTE]
>  啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。 這個錯誤是良性的。 您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。 若要防止 Visual Studio 的第一個錯誤的中斷，只要取消核取下的 [Just My Code] 核取方塊**工具、 選項、 偵錯、 一般**。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Net.WebClient.CancelAsync%2A> 方法註冊為透過取消語彙基元要求取消時，所要叫用的方法。  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 如果註冊回呼時，已經要求過取消，仍然保證會呼叫回呼。 在這個特殊案例中，如果沒有任何非同步作業正在進行中，<xref:System.Net.WebClient.CancelAsync%2A> 方法就不會做任何事，所以呼叫方法一定是安全的。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)
