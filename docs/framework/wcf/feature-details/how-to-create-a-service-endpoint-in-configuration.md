---
title: "HOW TO：在組態中建立服務端點"
ms.custom: 
ms.date: 06/16/2016
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b96ccdb7e80faa35748a41947ed97f273cb330e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="e61b1-102">HOW TO：在組態中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="e61b1-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="e61b1-103">端點可讓用戶端存取 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務提供的功能。</span><span class="sxs-lookup"><span data-stu-id="e61b1-103">Endpoints provide clients with access to the functionality a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service offers.</span></span> <span data-ttu-id="e61b1-104">您可以使用相對與絕對端點位址的組合，定義一個或多個端點，如果您沒有定義任何服務端點，執行階段預設會提供一些服務端點。</span><span class="sxs-lookup"><span data-stu-id="e61b1-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="e61b1-105">本主題說明如何使用包含相對與絕對位址的組態檔來加入端點。</span><span class="sxs-lookup"><span data-stu-id="e61b1-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e61b1-106">範例</span><span class="sxs-lookup"><span data-stu-id="e61b1-106">Example</span></span>  
 <span data-ttu-id="e61b1-107">下列服務組態會指定一個基底位址與五個端點。</span><span class="sxs-lookup"><span data-stu-id="e61b1-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced  
         in .NET Framework 4. -->  
      <service  
          name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="e61b1-108">範例</span><span class="sxs-lookup"><span data-stu-id="e61b1-108">Example</span></span>  
 <span data-ttu-id="e61b1-109">基底位址會透過 `add` 項目來指定，而此項目位於 service/host/baseAddresses 底下，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e61b1-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="e61b1-110">範例</span><span class="sxs-lookup"><span data-stu-id="e61b1-110">Example</span></span>  
 <span data-ttu-id="e61b1-111">下列範例中的第一個端點定義會指定相對位址，表示端點位址是符合統一資源識別元 (URI) 撰寫規則的基底位址與相對位址組合。</span><span class="sxs-lookup"><span data-stu-id="e61b1-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="e61b1-112">相對位址為空白位址 ("")，因此端點位址與基底位址是同一個。</span><span class="sxs-lookup"><span data-stu-id="e61b1-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="e61b1-113">實際的端點位址是 http://localhost:8000/servicemodelsamples/service。</span><span class="sxs-lookup"><span data-stu-id="e61b1-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="e61b1-114">範例</span><span class="sxs-lookup"><span data-stu-id="e61b1-114">Example</span></span>  
 <span data-ttu-id="e61b1-115">第二個端點定義也是指定相對位址，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="e61b1-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="e61b1-116">此相對位址 "test" 會附加在基底位址。</span><span class="sxs-lookup"><span data-stu-id="e61b1-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="e61b1-117">實際的端點位址是 http://localhost:8000/servicemodelsamples/service/test。</span><span class="sxs-lookup"><span data-stu-id="e61b1-117">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="e61b1-118">範例</span><span class="sxs-lookup"><span data-stu-id="e61b1-118">Example</span></span>  
 <span data-ttu-id="e61b1-119">第三個端點定義是指定絕對位址，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="e61b1-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="e61b1-120">位址中不需要基底位址。</span><span class="sxs-lookup"><span data-stu-id="e61b1-120">The base address plays no role in the address.</span></span> <span data-ttu-id="e61b1-121">實際的端點位址是 http://localhost:8001/hello/servicemodelsamples。</span><span class="sxs-lookup"><span data-stu-id="e61b1-121">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="e61b1-122">範例</span><span class="sxs-lookup"><span data-stu-id="e61b1-122">Example</span></span>  
 <span data-ttu-id="e61b1-123">第四個端點位址是指定絕對位址以及不同的傳輸 (TCP)。</span><span class="sxs-lookup"><span data-stu-id="e61b1-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="e61b1-124">位址中不需要基底位址。</span><span class="sxs-lookup"><span data-stu-id="e61b1-124">The base address plays no role in the address.</span></span> <span data-ttu-id="e61b1-125">實際的端點位址是 net.tcp://localhost:9000/servicemodelsamples/service。</span><span class="sxs-lookup"><span data-stu-id="e61b1-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="e61b1-126">範例</span><span class="sxs-lookup"><span data-stu-id="e61b1-126">Example</span></span>  
 <span data-ttu-id="e61b1-127">若要使用執行階段提供的預設端點，請不要在程式碼或組態檔中指定任何服務端點。</span><span class="sxs-lookup"><span data-stu-id="e61b1-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="e61b1-128">在這個範例中，執行階段會在服務開啟時建立預設端點。</span><span class="sxs-lookup"><span data-stu-id="e61b1-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e61b1-129">預設端點、 繫結和行為，請參閱[簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e61b1-129"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```
