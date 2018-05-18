---
title: 事件架構非同步模式概觀
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 792aa8da-918b-458e-b154-9836b97735f3
ms.openlocfilehash: 0f78ae4b6abacea6fd1240a1472e1de0e625a8e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="event-based-asynchronous-pattern-overview"></a>事件架構非同步模式概觀
要同時執行許多工作，還能繼續回應使用者互動，這樣的應用程式通常都需要可以使用多執行緒的設計。 <xref:System.Threading> 命名空間提供建立高效能多執行緒應用程式的所有必要工具，但是要有效地使用這些工具，需要具備多執行緒軟體工程的豐富經驗。 對於較簡單的多執行緒應用程式，<xref:System.ComponentModel.BackgroundWorker> 元件提供了簡單明瞭的方案。 如果是較為複雜精細的非同步應用程式，請考慮實作遵守事件架構非同步模式的類別。  
  
 事件架構非同步模式提供多執行緒應用程式的優點，同時隱藏多執行緒設計中許多原有的複雜問題。 使用支援此模式的類別，可以讓您：  
  
-   「在背景中」執行耗時的工作，像是下載及資料庫作業，而不會中斷應用程式。  
  
-   同時執行多項作業，並在每項作業完成時都收到通知。  
  
-   等候資源變成可供使用，而不需要停止 (「擱置」) 應用程式。  
  
-   使用熟悉的事件和委派模型，與暫止的非同步作業通訊。 如需使用事件處理常式和委派的詳細資訊，請參閱[事件](../../../docs/standard/events/index.md)。  
  
 支援事件架構非同步模式的類別，會有一個或多個名為 *MethodName*Async的方法。這些方法可能鏡像在目前執行緒上執行相同作業的同步版本。這個類別可能也具有 MethodName***Completed* 事件，並且具有 MethodName***AsyncCancel* (或簡單地說 **CancelAsync**) 方法。  
  
 <xref:System.Windows.Forms.PictureBox> 是支援事件架構非同步模式的一般元件。 您可以呼叫影像的 <xref:System.Windows.Forms.PictureBox.Load%2A> 方法以同步下載影像，不過如果影像非常龐大或是網路連接相當緩慢，在下載作業完成且對 <xref:System.Windows.Forms.PictureBox.Load%2A> 的呼叫傳回之前，應用程式都會是停止 (「擱置」) 狀態。  
  
 如果要讓應用程式在載入影像時持續執行，您可以呼叫 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> 方法並處理 <xref:System.Windows.Forms.PictureBox.LoadCompleted> 事件，就像處理其他任何事件一樣。 當您呼叫 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> 方法時，應用程式就會繼續執行，同時下載會在個別的執行緒上 (「在背景中」) 進行。 當影像載入作業完成時，就會呼叫您的事件處理常式，此時事件處理常式便可以檢查 <xref:System.ComponentModel.AsyncCompletedEventArgs> 參數，以判斷下載是否順利完成。  
  
 事件架構非同步模式需要能夠取消非同步作業，而 <xref:System.Windows.Forms.PictureBox> 控制項以它所具有的 <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> 方法支援這項需求。 呼叫 <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> 便會發出要求讓暫止的下載停止，而且在取消工作時，就會引發 <xref:System.Windows.Forms.PictureBox.LoadCompleted> 事件。  
  
> [!CAUTION]
>  產生 <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> 要求時剛好完成下載也是可能發生的，因此 <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> 可能無法反映取消的要求。 這種情況稱為「競爭情形」(Race Condition)，這是多執行緒程式設計中的常見問題。 如需多執行緒程式設計問題的詳細資訊，請參閱[受控執行緒處理的最佳做法](../../../docs/standard/threading/managed-threading-best-practices.md)。  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>事件架構非同步模式的特性  
 事件架構非同步模式可能會採用數種格式，需視特定類別所支援作業的複雜度而定。 最簡單的類別可以有單一的 MethodName***Async* 方法和對應的 MethodName***Completed* 事件。 比較複雜的類別則可以有數個 MethodName***Async* 方法，每一個方法都有對應的 MethodName***Completed* 事件，以及這些方法的同步版本。 這些類別可以選擇性地支援每個非同步方法的取消、進度報告和累加結果。  
  
 非同步方法也可以支援多次暫止呼叫 (多個並行引動過程)，讓您的程式碼能在完成其他暫止作業之前，對這種方法呼叫任意次數。 要正確地處理這種情況，您的應用程式可能需要追蹤每個作業的完成狀態。  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>事件架構非同步模式的範例  
 <xref:System.Media.SoundPlayer> 和 <xref:System.Windows.Forms.PictureBox> 元件代表事件架構非同步模式的簡單實作。 <xref:System.Net.WebClient> 和 <xref:System.ComponentModel.BackgroundWorker> 元件則代表事件架構非同步模式的較複雜實作。  
  
 以下是符合此模式的範例類別宣告：  
  
```vb  
Public Class AsyncExample  
    ' Synchronous methods.  
    Public Function Method1(ByVal param As String) As Integer   
    Public Sub Method2(ByVal param As Double)   
  
    ' Asynchronous methods.  
    Overloads Public Sub Method1Async(ByVal param As String)   
    Overloads Public Sub Method1Async(ByVal param As String, ByVal userState As Object)   
    Public Event Method1Completed As Method1CompletedEventHandler  
  
    Overloads Public Sub Method2Async(ByVal param As Double)   
    Overloads Public Sub Method2Async(ByVal param As Double, ByVal userState As Object)   
    Public Event Method2Completed As Method2CompletedEventHandler  
  
    Public Sub CancelAsync(ByVal userState As Object)   
  
    Public ReadOnly Property IsBusy () As Boolean  
  
    ' Class implementation not shown.  
End Class  
```  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 虛擬 `AsyncExample` 類別具有兩個方法，這兩種方法都支援同步和非同步引動過程。 同步多載的行為與任何方法呼叫都一樣，並且會在呼叫的執行緒上執行作業；如果作業相當耗時，在呼叫傳回之前，可能會明顯出現延遲。 非同步多載會在另一個執行緒上啟動作業，然後立即傳回，讓呼叫的執行緒能夠繼續進行，同時作業依然能「在背景中」執行。  
  
### <a name="asynchronous-method-overloads"></a>非同步方法多載  
 非同步作業具有兩種可能的多載：單一引動過程和多個引動過程。 您可以根據其方法簽章來區別這兩種格式：多個引動過程格式具有稱為 `userState` 的額外參數。 這種格式使您的程式碼能夠呼叫 `Method1Async(string param, object userState)` 多次，而不需要等候任何暫止的非同步作業完成。 另一方面，如果您在先前的引動過程完成之前，嘗試呼叫 `Method1Async(string param)`，此方法就會引發 <xref:System.InvalidOperationException>。  
  
 多個引動過程多載的 `userState` 參數可讓您區別各種非同步作業。 您可以為 `Method1Async(string param, object userState)` 的每個呼叫提供唯一值 (例如，GUID 或雜湊碼)，當每個作業完成時，事件處理常式就可以判斷是哪個作業的執行個體引發了完成事件。  
  
### <a name="tracking-pending-operations"></a>追蹤暫止的作業  
 如果使用多個引動過程多載，程式碼就必須持續追蹤暫止工作的 `userState` 物件 (工作 ID)。 對於 `Method1Async(string param, object userState)` 的每個呼叫，一般都會產生新的、唯一的 `userState` 物件，並將該物件加入至集合中。 當對應至這個 `userState` 物件的工作引發完成事件時，完成方法實作就會檢查 <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType>，並將它從您的集合中移除。 如果使用這種方式，`userState` 參數就會成為工作 ID。  
  
> [!NOTE]
>  在對多個引動過程多載的呼叫中，請務必謹慎地為 `userState` 提供唯一值。 非唯一的工作 ID 將會使非同步類別擲回 <xref:System.ArgumentException>。  
  
### <a name="canceling-pending-operations"></a>取消暫止的作業  
 在非同步作業完成之前，隨時都能取消這些作業是非常重要的。 實作事件架構非同步模式的類別會具有 `CancelAsync` 方法 (如果只有一個非同步方法) 或 MethodName***AsyncCancel* 方法 (如果有多個非同步方法)。  
  
 允許多個引動過程的方法使用 `userState` 參數，該參數可用於追蹤每個工作的存留期。 `CancelAsync` 使用 `userState` 參數，該參數可讓您取消特定的暫止工作。  
  
 您無法取消一次只能支援一個暫止作業的方法 (例如 `Method1Async(string param)`)。  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>接收進度更新和累加結果  
 遵守事件架構非同步模式的類別，可能會選擇性地提供用來追蹤進度和累加結果的事件。 這個事件通常會命名為 `ProgressChanged` 或 *MethodName*ProgressChanged，並且它的對應事件處理常式將會使用 <xref:System.ComponentModel.ProgressChangedEventArgs> 參數。  
  
 `ProgressChanged` 事件的事件處理常式可以檢查 <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> 屬性，以判斷已經完成非同步工作的百分比。 這個屬性的範圍會介於 0 到 100 之間，並且可以用來更新 <xref:System.Windows.Forms.ProgressBar.Value%2A> 的 <xref:System.Windows.Forms.ProgressBar> 屬性。 如果正在暫止多個非同步作業，您可以使用 <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> 屬性來區別哪個作業在報告進度。  
  
 有些類別可以在進行非同步作業時報告累加結果。 這些結果將會儲存在衍生自 <xref:System.ComponentModel.ProgressChangedEventArgs> 的類別中，並且會顯示為衍生類別中的屬性。 您可以像是存取 `ProgressChanged` 屬性一般，存取 <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> 事件之事件處理常式中的這些結果。 如果正在暫止多個非同步作業，您可以使用 <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> 屬性來區別哪個作業在報告累加結果。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [操作說明：使用支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 [操作說明：在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [操作說明：實作使用背景作業的表單](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [使用事件架構非同步模式設計多執行緒程式](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [決定何時實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
