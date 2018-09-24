---
title: AutoResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38efbe0ecd88c02752d610de4b1eec8b62eca1f8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46937539"
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> 類別代表在釋出單一等候執行緒後，收到信號時會自動重設的本機等候控制代碼事件。 此類別代表其基底類別 <xref:System.Threading.EventWaitHandle> 的特殊案例。 如需自動重設事件的用法和功能，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。  
  
 在單一等候執行緒釋出之後，系統自動會將 <xref:System.Threading.AutoResetEvent> 物件重設為未收到信號。 如果沒有執行緒在等候，事件物件的狀態會維持已收到信號。
  
 如需使用 <xref:System.Threading.AutoResetEvent> 的範例，請參閱 <xref:System.Threading.Monitor>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Monitor>  
- [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [執行緒處理](../../../docs/standard/threading/index.md)  
- [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)  
- [等候控制代碼](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
