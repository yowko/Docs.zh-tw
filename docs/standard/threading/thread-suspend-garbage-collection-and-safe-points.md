---
title: "Thread.Suspend、記憶體回收和安全點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e47674ef8d1b1a7487e42765bcbce4b33cf98769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend、記憶體回收和安全點
當您呼叫<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>執行緒上、 系統資訊執行緒暫止要求，並且可讓執行緒執行，直到它到達之前實際暫止執行緒安全的點。 安全執行緒的點是在記憶體回收的集合可以執行其執行中的點。  
  
 一旦達到安全點時，執行階段可保證，暫停的執行緒不會進行任何進一步的處理 managed 程式碼中。 執行 managed 程式碼以外的執行緒會一律安全地進行記憶體回收，而且它會嘗試繼續執行 managed 程式碼直到其執行。  
  
> [!NOTE]
>  若要執行記憶體回收，執行階段必須暫停執行回收的執行緒除外的所有執行緒。 在暫停之前，必須讓每個執行緒安全的點。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [自動管理記憶體](../../../docs/standard/automatic-memory-management.md)
