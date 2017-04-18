---
title: "Managed Threading Best Practices | Microsoft Docs"
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
  - "threading [.NET Framework], design guidelines"
  - "threading [.NET Framework], best practices"
  - "managed threading"
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Managed Threading Best Practices
多執行緒處理需要仔細的程式設計。  對於大多數工作而言，您可以藉由執行緒集區執行緒將執行要求排入佇列，以減低複雜度。  這個主題提出更困難的狀況，例如協調多執行緒的工作，或處理封鎖的執行緒。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]中，工作平行程式庫與 PLINQ 提供可簡化某種程度複雜性以及多執行序程式設計風險的 API。  如需詳細資訊，請參閱[Parallel Programming](../../../docs/standard/parallel-programming/index.md)。  
  
## 死結和競爭情形  
 多執行緒處理解決了生產率和回應效能的問題，但是這樣做也導致新的問題：死結 \(Deadlock\) 和競爭情形 \(Race Condition\)。  
  
### 死結  
 當兩個執行緒都嘗試鎖定另一個執行緒已經鎖定的資源時，就會發生死結。  兩個執行緒都不能繼續進行。  
  
 Managed 執行緒處理類別的許多方法都提供等候逾時，以幫助您偵測死結。  例如，下列程式碼嘗試對目前的執行個體取得鎖定。  如果無法在 300 毫秒內取得鎖定，則 <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=fullName> 會傳回 **false**。  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(Me)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(this);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### 競爭情形  
 競爭情形是一種錯誤，這種錯誤是指根據兩個或多個執行緒之中，哪一個先到達程式碼的特定區塊而決定程式的結果。  執行程式多次會產生不同的結果，並且無法預測任何指定的執行結果。  
  
 遞增欄位是競爭情形的一個簡單範例。  假設某個類別有一個私用 **static** 欄位 \(在 Visual Basic 中為 **Shared**\)，您可以使用類似 `objCt++;` \(C\#\) 或 `objCt += 1` \(Visual Basic\) 的程式碼，在每次建立此類別的執行個體時，該欄位就遞增。  這個作業需要從 `objCt` 載入值到暫存器、遞增這個值，並且將它儲存到 `objCt` 中。  
  
 在多執行緒的應用程式中，已經載入並遞增值的執行緒，可能被其他執行緒搶先並執行完所有步驟；當第一個執行緒繼續執行並儲存它的值時，它會覆寫 `objCt` 而沒有考慮到在這期間值已經變更的事實。  
  
 使用 <xref:System.Threading.Interlocked> 類別的方法，如 <xref:System.Threading.Interlocked.Increment%2A?displayProperty=fullName>，很容易就可以避免這個特定的競爭情形。  若要閱讀有關同步處理多執行緒之間資料的其他技術，請參閱[同步處理多執行緒處理的資料](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)。  
  
 競爭情形也可能在同步處理多執行緒的活動時發生。  當您撰寫一行程式碼時，必須要考慮在該行執行之前 \(或者在構成該行的任一個別電腦指令執行之前\)，如果執行緒已經優先執行而又被其他執行緒取代時會發生的問題。  
  
## 處理器的數量  
 現在大部分電腦都有多個處理器 \(也稱為核心\)，即使像平板電腦和手機這樣的小型裝置也是如此。  如果您知道您正在開發的軟體也會在單一處理器電腦上執行，就應該了解多執行緒為單一處理器電腦和多處理器電腦解決的問題是有所不同的。  
  
### 多處理器電腦  
 多執行緒處理提供更佳的速度。  十個處理器可以做到一個處理器工作的十倍，但是工作必須分割，如此十份工作才能同時進行；執行緒提供簡單的方式來分割工作，並且利用額外的處理能力。  如果在多處理器電腦上使用多執行緒處理，則會有下列情況：  
  
-   可以並行執行的執行緒數量受限於處理器的數量。  
  
-   只有在前景執行緒的執行數量小於處理器數量時，背景執行緒才會執行。  
  
-   在執行緒呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> 方法時，該執行緒是否會立即開始執行，這要看處理器的數量和目前等待執行的執行緒數量而定。  
  
-   競爭情形不只因為執行緒未預期地被取代執行才可能發生，也可能因為在不同處理器上執行的兩個執行緒爭先到達相同的程式碼區塊而發生。  
  
### 單一處理器電腦  
 多執行緒處理提供電腦使用者更佳的回應效能，並且利用閒置時間執行背景工作。  如果在單一處理器電腦上使用多執行緒處理，則會有下列情況：  
  
-   在任一執行個體上只會執行一個執行緒。  
  
-   只有在主使用者執行緒閒置時才會執行背景執行緒。  不斷執行的前景執行緒會消耗掉背景執行緒所需的執行緒時間。  
  
-   在執行緒呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> 方法時，該執行緒會等到目前執行緒停止或被作業系統取代時才開始執行。  
  
-   競爭情形通常是因為程式設計師沒有預期執行緒會在不方便的時機被取代執行而發生，有時會允許其他執行緒先到達程式碼區塊。  
  
## 靜態成員和靜態建構函式  
 當類別的類別建構函式 \(Constructor\) \(C\# 內為 `static` 建構函式，Visual Basic 內為 `Shared Sub New`\) 執行完畢之後，才會將此類別初始化。  為了避免在未初始化的型別上執行程式碼，Common Language Runtime 會封鎖所有從其他執行緒對該類別之 `static` 成員的呼叫 \(Visual Basic 內為 `Shared` 成員\)，直到類別建構函式執行完畢為止。  
  
 例如，如果某個類別建構函式啟動新的執行緒，而且該執行緒程序呼叫了此類別的 `static` 成員，則會封鎖新的執行緒，直到類別建構函式完成為止。  
  
 這種情形適用於可擁有 `static` 建構函式的任何型別。  
  
## 一般建議  
 使用多執行緒時請考慮下列方針：  
  
-   請不要使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 來結束其他執行緒。  在其他執行緒呼叫 **Abort** 類似於在該執行緒傳回例外狀況，而不知道執行緒在處理中已到達哪個點。  
  
-   請不要使用 <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> 和 <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> 來同步處理多個執行緒的活動。  請使用 <xref:System.Threading.Mutex>、<xref:System.Threading.ManualResetEvent>、<xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.Monitor>。  
  
-   不要從主程式 \(例如使用事件\) 來控制背景工作執行緒 \(Worker Thread\) 的執行。  反而是在設計程式時，將背景工作執行緒設定在等待狀態，直到可以使用工作時才執行它，並在工作完成時通知程式的其他部分。  如果背景工作執行緒並未封鎖，請考慮使用執行緒集區執行緒。  <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=fullName> 在背景工作執行緒封鎖的狀況下非常有用。  
  
-   請勿將型別當做鎖定物件使用，  也就是說，要避免使用類似 C\# 內的 `lock(typeof(X))` 或 Visual Basic 內的 `SyncLock(GetType(X))` 程式碼，或是搭配 <xref:System.Type> 物件使用 <xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName>。  如果是指定的型別，每個應用程式定義域只能有一個 <xref:System.Type?displayProperty=fullName> 執行個體 \(Instance\)。  如果您鎖定的型別是公用 \(Public\) 型別，則如果使用您自己的程式碼之外的程式碼鎖定該型別，將會導致死結 \(Deadlock\)。  如需其他問題的詳細資訊，請參閱[可靠性最佳作法](../../../docs/framework/performance/reliability-best-practices.md)。  
  
-   在鎖定執行個體時要特別小心，例如，在 C\# 內使用 `lock(this)`，或在 Visual Basic 內使用 `SyncLock(Me)`。  如果應用程式內的其他程式碼 \(型別的外部\) 鎖定了物件，則可能會發生死結。  
  
-   請確認已經輸入監視器的執行緒永久保留該監視器，即使當執行緒在監視器中發生例外狀況。  C\# [lock](../Topic/lock%20Statement%20\(C%23%20Reference\).md) 陳述式和 Visual Basic [SyncLock](../../../ocs/visual-basic/language-reference/statements/synclock-statement.md) 陳述式藉由使用 **finally** 區塊，確認已經呼叫 <xref:System.Threading.Monitor.Exit%2A?displayProperty=fullName> 來自動提供這個行為。  如果您無法確認 **Exit** 會被呼叫，請考慮變更設計來使用 **Mutex**。  在目前擁有 Mutex 的執行緒結束時，Mutex 就會被自動釋放。  
  
-   請將多執行緒用於需要不同資源的工作，並且避免指派多執行緒給單一資源。  例如，凡是涉及 I\/O 的工作都可藉由擁有自己的執行緒而獲益，因為該執行緒會在 I\/O 作業期間封鎖，所以會允許其他執行緒執行。  使用者輸入是另一個從專屬執行緒中獲益的資源。  在單一處理器的電腦上，涉及大量計算的工作會與使用者輸入和包含 I\/O 的工作共存，但是多個大量計算的工作卻會互相競爭。  
  
-   請考慮使用 <xref:System.Threading.Interlocked> 類別的方法進行簡單的狀態變更，而不要使用 `lock` 陳述式 \(Visual Basic 中的 `SyncLock`\)。  `lock` 陳述式是用於一般用途的好工具，但是 <xref:System.Threading.Interlocked> 類別能為不可部分完成的更新提供更佳的效能。  如果沒有爭用情形，此類別會在內部執行單一的鎖定前置詞。  在檢視程式碼時，請注意類似下列範例所示的程式碼。  在第一個範例中會遞增狀態變數：  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     您可以藉由使用 <xref:System.Threading.Interlocked.Increment%2A> 方法 \(而不是 `lock` 陳述式\) 改進效能，如下所示：  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  在 .NET Framework 2.0 版中，<xref:System.Threading.Interlocked.Add%2A> 方法會以大於 1 的遞增量提供不可部分完成的更新。  
  
     在第二個範例中，參考型別變數只有在它是 null 參考 \(在 Visual Basic 中為 `Nothing`\) 時才會更新。  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     可藉由改用 <xref:System.Threading.Interlocked.CompareExchange%2A> 方法改善效能，如下所示：  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  在 .NET Framework 2.0 版中，<xref:System.Threading.Interlocked.CompareExchange%2A> 方法具有泛型多載，可用於任何參考型別的型別安全取代。  
  
## 給類別庫的建議  
 在設計多執行緒的類別庫時請考慮下列方針：  
  
-   如有可能，請盡量減少同步處理的需要。  對於經常使用的程式碼特別是如此。  例如，可以將演算法調整為能夠接受某一競爭情形的程度，而不是排除該競爭情形。  不必要的同步處理會降低效能，並且可能會導致死結和競爭情形。  
  
-   請將靜態資料 \(在 Visual Basic 中為 `Shared`\) 預設為執行緒安全。  
  
-   請勿將執行個體資料預設為執行緒安全。  增加鎖定以建立執行緒安全的程式碼會使效能降低、增加鎖定爭用，並製造死結發生的可能性。  在通用的應用程式模型中，一次只有一個執行緒會執行使用者程式碼，這樣可使執行緒安全性的需求降至最低。  因為這個原因，.NET Framework 類別庫預設並非執行緒安全。  
  
-   請避免提供會變更靜態狀態的靜態方法。  在一般的伺服器案例中，所有的要求都會共用靜態狀態，這表示該程式碼可由多執行緒同時執行。  這樣會增加發生執行緒處理錯誤的可能性。  請考慮使用將資料封裝在執行個體內的設計模式 \(這些執行個體不會在要求之間共用\)。  此外，如果靜態資料經過同步處理，則在能夠改變狀態的靜態方法之間的呼叫可能會導致死結或重複同步處理的情況，因而對效能造成負面的影響。  
  
## 請參閱  
 [Threading](../../../docs/standard/threading/index.md)   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)