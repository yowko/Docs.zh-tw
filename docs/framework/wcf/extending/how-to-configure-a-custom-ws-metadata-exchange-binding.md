---
title: HOW TO：設定自訂 WS-Metadata Exchange 繫結
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 51681e258e6a21b3a7ae604d1c0ef65d320bfb4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311873"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="c1b3d-102">HOW TO：設定自訂 WS-Metadata Exchange 繫結</span><span class="sxs-lookup"><span data-stu-id="c1b3d-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="c1b3d-103">本主題說明如何設定自訂的 WS-Metadata Exchange 繫結。</span><span class="sxs-lookup"><span data-stu-id="c1b3d-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="c1b3d-104">Windows Communication Foundation (WCF) 包含四個系統定義的中繼資料繫結，但您可以發行中繼資料使用任何您想要的繫結。</span><span class="sxs-lookup"><span data-stu-id="c1b3d-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="c1b3d-105">這個主題會告訴您如何使用 `wsHttpBinding` 發行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c1b3d-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="c1b3d-106">這個繫結會提供讓您以安全的方法公開中繼資料的選項。</span><span class="sxs-lookup"><span data-stu-id="c1b3d-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="c1b3d-107">這篇文章中的程式碼根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="c1b3d-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="c1b3d-108">使用組態檔</span><span class="sxs-lookup"><span data-stu-id="c1b3d-108">Using a configuration file</span></span>  
  
1. <span data-ttu-id="c1b3d-109">在服務組態檔中，新增包含 `serviceMetadata` 標記的服務行為：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="c1b3d-110">將 `behaviorConfiguration` 屬性新增至參照這個新行為的服務標記：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. <span data-ttu-id="c1b3d-111">新增指定 MEX 為位址、指定 `wsHttpBinding` 為繫結，並指定 <xref:System.ServiceModel.Description.IMetadataExchange> 為合約的中繼資料端點：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="c1b3d-112">若要驗證中繼資料交換端點是否正常運作，請在用戶端組態檔中新增端點標記：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="c1b3d-113">在用戶端的 Main() 方法中，建立新的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 執行個體、將其 <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> 屬性設為 `true`、呼叫 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>，然後逐一查看傳回的中繼資料集合：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="c1b3d-114">以程式碼設定</span><span class="sxs-lookup"><span data-stu-id="c1b3d-114">Configuring by code</span></span>  
  
1. <span data-ttu-id="c1b3d-115">建立 <xref:System.ServiceModel.WSHttpBinding> 繫結執行個體：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="c1b3d-116">建立 <xref:System.ServiceModel.ServiceHost> 執行個體：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="c1b3d-117">新增服務端點，並新增 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 執行個體：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="c1b3d-118">新增中繼資料交換端點，指定稍早建立的 <xref:System.ServiceModel.WSHttpBinding>：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="c1b3d-119">若要驗證中繼資料交換端點是否正常運作，請在用戶端組態檔中新增端點標記：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="c1b3d-120">在用戶端的 Main() 方法中，建立新的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 執行個體、將 <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> 屬性設為 `true`、呼叫 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>，然後逐一查看傳回的中繼資料集合：</span><span class="sxs-lookup"><span data-stu-id="c1b3d-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c1b3d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1b3d-121">See also</span></span>

- [<span data-ttu-id="c1b3d-122">中繼資料發行行為</span><span class="sxs-lookup"><span data-stu-id="c1b3d-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="c1b3d-123">擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="c1b3d-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)
- [<span data-ttu-id="c1b3d-124">中繼資料</span><span class="sxs-lookup"><span data-stu-id="c1b3d-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="c1b3d-125">發行中繼資料</span><span class="sxs-lookup"><span data-stu-id="c1b3d-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)
- [<span data-ttu-id="c1b3d-126">發行中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="c1b3d-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
