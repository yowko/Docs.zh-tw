---
title: 實作事件架構非同步模式
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
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: 2c95b903ae03ea261674885262b24a33efa9e2db
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973739"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>實作事件架構非同步模式
如果您正在撰寫某項類別，其擁有的一些作業可能會造成明顯延遲，請考慮實作[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)以賦予它非同步功能。  
  
 事件架構非同步模式提供標準化方式來封裝具有非同步功能的類別。 您的類別若是使用協助程式類別 (例如 <xref:System.ComponentModel.AsyncOperationManager>) 來實作，就能夠在任何應用程式模型下正確運作，這些模型包括 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]、主控台應用程式和 Windows Forms 應用程式。  
  
 如需實作事件架構非同步模式的範例，請參閱[如何：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)。  
  
 您可能會發現 <xref:System.ComponentModel.BackgroundWorker> 元件適用於簡單的非同步作業。 如需 <xref:System.ComponentModel.BackgroundWorker> 的詳細資訊，請參閱[如何：在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)。  
  
 下列清單所描述的事件架構非同步模式功能，本主題會加以討論。  
  
-   實作事件架構非同步模式的機會  
  
-   為非同步方法命名  
  
-   選擇性地支援取消方法  
  
-   選擇性地支援 IsBusy 屬性  
  
-   選擇性地提供進度報告支援  
  
-   選擇性地提供可傳回累加結果的支援  
  
-   在方法中處理 Out 和 Ref 參數  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>實作事件架構非同步模式的機會  
 若有下列情況，請考慮實作事件架構非同步模式：  
  
-   類別的用戶端不需要非同步作業可使用 <xref:System.Threading.WaitHandle> 和 <xref:System.IAsyncResult> 物件，這表示輪詢和 <xref:System.Threading.WaitHandle.WaitAll%2A> 或 <xref:System.Threading.WaitHandle.WaitAny%2A> 都必須由用戶端所建立。  
  
-   您想要由用戶端使用熟悉的事件/委派模型來管理非同步作業。  
  
 任何作業都適合進行非同步實作，但您應該考慮那些預期會產生較長延遲的作業。 用戶端會呼叫方法並在完成時收到通知的作業尤其適合，因為您不必進一步介入。 會持續執行，並定期將進度、累加結果或狀態變更通知用戶端的作業也很適合。  
  
 如需有關如何決定何時該支援事件架構非同步模式的詳細資訊，請參閱[決定何時實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)。  
  
## <a name="naming-asynchronous-methods"></a>為非同步方法命名  
 對於您要為其提供非同步對應的每一個 MethodName 同步方法：  
  
 定義有下列情形的 _MethodName_**Async** 方法：  
  
-   傳回 `void`。  
  
-   使用與 MethodName 方法相同的參數。  
  
-   接受多個引動過程。  
  
 選擇性地定義 _MethodName_**Async** 多載，它與 _MethodName_**Async** 相同，但是具有稱為 `userState` 的額外物件值參數。 需要這麼做的前提是，您已準備好管理您擁有之方法的多個並行引動過程，在此情況下，`userState` 值會傳回給所有的事件處理常式，以供區別該方法的各個引動過程。 您也可以純粹為了能有位置可儲存使用者狀態以供日後擷取，而選擇這樣做。  
  
 針對每個個別的 _MethodName_**Async** 方法簽章：  
  
1.  在相同的類別中定義下列事件來作為方法︰  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  定義下列委派和 <xref:System.ComponentModel.AsyncCompletedEventArgs>。 此外，這些項目可能會在類別本身之外來定義，但會在相同的命名空間中。  
  
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
  
    -   確定 _MethodName_**CompletedEventArgs** 類別將其成員公開為唯讀屬性，而不是欄位，因為欄位會防止資料繫結。  
  
    -   不要為不會產生結果的方法定義任何 <xref:System.ComponentModel.AsyncCompletedEventArgs> 衍生類別。 只要使用 <xref:System.ComponentModel.AsyncCompletedEventArgs> 本身的執行個體。  
  
        > [!NOTE]
        >  只要可行且適當，重複使用委派和 <xref:System.ComponentModel.AsyncCompletedEventArgs> 型別也是完全可以接受的。 在此情況下，其命名將不會與方法名稱一致，因為給定的委派和 <xref:System.ComponentModel.AsyncCompletedEventArgs> 不會繫結至單一方法。  
  
## <a name="optionally-support-cancellation"></a>選擇性地支援取消方法  
 如果您的類別會支援取消非同步作業，請如下所述對用戶端公開取消方法。 請注意，在定義取消支援之前，您必須先達成兩個決策點︰  
  
-   您的類別 (包括其未來預期的新增項目) 是否只有一個支援取消方法的非同步作業？  
  
-   可支援取消方法的非同步作業能否支援多個暫止作業？ 也就是說，_MethodName_**Async** 方法是否使用 `userState` 參數，而且是否在等候任何作業完成之前允許多個引動過程？  
  
 使用下表中對於這兩個問題的回答，來判斷您的取消方法應該使用的簽章。  
  
### <a name="visual-basic"></a>Visual Basic  
  
||支援多個同時作業|一次只有一個作業|  
|------|------------------------------------------------|----------------------------------|  
|整個類別只有一個非同步作業|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|類別中有多個非同步作業|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C\#
  
||支援多個同時作業|一次只有一個作業|  
|------|------------------------------------------------|----------------------------------|  
|整個類別只有一個非同步作業|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|類別中有多個非同步作業|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 如果您定義 `CancelAsync(object userState)` 方法，用戶端必須小心地選擇它們的狀態值，以便能夠區別物件上所叫用的所有非同步方法，而不只是能夠區別單一非同步方法的所有引動過程。  
  
 決定命名單一非同步作業版本 _MethodName_**AsyncCancel**，是基於能在像是 Visual Studio's IntelliSense 的設計環境中，更容易地探索到這個方法。 這會將相關的成員群組在一起，並讓與非同步功能無關的其他成員可與它們區別開來。 如果您預期後續版本中可能會新增其他非同步作業，您最好要定義 `CancelAsync`。  
  
 請勿將上述表格中的多個方法定義到相同類別中。 這麼做毫無意義，而且類別介面也會因為方法數量暴增而變得雜亂。  
  
 這些方法通常會立即傳回，而且作業實際上不一定會取消。 在 _MethodName_**Completed** 事件的事件處理常式中，_MethodName_**CompletedEventArgs** object contains a `Cancelled` 欄位，可讓用戶端用來判斷是否已取消。  
  
 請遵守[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)中所述的取消語意。  
  
## <a name="optionally-support-the-isbusy-property"></a>選擇性地支援 IsBusy 屬性  
 如果您的類別不支援多個並行引動過程，請考慮公開 `IsBusy` 屬性。 如此讓開發人員不需攔截 _MethodName_**Async** 方法中的例外狀況，就可以判斷是否有 _MethodName_**Async** 方法正在執行。  
  
 請遵守[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)中所述的 `IsBusy` 語意。  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>選擇性地提供進度報告支援  
 非同步作業經常需要在其作業期間報告進度。 事件架構非同步模式提供了這方面的指導方針。  
  
-   選擇性地定義要供非同步作業引發，並在適當的執行緒上叫用的事件。 <xref:System.ComponentModel.ProgressChangedEventArgs> 物件帶有以整數值表示的進度指示器，其值應該會介於 0 到 100 之間。  
  
-   將此事件命名如下︰  
  
    -   `ProgressChanged`，如果類別具有多個非同步作業 (或預期會有成長，而會在未來的版本中包含多個非同步作業)。  
  
    -   _MethodName_**ProgressChanged**，如果類別具有單一非同步作業。  
  
     這個命名選擇和取消方法的選擇類似，後者在＜選擇性地支援取消方法＞一節中有所說明。  
  
 此事件應使用 <xref:System.ComponentModel.ProgressChangedEventHandler> 委派簽章和 <xref:System.ComponentModel.ProgressChangedEventArgs> 類別。 或者，如果您可以提供更具網域特性的進度指示器 (例如，下載作業的已讀位元組數和位元組總數)，就應該定義 <xref:System.ComponentModel.ProgressChangedEventArgs> 的衍生類別。  
  
 請注意，不論一個類別支援多少非同步方法，每個類別都只有一個 `ProgressChanged` 或 _MethodName_**ProgressChanged** 事件。 用戶端必須使用傳遞至 _MethodName_**Async** 方法的 `userState` 物件區分多個並行作業上的進度更新。  
  
 有時候可能會有多個作業都支援進度報告，而各自傳回不同的進度指示器。 在此情況下，使用單一的 `ProgressChanged` 事件就不是合適的作法，因此您可能會考慮支援多個 `ProgressChanged` 事件。 在此情況下，請為每個 _MethodName_**Async** 方法使用 _MethodName_**ProgressChanged** 的命名模式。  
  
 請遵守[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)中所述的進度報告語意。  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>選擇性地提供可傳回累加結果的支援  
 有時候非同步作業會在完成之前傳回累加結果。 您有許多選項可用來支援這種情況。 下面有一些範例。  
  
### <a name="single-operation-class"></a>單一作業類別  
 如果您的類別只支援單一非同步作業，而且該作業可傳回累加結果，則請︰  
  
-   擴充 <xref:System.ComponentModel.ProgressChangedEventArgs> 型別以附帶累加結果資料，並以這個擴充資料來定義 _MethodName_**ProgressChanged** 事件。  
  
-   在出現可回報的累加結果時，引發這個 _MethodName_**ProgressChanged** 事件。  
  
 這個解決方案特別適用於單一非同步作業類別，因為就像 _MethodName_**ProgressChanged** 事件一樣，相同事件在「所有作業」上發生並傳回累加結果時，並不會造成問題。  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>具有同質累加結果的多重作業類別  
 在此案例中，您的類別會支援多個非同步方法，每個方法都能傳回累加結果，而且這些累加結果全都有相同型別的資料。  
  
 請遵循上述的單一作業類別模型，因為同樣的 <xref:System.EventArgs> 結構適用於所有累加結果。 定義 `ProgressChanged` 事件而非 _MethodName_**ProgressChanged** 事件，因為它會套用到多個非同步方法。  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>具有異質累加結果的多重作業類別  
 如果您的類別支援多個非同步方法，而且各會傳回不同型別的資料，您應該︰  
  
-   將累加結果報告和進度報告區隔開來。  
  
-   對於每個非同步方法，以適當的 <xref:System.EventArgs> 定義個別的 _MethodName_**ProgressChanged** 事件，以處理該方法的累加結果資料。  
  
 如[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)所述，在適當的執行緒上叫用該事件處理常式。  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>在方法中處理 Out 和 Ref 參數  
 一般而言，雖然我們不建議您在 .NET Framework 中使用 `out` 和 `ref`，但如果它們存在，請遵循以下規則︰  
  
 假設同步方法為 MethodName：  
  
-   MethodName 的 `out` 參數不應成為 _MethodName_**Async** 的一部分。 相反地，這些參數應該成為 _MethodName_**CompletedEventArgs** 的一部分，其名稱會與 MethodName 中的對等參數相同 (除非還有更適當的名稱)。  
  
-   MethodName 的 `ref` 參數應該為 _MethodName_**Async** 的一部分，並且也必須是 _MethodName_**CompletedEventArgs** 的一部分，其名稱會與 MethodName 中的對等參數相同 (除非還有更適當的名稱)。  
  
 例如，假設︰  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 您的非同步方法與其 <xref:System.ComponentModel.AsyncCompletedEventArgs> 類別看起來應該像這樣：  
  
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

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [如何：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [如何：在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [如何：實作使用背景作業的表單](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [決定何時實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
