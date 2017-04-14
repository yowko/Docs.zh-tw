---
title: "EventWaitHandle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threading [.NET Framework], EventWaitHandle class"
  - "EventWaitHandle class"
  - "event wait handles [.NET Framework]"
  - "threading [.NET Framework], cross-process synchronization"
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# EventWaitHandle
<xref:System.Threading.EventWaitHandle> 類別允許執行緒藉由發出信號和等候信號的方式，彼此互相通訊。  事件等候處理 \(又簡稱為事件\)，是一種可以接收信號，以便釋放一個或多個等候中執行緒的等候處理。  在收到信號之後，事件等候處理就會以手動或自動方式重設。  <xref:System.Threading.EventWaitHandle> 類別可以表示本機事件等候處理 \(本機事件\)，或是具名的系統事件等候處理 \(具名事件或系統事件，可見於所有的處理序\)。  
  
> [!NOTE]
>  事件等候處理與 .NET Framework 中「事件」一詞通常表示的意義並不相同。  在此並沒有涉及到委派 \(Delegate\) 或事件處理常式。  由於傳統習慣將委派和事件處理常式稱為作業系統事件，並且對等候處理發出信號的動作，會指示等候中執行緒事件已經發生，所以，用「事件」來描述它們。  
  
 本機和具名事件等候處理都會使用系統同步物件 \(Synchronization Object\)，這些物件由 <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> 包裝函式保護，以確定會釋放資源。  當您使用過物件之後，可以使用 <xref:System.Threading.WaitHandle.System%23IDisposable%23Dispose%2A> 方法立即釋放資源。  
  
## 自動重設的事件等候處理  
 只要在建立 <xref:System.Threading.EventWaitHandle> 物件時，指定 <xref:System.Threading.EventResetMode?displayProperty=fullName>，即可建立自動重設的事件。  如同它的名稱所指的，這個同步處理事件會在收到信號，並且釋放單一等候中執行緒之後自動重設。  呼叫事件的 <xref:System.Threading.EventWaitHandle.Set%2A> 方法，即可對事件發出信號。  
  
 自動重設事件通常是用來一次對單一執行緒提供某項資源的獨佔存取權。  執行緒會呼叫 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法以要求資源。  如果沒有其他執行緒持有等候處理，方法就會傳回 `true`，而呼叫的執行緒便能夠控制資源。  
  
> [!IMPORTANT]
>  就如同所有的同步處理機制般，在能夠存取受保護的資源以前，您必須確定所有的程式碼路徑都會等候適當的等候處理。  執行緒同步處理是具有合作性的。  
  
 如果自動重設事件在沒有執行緒等候時收到信號，就會維持收到信號的狀態，直到有執行緒嘗試等候這個事件為止。  事件會釋放該執行緒並立即重設，以封鎖住後續的執行緒。  
  
## 手動重設的事件等候處理  
 只要在建立 <xref:System.Threading.EventWaitHandle> 物件時，指定 <xref:System.Threading.EventResetMode?displayProperty=fullName>，即可建立手動重設的事件。  如同它的名稱所指的，這個同步處理事件必須在收到信號之後，以手動重設。  直到重設為止，藉著呼叫其 <xref:System.Threading.EventWaitHandle.Reset%2A> 方法，等候事件處理的執行緒都會在無封鎖的情況下立即繼續進行。  
  
 手動重設事件的作用與圍欄的門一樣。  當事件沒有收到信號時，等候事件的執行緒就會遭到封鎖，就像是圍欄中的馬匹。  當事件收到信號時，藉著呼叫其 <xref:System.Threading.EventWaitHandle.Set%2A> 方法，所有的等候中執行緒都能自由繼續進行。  事件會一直維持收到信號的狀態，直到有人呼叫其 <xref:System.Threading.EventWaitHandle.Reset%2A> 方法為止。  如此，在需要等候一個執行緒完成工作時，手動重設事件會是阻擋其他執行緒的理想方式。  
  
 就像讓馬匹離開圍欄一樣，讓作業系統排程以釋放執行緒並繼續執行，需要耗費一些時間。  如果在所有的執行緒都繼續執行之前，呼叫 <xref:System.Threading.EventWaitHandle.Reset%2A> 方法，其餘的執行緒就會再次遭到封鎖。  要繼續執行和封鎖那些執行緒，都取決於隨機的因素，例如系統的負載、等候排程器的執行緒數目等等。  如果對事件發出信號的執行緒在發出信號後便結束了 \(這是最常見的使用模式\)，這就不會造成問題。  如果要讓對事件發出信號的執行緒，在所有等候中執行緒都已繼續執行之後，才開始新的工作，您必須在所有等候中執行緒都繼續執行之前，一直封鎖那些執行緒。  否則，就會造成競爭情況，並使程式碼的行為變得無法預期。  
  
## 自動和手動事件的通用功能  
 通常，在未封鎖的執行緒呼叫 <xref:System.Threading.EventWaitHandle.Set%2A> 方法，以釋放一個等候中執行緒 \(在自動重設事件的情況中\)，或是所有等候中執行緒 \(在手動重設事件的情況中\) 之前，<xref:System.Threading.EventWaitHandle> 上都會封鎖一個或多個執行緒。  就像是不可部分完成的作業 \(Atomic Operation\) 一樣，執行緒可以藉由呼叫靜態 <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=fullName> 方法，對 <xref:System.Threading.EventWaitHandle> 發出信號，然後在其上封鎖。  
  
 <xref:System.Threading.EventWaitHandle> 物件可以與靜態的 <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName> 和 <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName> 方法搭配使用。  由於 <xref:System.Threading.EventWaitHandle> 和 <xref:System.Threading.Mutex> 類別都衍生自 <xref:System.Threading.WaitHandle>，您可以將這兩種類別與這些方法搭配使用。  
  
### 具名事件  
 Windows 作業系統允許事件等候處理具有名稱。  具名事件是全系統的。  也就是說，一旦建立具名事件，所有處理序中的所有執行緒都可以看見該事件。  因此，具名事件可以用來對處理序及執行緒的活動同步處理。  
  
 使用指定事件名稱的其中一個建構函式，即可建立表示具名系統事件的 <xref:System.Threading.EventWaitHandle> 物件。  
  
> [!NOTE]
>  由於具名事件是全系統的，因此可能會具有多個表示相同具名事件的 <xref:System.Threading.EventWaitHandle> 物件。  每當您呼叫建構函式或 <xref:System.Threading.EventWaitHandle.OpenExisting%2A> 方法時，都會建立新的 <xref:System.Threading.EventWaitHandle> 物件。  重複指定相同的名稱，便會建立多個表示相同具名事件的物件。  
  
 請謹慎地使用具名事件。  由於具名事件是全系統的，使用相同名稱的另一個處理序可能會意外地封鎖您的執行緒。  在同一部電腦上執行的惡意程式碼，可能會利用這點發動拒絕服務攻擊。  
  
 請使用存取控制項安全性來保護表示具名物件的 <xref:System.Threading.EventWaitHandle> 物件，並且最好使用會指定 <xref:System.Security.AccessControl.EventWaitHandleSecurity> 物件的建構函式。  您也可以使用 <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> 方法來套用存取控制項安全性，不過這樣會在建立事件等候處理之後，以及事件等候處理得到保護之前，形成具有弱點的一段時間。  以存取控制項安全性來保護事件，有助於防止惡意攻擊，但是並不能解決意外名稱衝突的問題。  
  
> [!NOTE]
>  不同於 <xref:System.Threading.EventWaitHandle> 類別，衍生類別 <xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.ManualResetEvent> 都只能表示本機等候處理。  這些類別不能表示具名系統事件。  
  
## 請參閱  
 <xref:System.Threading.EventWaitHandle>   
 <xref:System.Threading.WaitHandle>   
 <xref:System.Threading.AutoResetEvent>   
 <xref:System.Threading.ManualResetEvent>   
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)