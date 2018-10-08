---
title: 永久性雙工相互關聯
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: f2f5fe557f1f8754758d0dd9b4042cacc62cc61f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850794"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="4626a-102">永久性雙工相互關聯</span><span class="sxs-lookup"><span data-stu-id="4626a-102">Durable Duplex Correlation</span></span>
<span data-ttu-id="4626a-103">永久性雙工相互關聯也稱為回呼相互關聯，在工作流程服務需要傳送回呼至初始呼叫端時相當實用。</span><span class="sxs-lookup"><span data-stu-id="4626a-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="4626a-104">與 WCF 雙工不同的是，回呼可以在未來隨時進行，並且不受限於相同通道或通道存留期；唯一的需求是呼叫端擁有主動端點，可接聽回呼訊息。</span><span class="sxs-lookup"><span data-stu-id="4626a-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="4626a-105">如此可讓兩項工作流程服務在長時間執行的對話中彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="4626a-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="4626a-106">本主題提供永久性雙工相互關聯的概觀。</span><span class="sxs-lookup"><span data-stu-id="4626a-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="4626a-107">使用永久性雙工相互關聯</span><span class="sxs-lookup"><span data-stu-id="4626a-107">Using Durable Duplex Correlation</span></span>  
 <span data-ttu-id="4626a-108">若要使用永久性雙工相互關聯，兩項服務必須使用支援雙向作業的啟用內容繫結，例如 <xref:System.ServiceModel.NetTcpContextBinding> 或 <xref:System.ServiceModel.WSHttpContextBinding>。</span><span class="sxs-lookup"><span data-stu-id="4626a-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="4626a-109">呼叫服務會將 <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> 註冊至其用戶端 <xref:System.ServiceModel.Endpoint> 上所需的繫結。</span><span class="sxs-lookup"><span data-stu-id="4626a-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="4626a-110">接收服務會在初始呼叫中接收這項資料，然後在對呼叫服務進行回呼的 <xref:System.ServiceModel.Endpoint> 活動中，於自己的 <xref:System.ServiceModel.Activities.Send> 上使用該資料。</span><span class="sxs-lookup"><span data-stu-id="4626a-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="4626a-111">在這個範例中，兩項服務會彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="4626a-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="4626a-112">第一項服務會在第二項服務上叫用方法，然後等候回覆。</span><span class="sxs-lookup"><span data-stu-id="4626a-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="4626a-113">第二項服務知道回呼方法的名稱，但是在設計階段並不知道實作這個方法的服務端點。</span><span class="sxs-lookup"><span data-stu-id="4626a-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4626a-114">只有當端點的 <xref:System.ServiceModel.Channels.AddressingVersion> 是使用 <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A> 來設定時，才能使用永久性雙工。</span><span class="sxs-lookup"><span data-stu-id="4626a-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="4626a-115">如果不是，則<xref:System.InvalidOperationException>例外狀況會擲回下列訊息: 「 訊息包含與端點參考的回呼內容標頭[AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing)。</span><span class="sxs-lookup"><span data-stu-id="4626a-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="4626a-116">只有當 AddressingVersion 設定為 'WSAddressing10' 時，會傳送回呼內容。</span><span class="sxs-lookup"><span data-stu-id="4626a-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="4626a-117">下列範例會裝載工作流程服務，以便使用 <xref:System.ServiceModel.Endpoint> 來建立回呼 <xref:System.ServiceModel.WSHttpContextBinding>。</span><span class="sxs-lookup"><span data-stu-id="4626a-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
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
  
 <span data-ttu-id="4626a-118">實作此工作流程服務的工作流程會使用其 <xref:System.ServiceModel.Activities.Send> 活動初始化回呼相互關聯，並且從與 <xref:System.ServiceModel.Activities.Receive> 相互關聯的 <xref:System.ServiceModel.Activities.Send> 活動參考此回呼端點。</span><span class="sxs-lookup"><span data-stu-id="4626a-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="4626a-119">下列範例表示自 `GetWF1` 方法傳回的工作流程。</span><span class="sxs-lookup"><span data-stu-id="4626a-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
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
  
 <span data-ttu-id="4626a-120">第二項工作流程服務是使用系統提供之以內容為主的繫結進行裝載。</span><span class="sxs-lookup"><span data-stu-id="4626a-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
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
  
 <span data-ttu-id="4626a-121">實作此工作流程服務的工作流程會以 <xref:System.ServiceModel.Activities.Receive> 活動開始執行。</span><span class="sxs-lookup"><span data-stu-id="4626a-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="4626a-122">此接收活動會初始化此服務的回呼相互關聯，延遲一段時間以模擬長時間執行的工作，然後使用第一次服務呼叫中傳遞的回呼內容來回呼第一項服務。</span><span class="sxs-lookup"><span data-stu-id="4626a-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="4626a-123">下列範例表示自 `GetWF2` 的呼叫傳回的工作流程。</span><span class="sxs-lookup"><span data-stu-id="4626a-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="4626a-124">請注意，<xref:System.ServiceModel.Activities.Send> 活動有預留位置位址 `http://www.contoso.com`，在執行階段使用的實際位址是提供的回呼位址。</span><span class="sxs-lookup"><span data-stu-id="4626a-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
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
  
 <span data-ttu-id="4626a-125">在第一個工作流程上叫用 `StartOrder` 方法時，會顯示下列輸出，其中顯示兩個工作流程之間執行的流向。</span><span class="sxs-lookup"><span data-stu-id="4626a-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
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
  
 <span data-ttu-id="4626a-126">在這個範例中，兩個工作流程都會使用 <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> 明確管理相互關聯。</span><span class="sxs-lookup"><span data-stu-id="4626a-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="4626a-127">由於上述這些範例工作流程中只有單一相互關聯，因此預設的 <xref:System.ServiceModel.Activities.CorrelationHandle> 管理就已經足夠。</span><span class="sxs-lookup"><span data-stu-id="4626a-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>
