---
title: "在程式碼中設定 WCF 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 202214a6c9279eb61db560321a8f36943ce5d635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="91527-102">在程式碼中設定 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="91527-102">Configuring WCF Services in Code</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="91527-103"> 可讓開發人員使用組態檔或程式碼來設定服務。</span><span class="sxs-lookup"><span data-stu-id="91527-103"> allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="91527-104">當服務需要在部署後進行設定時，組態檔非常有用。</span><span class="sxs-lookup"><span data-stu-id="91527-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="91527-105">使用組態檔時，IT 專業人員只需更新組態檔，不必重新編譯。</span><span class="sxs-lookup"><span data-stu-id="91527-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="91527-106">但是組態檔可能會很複雜而難以維護。</span><span class="sxs-lookup"><span data-stu-id="91527-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="91527-107">由於不支援組態檔偵錯，而且組態項目是以名稱來參考，這使得製作組態檔容易出錯且難度增加。</span><span class="sxs-lookup"><span data-stu-id="91527-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="91527-108"> 也允許您以程式碼來設定服務。</span><span class="sxs-lookup"><span data-stu-id="91527-108"> also allows you to configure services in code.</span></span> <span data-ttu-id="91527-109">在舊版 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 及更早版本) 的在自我裝載案例中，您可以輕鬆使用程式碼來設定服務，因為 <xref:System.ServiceModel.ServiceHost> 類別可讓您在呼叫 ServiceHost.Open 之前設定端點和行為。</span><span class="sxs-lookup"><span data-stu-id="91527-109">In earlier versions of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="91527-110">但是在 Web 裝載案例中，您就無法直接存取 <xref:System.ServiceModel.ServiceHost> 類別。</span><span class="sxs-lookup"><span data-stu-id="91527-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="91527-111">為了設定 Web 裝載服務，您需要建立會建立 `System.ServiceModel.ServiceHostFactory` 的 <xref:System.ServiceModel.Activation.ServiceHostFactory>，並執行任何所需的設定。</span><span class="sxs-lookup"><span data-stu-id="91527-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="91527-112">從 .NET 4.5 開始，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 提供了更簡單的方法，以程式碼來設定自我裝載和 Web 裝載服務。</span><span class="sxs-lookup"><span data-stu-id="91527-112">Starting with .NET 4.5, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="91527-113">Configure 方法</span><span class="sxs-lookup"><span data-stu-id="91527-113">The Configure method</span></span>  
 <span data-ttu-id="91527-114">只需定義名為 `Configure` 的公用靜態方法，並在您的服務實作類別中包含下列簽章：</span><span class="sxs-lookup"><span data-stu-id="91527-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="91527-115">Configure 方法接受可讓開發人員加入端點和行為的 <xref:System.ServiceModel.ServiceConfiguration> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="91527-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="91527-116">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 會在服務主機開啟之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="91527-116">This method is called by [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] before the service host is opened.</span></span> <span data-ttu-id="91527-117">一旦定義之後，將會忽略 app.config 或 web.config 檔案中指定的任何服務組態設定。</span><span class="sxs-lookup"><span data-stu-id="91527-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="91527-118">下列程式碼片段說明如何定義 `Configure` 方法，以及加入服務端點、端點行為和服務行為：</span><span class="sxs-lookup"><span data-stu-id="91527-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return string.Format("You entered: {0}", value);  
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 <span data-ttu-id="91527-119">若要為服務啟用通訊協定 (例如 https)，您可以明確加入使用該通訊協定的端點，或是呼叫 ServiceConfiguration.EnableProtocol(Binding) 以自動加入端點，也就是自動為每個與通訊協定相容的基底位址 (Base Address) 及所定義的每份服務合約加入端點。</span><span class="sxs-lookup"><span data-stu-id="91527-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="91527-120">下列程式碼示範如何使用 ServiceConfiguration.EnableProtocol 方法：</span><span class="sxs-lookup"><span data-stu-id="91527-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <span data-ttu-id="91527-121">在 設定 <`protocolMappings`> 區段只有在任何應用程式端點會加入至<xref:System.ServiceModel.ServiceConfiguration>以程式設計的方式。您可以選擇性地服務組態從載入預設應用程式組態檔藉由呼叫<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>然後變更設定。</span><span class="sxs-lookup"><span data-stu-id="91527-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="91527-122"><xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> 類別也允許您從集中式組態載入組態。</span><span class="sxs-lookup"><span data-stu-id="91527-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="91527-123">下列程式碼說明如何實作此作業：</span><span class="sxs-lookup"><span data-stu-id="91527-123">The following code illustrates how to implement this:</span></span>  
  
```  
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="91527-124">請注意，<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>會忽略 <`host`> 中的設定 <`service`> 標記 <`system.serviceModel`>。</span><span class="sxs-lookup"><span data-stu-id="91527-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="91527-125">就概念而言，<`host`> 主應用程式組態、 沒有服務組態和它的設定方法執行之前取得已載入。</span><span class="sxs-lookup"><span data-stu-id="91527-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91527-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="91527-126">See Also</span></span>  
 [<span data-ttu-id="91527-127">使用設定檔設定服務</span><span class="sxs-lookup"><span data-stu-id="91527-127">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="91527-128">設定用戶端行為</span><span class="sxs-lookup"><span data-stu-id="91527-128">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="91527-129">簡化設定</span><span class="sxs-lookup"><span data-stu-id="91527-129">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="91527-130">以組態為基礎的啟用</span><span class="sxs-lookup"><span data-stu-id="91527-130">Configuration-Based Activation</span></span>](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [<span data-ttu-id="91527-131">組態</span><span class="sxs-lookup"><span data-stu-id="91527-131">Configuration</span></span>](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [<span data-ttu-id="91527-132">IIS 和 WAS 中以組態為基礎的啟用</span><span class="sxs-lookup"><span data-stu-id="91527-132">Configuration-Based Activation in IIS and WAS</span></span>](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [<span data-ttu-id="91527-133">組態與中繼資料支援</span><span class="sxs-lookup"><span data-stu-id="91527-133">Configuration and Metadata Support</span></span>](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [<span data-ttu-id="91527-134">組態</span><span class="sxs-lookup"><span data-stu-id="91527-134">Configuration</span></span>](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [<span data-ttu-id="91527-135">如何：在設定中指定服務繫結</span><span class="sxs-lookup"><span data-stu-id="91527-135">How to: Specify a Service Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [<span data-ttu-id="91527-136">如何：在組態中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="91527-136">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [<span data-ttu-id="91527-137">如何：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="91527-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="91527-138">如何：在設定中指定用戶端繫結</span><span class="sxs-lookup"><span data-stu-id="91527-138">How to: Specify a Client Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
