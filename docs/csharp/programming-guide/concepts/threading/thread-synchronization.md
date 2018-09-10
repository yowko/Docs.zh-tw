---
title: 執行緒同步處理 (C#)
ms.date: 07/20/2015
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
ms.openlocfilehash: 6f0fe42c06b27369612cf586c7a93ce098822162
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509382"
---
# <a name="thread-synchronization-c"></a>執行緒同步處理 (C#)
下列各節描述可用來同步處理多執行緒應用程式中資源存取的功能和類別。  
  
 在應用程式中使用多個執行緒的其中一個優點是每個執行緒都是以非同步方式執行。 針對 Windows 應用程式，這可在應用程式視窗和控制項保持回應時，於背景執行耗時工作。 針對伺服器應用程式，多執行緒處理會提供可使用不同執行緒來處理每個傳入要求的能力。 否則，在完全滿足前一個要求之前，不會服務每個新的要求。  
  
 不過，執行緒的非同步性質表示必須協調檔案控制代碼、網路連線和記憶體這類資源的存取。 否則，兩個以上的執行緒可以同時存取相同的資源，而每個都不知道對方的動作。 結果是無法預期的資料損毀。  
  
 針對整數數值資料類型的一些簡單運算，使用 <xref:System.Threading.Interlocked> 類別的成員可以完成執行緒的同步處理。 對於所有其他資料類型和非執行緒安全資源，只能使用本主題中的建構安全地執行多執行緒處理。  
  
 如需多執行緒程式設計的背景資訊，請參閱：  
  
-   [Managed 執行緒處理的基本概念](../../../../standard/threading/managed-threading-basics.md)  
  
-   [使用執行緒和執行緒處理](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Managed 執行緒處理的最佳實施方針](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a>lock 關鍵字  
 C# `lock` 陳述式可以用來確保程式碼區塊執行到完成，未遭其他執行緒中斷。 這項作業的完成方式是取得程式碼區塊期間內所指定物件的互斥鎖定。  
  
 `lock` 陳述式是將物件指定為引數，而且後面接著一次只由一個執行緒執行的程式碼區塊。 例如:   
  
```csharp  
public class TestThreading  
{  
    private System.Object lockThis = new System.Object();  
  
    public void Process()  
    {  
  
        lock (lockThis)  
        {  
            // Access thread-sensitive resources.  
        }  
    }  
  
}  
```  
  
 提供給 `lock` 關鍵字的引數必須是根據參考型別的物件，並且用來定義鎖定範圍。 在上述範例中，因為函式外部沒有 `lockThis` 物件的參考，所以鎖定範圍限於此函式。 如果存在這類的參考，則鎖定範圍會延伸至該物件。 嚴格來說，提供的物件僅用於唯一識別在多個執行緒之間共用的資源，因此它可以是任意類別執行個體。 不過，實際上，這個物件通常代表需要執行緒同步處理的資源。 例如，如果容器物件是要供多個執行緒使用，則可以將容器傳遞至鎖定，而鎖定後面的已同步處理程式碼區塊將會存取容器。 只要其他執行緒在存取相同容器之前先將它鎖定，則可以放心地同步處理物件的存取權。  
  
 一般而言，最好是避免鎖定 `public` 類型，或鎖定不受您應用程式控制的物件執行個體。 例如，因為不受您控制的程式碼可能也會鎖定物件，所以如果可以公開存取執行個體，則 `lock(this)` 可能會有問題。 這樣可能會建立兩個以上執行緒等待釋放相同物件的死結狀況。 鎖定公用資料類型，而不是物件，可能會因相同原因而造成問題。 鎖定常值字串特別危險，因為 Common Language Runtime (CLR) 會「保留」常值字串。 這表示整個程式之任何指定的字串常值都有一個執行個體，而完全相同的物件代表所有執行緒上所有執行中應用程式定義域中的常值。 因此，鎖定應用程式處理序中任意位置且內容相同的字串，即會鎖定應用程式中該字串的所有執行個體。 因此，最好鎖定未保留的私用或受保護成員。 某些類別會提供特別用於鎖定的成員。 例如，<xref:System.Array> 類型會提供 <xref:System.Array.SyncRoot%2A>。 許多集合類型也都會提供 `SyncRoot` 成員。  
  
 如需 `lock` 陳述式的詳細資訊，請參閱下列主題：  
  
-   [lock 陳述式](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a>監視  
 與 `lock` 關鍵字類似，監視器會防止多個執行緒同時執行程式碼區塊。 <xref:System.Threading.Monitor.Enter%2A> 方法只允許在下列陳述式中繼續執行一個執行緒；除非執行中執行緒呼叫 <xref:System.Threading.Monitor.Exit%2A>，否則會封鎖所有其他執行緒。 這只要使用 `lock` 關鍵字即可。 例如:   
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 這相當於：  
  
```csharp  
System.Object obj = (System.Object)x;  
System.Threading.Monitor.Enter(obj);  
try  
{  
    DoSomething();  
}  
finally  
{  
    System.Threading.Monitor.Exit(obj);  
}  
```  
  
 通常會優先使用 `lock` 關鍵字，而不是直接使用 <xref:System.Threading.Monitor> 類別，因為 `lock` 更為精簡，而且 `lock` 確保釋放基準監視器，即使受保護程式碼擲回例外狀況也是一樣。 這是使用 `finally` 關鍵字所完成，而不論是否擲回例外狀況，這個關鍵字都會執行其關聯的程式碼區塊。  
  
## <a name="synchronization-events-and-wait-handles"></a>同步處理事件和等候控制代碼  
 使用鎖定或監視器適用於防止同時執行執行緒敏感程式碼區塊，但這些建構不允許某個執行緒與另一個執行緒針對事件進行通訊。 這需要「同步處理事件」，這是一個具有可用來啟動和暫止執行緒的兩種狀態 (發出訊號和未發出訊號) 之一的物件。 執行緒的暫止方式是等候未發出訊號的同步處理事件，而啟動方式是將事件狀態變更為發出訊號。 如果執行緒嘗試等候已收到訊號的事件，則執行緒會繼續執行，而不會延遲。  
  
 有兩種類型的同步處理事件：<xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.ManualResetEvent>。 它們的差異只在於 <xref:System.Threading.AutoResetEvent> 會在啟動執行緒時即自動從發出訊號變更為未發出訊號。 相之，<xref:System.Threading.ManualResetEvent> 允許透過其發出信號狀態來啟動任意數目的執行緒，並只在呼叫其 <xref:System.Threading.EventWaitHandle.Reset%2A> 方法時還原為未發出信號狀態。  
  
 讓執行緒等候事件的方式，就是呼叫其中一個等待方法，例如 <xref:System.Threading.WaitHandle.WaitOne%2A>、<xref:System.Threading.WaitHandle.WaitAny%2A> 或 <xref:System.Threading.WaitHandle.WaitAll%2A>。 <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> 會使得執行緒等到單一事件變成發出信號狀態為止，<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> 則會封鎖執行緒，直到一或多個指定的事件變成發出信號狀態，而 <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> 會封鎖執行緒，直到所有指定的事件變成發出信號狀態。 呼叫事件的 <xref:System.Threading.EventWaitHandle.Set%2A> 方法時，該事件就會變成發出信號狀態。  
  
 在下列範例中，`Main` 函式會建立並啟動執行緒。 新的執行緒會使用 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法等候事件。 除非執行 `Main` 函式的主要執行緒讓事件變成發出訊號，否則會暫止執行緒。 一旦事件變成發出訊號，就會傳回輔助執行緒。 在此情況下，由於事件僅用於啟動某個執行緒，因此可以使用 <xref:System.Threading.AutoResetEvent> 或 <xref:System.Threading.ManualResetEvent> 類別。  
  
```csharp  
using System;  
using System.Threading;  
  
class ThreadingExample  
{  
    static AutoResetEvent autoEvent;  
  
    static void DoWork()  
    {  
        Console.WriteLine("   worker thread started, now waiting on event...");  
        autoEvent.WaitOne();  
        Console.WriteLine("   worker thread reactivated, now exiting...");  
    }  
  
    static void Main()  
    {  
        autoEvent = new AutoResetEvent(false);  
  
        Console.WriteLine("main thread starting worker thread...");  
        Thread t = new Thread(DoWork);  
        t.Start();  
  
        Console.WriteLine("main thread sleeping for 1 second...");  
        Thread.Sleep(1000);  
  
        Console.WriteLine("main thread signaling worker thread...");  
        autoEvent.Set();  
    }  
}  
```  
  
## <a name="mutex-object"></a>Mutex 物件  
 *Mutex* 與監視器類似，可防止多個執行緒一次同時執行程式碼區塊。 事實上，名稱 "Mutex" 是「互斥」這個詞彙的縮短格式。 不過，與監視器不同，Mutex 可以用來跨處理序同步處理執行緒。 Mutex 由 <xref:System.Threading.Mutex> 類別代表。  
  
 用於處理序間同步處理時，Mutex 稱為「具名 Mutex」，因為它是要用在另一個應用程式中，因此無法透過全域或靜態變數共用。 必須指定它的名稱，以讓兩個應用程式可以存取相同的 Mutex 物件。  
  
 雖然 Mutex 可以用於處理序間執行緒同步處理，但是一般偏好使用 <xref:System.Threading.Monitor>，因為已特別針對 .NET Framework 設計監視器，因此能夠更恰當地使用資源。 相反地，<xref:System.Threading.Mutex> 類別是 Win32 建構的包裝函式。 雖然 Mutex 比監視器的功能更為強大，但是所需的 Interop 轉換比 <xref:System.Threading.Monitor> 類別所需的 Interop 轉換耗費更大量的運算資源。 如需使用 Mutex 的範例，請參閱 [Mutex](../../../../standard/threading/mutexes.md)。  
  
## <a name="interlocked-class"></a>Interlocked 類別  
 您可以使用 <xref:System.Threading.Interlocked> 類別的方法，防止多個執行緒嘗試同時更新或比較相同值時可能發生的問題。 這個類別的方法可讓您安全地遞增、遞減、交換和比較任何執行緒中的值。  
  
## <a name="readerwriter-locks"></a>ReaderWriter 鎖定  
 在某些情況下，只有正在寫入資料時，才會想要鎖定資源，並允許多個用戶端在未更新資料時同時讀取資料。 <xref:System.Threading.ReaderWriterLock> 類別會在執行緒正在修改資源時強制獨佔資源存取，但在讀取資源時允許非獨佔存取。 ReaderWriter 鎖定是造成其他執行緒等待之獨佔鎖定的有用替代方式，即使這些執行緒不需要更新資料時也是一樣。  
  
## <a name="deadlocks"></a>死結  
 執行緒同步處理是多執行緒應用程式中十分寶貴的功能，但建立 `deadlock` 一律有其危險性；在其中，多個執行緒將等候彼此，而應用程式就像停止一樣。 死結類似汽車停在四方停車再開的位置，而每個人都在等候其他人先離開。 避免死結十分重要；關鍵在於仔細規劃。 在開始撰寫程式碼之前，先將多執行緒應用程式圖表化，通常就可以預測死結狀況。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Threading.Thread>  
- <xref:System.Threading.WaitHandle.WaitOne%2A>  
- <xref:System.Threading.WaitHandle.WaitAny%2A>  
- <xref:System.Threading.WaitHandle.WaitAll%2A>  
- <xref:System.Threading.Thread.Join%2A>  
- <xref:System.Threading.Thread.Start%2A>  
- <xref:System.Threading.Thread.Sleep%2A>  
- <xref:System.Threading.Monitor>  
- <xref:System.Threading.Mutex>  
- <xref:System.Threading.AutoResetEvent>  
- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Interlocked>  
- <xref:System.Threading.WaitHandle>  
- <xref:System.Threading.EventWaitHandle>  
- <xref:System.Threading>  
- <xref:System.Threading.EventWaitHandle.Set%2A>  
- <xref:System.Threading.Monitor>  
- [lock 陳述式](../../../../csharp/language-reference/keywords/lock-statement.md)  
- [Mutex](../../../../standard/threading/mutexes.md)  
- [Interlocked 作業](../../../../standard/threading/interlocked-operations.md)  
- [AutoResetEvent](../../../../standard/threading/autoresetevent.md)  
- [同步處理多執行緒處理的資料](../../../../standard/threading/synchronizing-data-for-multithreading.md)
