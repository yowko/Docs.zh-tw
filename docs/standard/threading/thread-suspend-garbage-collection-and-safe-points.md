---
title: Thread.Suspend、記憶體回收和安全點
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ded5c057b1c257e8bcf3c8427f5810720eaf0947
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582157"
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend、記憶體回收和安全點
當您在執行緒上呼叫 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> 時，系統會注意到已要求執行緒暫止，並允許執行緒在實際暫止執行緒之前執行，直到它到達安全點為止。 執行緒的安全點是在其執行中可執行記憶體回收的點。  
  
 一旦達到安全點之後，執行階段可保證暫止的執行緒將不會在受控碼中有任何進一步的進展。 在受控碼以外執行的執行緒一律可安全地進行記憶體回收，而且它的執行會繼續，直到它嘗試繼續執行受控碼為止。  
  
> [!NOTE]
>  若要執行記憶體回收，執行階段必須暫止所有執行緒，但執行記憶體回收的執行緒除外。 每個執行緒都必須在暫止之前被帶至安全點。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [自動管理記憶體](../../../docs/standard/automatic-memory-management.md)
