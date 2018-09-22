---
title: 永久性雙工相互關聯
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: 82c052ff87eb8b125dfc64e1567dbd00d255894d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46699179"
---
# <a name="durable-duplex-correlation"></a>永久性雙工相互關聯
永久性雙工相互關聯也稱為回呼相互關聯，在工作流程服務需要傳送回呼至初始呼叫端時相當實用。 與 WCF 雙工不同的是，回呼可以在未來隨時進行，並且不受限於相同通道或通道存留期；唯一的需求是呼叫端擁有主動端點，可接聽回呼訊息。 如此可讓兩項工作流程服務在長時間執行的對話中彼此通訊。 本主題提供永久性雙工相互關聯的概觀。  
  
## <a name="using-durable-duplex-correlation"></a>使用永久性雙工相互關聯  
 若要使用永久性雙工相互關聯，兩項服務必須使用支援雙向作業的啟用內容繫結，例如 <xref:System.ServiceModel.NetTcpContextBinding> 或 <xref:System.ServiceModel.WSHttpContextBinding>。 呼叫服務會將 <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> 註冊至其用戶端 <xref:System.ServiceModel.Endpoint> 上所需的繫結。 接收服務會在初始呼叫中接收這項資料，然後在對呼叫服務進行回呼的 <xref:System.ServiceModel.Endpoint> 活動中，於自己的 <xref:System.ServiceModel.Activities.Send> 上使用該資料。 在這個範例中，兩項服務會彼此通訊。 第一項服務會在第二項服務上叫用方法，然後等候回覆。 第二項服務知道回呼方法的名稱，但是在設計階段並不知道實作這個方法的服務端點。  
  
> [!NOTE]
> 只有當端點的 <xref:System.ServiceModel.Channels.AddressingVersion> 是使用 <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A> 來設定時，才能使用永久性雙工。 如果不是，則<xref:System.InvalidOperationException>例外狀況會擲回下列訊息: 「 訊息包含與端點參考的回呼內容標頭[AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing)。 只有當 AddressingVersion 設定為 'WSAddressing10' 時，會傳送回呼內容。
  
 下列範例會裝載工作流程服務，以便使用 <xref:System.ServiceModel.Endpoint> 來建立回呼 <xref:System.ServiceModel.WSHttpContextBinding>。  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 實作此工作流程服務的工作流程會使用其 <xref:System.ServiceModel.Activities.Send> 活動初始化回呼相互關聯，並且從與 <xref:System.ServiceModel.Activities.Receive> 相互關聯的 <xref:System.ServiceModel.Activities.Send> 活動參考此回呼端點。 下列範例表示自 `GetWF1` 方法傳回的工作流程。  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =   
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")                          
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 第二項工作流程服務是使用系統提供之以內容為主的繫結進行裝載。  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 實作此工作流程服務的工作流程會以 <xref:System.ServiceModel.Activities.Receive> 活動開始執行。 此接收活動會初始化此服務的回呼相互關聯，延遲一段時間以模擬長時間執行的工作，然後使用第一次服務呼叫中傳遞的回呼內容來回呼第一項服務。 下列範例表示自 `GetWF2` 的呼叫傳回的工作流程。 請注意，<xref:System.ServiceModel.Activities.Send> 活動有預留位置位址 `http://www.contoso.com`，在執行階段使用的實際位址是提供的回呼位址。  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =   
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 在第一個工作流程上叫用 `StartOrder` 方法時，會顯示下列輸出，其中顯示兩個工作流程之間執行的流向。  
  
```Output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.   
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 在這個範例中，兩個工作流程都會使用 <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> 明確管理相互關聯。 由於上述這些範例工作流程中只有單一相互關聯，因此預設的 <xref:System.ServiceModel.Activities.CorrelationHandle> 管理就已經足夠。  
  
## <a name="see-also"></a>另請參閱  
 [永久性雙工&#91;WF 範例&#93;](../../../../docs/framework/windows-workflow-foundation/samples/durable-duplex.md)
