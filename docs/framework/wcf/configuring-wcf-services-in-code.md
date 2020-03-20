---
title: 在程式碼中設定 WCF 服務
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 4ff49b4e17ae179426cc033a955ecf2c71f2a3e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174806"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="24e73-102">在程式碼中設定 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="24e73-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="24e73-103">Windows 通信基礎 （WCF） 允許開發人員使用設定檔或代碼佈建服務。</span><span class="sxs-lookup"><span data-stu-id="24e73-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="24e73-104">當服務需要在部署後進行設定時，組態檔非常有用。</span><span class="sxs-lookup"><span data-stu-id="24e73-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="24e73-105">使用組態檔時，IT 專業人員只需更新組態檔，不必重新編譯。</span><span class="sxs-lookup"><span data-stu-id="24e73-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="24e73-106">但是組態檔可能會很複雜而難以維護。</span><span class="sxs-lookup"><span data-stu-id="24e73-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="24e73-107">由於不支援組態檔偵錯，而且組態項目是以名稱來參考，這使得製作組態檔容易出錯且難度增加。</span><span class="sxs-lookup"><span data-stu-id="24e73-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="24e73-108">WCF 還允許您在代碼中佈建服務。</span><span class="sxs-lookup"><span data-stu-id="24e73-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="24e73-109">在早期版本的 WCF（4.0 和更早版本）中，在自託管方案中佈建服務很容易，<xref:System.ServiceModel.ServiceHost>該類允許您在調用 ServiceHost.Open 之前配置終結點和行為。</span><span class="sxs-lookup"><span data-stu-id="24e73-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="24e73-110">但是在 Web 裝載案例中，您就無法直接存取 <xref:System.ServiceModel.ServiceHost> 類別。</span><span class="sxs-lookup"><span data-stu-id="24e73-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="24e73-111">為了設定 Web 裝載服務，您需要建立會建立 `System.ServiceModel.ServiceHostFactory` 的 <xref:System.ServiceModel.Activation.ServiceHostFactory>，並執行任何所需的設定。</span><span class="sxs-lookup"><span data-stu-id="24e73-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="24e73-112">從 .NET 4.5 開始，WCF 提供了一種更簡單的方法來在代碼中配置自託管服務和 Web 託管服務。</span><span class="sxs-lookup"><span data-stu-id="24e73-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="24e73-113">Configure 方法</span><span class="sxs-lookup"><span data-stu-id="24e73-113">The Configure method</span></span>  
 <span data-ttu-id="24e73-114">只需定義名為 `Configure` 的公用靜態方法，並在您的服務實作類別中包含下列簽章：</span><span class="sxs-lookup"><span data-stu-id="24e73-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="24e73-115">Configure 方法接受可讓開發人員加入端點和行為的 <xref:System.ServiceModel.ServiceConfiguration> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="24e73-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="24e73-116">在打開服務主機之前，WCF 會調用此方法。</span><span class="sxs-lookup"><span data-stu-id="24e73-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="24e73-117">一旦定義之後，將會忽略 app.config 或 web.config 檔案中指定的任何服務組態設定。</span><span class="sxs-lookup"><span data-stu-id="24e73-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="24e73-118">下列程式碼片段說明如何定義 `Configure` 方法，以及加入服務端點、端點行為和服務行為：</span><span class="sxs-lookup"><span data-stu-id="24e73-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
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
            return $"You entered: {value}";
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
  
 <span data-ttu-id="24e73-119">若要為服務啟用通訊協定 (例如 https)，您可以明確加入使用該通訊協定的端點，或是呼叫 ServiceConfiguration.EnableProtocol(Binding) 以自動加入端點，也就是自動為每個與通訊協定相容的基底位址 (Base Address) 及所定義的每份服務合約加入端點。</span><span class="sxs-lookup"><span data-stu-id="24e73-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="24e73-120">下列程式碼示範如何使用 ServiceConfiguration.EnableProtocol 方法：</span><span class="sxs-lookup"><span data-stu-id="24e73-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
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
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```  
  
 <span data-ttu-id="24e73-121">僅當未以程式設計方式`protocolMappings`將應用程式終結點添加到中時，才會使用<>部分中的<xref:System.ServiceModel.ServiceConfiguration>設置。您可以通過調用<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>然後更改設置，從預設應用程式佈建檔中選擇載入服務配置。</span><span class="sxs-lookup"><span data-stu-id="24e73-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="24e73-122"><xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> 類別也允許您從集中式組態載入組態。</span><span class="sxs-lookup"><span data-stu-id="24e73-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="24e73-123">下列程式碼說明如何實作此作業：</span><span class="sxs-lookup"><span data-stu-id="24e73-123">The following code illustrates how to implement this:</span></span>  
  
```csharp
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
> <span data-ttu-id="24e73-124">請注意，<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>忽略<><>`host``service``system.serviceModel`標記中<>設置。</span><span class="sxs-lookup"><span data-stu-id="24e73-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="24e73-125">從概念上講`host`，<>是關於主機配置的，而不是服務配置，並且在"配置"方法執行之前載入它。</span><span class="sxs-lookup"><span data-stu-id="24e73-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e73-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24e73-126">See also</span></span>

- [<span data-ttu-id="24e73-127">使用組態檔設定服務</span><span class="sxs-lookup"><span data-stu-id="24e73-127">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="24e73-128">設定用戶端行為</span><span class="sxs-lookup"><span data-stu-id="24e73-128">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
- [<span data-ttu-id="24e73-129">簡化設定</span><span class="sxs-lookup"><span data-stu-id="24e73-129">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="24e73-130">組態</span><span class="sxs-lookup"><span data-stu-id="24e73-130">Configuration</span></span>](./samples/configuration-sample.md)
- [<span data-ttu-id="24e73-131">在 IIS 與 WAS 中以組態為基礎的啟動</span><span class="sxs-lookup"><span data-stu-id="24e73-131">Configuration-Based Activation in IIS and WAS</span></span>](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="24e73-132">組態與中繼資料支援</span><span class="sxs-lookup"><span data-stu-id="24e73-132">Configuration and Metadata Support</span></span>](./extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="24e73-133">組態</span><span class="sxs-lookup"><span data-stu-id="24e73-133">Configuration</span></span>](./diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="24e73-134">如何：在設定中指定服務繫結</span><span class="sxs-lookup"><span data-stu-id="24e73-134">How to: Specify a Service Binding in Configuration</span></span>](how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="24e73-135">HOW TO：在組態中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="24e73-135">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="24e73-136">HOW TO：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="24e73-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="24e73-137">如何：在設定中指定用戶端繫結</span><span class="sxs-lookup"><span data-stu-id="24e73-137">How to: Specify a Client Binding in Configuration</span></span>](how-to-specify-a-client-binding-in-configuration.md)
