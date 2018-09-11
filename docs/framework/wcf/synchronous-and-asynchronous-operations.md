---
title: 同步和非同步作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: c2948cf76f7763eae51689973346965bc6c720a8
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361559"
---
# <a name="synchronous-and-asynchronous-operations"></a>同步和非同步作業
本主題討論實作和呼叫非同步服務作業。  
  
 許多應用程式會非同步呼叫方法，因為這麼做使應用程式可以在方法呼叫執行的同時繼續進行有用的工作。 Windows Communication Foundation (WCF) 服務和用戶端可以在應用程式兩個不同的特定層級參與非同步作業呼叫，這能讓 WCF 應用程式在互動性的權衡之下，具有更大的彈性將輸送量最大化。  
  
## <a name="types-of-asynchronous-operations"></a>非同步作業的類型  
 WCF 中的所有服務合約，無論參數型別和傳回值為何，都會使用 WCF 屬性來指定用戶端與服務之間的特定訊息交換模式。 WCF 會自動將傳入和傳出訊息路由傳送至適當的服務作業或正在執行的用戶端程式碼。  
  
 用戶端僅擁有服務合約，而這個服務合約會指定特定作業的訊息交換模式。 只要觀察到基礎訊息交換模式，用戶端便可以提供開發人員所選擇的程式設計模型。 同樣的，只要觀察到指定的訊息模式，服務便可以任何方式實作作業。  
  
 服務合約與服務或用戶端實作無關，而這樣的獨立性可在 WCF 應用程式中進行下列形式的非同步執行：  
  
-   用戶端可以使用同步訊息交換，以非同步方式叫用要求/回應作業。  
  
-   服務可以使用同步訊息交換，來以非同步方式實作要求/回應作業。  
  
-   不管用戶端或服務的實作如何，訊息交換可以是單向。  
  
### <a name="suggested-asynchronous-scenarios"></a>建議的非同步案例  
 如果作業服務實作發出封鎖呼叫 (例如進行 I/O 工作)，這時請在服務作業實作中使用非同步方法。 當您處於非同步作業實作中時，請嘗試呼叫非同步作業和方法，盡可能地延伸非同步呼叫路徑。 例如，從 `BeginOperationTwo()` 內呼叫 `BeginOperationOne()`。  
  
-   在下列情況中，在用戶端中使用非同步化方法或呼叫應用程式：  
  
-   如果您是從中介層應用程式叫用作業。 (如需此類案例的詳細資訊，請參閱[中介層用戶端應用程式](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md))。  
  
-   如果您是叫用 ASP.NET 頁面內的作業，請使用非同步頁面。  
  
-   如果您是從任何為單一執行緒的應用程式叫用作業，例如 Windows Forms 或 Windows Presentation Foundation (WPF)。 使用事件架構非同步呼叫模型時，結果事件會在 UI 執行緒上引發，並將回應新增至應用程式中，而不需要您自己去處理多個執行緒。  
  
-   一般而言，如果您在同步與非同步呼叫之間有選擇，請選擇非同步呼叫。  
  
### <a name="implementing-an-asynchronous-service-operation"></a>實作非同步服務作業  
 您可以使用下列三個方法的其中一個來實作非同步服務作業：  
  
1.  工作架構非同步模式  
  
2.  事件架構非同步模式  
  
3.  IAsyncResult 非同步模式  
  
#### <a name="task-based-asynchronous-pattern"></a>以工作為基礎的非同步模式  
 工作架構非同步模式是實作非同步作業的慣用方式，因為這是最簡單且最直接的方式。 若要使用這個方法，只需實作服務作業並指定 Task\<T> 的傳回類型，其中 T 是由邏輯作業傳回的類型。 例如:   
  
```csharp  
public class SampleService:ISampleService   
{   
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)   
   {   
      return Task<string>.Factory.StartNew(() =>   
      {   
         return msg;   
      });   
   }  
   // ...  
}  
```  
  
 SampleMethodTaskAsync 作業會傳回 Task\<string>，因為邏輯作業傳回的是字串。 如需工作架構非同步模式的詳細資訊，請參閱[工作架構非同步模式](https://go.microsoft.com/fwlink/?LinkId=232504) \(英文\)。  
  
> [!WARNING]
>  使用工作架構非同步模式時，如果在等待作業完成期間發生例外狀況，則可能擲回 T:System.AggregateException。 這個例外狀況可能在用戶端或服務上發生  
  
#### <a name="event-based-asynchronous-pattern"></a>事件架構非同步模式  
 支援事件架構非同步模式的服務會有一個或多個名為 MethodNameAsync 的方法。 這些方法可能鏡像在目前執行緒上執行相同作業的同步版本。 這個類別可能也具有 MethodNameCompleted 事件，並且具有 MethodNameAsyncCancel (或簡單地說 CancelAsync) 方法。 想要呼叫作業的用戶端將會定義要在作業完成時呼叫的事件處理常式。  
  
 下列程式碼片段示範如何使用事件架構非同步模式宣告非同步作業。  
  
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
  
 如需事件架構非同步模式的詳細資訊，請參閱[事件架構非同步模式](https://go.microsoft.com/fwlink/?LinkId=232515)。  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>IAsyncResult 非同步模式  
 使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 非同步程式設計模式並使 `<Begin>` 方法的 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> 屬性設定為 `true`，即可以非同步方式實作服務作業。 在此情況下，會使用和同步作業相同的形式，在中繼資料中公開非同步作業：非同步作業會公開為具有要求訊息和相關聯之回應訊息的單一作業。 用戶端程式設計模型接著就會做出選擇。 只要在叫用服務時發生要求/回應訊息交換，這些程式設計模型就會將此模式表示為同步作業或非同步作業。  
  
 一般而言，基於系統的非同步本質，您不應該相依於執行緒。  將資料傳遞至作業分派處理之各種階段最可靠的方式就是使用延伸模組。  
  
 如需範例，請參閱[如何：實作非同步服務作業](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)。  
  
 若不管在用戶端應用程式中呼叫合約作業的方式，而要定義以非同步方式執行的合約作業 `X`：  
  
-   使用模式 `BeginOperation` 和 `EndOperation` 定義兩種方法。  
  
-   `BeginOperation` 方法包含用於作業的 `in` 和 `ref` 參數，並會傳回 <xref:System.IAsyncResult> 型別。  
  
-   `EndOperation` 方法包含 <xref:System.IAsyncResult> 參數、`out` 和 `ref` 參數，並會傳回作業的傳回型別。  
  
 以下列方法為例：  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 若要建立非同步作業，這兩個方法將會：  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationContractAttribute> 屬性只會套用至 `BeginDoWork` 方法。 產生的合約具有一個名為 `DoWork` 的 WSDL 作業。  
  
### <a name="client-side-asynchronous-invocations"></a>用戶端非同步叫用  
 WCF 用戶端應用程式可以使用前述三個非同步呼叫模型中的任何一個模型  
  
 使用工作架構模型時，只需使用 await 關鍵字呼叫作業，如下列程式碼片段所示。  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 使用事件架構非同步模式時，只需要加入事件處理常式以接收回應的通知 -- 結果事件會自動在使用者介面執行緒上引發。 若要使用此方法，請使用 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 同時指定 **/async** 和 **/tcv:Version35** 命令選項，如下列範例所示。  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 當完成時，Svcutil.exe 會產生 WCF 用戶端類別，其中的事件基礎結構能夠呼叫應用程式去實作與指派事件處理常式，以接收回應並採取適當的動作。 如需完整範例，請參閱[如何：以非同步方式呼叫服務作業](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)。  
  
 但是，事件架構非同步呼叫只能在 [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] 中使用。 此外，使用 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 建立 WCF 用戶端通道時，即使在 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 中亦不支援此呼叫。 透過 WCF 用戶端通道物件，您必須使用 <xref:System.IAsyncResult?displayProperty=nameWithType> 物件以非同步方式叫用您的作業。 若要使用此方法，請使用 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 指定 **/async** 命令選項，如下列範例所示。  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 這會產生服務合約，其中的每個作業會模型化為其 `<Begin>` 屬性會設為 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> 的 `true` 方法，和對應的 `<End>` 方法。 如需使用 <xref:System.ServiceModel.ChannelFactory%601> 的完整範例，請參閱[如何：使用通道處理站以非同步方式呼叫作業](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)。  
  
 無論何種情況下，即使是以同步方式實作服務，應用程式仍可以使用非同步方式叫用作業，而透過相同的方式，應用程式可以使用相同的模式，以非同步方式叫用本機同步方法。 實作作業的方式對用戶端來說並不重要；回應訊息送達時，其內容會分派至用戶端的非同步 <`End`> 方法，而用戶端便會擷取該資訊。  
  
### <a name="one-way-message-exchange-patterns"></a>單向訊息交換模式  
 您也可以建立非同步訊息交換模式，而在這個模式中，用戶端或服務可以不管另一端，以任何方向傳送單向作業 (這是 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> 為 `true` 的作業，而且沒有相關聯的回應)  (這會使用具有單向訊息的雙工訊息交換模式)。在這個情況下，服務合約會指定單向訊息交換，這表示每一端都可在適當時，選擇是否要實作為非同步呼叫或實作。 一般來說，當合約為單向訊息交換時，就可以大量地非同步實作，因為一旦傳送訊息時，應用程式不會等待回覆就可繼續執行其他工作。  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>事件架構非同步用戶端和訊息合約  
 事件架構非同步模型的設計方針指出，如果傳回多個值，則其中一個值會傳回做為 `Result` 屬性，其他值則傳回做為 <xref:System.EventArgs> 物件上的屬性。 這麼做的結果就是，如果用戶端使用事件架構非同步命令選項匯入中繼資料，且作業傳回多個值，則預設 <xref:System.EventArgs> 物件會傳回一個值做為 `Result` 屬性，而其餘則做為 <xref:System.EventArgs> 物件的屬性。  
  
 如果您要以 `Result` 屬性的形式接收訊息物件，並讓傳回值以該物件屬性的形式呈現，請使用 **/messageContract** 命令選項。 這會產生一個簽章，此簽章會將回應訊息傳回做為 `Result` 物件的 <xref:System.EventArgs> 屬性。 然後，所有的內部傳回值都成為回應訊息物件的屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
