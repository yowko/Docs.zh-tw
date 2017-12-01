---
title: "ManualResetEvent 和 ManualResetEventSlim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f663dd17b063f77e2f9ce6bd4bbd0f8859ba4116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent 和 ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>類別表示本機等候控制代碼事件，必須手動重設之後收到信號。 此類別代表其基底類別的特殊案例<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>。 如需手動重設事件的用法和功能，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。  
  
 A<xref:System.Threading.ManualResetEvent>物件仍會維持已收到信號，直到其<xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType>方法呼叫。 任何數目的等候執行緒或在收到訊號之後等候事件的執行緒，皆可在物件的狀態為收到訊號時加以釋放。 <xref:System.Threading.ManualResetEvent>對應至 Win32`CreateEvent`呼叫時，指定`true`如`bManualReset`引數。  
  
 在[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>類別以提升效能，應等候時間很短，而且事件不會跨處理序界限時。 <xref:System.Threading.ManualResetEventSlim>使用忙碌旋轉一小段時間，同時等候事件發出訊號。 若等候時間很短，旋轉功能的成本會遠低於使用等候控制代碼來等候。 不過，如果事件不會不會被通知的時間，在特定期間內<xref:System.Threading.ManualResetEventSlim>訴諸等候一般事件控制代碼。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [等候控制代碼](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Semaphore 和 SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
