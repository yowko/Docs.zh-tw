---
title: 實作事件架構非同步模式的最佳作法
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 4acd2094-4f46-4eff-9190-92d0d9ff47db
ms.openlocfilehash: 26e1fd4231964be5448229a6b3c7d90c0ba64499
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882507"
---
# <a name="best-practices-for-implementing-the-event-based-asynchronous-pattern"></a>實作事件架構非同步模式的最佳作法
事件架構非同步模式提供有效率的方式，讓您運用熟悉的事件和委派語意，公開類別中的非同步行為。 若要實作事件架構非同步模式，您需要遵循一些特定的行為需求。 下列各節說明在實作遵循事件架構非同步模式的類別時，所應考量的需求和方針。  
  
 如需概觀，請參閱[實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)。  
  
## <a name="required-behavioral-guarantees"></a>需要的行為保證  
 如果您實作事件架構非同步模式，則必須提供一些保證，以確保類別的行為正確，並且類別的用戶端可依賴此行為。  
  
### <a name="completion"></a>完成  
 在成功完成、發生錯誤或取消時，一律會叫用 <em>MethodName</em>**Completed** 事件處理常式。 應用程式絕對不應該發生保持閒置狀態和永遠無法完成的情況。 這項規則的唯一例外，是在非同步作業本身設計為永遠無法完成的時候。  
  
### <a name="completed-event-and-eventargs"></a>Completed 事件和 EventArgs  
 對每個 <em>MethodName</em>**Async** 方法，會套用下列設計需求：  
  
- 在與此方法相同的類別上定義 <em>MethodName</em>**Completed** 事件。  
  
- 對衍生自 <xref:System.ComponentModel.AsyncCompletedEventArgs> 類別的 <em>MethodName</em>**Completed** 事件，定義 <xref:System.EventArgs> 類別和伴隨的委派。 預設類別名稱的格式應該為 <em>MethodName</em>**CompletedEventArgs**。  
  
- 確定 <xref:System.EventArgs> 類別是 <em>MethodName</em> 方法的傳回值所特有。 當您使用 <xref:System.EventArgs> 類別時，應該不需要開發人員轉換結果。  
  
     下列程式碼範例分別示範這項設計需求的良好和不良實作。  
  
```csharp  
// Good design  
private void Form1_MethodNameCompleted(object sender, xxxCompletedEventArgs e)   
{   
    DemoType result = e.Result;  
}  
  
// Bad design  
private void Form1_MethodNameCompleted(object sender, MethodNameCompletedEventArgs e)   
{   
    DemoType result = (DemoType)(e.Result);  
}  
```  
  
- 請勿對傳回 <xref:System.EventArgs> 的傳回方法定義 `void` 類別， 而是使用 <xref:System.ComponentModel.AsyncCompletedEventArgs> 類別的執行個體。  
  
- 確定一律引發 <em>MethodName</em>**Completed** 事件。 此事件應該在成功完成、發生錯誤或取消時引發。 應用程式絕對不應該發生保持閒置狀態和永遠無法完成的情況。  
  
- 確定攔截非同步作業中發生的任何例外狀況，並且將攔截到的例外狀況指派給 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> 屬性。  
  
- 如果完成工作時發生錯誤，應該會無法存取結果。 當 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> 屬性不是 `null` 時，確定存取 <xref:System.EventArgs> 結構中的任何屬性都會引發例外狀況。 使用 <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> 方法來執行這項驗證。  
  
- 將逾時模型化為錯誤。 如果發生逾時，則引發 <em>MethodName</em>**Completed** 事件，並將 <xref:System.TimeoutException> 指派給 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> 屬性。  
  
- 如果您的類別支援多個並行引動過程，請確定 <em>MethodName</em>**Completed** 事件包含適當的 `userSuppliedState` 物件。  
  
- 確定 <em>MethodName</em>**Completed** 事件會在適當的執行緒上，以及應用程式生命週期中的適當時間引發。 如需詳細資訊，請參閱＜執行緒和內容＞一節。  
  
### <a name="simultaneously-executing-operations"></a>同時執行作業  
  
- 如果您的類別支援多個並行引動過程，請讓開發人員定義 <em>MethodName</em>**Async** 多載 (此多載使用物件值狀態參數，或是稱為 `userSuppliedState` 的工作 ID)，以分別追蹤每個引動過程。 這個參數應該一律是 <em>MethodName</em>**Async** 方法簽章中的最後一個參數。  
  
- 如果您的類別定義使用物件值狀態參數或工作 ID 的 <em>MethodName</em>**Async** 多載，請務必使用此工作 ID 來追蹤作業的存留期，並務必將此 ID 傳回完成處理常式。 有一些 Helper 類別能提供協助。 如需並行管理的詳細資訊，請參閱[如何：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)。  
  
- 如果您的類別定義不含狀態參數的 <em>MethodName</em>**Async** 方法，而且不支援多個並行引動過程，請確定之前的 <em>MethodName</em>**Async** 引動過程完成之前，叫用 <em>MethodName</em>**Async** 的任何嘗試動作都會引發 <xref:System.InvalidOperationException>。  
  
- 一般而言，如果叫用 <em>MethodName</em>**Async** 方法多次而不使用 `userSuppliedState` 參數，就會形成多個未完成作業，此時請不要引發例外狀況。 當您的類別明確地無法處理這種情況，但開發人員應該能夠處理這些無法區分的多個回呼時，便可以引發例外狀況。  
  
### <a name="accessing-results"></a>存取結果  
  
- 如果在執行非同步作業時發生錯誤，應該會無法存取結果。 確定當 <xref:System.ComponentModel.AsyncCompletedEventArgs> 不是 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> 時，存取 `null` 中的任何屬性，都會引發 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> 所參考的例外狀況。 為此，<xref:System.ComponentModel.AsyncCompletedEventArgs> 類別提供了 <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A> 方法。  
  
- 確定存取結果的任何嘗試動作都會引發 <xref:System.InvalidOperationException>，指出作業已取消。 使用 <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> 方法來執行這項驗證。  
  
### <a name="progress-reporting"></a>進度報告  
  
- 在可能的情況下，會支援進度報告。 這讓開發人員能在使用您的類別時，對應用程式使用者提供更好的體驗。  
  
- 如果您實作 **ProgressChanged** 或 <em>MethodName</em>**ProgressChanged** 事件，請確定在引發特定非同步作業的 <em>MethodName</em>**Completed** 事件之後，不會對該作業引發這類事件。  
  
- 如果已填入標準 <xref:System.ComponentModel.ProgressChangedEventArgs>，請確定 <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> 一律可以解譯為百分比。 百分比不需要很精確，但應該代表某個百分比。 如果您的進度報告單位必須是百分比以外的單位，請從 <xref:System.ComponentModel.ProgressChangedEventArgs> 類別衍生一個類別，並將 <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> 保持為 0。 避免使用百分比以外的報告單位。  
  
- 確定 `ProgressChanged` 事件會在適當的執行緒上，以及應用程式生命週期中的適當時間引發。 如需詳細資訊，請參閱＜執行緒和內容＞一節。  
  
### <a name="isbusy-implementation"></a>IsBusy 實作  
  
- 如果您的類別支援多個並行引動過程，請勿公開 `IsBusy` 屬性。 例如，XML Web 服務 Proxy 不會公開 `IsBusy` 屬性，因為這些 Proxy 支援非同步方法的多個並行引動過程。  
  
- `IsBusy` 屬性在呼叫 <em>MethodName</em>**Async** 方法之後，以及引發 <em>MethodName</em>**Completed** 事件之前，應該傳回 `true`。 否則應該傳回 `false`。 <xref:System.ComponentModel.BackgroundWorker> 和 <xref:System.Net.WebClient> 元件都是公開 `IsBusy` 屬性之類別的範例。  
  
### <a name="cancellation"></a>取消  
  
- 在可能的情況下，會支援取消。 這讓開發人員能在使用您的類別時，對應用程式使用者提供更好的體驗。  
  
- 在取消的情況下，請設定 <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> 物件中的 <xref:System.ComponentModel.AsyncCompletedEventArgs> 旗標。  
  
- 確定存取結果的任何嘗試動作都會引發 <xref:System.InvalidOperationException>，指出作業已取消。 使用 <xref:System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary%2A?displayProperty=nameWithType> 方法來執行這項驗證。  
  
- 確定對取消方法的呼叫一律會成功傳回，而且絕對不會引發例外狀況。 一般而言，用戶端不會收到通知，指出作業是否真的可以在任何指定時間取消；用戶端也不會收到通知，指出先前發出的取消是否成功。 不過，由於應用程式參與完成狀態，因此應用程式一律會在取消成功時收到通知。  
  
- 在取消作業時，引發 <em>MethodName</em>**Completed** 事件。  
  
### <a name="errors-and-exceptions"></a>錯誤和例外狀況  
  
- 攔截非同步作業中發生的任何例外狀況，並將 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> 屬性的值設定為該例外狀況。  
  
### <a name="threading-and-contexts"></a>執行緒和內容  
 類別若要正常運作，必須在適當執行緒上或指定應用程式模型 (包括 ASP.NET 和 Windows Forms 應用程式) 的內容中，叫用用戶端的事件處理常式。 <xref:System.ComponentModel.AsyncOperation> 和 <xref:System.ComponentModel.AsyncOperationManager> 等兩個重要的 Helper 類別，可用於確保您的非同步類別在任何應用程式模型下皆運作正常。  
  
 <xref:System.ComponentModel.AsyncOperationManager> 提供一個方法 <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>，此方法會傳回 <xref:System.ComponentModel.AsyncOperation>。 您的 <em>MethodName</em>**Async** 方法會呼叫 <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>，而您的類別會使用傳回的 <xref:System.ComponentModel.AsyncOperation> 來追蹤非同步工作的存留期。  
  
 若要向用戶端報告進度、累加結果和完成，請呼叫 <xref:System.ComponentModel.AsyncOperation.Post%2A> 上的 <xref:System.ComponentModel.AsyncOperation.OperationCompleted%2A> 和 <xref:System.ComponentModel.AsyncOperation> 方法。 <xref:System.ComponentModel.AsyncOperation> 會負責將用戶端事件處理常式的呼叫，封送處理至適當的執行緒或內容。  
  
> [!NOTE]
>  如果要明確違背應用程式模型的原則，不過依然要受益於使用事件架構非同步模式的其他優點，您可以規避這些規則。 例如，您可能需要將 Windows Form 中執行的類別設定為無限制執行緒的類別。 只要開發人員了解隱含的限制，您就可以建立無限制執行緒的類別。 主控台應用程式不會同步執行 <xref:System.ComponentModel.AsyncOperation.Post%2A> 呼叫。 這可能會造成 `ProgressChanged` 事件不按順序引發。 如果您想要以序列化方式執行 <xref:System.ComponentModel.AsyncOperation.Post%2A> 呼叫，請實作及安裝 <xref:System.Threading.SynchronizationContext?displayProperty=nameWithType> 類別。  
  
 如需使用 <xref:System.ComponentModel.AsyncOperation> 和 <xref:System.ComponentModel.AsyncOperationManager> 啟用非同步作業的詳細資訊，請參閱[如何：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)。  
  
## <a name="guidelines"></a>方針  
  
- 理想上，每個方法引動過程都應該獨立於其他引動過程。 您應該避免將引動過程與共用資源結合。 如果要在引動過程之間共用資源，您需要在實作中提供適當的同步處理機制。  
  
- 不建議使用需要用戶端實作同步處理的設計。 例如，您可以有一個非同步方法，接收全域靜態物件做為參數；這種方法的多個並行引動過程可能會造成資料損毀或死結。  
  
- 如果您實作具有多個引動過程多載 (簽章中的 `userState`) 的方法，您的類別將需要管理使用者狀態 (或工作 ID) 及其對應暫止作業的集合。 這個集合應該以 `lock` 區域保護，因為各種引動過程都會加入和移除集合中的 `userState` 物件。  
  
- 如果可行且適當，請考慮重複使用 `CompletedEventArgs` 類別。 在此情況下，由於指定的委派和 <xref:System.EventArgs> 類型不會繫結至單一方法，因此命名將不會與方法名稱一致。 不過，絕對禁止強制開發人員轉換從 <xref:System.EventArgs> 上屬性擷取的值。  
  
- 如果您正在撰寫衍生自 <xref:System.ComponentModel.Component> 的類別，請勿實作及安裝您自己的 <xref:System.Threading.SynchronizationContext> 類別。 應用程式模型 (而不是元件) 會控制使用的 <xref:System.Threading.SynchronizationContext>。  
  
- 當您使用任何類型的多執行緒時，您很有可能會暴露在非常嚴重且複雜的錯誤下。 在實作任何使用多執行緒的解決方案之前，請參閱 [Managed 執行緒最佳做法](../../../docs/standard/threading/managed-threading-best-practices.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- [實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)
- [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [決定何時實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [如何：使用支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [如何：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
