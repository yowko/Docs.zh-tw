---
title: dangerousThreadingAPI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3cfbc1439be457987c058ee6d0298e93aa37f5d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716009"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI MDA
在目前執行緒以外的執行緒上呼叫 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> 方法時，會啟用 `dangerousThreadingAPI` Managed 偵錯助理 (MDA)。  
  
## <a name="symptoms"></a>徵兆  
 應用程式沒有回應或無限期停止回應。 系統或應用程式資料可能會暫時處於無法預測的狀態，或甚至已關閉應用程式。 某些作業未如預期完成。  
  
 由於這個問題原有的隨機性，徵兆可能會有很大的不同。  
  
## <a name="cause"></a>原因  
 使用 <xref:System.Threading.Thread.Suspend%2A> 方法，將執行緒非同步取代為另一個執行緒。 沒有任何方法可判斷執行緒何時可以安全地暫止另一個執行緒，而後者可能正在進行。 暫止執行緒可能會導致資料損毀或非變異值中斷。 如果執行緒進入暫止狀態，而且絕不會繼續使用 <xref:System.Threading.Thread.Resume%2A> 方法，則應用程式可能會無限期停止回應，並且可能破壞應用程式資料。 這些方法已標記為過時。  
  
 如果目標執行緒擁有同步處理原始物件，則在暫止期間仍會擁有它們。 如果另一個執行緒 (例如執行 <xref:System.Threading.Thread.Suspend%2A> 的執行緒) 嘗試取得原始物件的鎖定，則這可能會導致死結。 在此情況下，問題資訊清單本身會是死結。  
  
## <a name="resolution"></a>解決方式  
 請避免需要使用 <xref:System.Threading.Thread.Suspend%2A> 和 <xref:System.Threading.Thread.Resume%2A> 的設計。 對於執行緒之間的合作，請使用同步處理原始物件，例如 <xref:System.Threading.Monitor>、<xref:System.Threading.ReaderWriterLock>、<xref:System.Threading.Mutex> 或 C# `lock` 陳述式。 如果您必須使用這些方法，請減少時間範圍，並將執行緒處於暫止狀態時執行的程式碼數量降至最低。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。 它只會報告危險執行緒處理作業的資料。  
  
## <a name="output"></a>輸出  
 MDA 識別可啟用它的危險執行緒處理方法。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何呼叫 <xref:System.Threading.Thread.Suspend%2A> 方法，以啟用 `dangerousThreadingAPI`。  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();   
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Threading.Thread>
- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [lock 陳述式](~/docs/csharp/language-reference/keywords/lock-statement.md)
