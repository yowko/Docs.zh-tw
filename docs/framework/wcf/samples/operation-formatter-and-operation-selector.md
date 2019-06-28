---
title: 作業格式器和作業選取器
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 06f6d3e79844f719efc33788b6ea3bd5326e736b
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424977"
---
# <a name="operation-formatter-and-operation-selector"></a>作業格式器和作業選取器
這個範例會示範如何使用 Windows Communication Foundation (WCF) 擴充性點，以允許在不同的格式，從 WCF 所預期的內容中的訊息資料。 根據預設，WCF 格式器預期方法參數包含`soap:body`項目。 此範例會示範如何實作自訂作業格式器，而這個作業格式器會剖析 HTTP GET 查詢字串中的參數資料，然後使用該資料叫用方法。  
  
 此樣本根據[快速入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作`ICalculator`服務合約。 它會示範如何將 Add、Subtract、Multiply 和 Divide 訊息變更為針對用戶端對伺服器的要求使用 HTTP GET，以及針對伺服器對用戶端的回應使用具有 POX 訊息的 HTTP POST。  
  
 為了此示範，範例提供下列各項：  
  
- `QueryStringFormatter`，會分別對用戶端和伺服器實作 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 和 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>，並處理查詢字串中的資料。  
  
- `UriOperationSelector`，會在伺服器上實作 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>，以根據 GET 要求中的作業名稱執行作業分派。  
  
- `EnableHttpGetRequestsBehavior` 端點行為 (以及對應的組態)，會將必要的作業選取器加入至執行階段。  
  
- 示範如何將新作業格式器插入至執行階段。  
  
- 在這個範例中，用戶端和服務都是主控台應用程式 (.exe)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
## <a name="key-concepts"></a>重要概念  
 `QueryStringFormatter` -作業格式器會負責將訊息轉換的參數物件陣列和訊息參數物件的陣列的 WCF 中的元件。 此轉換是透過用戶端上的 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 介面和伺服器上的 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> 介面來完成。 這些介面都可讓使用者從 `Serialize` 和 `Deserialize` 方法中取得要求和回應訊息。  
  
 在這個範例中，`QueryStringFormatter` 會實作這兩個介面，並且在用戶端和伺服器上實作。  
  
 要求：  
  
- 此範例會使用 <xref:System.ComponentModel.TypeConverter> 類別，將要求訊息中的參數資料與字串互相轉換。 如果特定型別無法使用 <xref:System.ComponentModel.TypeConverter>，則範例格式器會擲回例外狀況。  
  
- 在用戶端的 `IClientMessageFormatter.SerializeRequest` 方法中，格式器會使用適當的收件者地址來建立 URI，並將作業名稱附加為後置字元。 這個名稱會分派至伺服器上的適當作業。 接著會採用參數物件的陣列，並使用 <xref:System.ComponentModel.TypeConverter> 類別轉換的參數名稱和值，將參數資料序列化為 URI 查詢字串。 然後會將 <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> 和 <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> 屬性設定為這個 URI。 <xref:System.ServiceModel.Channels.MessageProperties> 是透過 <xref:System.ServiceModel.Channels.Message.Properties%2A> 屬性來存取。  
  
- 在伺服器的 `IDispatchMessageFormatter.DeserializeRequest` 方法中，格式器會在傳入要求訊息屬性中擷取 `Via` URI。 這個格式器會將 URI 查詢字串中的名稱/值組剖析為參數名稱和值，並使用參數名稱和值填入 (Populate) 傳遞至方法的參數陣列。 請注意，已進行作業分派，因此這個方法會忽略作業名稱後置字元。  
  
 回應：  
  
- 在這個範例中，HTTP GET 只能用於要求。 格式器會將傳送回應的職責委派給原始格式器，但已使用原始格式器來產生 XML 訊息。 這個範例的其中一個目標就是告訴您如何實作此種委派格式器。  
  
### <a name="uripathsuffixoperationselector-class"></a>UriPathSuffixOperationSelector 類別  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 介面可讓使用者實作自己的邏輯，而這是特定訊息應該分派的作業。  
  
 在這個範例中，由於作業名稱是包含在 HTTP GET URI，而非訊息的動作標頭中，因此必須在伺服器上實作 `UriPathSuffixOperationSelector` 才能選取適當的作業。 會將範例設定為僅允許不會區分大小寫的作業名稱。  
  
 `SelectOperation` 方法接著採用傳入訊息，並在其訊息屬性中查詢 `Via` URI。 該方法會從 URI 中擷取作業名稱後置字元、查閱內部表格以取得應將訊息分派至的作業名稱，然後傳回該作業名稱。  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>EnableHttpGetRequestsBehavior 類別  
 您可以透過程式設計的方法或端點行為來設定 `UriPathSuffixOperationSelector` 元件。 此範例會實作 `EnableHttpGetRequestsBehavior` 行為，而這個行為是在服務的應用程式組態檔中指定。  
  
 在伺服器上：  
  
 將 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> 設定為 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> 實作。  
  
 根據預設，WCF 會使用完全符合的位址篩選器。 傳入訊息上的 URI 包含作業名稱後置字元，後面跟著包含參數資料的查詢字串，因此端點行為也會將位址篩選條件變更為開頭相符的篩選條件。 它會使用 WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>針對此目的。  
  
### <a name="installing-operation-formatters"></a>安裝作業格式器  
 指定格式器的作業行為都是獨一無二。 預設一定會對每個作業實作一個這樣的行為，以建立所需的作業格式器。 不過，這些行為看起來就像其他作業行為，其他屬性無法識別這些行為。 若要安裝取代行為，實作必須尋找特定的格式器行為，根據預設，而且不是 WCF 型別載入器會安裝取代它，或新增相容的預設行為之後執行的行為。  
  
 在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> 之前，可以透過程式設計方式設定這些作業格式器行為，或在預設行為之後指定要執行的作業行為來設定。 不過，無法輕易地透過端點行為 (以及組態) 來設定作業格式器行為，因為行為模型不允許取代其他行為，否則會修改描述樹狀。  
  
 在用戶端上：  
  
 必須實作 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 實作，因此可將要求轉換為 HTTP GET 要求，並針對回應委派至原始格式器。 呼叫 `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` Helper 方法即可完成此動作。  
  
 這個動作必須在呼叫 `CreateChannel` 之前完成。  
  
```  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 在伺服器上：  
  
- 必須實作 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> 介面，因此可讀取 HTTP GET 要求並委派至原始格式器以撰寫回應。 呼叫相同 `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` Helper 方法以做為用戶端 (請參閱先前的程式碼範例)，即可完成此動作。  
  
- 這個動作必須在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 之前完成。 在此範例中，會顯示如何在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 之前，以手動方式修改格式器。 其他一種可達到相同目標的方法為，從 <xref:System.ServiceModel.ServiceHost> (會在開啟之前呼叫 `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior`) 衍生類別 (如需範例，請參閱裝載文件和範例)。  
  
### <a name="user-experience"></a>使用者經驗  
 在伺服器上：  
  
- 您不需要變更伺服器 `ICalculator` 實作。  
  
- 服務的 App.config 必須使用自訂 POX 繫結，而這個繫結會將 `messageVersion` 項目的 `textMessageEncoding` 屬性設定為 `None`。  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- 服務的 App.config 也必須指定自訂 `EnableHttpGetRequestsBehavior`，方法是新增至行為延伸區段之後再使用即可。  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add   
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
- 呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 之前新增作業格式器。  
  
 在用戶端上：  
  
- 您不需要變更用戶端實作。  
  
- 用戶端的 App.config 必須使用自訂 POX 繫結，而這個繫結會將 `messageVersion` 項目的 `textMessageEncoding` 屬性設定為 `None`。 與服務的某項差異為用戶端必須啟用手動定址，這樣才能修改傳出的收件者地址。  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- 用戶端的 App.config 必須指定和伺服器一樣的自訂 `EnableHttpGetRequestsBehavior`。  
  
- 呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel> 之前新增作業格式器。  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 這四個作業 (Add、Subtract、Multiply 和 Divide) 都必須成功。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3. 若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
