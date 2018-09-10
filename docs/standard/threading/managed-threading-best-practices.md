---
title: Managed 執行緒處理的最佳實施方針
ms.date: 11/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f95fb3ccab7362021a7a195ea199a1370e003dd2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204977"
---
# <a name="managed-threading-best-practices"></a>Managed 執行緒處理的最佳實施方針
在為多執行緒功能設計程式時需要非常小心。 您可以藉由將要求排入佇列以供執行緒集區的執行緒執行，來降低大部分工作的複雜性。 本主題要解決的是更困難的情況，例如協調多個執行緒的工作，或處理封鎖起來的執行緒。  
  
> [!NOTE]
> 從 .NET Framework 4 開始，工作平行程式庫和 PLINQ 會提供 API，來為多執行緒的程式設計工作降低一定的複雜度和風險。 如需詳細資訊，請參閱 [.NET 的平行程式設計](../../../docs/standard/parallel-programming/index.md)。  
  
## <a name="deadlocks-and-race-conditions"></a>死結和競爭情形  
 多執行緒可透過輸送量和回應性來解決問題，但這麼做又會引發新的問題︰死結和競爭情形。  
  
### <a name="deadlocks"></a>死結  
 當兩個執行緒各自嘗試鎖定彼此已鎖定的資源時，系統就會發生死結。 這兩個執行緒都無法再有所進展。  
  
 Managed 執行緒類別有許多方法會提供逾時機制，以幫助您偵測死結情形。 例如，下列程式碼會嘗試在名為 `lockObject` 的物件上取得鎖定。 如果未在 300 毫秒內取得鎖定，<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> 就會傳回 `false`。  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
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
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a>追蹤條件  
 當程式的結果取決於兩個以上的執行緒何者先到達特定程式碼區塊時，系統便會發生競爭情形這個錯誤。 執行程式多次會產生不同的結果，因而讓系統無法預測當回執行的結果。  
  
 遞增欄位值的作業就是簡單的競爭情形範例。 假設某個類別具有 **static** 私用欄位 (在 Visual Basic 中是 **Shared**)，每當該類別建立了執行個體，該欄位就會使用 `objCt++;` (C#) 或 `objCt += 1` (Visual Basic) 之類的程式碼來遞增值。 這項作業需要將 `objCt` 的值載入到暫存器、將值遞增，然後儲存在 `objCt` 中。  
  
 在多執行緒應用程式中，已經載入並遞增值的執行緒可能會讓另一個將三個步驟全都執行完畢的執行緒來先佔；當第一個執行緒繼續執行並儲存其值時，它會不顧值已在過渡期間變更的事實而覆寫 `objCt`。  
  
 您可以使用 <xref:System.Threading.Interlocked> 類別的方法 (例如 <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> 方法)，輕鬆地避免這個特定的競爭情形。 若要了解其他可用來在多個執行緒之間同步處理資料的技術，請參閱[同步處理多執行緒的資料](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)。  
  
 當您同步處理多個執行緒的活動時，系統也會發生競爭情形。 每當您編寫一行程式碼時，您必須考慮如果某個執行緒在執行該行程式碼之前 (或在構成該行程式碼的個別電腦指令之前) 就讓其他執行緒先佔，而且另一個執行緒超過該執行緒時，系統可能會發生什麼狀況。  
  
## <a name="number-of-processors"></a>處理器數目  
 現今大多數的電腦都有多個處理器 (也稱為核心)，即使是小如平板電腦和手機的裝置也是如此。 如果您知道您要開發的軟體也會在單一處理器的電腦上執行，您應該了解多執行緒可為單一處理器電腦和多處理器電腦解決不同的問題。  
  
### <a name="multiprocessor-computers"></a>多處理器電腦  
 多執行緒可提供更大的輸送量。 十個處理器可以執行的工作是一個處理器的十倍，但前提是該項工作必須分割，方能讓十個處理器可以同時工作；執行緒可讓您輕鬆地分割工作，並利用額外的處理能力。 如果您在多處理器電腦上使用多執行緒︰  
  
-   可以同時執行的執行緒數目受限於處理器數目。  
  
-   執行中的前景執行緒數目小於處理器數目時，背景執行緒才會執行。  
  
-   當您在執行緒上呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> 方法時，該執行緒不一定會立即開始執行，一切視處理器數目和目前等待執行的執行緒數目而定。  
  
-   之所以會發生競爭情形，不僅是因為執行緒意外讓其他執行緒先佔，還因為在不同處理器上執行的兩個執行緒可能會競相到達相同的程式碼區塊。  
  
### <a name="single-processor-computers"></a>單一處理器電腦  
 多執行緒可為電腦使用者提供更高的回應性，並且會使用閒置時間來處理背景工作。 如果您在單一處理器電腦上使用多執行緒︰  
  
-   不論何時都只會有一個執行緒執行。  
  
-   只有當主要的使用者執行緒閒置時，背景執行緒才會執行。 持續執行的前景執行緒會讓背景執行緒無法獲得半點處理器時間。  
  
-   當您在執行緒上呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> 方法時，該執行緒要等到目前的執行緒退讓或讓作業系統先佔後才會開始執行。  
  
-   競爭情形的一般發生原因是，程式設計人員實際上未預期到執行緒會在棘手的時機讓其他執行緒先佔，這有時會讓其他執行緒先到達程式碼區塊。  
  
## <a name="static-members-and-static-constructors"></a>Static 成員和 Static 建構函式  
 類別要等到其類別建構函式 (C# 中是 `static` 建構函式，Visual Basic 中是 `Shared Sub New`) 執行完畢後才會初始化。 為避免程式碼在未初始化的型別上執行，通用語言執行平台會在類別建構函式執行完畢前，封鎖其他執行緒對該類別之 `static` 成員 (Visual Basic 中是 `Shared` 成員) 的所有呼叫。  
  
 例如，如果類別建構函式會開始新的執行緒，而執行緒程序會呼叫該類別的 `static` 成員，則新的執行緒會封鎖起來，直到類別建構函式完成。  
  
 這適用於任何可以具有 `static` 建構函式的型別。  
  
## <a name="general-recommendations"></a>一般建議  
 在使用多執行緒時，請考慮下列指導方針︰  
  
-   請勿使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 來終止其他執行緒。 對另一個執行緒呼叫 **Abort** 就像對該執行緒擲回例外狀況，卻不知道該執行緒已到達哪個處理階段。  
  
-   請勿使用 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> 來同步處理多個執行緒的活動。 請使用 <xref:System.Threading.Mutex>、<xref:System.Threading.ManualResetEvent>、<xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.Monitor>。  
  
-   不要從主要程式控制背景工作執行緒的執行 (例如，使用事件)。 相反地，請設計您的程式，讓背景工作執行緒負責等候到可進行工作、執行工作，並在工作完成時通知程式的其他組件。 如果背景工作執行緒不會封鎖起來，請考慮使用執行緒集區的執行緒。 <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> 在背景工作執行緒封鎖的情況下很有用。  
  
-   請勿使用型別來作為鎖定物件。 也就是避免像是 C# 中的 `lock(typeof(X))` 或 Visual Basic 中的 `SyncLock(GetType(X))` 的程式碼，或避免搭配 <xref:System.Type> 物件使用 <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>。 針對指定的類型，每個應用程式定義域都會有 <xref:System.Type?displayProperty=nameWithType> 的一個執行個體。 如果您鎖定的型別是公用的，則不是您自有的程式碼也可鎖定該型別，而導致死結。 若要了解其他問題，請參閱[可靠性最佳作法](../../../docs/framework/performance/reliability-best-practices.md)。  
  
-   鎖定執行個體時請小心，例如 C# 中的 `lock(this)` 或 Visual Basic 中的 `SyncLock(Me)`。 如果您應用程式中屬於該型別之外的其他程式碼鎖定物件，系統可能會發生死結。  
  
-   請務必要確定已進入監視器的執行緒一律會離開該監視器，即使執行緒還在監視器內卻發生例外狀況時亦然。 C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) 陳述式和 Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) 陳述式會自動提供這種行為，利用 **finally** 區塊來確保系統會呼叫 <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>。 如果您無法確保系統會呼叫 **Exit**，請考慮將您的設計改為使用 **Mutex**。 目前擁有 Mutex 的執行緒在終止時會自動將其釋放。  
  
-   對於需要不同資源的工作，請使用多個執行緒，並避免將多個執行緒指派給單一資源。 例如，任何涉及 I/O 的工作都可受惠於擁有自己的執行緒，因為該執行緒會在 I/O 作業期間封鎖起來，進而讓其他執行緒得以執行。 使用者輸入是受惠於專用執行緒的另一項資源。 在單一處理器電腦上，涉及大量計算的工作會與使用者輸入共存，並與涉及 I/O 的工作共存，但多個需要大量計算的工作會彼此爭用。  
  
-   請考慮使用 <xref:System.Threading.Interlocked> 類別的方法來處理簡單的狀態變更，而不要使用 `lock` 陳述式 (Visual Basic 中是 `SyncLock`)。 `lock` 陳述式是很好的泛用工具，但 <xref:System.Threading.Interlocked> 類別可為必須是不可部分完成的更新提供較好的效能。 就內部而言，如果沒有爭用的情況，它會執行單一鎖定前置詞。 在檢閱程式碼時，請注意如下列範例所示的程式碼。 在第一個範例中，狀態變數會遞增︰  
  
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
  
     您可以使用 <xref:System.Threading.Interlocked.Increment%2A> 方法而非 `lock` 陳述式來改善效能，如下所示：  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  在 .NET Framework 2.0 版中，<xref:System.Threading.Interlocked.Add%2A> 方法會在增量大於 1 時提供不可部分完成的更新。  
  
     在第二個範例中，只有當參考型別變數是 Null 參考 (在 Visual Basic 中是 `Nothing`) 時，該變數才會更新。  
  
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
  
     您可以使用 <xref:System.Threading.Interlocked.CompareExchange%2A> 方法來改善效能，如下所示：  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  在 .NET Framework 2.0 版中，<xref:System.Threading.Interlocked.CompareExchange%2A> 方法具有泛型多載，可用於任何參考類型的類型安全取代。  
  
## <a name="recommendations-for-class-libraries"></a>類別庫的建議  
 在設計類別庫的多執行緒功能時，請考慮下列指導方針︰  
  
-   盡可能避免同步處理需求。 經常使用的程式碼更該避免這一點。 例如，您可以調整演算法，使它容許競爭情形，而非消除此情形。 不必要的同步處理會降低效能，並有可能產生死結和競爭情形。  
  
-   讓 static 資料 (在 Visual Basic 中是 `Shared`) 的執行緒預設保有安全性。  
  
-   不要讓執行個體資料的執行緒預設保有安全性。 新增鎖定以建立安全執行緒程式碼的作法，會降低效能、增加鎖定爭用並可能導致死結發生。 在一般的應用程式模型中，一次只會有一個執行緒執行使用者程式碼，這種方式可將執行緒安全性的需求降到最低。 為此，.NET Framework 類別庫依預設不會保有執行緒安全性。  
  
-   避免提供會變更靜態狀態的靜態方法。 在一般的伺服器案例中，所有要求會共用靜態狀態，這表示多個執行緒可以同時執行該程式碼。 這可能會讓執行緒發生錯誤。 請考慮使用某種設計模式，以將資料封裝到不會讓所有要求共用的執行個體。 此外，如果靜態資料會同步處理，會在靜態方法之間改變狀態的呼叫將會導致死結或多餘的同步處理，而對效能造成負面影響。  
  
## <a name="see-also"></a>另請參閱

- [執行緒處理](../../../docs/standard/threading/index.md)  
- [執行緒和執行緒處理](../../../docs/standard/threading/threads-and-threading.md)
