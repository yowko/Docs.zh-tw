---
title: 如何：透過輪詢接聽取消要求
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1794b47db87f636cc2ccdf2eecb9e7ca334ae659
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266848"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>如何：透過輪詢接聽取消要求
下列範例將示範一種方式：使用者程式碼可定期輪詢取消語彙基元，以查看呼叫執行緒是否已要求取消。 這個範例會使用 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類型，但相同的模式適用於 <xref:System.Threading.ThreadPool?displayProperty=nameWithType> 類型或 <xref:System.Threading.Thread?displayProperty=nameWithType> 類型直接建立的非同步作業。  
  
## <a name="example"></a>範例  
 輪詢需要某種可定期讀取布林值 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性值的迴圈或遞迴程式碼。 如果您使用 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類型且正在等候呼叫執行緒上的工作完成，您可以使用 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 方法來檢查屬性，並擲回例外狀況。 使用此方法，您可以確保會擲回正確的例外狀況來回應要求。 如果您使用 <xref:System.Threading.Tasks.Task>，則呼叫此方法優於手動擲回 <xref:System.OperationCanceledException>。 如果您不需擲回例外狀況，則只需檢查屬性，如果屬性為 `true`，即從方法返回。  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 呼叫 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 相當快速，不會在迴圈中引進大量額外負荷。  
  
 如果您正在呼叫 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>，當您要進行其他工作來回應取消 (擲回例外狀況除外) 時，只需明確檢查 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性。 在此範例中，您可以看到程式碼會實際存取屬性兩次：一次是明確的存取，另一次則是在 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 方法中。 但由於讀取 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性的動作牽涉到每次存取只能有一個暫時性讀取指令，因此，從效能觀點來看，兩次存取並不重要。 最好還是呼叫方法，而非手動擲回 <xref:System.OperationCanceledException>。  
  
## <a name="see-also"></a>另請參閱

- [Managed 執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)
