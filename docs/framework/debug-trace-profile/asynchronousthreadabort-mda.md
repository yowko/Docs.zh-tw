---
title: asynchronousThreadAbort MDA
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08f67ad363d0bd3efcc7a1eeedd1f48d3bae9407
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59114882"
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort MDA
當執行緒嘗試在另一個執行緒中在引入非同步中止時，就會啟用 `asynchronousThreadAbort` Managed 偵錯助理 (MDA)。 同步執行緒中止不會啟動 `asynchronousThreadAbort` MDA。

## <a name="symptoms"></a>徵兆
 當主應用程式執行緒中止時，應用程式會當機，並出現未處理的 <xref:System.Threading.ThreadAbortException>。 如果繼續執行應用程式，可能會出現比應用程式當機更糟的結果，甚至還會造成資料損毀。

 原本該自動進行的作業，很可能在部分完成後遭到中斷，使得應用程式資料處於無法預期的狀態。 <xref:System.Threading.ThreadAbortException> 可以從程式碼執行中似乎是隨機點的位置產生，這些通常預期不會引發例外狀況。 程式碼可能無法處理這類例外狀況，因而導致損毀狀態。

 由於這個問題原有的隨機性，徵兆可能會有很大的不同。

## <a name="cause"></a>原因
 一個執行緒中的程式碼呼叫了目標執行緒上的 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法，以引入非同步執行緒中止。 由於對 <xref:System.Threading.Thread.Abort%2A> 發出呼叫的程式碼不是在中止作業目標的執行緒上執行；因此，執行緒中止為非同步。 同步執行緒中止應該不會造成問題，因為執行 <xref:System.Threading.Thread.Abort%2A> 的執行緒應該只會在應用程式狀態一致的安全檢查點上完成。

 由於非同步執行緒中止是在目標執行緒執行中的不可預期點進行處理，因而出現問題。 若要避免發生這種情形，請撰寫程式碼，並在可能以這種方式中止的執行緒上執行該程式碼，以便在程式碼的幾乎每一行處理 <xref:System.Threading.ThreadAbortException>，讓應用程式資料能夠回到一致的狀態。 期待在撰寫程式碼時已設想這個問題，或是撰寫出能夠預防各種可能情況的程式碼，都是不切實際的。

 呼叫進入 Unmanaged 程式碼和 `finally` 區塊，並不會非同步地中止，而是會立即從這些分類的其中一個分類中結束。

 由於本問題原有的隨機性，可能會難以判定原因。

## <a name="resolution"></a>解決方式
 避免需要使用非同步執行緒中止的程式碼設計。 有數種方法更適合用來中斷不需要呼叫 <xref:System.Threading.Thread.Abort%2A> 的目標執行緒。 最安全的方法就是採用一種機制，例如通用的屬性，對目標執行緒發出信號以要求中斷。 目標執行緒會在特定的安全檢查點上檢查信號。 如果注意到已經要求中斷，目標執行緒就會順利地關閉。

## <a name="effect-on-the-runtime"></a>對執行階段的影響
 此 MDA 對 CLR 沒有影響。 它只會報告有關非同步執行緒中止的資料。

## <a name="output"></a>Output
 此 MDA 會報告執行中止之執行緒的 ID，以及作為中止目標之執行緒的 ID。 由於僅限於非同步中止，因此這兩者絕對不會相同。

## <a name="configuration"></a>組態

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>範例
 若要啟用 `asynchronousThreadAbort` MDA ，只需要在個別執行的執行緒上呼叫 <xref:System.Threading.Thread.Abort%2A>。 請考慮如果執行緒啟動函式的內容是一組更為複雜的作業，而那些作業可能會在任意一點因為中止而中斷的後果。

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Thread>
- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
