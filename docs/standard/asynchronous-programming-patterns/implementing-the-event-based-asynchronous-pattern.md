---
title: "實作事件架構非同步模式 | Microsoft Docs"
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
  - "事件架構非同步模式"
  - "ProgressChangedEventArgs 類別"
  - "BackgroundWorker 元件"
  - "事件 [.NET Framework], 非同步"
  - "非同步模式"
  - "AsyncOperationManager 類別"
  - "執行緒處理 [.NET Framework], 非同步功能"
  - "元件 [.NET Framework] 非同步"
  - "AsyncOperation 類別"
  - "AsyncCompletedEventArgs 類別"
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 實作事件架構非同步模式
如果您正在撰寫的類別有一些作業，可能會造成明顯的延遲，請考慮並賦予它所實作的非同步功能[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)。  
  
 事件架構非同步模式提供具有非同步功能的類別封裝起來的標準化方式。 若使用協助程式類別實作，例如<xref:System.ComponentModel.AsyncOperationManager>，您的類別能夠正確地在任何應用程式模型，包括[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]，主控台應用程式和 Windows Form 應用程式。  
  
 如需實作事件架構非同步模式的範例，請參閱[How to︰ 實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)。  
  
 對於簡單的非同步作業，您可能會發現<xref:System.ComponentModel.BackgroundWorker>適當的元件。 如需詳細資訊<xref:System.ComponentModel.BackgroundWorker>，請參閱[How to︰ 在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)。  
  
 下列清單描述事件架構非同步模式的本主題中討論的功能。  
  
-   實作事件架構非同步模式的機會  
  
-   命名的非同步方法  
  
-   選擇性地支援取消作業  
  
-   選擇性地支援 IsBusy 屬性  
  
-   選擇性地提供支援進度報告  
  
-   選擇性地提供支援傳回累加結果  
  
-   處理 Out 和 Ref 參數在方法中  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>實作事件架構非同步模式的機會  
 請考慮實作事件架構非同步模式時︰  
  
-   類別的用戶端不需要<xref:System.Threading.WaitHandle>和<xref:System.IAsyncResult>物件可使用的非同步作業，這表示該輪詢和<xref:System.Threading.WaitHandle.WaitAll%2A>或<xref:System.Threading.WaitHandle.WaitAny%2A>必須設定用戶端所建立。  
  
-   您想要由用戶端使用熟悉的事件委派模型的非同步作業。  
  
 任何作業都做為非同步實作，但應視為那些您預期耗費很長的延遲。 特別適合是的作業的用戶端呼叫的方法和通知完成時，不需要進一步介入。 適當還有，持續執行定期對用戶端進度、 累加結果或狀態變更通知的作業。  
  
 如需有關如何決定何時支援事件架構非同步模式的詳細資訊，請參閱[決定何時實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)。  
  
## <a name="naming-asynchronous-methods"></a>命名的非同步方法  
 每個同步方法*MethodName*您想要提供非同步對應︰  
  
 定義*MethodName* `Async`方法的︰  
  
-   傳回 `void`。  
  
-   採用相同的參數*MethodName*方法。  
  
-   可接受多個引動過程。  
  
 選擇性地定義*MethodName* `Async`多載，等於*MethodName*`Async`，但使用了額外的物件值參數呼叫`userState`。 如果您已在此情況下管理多個並行引動過程的方法，這樣`userState`值會傳遞回區別的方法引動過程的所有事件處理常式。 您也可以選擇這樣做只是做為儲存供日後擷取使用者狀態的位置。  
  
 對於每個個別*MethodName* `Async`方法簽章︰  
  
1.  做為方法的相同類別中定義下列事件︰  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  定義下列委派和<xref:System.ComponentModel.AsyncCompletedEventArgs>。 此外，這些可能會定義在類別本身之外，但在相同的命名空間中。  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   請確認*MethodName* `CompletedEventArgs`類別會公開其成員做為唯讀屬性，並不是欄位，因為欄位會防止資料繫結。  
  
    -   未定義任何<xref:System.ComponentModel.AsyncCompletedEventArgs>-衍生的類別不會產生結果的方法。 只要使用的執行個體<xref:System.ComponentModel.AsyncCompletedEventArgs>本身。  
  
        > [!NOTE]
        >  它時，才能完全可以接受的可行且適當，可以重複使用委派和<xref:System.ComponentModel.AsyncCompletedEventArgs>型別。 在此情況下，命名將不能是一致性與方法名稱，因為指定的委派和<xref:System.ComponentModel.AsyncCompletedEventArgs>不會繫結至單一方法。  
  
## <a name="optionally-support-cancellation"></a>選擇性地支援取消作業  
 如果您的類別支援取消非同步作業，請取消應該公開給用戶端，如下所述。 請注意，有兩個決策點，必須先定義您的取消支援之前達成︰  
  
-   您的類別，包括未來預期的新增項目，是否有只有一個非同步作業支援取消？  
  
-   可以支援取消支援多個暫止作業的非同步作業嗎？ 也就是沒有*MethodName* `Async`方法是否使用`userState`參數，並等待任何作業完成之前無法讓多個引動過程？  
  
 使用下表中的這兩個問題的答案，來判斷應取消方法的簽章。  
  
### <a name="visual-basic"></a>Visual Basic  
  
||支援多個同步作業|一次只有一項作業|  
|------|------------------------------------------------|----------------------------------|  
|在整個類別只有一個非同步作業|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|在類別中的多個非同步作業|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||支援多個同步作業|一次只有一項作業|  
|------|------------------------------------------------|----------------------------------|  
|在整個類別只有一個非同步作業|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|在類別中的多個非同步作業|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 如果您定義`CancelAsync(object userState)`方法，用戶端必須小心選擇它們狀態的值，讓它們能夠區別這些物件上叫用的所有非同步方法時，不能只有單一非同步方法的所有引動過程之間。  
  
 決定命名單一非同步作業版本*MethodName* `AsyncCancel`根據能夠更輕鬆地探索 Visual Studio IntelliSense 之類的設計環境中的方法。 此分組相關的成員，並區別它們與具有非同步功能無關的其他成員。 如果您預期可能會有其他非同步加入作業在後續版本中，最好是定義`CancelAsync`。  
  
 請勿在相同類別中定義上述表格中的多個方法。 會毫無意義，或它將會充斥類別介面的過多的方法。  
  
 這些方法通常會立即傳回，並可能或可能實際上取消的作業。 事件處理常式中*MethodName* `Completed`事件， *MethodName* `CompletedEventArgs`物件包含`Cancelled`欄位中，用戶端可以用來判斷是否已取消。  
  
 取消語意 （semantics） 中所述，請遵守[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)。  
  
## <a name="optionally-support-the-isbusy-property"></a>選擇性地支援 IsBusy 屬性  
 如果您的類別不支援多個並行引動過程，請考慮公開`IsBusy`屬性。 這可讓開發人員決定是否*MethodName* `Async`方法執行時並沒有攔截例外狀況從*MethodName* `Async`方法。  
  
 遵守`IsBusy`語意 （semantics） 中所述[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)。  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>選擇性地提供支援進度報告  
 最好經常在其作業期間報告進度的非同步作業。 事件架構非同步模式提供這樣的指導方針。  
  
-   選擇性地定義的事件，產生非同步作業並在適當的執行緒上叫用。 <xref:System.ComponentModel.ProgressChangedEventArgs>物件攜帶應該是介於 0 到 100 之間的整數值的進度指示器。  
  
-   此事件的名稱，如下所示︰  
  
    -   `ProgressChanged`如果類別具有多個非同步作業 （或成長到未來的版本中包含多個非同步作業預期）。  
  
    -   *MethodName* `ProgressChanged`如果類別具有單一非同步作業。  
  
     這個命名選擇平行進行取消方法，選擇性地支援取消 」 一節中所述。  
  
 此事件應該使用<xref:System.ComponentModel.ProgressChangedEventHandler>委派簽章和<xref:System.ComponentModel.ProgressChangedEventArgs>類別。 或者，如果可以提供更特定的網域進度指示器 （適用於執行個體，讀取位元組和下載作業的總位元組），然後您應該定義的衍生的類別<xref:System.ComponentModel.ProgressChangedEventArgs>。  
  
 請注意，只有一個`ProgressChanged`或*MethodName* `ProgressChanged`事件類別，無論它支援非同步方法的數目。 用戶端應使用`userState`物件傳遞至*MethodName* `Async`方法，以區分多個並行作業的進度更新。  
  
 可能有多個作業都支援進度，而每一個都會傳回不同的進度指示器的。 在此情況下，單一`ProgressChanged`事件就不適當，以及您可以考慮支援多個`ProgressChanged`事件。 在此情況下使用的命名模式*MethodName* `ProgressChanged`每個*MethodName* `Async`方法。  
  
 進度報告語意 （semantics） 所述，請遵守[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)。  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>選擇性地提供支援傳回累加結果  
 有時候非同步作業可以傳回累加結果之前完成。 有許多可以用來支援這種情況下的選項。 以下是一些範例。  
  
### <a name="single-operation-class"></a>單一作業類別  
 如果您的類別只支援單一非同步作業，而且該作業會傳回累加結果，然後︰  
  
-   擴充<xref:System.ComponentModel.ProgressChangedEventArgs>類型以附帶累加結果資料，並定義*MethodName* `ProgressChanged`事件與這個擴充資料。  
  
-   這會引發*MethodName* `ProgressChanged`事件時報告累加結果。  
  
 此方案特別適用於單一非同步作業類別是與相同的事件發生在 「 所有作業 」，傳回累加結果，做為沒有問題，因為*MethodName* `ProgressChanged`沒有事件。  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>與同質累加結果的多重作業類別  
 在此案例中，您的類別支援多個非同步方法，每個都能傳回累加結果，而且這些累加結果都有相同的資料類型。  
  
 請遵循上述單一作業的類別，是相同的模型<xref:System.EventArgs>結構適用於所有的累加結果。 定義`ProgressChanged`事件，而不是*MethodName* `ProgressChanged`事件，因為它會套用至多個非同步方法。  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>具有異質累加結果的多重作業類別  
 如果您的類別支援多個非同步方法，每個傳回不同類型的資料，您應該︰  
  
-   區隔您的報告和進度報告累加結果。  
  
-   定義個別*MethodName* `ProgressChanged`具有適當事件<xref:System.EventArgs>每個非同步方法來處理該方法的累加結果資料。  
  
 叫用適當的執行緒上的事件處理常式中所述[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)。  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>處理 Out 和 Ref 參數在方法中  
 雖然使用`out`和`ref`，一般而言，建議您不要在.NET Framework 中，以下是它們的存在時要遵循的規則︰  
  
 提供同步方法*MethodName*:  
  
-   `out`參數*MethodName*不應屬於*MethodName*`Async`。 相反地，它們應屬於*MethodName* `CompletedEventArgs`具有相同名稱做為其參數相當於*MethodName* （除非還有更適當的名稱）。  
  
-   `ref`參數*MethodName*應該會顯示為部分*MethodName*`Async`，而且會*MethodName* `CompletedEventArgs`具有相同名稱做為其參數相當於*MethodName* （除非還有更適當的名稱）。  
  
 例如，假設︰  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 您的非同步方法並將其<xref:System.ComponentModel.AsyncCompletedEventArgs>類別看起來像這樣︰  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ComponentModel.ProgressChangedEventArgs>   
 <xref:System.ComponentModel.AsyncCompletedEventArgs>   
 [How to︰ 實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)   
 [如何︰ 在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [How to︰ 實作使用背景作業的表單](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [決定何時實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)   
 [使用事件架構非同步模式的多執行緒的程式設計](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)   
 [實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)