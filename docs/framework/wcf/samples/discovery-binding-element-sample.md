---
title: 探索繫結項目範例
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: d906d9a389c50095f2af5d52e3874c3e43199e68
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45687594"
---
# <a name="discovery-binding-element-sample"></a><span data-ttu-id="701c5-102">探索繫結項目範例</span><span class="sxs-lookup"><span data-stu-id="701c5-102">Discovery Binding Element Sample</span></span>
<span data-ttu-id="701c5-103">此範例示範如何使用探索用戶端繫結項目探索服務。</span><span class="sxs-lookup"><span data-stu-id="701c5-103">This sample demonstrates how to use the discovery client binding element to discover a service.</span></span> <span data-ttu-id="701c5-104">此功能可讓開發人員將探索用戶端通道加入至其現有的用戶端通道堆疊中，讓程式設計模型變得非常直覺。</span><span class="sxs-lookup"><span data-stu-id="701c5-104">This feature enables developers to add a discovery client channel to their existing client channel stack, making the programming model very intuitive.</span></span> <span data-ttu-id="701c5-105">開啟相關聯的通道時，就會使用探索解析服務的位址。</span><span class="sxs-lookup"><span data-stu-id="701c5-105">When the associated channel is opened, the address of the service is resolved using discovery.</span></span> <span data-ttu-id="701c5-106">這個範例包含下列專案：</span><span class="sxs-lookup"><span data-stu-id="701c5-106">This sample consists of the following projects:</span></span>  
  
-   <span data-ttu-id="701c5-107">**CalculatorService**： 可探索的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="701c5-107">**CalculatorService**: A discoverable WCF service.</span></span>  
  
-   <span data-ttu-id="701c5-108">**CalculatorClient**： 使用探索用戶端通道搜尋與呼叫 CalculatorService 的 WCF 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="701c5-108">**CalculatorClient**: A WCF client application that uses the discovery client channel to search for and call the CalculatorService.</span></span>  
  
-   <span data-ttu-id="701c5-109">**DynamicCalculatorClient**： 使用動態端點搜尋與呼叫 CalculatorService 的 WCF 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="701c5-109">**DynamicCalculatorClient**: A WCF client application that uses a dynamic endpoint to search for and call the CalculatorService.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="701c5-110">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="701c5-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="701c5-111">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="701c5-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="701c5-112">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="701c5-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="701c5-113">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="701c5-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a><span data-ttu-id="701c5-114">CalculatorService</span><span class="sxs-lookup"><span data-stu-id="701c5-114">CalculatorService</span></span>  
 <span data-ttu-id="701c5-115">此專案包含實作 `ICalculatorService` 合約的簡易計算機服務。</span><span class="sxs-lookup"><span data-stu-id="701c5-115">This project contains a simple calculator service that implements the `ICalculatorService` contract.</span></span>  
  
 <span data-ttu-id="701c5-116">以下的 App.config 檔案用來在服務行為以及探索端點中加入 `<serviceDiscovery>` 行為。</span><span class="sxs-lookup"><span data-stu-id="701c5-116">The following App.config file is used to add a `<serviceDiscovery>` behavior in the service behaviors as well as the discovery endpoint.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">  
        <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <!--Enable discovery through configuration.-->  
      <serviceBehaviors>  
        <behavior name="CalculatorBehavior">  
          <serviceDiscovery>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="701c5-117">這會讓服務及其端點變成可搜尋。</span><span class="sxs-lookup"><span data-stu-id="701c5-117">This makes the service and its endpoints discoverable.</span></span> <span data-ttu-id="701c5-118">CalculatorService 是一個自我裝載的服務，此服務會使用 NetTcpBinding binding 加入一個端點。</span><span class="sxs-lookup"><span data-stu-id="701c5-118">The CalculatorService is a self-hosted service that adds one endpoint using the NetTcpBinding binding.</span></span> <span data-ttu-id="701c5-119">它也會將 `EndpointDiscoveryBehavior` 加入至端點並指定範圍，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="701c5-119">It also adds an `EndpointDiscoveryBehavior` to the endpoint and specifies a scope as shown in the following code.</span></span>  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a><span data-ttu-id="701c5-120">CalculatorClient</span><span class="sxs-lookup"><span data-stu-id="701c5-120">CalculatorClient</span></span>  
 <span data-ttu-id="701c5-121">此專案包含將訊息傳送至 CalculatorService 的用戶端實作。</span><span class="sxs-lookup"><span data-stu-id="701c5-121">This project contains a client implementation that sends messages to the CalculatorService.</span></span> <span data-ttu-id="701c5-122">此程式會使用 `CreateCustomBindingWithDiscoveryElement()` 方法建立使用探索用戶端通道的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="701c5-122">This program uses the `CreateCustomBindingWithDiscoveryElement()` method to create a custom binding that uses the Discovery Client Channel.</span></span>  
  
```  
static CustomBinding CreateCustomBindingWithDiscoveryElement()  
 {  
      DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
            // Provide the search criteria and the endpoint over which the probe is sent  
            discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
            discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
            CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
            // Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
            // An exception is thrown if this binding element is not at the top  
            customBinding.Elements.Insert(0, discoveryBindingElement);  
  
            return customBinding; }  
```  
  
 <span data-ttu-id="701c5-123">具現化 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 之後，開發人員會指定搜尋服務時使用的準則。</span><span class="sxs-lookup"><span data-stu-id="701c5-123">After the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is instantiated, the developer specifies the criteria to use when searching for a service.</span></span> <span data-ttu-id="701c5-124">在此情況下，探索尋找準則為 `ICalculatorService` 類型。</span><span class="sxs-lookup"><span data-stu-id="701c5-124">In this case, the discovery find criterion is the `ICalculatorService` type.</span></span> <span data-ttu-id="701c5-125">此外，開發人員會指定 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>，以傳回指定搜尋服務之位置的 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="701c5-125">Additionally, the developer specifies a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> which returns a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> that specifies where to look for the services.</span></span> <span data-ttu-id="701c5-126"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> 會傳回新的 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="701c5-126">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> returns a new <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span></span> <span data-ttu-id="701c5-127">如需詳細資訊，請參閱 <<c0> [ 使用具有探索用戶端通道的自訂繫結](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md)。</span><span class="sxs-lookup"><span data-stu-id="701c5-127">For more information, see [Using a Custom Binding with the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span></span>  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
    // to the DiscoveryClientBindingElement. The Discovery ClientChannel   
    // uses this endpoint to send Probe message.  
    public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
    {  
        public override DiscoveryEndpoint GetDiscoveryEndpoint()  
        {  
            return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
        }  
    }  
```  
  
 <span data-ttu-id="701c5-128">在此情況下，用戶端會使用探索通訊協定所定義的 UDP 多點傳送機制搜尋區域子網路上的服務。</span><span class="sxs-lookup"><span data-stu-id="701c5-128">In this case, the client uses the UDP multicast mechanism defined by the Discovery protocol to search for services on the local subnet.</span></span> <span data-ttu-id="701c5-129">方法的其他部分會建立自訂繫結，並將探索繫結項目插入堆疊頂端。</span><span class="sxs-lookup"><span data-stu-id="701c5-129">The remainder of the method creates a custom binding and inserts the Discovery binding element at the top of the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="701c5-130"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 必須放在繫結堆疊的頂端。</span><span class="sxs-lookup"><span data-stu-id="701c5-130">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must be placed on the top of the binding stack.</span></span> <span data-ttu-id="701c5-131"><xref:System.ServiceModel.Channels.BindingElement> 頂端的任何 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 都必須確認它所建立的通道處理站或通道沒有使用 `EndpointAddress` 或 `Via` 屬性，因為實際位址只會在探索用戶端通道找到。</span><span class="sxs-lookup"><span data-stu-id="701c5-131">Any <xref:System.ServiceModel.Channels.BindingElement> on top of <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the channel factory or channel it creates does not use the `EndpointAddress` or `Via` properties, because the actual address is found only at the Discovery client channel.</span></span>  
  
 <span data-ttu-id="701c5-132">接著，`CalculatorClient` 可以透過傳入這個自訂繫結以及端點位址來進行具現化。</span><span class="sxs-lookup"><span data-stu-id="701c5-132">Next, the `CalculatorClient` can be instantiated by passing in this custom binding as well as an endpoint address.</span></span>  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 <span data-ttu-id="701c5-133">使用探索用戶端通道時，會傳入先前指定的固定端點位址。</span><span class="sxs-lookup"><span data-stu-id="701c5-133">When using the Discovery Client Channel, the constant endpoint address specified previously is passed in.</span></span> <span data-ttu-id="701c5-134">現在探索用戶端通道會在執行階段尋找由尋找準則所指定的服務並進行連接。</span><span class="sxs-lookup"><span data-stu-id="701c5-134">Now at runtime, the Discovery Client Channel finds the service specified by the find criteria and connects to it.</span></span> <span data-ttu-id="701c5-135">若要讓服務和用戶端建立連接，它們必須擁有相同的基礎繫結堆疊。</span><span class="sxs-lookup"><span data-stu-id="701c5-135">For the service and the client to establish a connection, they must also have the same underlying binding stack.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="701c5-136">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="701c5-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="701c5-137">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="701c5-137">Open the solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="701c5-138">建置方案。</span><span class="sxs-lookup"><span data-stu-id="701c5-138">Build the solution.</span></span>  
  
3.  <span data-ttu-id="701c5-139">執行服務應用程式以及每個用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="701c5-139">Run the service application and each of the client applications.</span></span>  
  
4.  <span data-ttu-id="701c5-140">請注意，用戶端不需知道位址，就能找到此服務。</span><span class="sxs-lookup"><span data-stu-id="701c5-140">Observe that the client was able to find the service without knowing its address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="701c5-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="701c5-141">See Also</span></span>
