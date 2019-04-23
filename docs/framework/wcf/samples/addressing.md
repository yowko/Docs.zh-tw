---
title: 定址
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: a59c3b354404169c2baadd4ab8c2702728d9a891
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767977"
---
# <a name="addressing"></a><span data-ttu-id="310e4-102">定址</span><span class="sxs-lookup"><span data-stu-id="310e4-102">Addressing</span></span>
<span data-ttu-id="310e4-103">此定址範例會示範端點位址的各方面與功能。</span><span class="sxs-lookup"><span data-stu-id="310e4-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="310e4-104">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="310e4-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="310e4-105">在此範例中的服務會自動裝載。</span><span class="sxs-lookup"><span data-stu-id="310e4-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="310e4-106">服務和用戶端都是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="310e4-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="310e4-107">服務會定義使用相對與絕對端點位址組合的多個端點。</span><span class="sxs-lookup"><span data-stu-id="310e4-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="310e4-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="310e4-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="310e4-109">服務組態檔會指定基底位址與四個端點。</span><span class="sxs-lookup"><span data-stu-id="310e4-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="310e4-110">基底位址是以 service/host/baseAddresses 下的新增項目所指定，如下列範例組態中所示。</span><span class="sxs-lookup"><span data-stu-id="310e4-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 <span data-ttu-id="310e4-111">在下列範例組態中所示的第一個端點定義是指定相對位址，這表示端點位址是遵守 URI 組合規則之基底位址與相對位址的組合。</span><span class="sxs-lookup"><span data-stu-id="310e4-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="310e4-112">在此範例中，相對位址是空白的 ("")，因此端點位址會與基底位址相同。</span><span class="sxs-lookup"><span data-stu-id="310e4-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="310e4-113">實際的端點位址是`http://localhost:8000/servicemodelsamples/service`。</span><span class="sxs-lookup"><span data-stu-id="310e4-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="310e4-114">第二個端點定義也是指定相對位址，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="310e4-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="310e4-115">此相對位址 "test" 會附加在基底位址。</span><span class="sxs-lookup"><span data-stu-id="310e4-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="310e4-116">實際的端點位址是`http://localhost:8000/servicemodelsamples/service/test`。</span><span class="sxs-lookup"><span data-stu-id="310e4-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="310e4-117">第三個端點定義是指定絕對位址，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="310e4-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="310e4-118">位址中不需要基底位址。</span><span class="sxs-lookup"><span data-stu-id="310e4-118">The base address plays no role in the address.</span></span> <span data-ttu-id="310e4-119">實際的端點位址是`http://localhost:8001/hello/servicemodelsamples`。</span><span class="sxs-lookup"><span data-stu-id="310e4-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="310e4-120">第四個端點位址是指定絕對位址以及不同的傳輸 (TCP)。</span><span class="sxs-lookup"><span data-stu-id="310e4-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="310e4-121">位址中不需要基底位址。</span><span class="sxs-lookup"><span data-stu-id="310e4-121">The base address plays no role in the address.</span></span> <span data-ttu-id="310e4-122">實際的端點位址是`net.tcp://localhost:9000/servicemodelsamples/service`。</span><span class="sxs-lookup"><span data-stu-id="310e4-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 <span data-ttu-id="310e4-123">用戶端只會存取這四種服務端點的其中一個，但是這四種端點都會定義在其組態檔中。</span><span class="sxs-lookup"><span data-stu-id="310e4-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="310e4-124">用戶端會在建立 `CalculatorProxy` 物件時選取端點。</span><span class="sxs-lookup"><span data-stu-id="310e4-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="310e4-125">透過變更從 `CalculatorEndpoint1` 到 `CalculatorEndpoint4` 的組態名稱，您便可以執行其中每一個端點。</span><span class="sxs-lookup"><span data-stu-id="310e4-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="310e4-126">當您執行範例時，服務會列舉其每個端點的位址、繫結名稱與合約名稱。</span><span class="sxs-lookup"><span data-stu-id="310e4-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="310e4-127">中繼資料交換 (MEX) 端點對 ServiceHost 而言只是另一個端點，因此它會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="310e4-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="310e4-128">當您執行用戶端時，作業要求和回應會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="310e4-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="310e4-129">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="310e4-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="310e4-130">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="310e4-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="310e4-131">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="310e4-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="310e4-132">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="310e4-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="310e4-133">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="310e4-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="310e4-134">如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以符合用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="310e4-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="310e4-135">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="310e4-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="310e4-136">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="310e4-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="310e4-137">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="310e4-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="310e4-138">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="310e4-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
