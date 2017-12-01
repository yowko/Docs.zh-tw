---
title: "如何：透過輪詢接聽取消要求"
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
helpviewer_keywords: cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f0e05e3f66d591a28d7e84d358934959764dab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>如何：透過輪詢接聽取消要求
下列範例會顯示其中一個方法，使用者程式碼可讓呼叫執行緒是否已要求取消的固定間隔輪詢取消語彙基元。 這個範例會使用<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>類型，但相同的模式適用於直接以建立非同步作業<xref:System.Threading.ThreadPool?displayProperty=nameWithType>類型或<xref:System.Threading.Thread?displayProperty=nameWithType>型別。  
  
## <a name="example"></a>範例  
 輪詢需要某種迴圈或遞迴可以定期讀取的布林值的程式碼<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>屬性。 如果您使用<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>類型和您等候工作完成呼叫的執行緒上，您可以使用<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>方法來檢查屬性，並擲回例外狀況。 使用此方法，您可以確保回應的要求中擲回正確的例外狀況。 如果您使用<xref:System.Threading.Tasks.Task>，則呼叫此方法優於手動擲回<xref:System.OperationCanceledException>。 如果您沒有擲回例外狀況，則只需要檢查的屬性，並從方法傳回，如果屬性是`true`。  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 呼叫<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>相當快速，不會產生迴圈中的重大額外負荷。  
  
 如果您將會呼叫<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>，您只需要明確檢查<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>屬性，如果您有其他工作來回應取消作業，除了擲回例外狀況。 在此範例中，您可以看到的程式碼實際屬性存取兩次： 一次在明確的存取，然後再次在<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>方法。 但是由於讀取動作<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>屬性牽涉只能有一個暫時性讀取每次存取的指令，表示兩個存取並不重要從效能觀點來看。 最好還是以呼叫方法，而非手動擲回<xref:System.OperationCanceledException>。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)
