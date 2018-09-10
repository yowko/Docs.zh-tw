---
title: 中繼資料發行行為
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: c3e26454cc9b29620d80a86df7d7aee131e18200
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140303"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="677d9-102">中繼資料發行行為</span><span class="sxs-lookup"><span data-stu-id="677d9-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="677d9-103">中繼資料發行行為範例會示範如何控制服務的中繼資料發行功能。</span><span class="sxs-lookup"><span data-stu-id="677d9-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="677d9-104">若要避免不小心洩露可能含有機密的服務中繼資料，Windows Communication Foundation (WCF) 服務的預設組態會停用中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="677d9-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="677d9-105">這個行為依預設為安全行為，但也表示您無法使用中繼資料匯入工具 (例如 Svcutil.exe) 來產生呼叫服務所需的用戶端程式碼，除非組態中已明確啟用服務的中繼發行行為。</span><span class="sxs-lookup"><span data-stu-id="677d9-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="677d9-106">為了清楚說明，這個範例示範如何建立不安全的中繼資料發行端點。</span><span class="sxs-lookup"><span data-stu-id="677d9-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="677d9-107">未經驗證的匿名使用者可能可以使用這類端點，所以部署前必須小心謹慎，才能確保公開服務中繼資料是否適切。</span><span class="sxs-lookup"><span data-stu-id="677d9-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="677d9-108">請參閱[自訂安全中繼資料端點](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)範例如需保護中繼資料端點的範例。</span><span class="sxs-lookup"><span data-stu-id="677d9-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="677d9-109">此樣本根據[快速入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作`ICalculator`服務合約。</span><span class="sxs-lookup"><span data-stu-id="677d9-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="677d9-110">在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="677d9-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="677d9-111">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="677d9-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="677d9-112">為了讓服務公開中繼資料，服務上必須設定 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>。</span><span class="sxs-lookup"><span data-stu-id="677d9-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="677d9-113">當這個行為存在時，您便可以發行中繼資料，方法是將端點設定成將 <xref:System.ServiceModel.Description.IMetadataExchange> 合約當做 WS-MetadataExchange (MEX) 通訊協定的實作來進行公開。</span><span class="sxs-lookup"><span data-stu-id="677d9-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="677d9-114">為了方便起見，這個合約已經被指定成縮寫組態名稱，"IMetadataExchange"。</span><span class="sxs-lookup"><span data-stu-id="677d9-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="677d9-115">這個範例會使用 `mexHttpBinding`，這個快捷標準繫結等同於安全性模式設為 `wsHttpBinding` 的 `None`。</span><span class="sxs-lookup"><span data-stu-id="677d9-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="677d9-116">"Mex"的相對位址用於端點中，當解析服務基底位址的端點位址 http://localhost/servicemodelsamples/service.svc/mex 。</span><span class="sxs-lookup"><span data-stu-id="677d9-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span> <span data-ttu-id="677d9-117">此行為組態列出如下：</span><span class="sxs-lookup"><span data-stu-id="677d9-117">The following shows the behavior configuration:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="677d9-118">此 MEX 端點列出如下。</span><span class="sxs-lookup"><span data-stu-id="677d9-118">The following shows the MEX endpoint.</span></span>  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="677d9-119">這個範例會將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 屬性設定為 `true`，也會使用 HTTP GET 公開服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="677d9-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="677d9-120">若要啟用 HTTP GET 中繼資料端點，服務必須有 HTTP 基底位址。</span><span class="sxs-lookup"><span data-stu-id="677d9-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="677d9-121">查詢字串 `?wsdl` 會用於服務的基底位址上，以便存取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="677d9-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="677d9-122">例如，若要查看在網頁瀏覽器服務的 WSDL 您會使用位址 http://localhost/servicemodelsamples/service.svc?wsdl。</span><span class="sxs-lookup"><span data-stu-id="677d9-122">For example, to see the WSDL for the service in a Web browser you would use the address http://localhost/servicemodelsamples/service.svc?wsdl.</span></span> <span data-ttu-id="677d9-123">此外，您可以將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> 設定為 `true`，以便使用這個行為來透過 HTTPS 公開中繼資料。</span><span class="sxs-lookup"><span data-stu-id="677d9-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="677d9-124">這個作業需要 HTTPS 基底位址。</span><span class="sxs-lookup"><span data-stu-id="677d9-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="677d9-125">若要存取服務的 MEX 端點，請使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="677d9-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="677d9-126">這樣便會產生以該服務中繼資料為基礎的用戶端。</span><span class="sxs-lookup"><span data-stu-id="677d9-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="677d9-127">若要存取服務的中繼資料，使用 HTTP GET，您的瀏覽器指向 http://localhost/servicemodelsamples/service.svc?wsdl。</span><span class="sxs-lookup"><span data-stu-id="677d9-127">To access the service's metadata using HTTP GET, point your browser to http://localhost/servicemodelsamples/service.svc?wsdl.</span></span>  
  
 <span data-ttu-id="677d9-128">如果您移除這項行為並嘗試開啟服務，這時會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="677d9-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="677d9-129">這個錯誤的發生原因是如果不使用這項行為，透過 `IMetadataExchange` 合約設定的端點就不會有任何實作。</span><span class="sxs-lookup"><span data-stu-id="677d9-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="677d9-130">如果將 `HttpGetEnabled` 設定為 `false`，您就會看到 CalculatorService 說明網頁而不是服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="677d9-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="677d9-131">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="677d9-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="677d9-132">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="677d9-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="677d9-133">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="677d9-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="677d9-134">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="677d9-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="677d9-135">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="677d9-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="677d9-136">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="677d9-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="677d9-137">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="677d9-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="677d9-138">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="677d9-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a><span data-ttu-id="677d9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="677d9-139">See Also</span></span>
