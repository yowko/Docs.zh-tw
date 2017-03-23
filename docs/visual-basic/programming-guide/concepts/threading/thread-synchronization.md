---
title: "執行緒同步處理 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 04f485d1-8333-4510-9e72-c334e7427e7e
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ec8fa89c8921eadee428a90971d9ae4ce305a109
ms.lasthandoff: 03/13/2017

---
# <a name="thread-synchronization-visual-basic"></a>執行緒同步處理 (Visual Basic)
下列章節說明功能和類別，可用來同步處理多執行緒應用程式資源的存取權。  
  
 其中一個應用程式中使用多執行緒的優點是每個執行緒以非同步方式執行。 對於 Windows 應用程式，這可讓應用程式視窗時在背景執行耗時的工作和控制項仍能繼續回應。 伺服器應用程式，進行多執行緒處理會提供能夠處理不同的執行緒與每個傳入要求。 否則，每個新的要求會取得之前無法提供服務一個要求已完全沒有問題。  
  
 不過，例如檔案控制代碼、 網路連線和記憶體資源存取權的執行緒方法的非同步性質，必須進行協調。 否則，兩個或多個執行緒可以存取相同資源一次，每個都不知道對方的動作。 結果是無法預期的資料損毀。  
  
 整數的數值資料型別上的簡單運算，如同步處理執行緒可以完成與成員的<xref:System.Threading.Interlocked>類別。</xref:System.Threading.Interlocked> 所有其他資料型別和多執行緒處理的非執行緒安全資源只能安全地執行本主題中使用的建構。  
  
 如需多執行緒程式設計的背景資訊，請參閱︰  
  
-   [Managed 執行緒處理的基本概念](http://msdn.microsoft.com/library/b2944911-0e8f-427d-a8bb-077550618935)  
  
-   [使用執行緒和執行緒處理](http://msdn.microsoft.com/library/9b5ec2cd-121b-4d49-b075-222cf26f2344)  
  
-   [Managed 執行緒處理最佳作法](http://msdn.microsoft.com/library/e51988e7-7f4b-4646-a06d-1416cee8d557)  
  
## <a name="the-lock-and-synclock-keywords"></a>Lock 和 SyncLock 關鍵字  
 Visual Basic`SyncLock`陳述式可以由其他執行緒用來確保程式碼區塊執行到完成為止，而不會中斷。 這被透過程式碼區塊的持續時間內取得指定物件的互斥鎖定。  
  
 A`SyncLock`陳述式指定的物件做為引數，且後面接著一次只能由一個執行緒執行的程式碼區塊。 例如:   
  
```vb  
Public Class TestThreading  
    Dim lockThis As New Object  
  
    Public Sub Process()  
        SyncLock lockThis  
            ' Access thread-sensitive resources.  
        End SyncLock  
    End Sub  
End Class  
```  
  
 若要提供的引數`SyncLock`關鍵字必須是參考型別為基礎的物件和用來定義鎖定的範圍。 在上述範例中，鎖定的範圍僅限於此函式因為物件未參考`lockThis`存在外部函式。 如果存在這類的參考，鎖定範圍會延伸至該物件。 嚴格來說，提供的物件僅用於唯一識別的資源，因此它可以是任意的類別執行個體在多個執行緒之間共用。 在實務上，不過，這個物件通常代表執行緒同步處理所需要的資源。 比方說，如果容器物件是可供多個執行緒，然後容器可以傳遞至鎖定，並在鎖定之後的同步處理的程式碼區塊會存取容器。 只要其他執行緒會在相同鎖定包含之前存取它，然後安全地進行同步處理物件的存取權。  
  
 一般而言，最好是避免鎖定`public`型別，或您的應用程式所控制的物件執行個體上。 例如，`lockThis`可能會造成問題，如果公開，存取的執行個體，因為您控制範圍之外的程式碼可能會鎖定物件。 這樣可能會建立兩個或多個執行緒會等待相同的物件版本的死結狀況。 鎖定在公用資料型別，而不是物件，可能會造成問題的理由。 常值字串鎖定是特別危險，因為常值字串完全*被保留了*common language runtime (CLR)。 這表示沒有任何指定之字串的一個執行個體的整個程式常值，完全相同的物件表示中所有的常值的所有執行緒上執行應用程式定義域。 如此一來，鎖定放在具有相同內容的字串中應用程式的處理序鎖定該字串的應用程式中的所有執行個體。 因此，最好鎖定不會被保留了私用或受保護成員。 某些類別會提供成員特別為鎖定。 的<xref:System.Array>型別，例如，提供<xref:System.Array.SyncRoot%2A>.</xref:System.Array.SyncRoot%2A> </xref:System.Array> 許多集合型別提供`SyncRoot`以及成員。  
  
 如需詳細資訊`SyncLock`陳述式，請參閱下列主題︰  
  
-   [SyncLock 陳述式](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
  
-   @System.Threading.Monitor  
  
## <a name="monitors"></a>監視  
 像`SyncLock`關鍵字，監視器會避免由多個執行緒同時執行的程式碼區塊。 <xref:System.Threading.Monitor.Enter%2A>方法可讓只有一個執行緒繼續執行下列陳述式; 所有其他執行緒會被封鎖，直到執行的執行緒呼叫<xref:System.Threading.Monitor.Exit%2A>。</xref:System.Threading.Monitor.Exit%2A> </xref:System.Threading.Monitor.Enter%2A> 就像使用`SyncLock`關鍵字。 例如:   
  
```vb  
SyncLock x  
    DoSomething()  
End SyncLock  
```  
  
 這相當於︰  
  
```vb  
Dim obj As Object = CType(x, Object)  
System.Threading.Monitor.Enter(obj)  
Try  
    DoSomething()  
Finally  
    System.Threading.Monitor.Exit(obj)  
End Try  
```  
  
 使用`SyncLock`關鍵字通常會優先使用<xref:System.Threading.Monitor>類別目錄，同時由於`SyncLock`更為精簡，而且因為`SyncLock`car 的基準監視會釋放，即使受保護的程式碼擲回例外狀況。</xref:System.Threading.Monitor> 這是與`Finally`關鍵字，它會執行其相關聯的程式碼區塊，不論是否擲回例外狀況。  
  
## <a name="synchronization-events-and-wait-handles"></a>同步處理事件和等候控制代碼  
 使用鎖定或監視器可用於防止同時執行的執行緒敏感程式碼區塊，但這些建構並不允許進行通訊的事件到另一個執行緒。 這需要*同步處理事件*，這是具有兩種狀態的其中一個物件收到信號，未收到信號，可以用來啟動和暫止執行緒。 執行緒會暫停等候信號，同步處理事件未發出，而且可以透過啟動變更為已收到訊號的事件狀態。 如果執行緒嘗試等候已收到信號的事件時，執行緒會繼續執行而不會延遲。  
  
 有兩種類型的同步處理事件︰ <xref:System.Threading.AutoResetEvent>，和<xref:System.Threading.ManualResetEvent>.</xref:System.Threading.ManualResetEvent> </xref:System.Threading.AutoResetEvent> 它們之間的差異只在於<xref:System.Threading.AutoResetEvent>變更通知到信號自動每當它會啟動執行緒。</xref:System.Threading.AutoResetEvent> 相反地，<xref:System.Threading.ManualResetEvent>允許任意數目的執行緒，其已收到信號的狀態，來啟動，並只將會還原成未發出信號狀態時其<xref:System.Threading.EventWaitHandle.Reset%2A>方法稱為 「。</xref:System.Threading.EventWaitHandle.Reset%2A> </xref:System.Threading.ManualResetEvent>  
  
 可以讓執行緒等待事件由呼叫其中一個等候方法，例如<xref:System.Threading.WaitHandle.WaitOne%2A>， <xref:System.Threading.WaitHandle.WaitAny%2A>，或<xref:System.Threading.WaitHandle.WaitAll%2A>.</xref:System.Threading.WaitHandle.WaitAll%2A> </xref:System.Threading.WaitHandle.WaitAny%2A> </xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName>造成執行緒等候單一事件發出信號，<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName>封鎖執行緒，直到一或多個指定的事件變成已收到訊號，和<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName>封鎖執行緒，直到所有指定的事件變成已收到訊號。</xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName> </xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName></xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName> 事件發出信號時其<xref:System.Threading.EventWaitHandle.Set%2A>方法稱為 「。</xref:System.Threading.EventWaitHandle.Set%2A>  
  
 在下列範例中，執行緒會建立並啟動`Main`函式。 新的執行緒在等待事件使用<xref:System.Threading.WaitHandle.WaitOne%2A>方法。</xref:System.Threading.WaitHandle.WaitOne%2A> 執行緒會暫停，直到對事件發出信號的主要執行緒正在執行`Main`函式。 一旦對事件發出信號，就會傳回輔助執行緒。 在此情況下，事件僅用於一個執行緒啟動，或是因為<xref:System.Threading.AutoResetEvent>或<xref:System.Threading.ManualResetEvent>可用類別。</xref:System.Threading.ManualResetEvent> </xref:System.Threading.AutoResetEvent>  
  
```vb  
Imports System.Threading  
  
Module Module1  
    Dim autoEvent As AutoResetEvent  
  
    Sub DoWork()  
        Console.WriteLine("   worker thread started, now waiting on event...")  
        autoEvent.WaitOne()  
        Console.WriteLine("   worker thread reactivated, now exiting...")  
    End Sub  
  
    Sub Main()  
        autoEvent = New AutoResetEvent(False)  
  
        Console.WriteLine("main thread starting worker thread...")  
        Dim t As New Thread(AddressOf DoWork)  
        t.Start()  
  
        Console.WriteLine("main thread sleeping for 1 second...")  
        Thread.Sleep(1000)  
  
        Console.WriteLine("main thread signaling worker thread...")  
        autoEvent.Set()  
    End Sub  
End Module  
```  
  
## <a name="mutex-object"></a>Mutex 物件  
 A *mutex*是類似於監視器; 它防止多個執行緒同時執行的程式碼區塊一次。 事實上，名稱"mutex 」 是 「 互斥。 」 一詞縮寫格式 不同於監視器，不過，mutex 可以用於跨處理序同步處理執行緒。 Mutex 被以<xref:System.Threading.Mutex>類別。</xref:System.Threading.Mutex>  
  
 Mutex 時用於處理序間的同步處理時，會呼叫*具名 mutex*因為它是以供其他應用程式，因此它無法共用透過全域或靜態變數。 必須授與它的名稱，讓兩個應用程式可以存取同一個 mutex 物件。  
  
 Mutex 可以用於進行了處理序的執行緒同步處理，但是使用<xref:System.Threading.Monitor>通常會優先，因為監視專為.NET Framework 設計，因此更妥善運用資源。</xref:System.Threading.Monitor> 相反地，<xref:System.Threading.Mutex>類別是 Win32 建構的包裝函式。</xref:System.Threading.Mutex> 雖然比監視器功能更強大，mutex 需要 interop 轉換時更耗費大量運算資源比所需的<xref:System.Threading.Monitor>類別。</xref:System.Threading.Monitor> 如需使用 mutex 的範例，請參閱[Mutex](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2)。  
  
## <a name="interlocked-class"></a>Interlocked 的類別  
 您可以使用的方法<xref:System.Threading.Interlocked>類別來防止當多個執行緒嘗試同時更新，或相同的值相比較時可能發生的問題。</xref:System.Threading.Interlocked> 這個類別的方法可讓您安全地遞增、 遞減、 交換，並比較值，從任何執行緒。  
  
## <a name="readerwriter-locks"></a>ReaderWriter 鎖定  
 在某些情況下，您可以只會被寫入資料時，鎖定資源，並允許多個用戶端無法更新資料時，同時讀取資料。 <xref:System.Threading.ReaderWriterLock>類別在執行緒正在修改資源，但它可讓非獨佔存取資源讀取時，會強制執行資源的獨佔存取權。</xref:System.Threading.ReaderWriterLock> ReaderWriter 鎖定是有用的替代方式，會造成其他執行緒等待，即使當這些執行緒不需要更新資料的獨佔鎖定。  
  
## <a name="deadlocks"></a>死結 （deadlock)  
 執行緒同步處理是非常寶貴的功能，在多執行緒應用程式，但總是有之上建立`deadlock`的多個執行緒正在等候彼此，且應用程式停止暫止。 死結是類似於汽車停止在四個方向停止，且每個人等候到其他的情況。 避免死結的重要性;關鍵在於仔細規劃。 您通常可以圖表化多執行緒應用程式，然後再開始撰寫程式碼，以預測死結狀況的可能性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Thread></xref:System.Threading.Thread>   
 <xref:System.Threading.WaitHandle.WaitOne%2A></xref:System.Threading.WaitHandle.WaitOne%2A>   
 <xref:System.Threading.WaitHandle.WaitAny%2A></xref:System.Threading.WaitHandle.WaitAny%2A>   
 <xref:System.Threading.WaitHandle.WaitAll%2A></xref:System.Threading.WaitHandle.WaitAll%2A>   
 <xref:System.Threading.Thread.Join%2A></xref:System.Threading.Thread.Join%2A>   
 <xref:System.Threading.Thread.Start%2A></xref:System.Threading.Thread.Start%2A>   
 <xref:System.Threading.Thread.Sleep%2A></xref:System.Threading.Thread.Sleep%2A>   
 <xref:System.Threading.Monitor></xref:System.Threading.Monitor>   
 <xref:System.Threading.Mutex></xref:System.Threading.Mutex>   
 <xref:System.Threading.AutoResetEvent></xref:System.Threading.AutoResetEvent>   
 <xref:System.Threading.ManualResetEvent></xref:System.Threading.ManualResetEvent>   
 <xref:System.Threading.Interlocked></xref:System.Threading.Interlocked>   
 <xref:System.Threading.WaitHandle></xref:System.Threading.WaitHandle>   
 <xref:System.Threading.EventWaitHandle></xref:System.Threading.EventWaitHandle>   
 <xref:System.Threading></xref:System.Threading>   
 <xref:System.Threading.EventWaitHandle.Set%2A></xref:System.Threading.EventWaitHandle.Set%2A>   
 [多執行緒應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [SyncLock 陳述式](../../../../visual-basic/language-reference/statements/synclock-statement.md)   
 [Mutex](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2)   
 @System.Threading.Monitor   
 [連鎖的作業](http://msdn.microsoft.com/library/cbda7114-c752-4f3e-ada1-b1e8dd262f2b)   
 [AutoResetEvent](http://msdn.microsoft.com/library/6d39c48d-6b37-4a9b-8631-f2924cfd9c18)   
 [同步處理資料的多執行緒處理](http://msdn.microsoft.com/library/b980eb4c-71d5-4860-864a-6dfe3692430a)
