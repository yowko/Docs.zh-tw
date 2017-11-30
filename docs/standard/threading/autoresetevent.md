---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent>類別表示收到信號時，發行單一等候中執行緒後自動重設本機等候控制代碼事件。 此類別代表其基底類別的特殊案例<xref:System.Threading.EventWaitHandle>。 如需自動重設事件的用法和功能，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。  
  
 <xref:System.Threading.AutoResetEvent>物件會自動重設為未收到訊號系統釋放單一等候中執行緒之後。 如果沒有執行緒在等候，事件物件的狀態會維持已收到信號。 <xref:System.Threading.AutoResetEvent>對應至 Win32`CreateEvent`呼叫時，指定`false`如`bManualReset`引數。  
  
 如需範例，會使用<xref:System.Threading.AutoResetEvent>，請參閱[監視器](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [等候控制代碼](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
