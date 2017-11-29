---
title: "簡化的組態"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7d8fea550d0def93cf1d86b9d4a7d6b09afaf90d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="simplified-configuration"></a><span data-ttu-id="83eaa-102">簡化的組態</span><span class="sxs-lookup"><span data-stu-id="83eaa-102">Simplified Configuration</span></span>
<span data-ttu-id="83eaa-103">設定 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務可能是一個複雜的工作。</span><span class="sxs-lookup"><span data-stu-id="83eaa-103">Configuring [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services can be a complex task.</span></span> <span data-ttu-id="83eaa-104">這項工作不但包含許多不同的選項，而且判斷需要哪些設定往往絕非易事。</span><span class="sxs-lookup"><span data-stu-id="83eaa-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="83eaa-105">雖然組態檔能夠增加 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務的靈活度，但是也會造成許多不易發現的問題。</span><span class="sxs-lookup"><span data-stu-id="83eaa-105">While configuration files increase the flexibility of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="83eaa-106"> 能夠解決這些問題，並且提供可讓使用者降低服務組態大小與複雜度的方式。</span><span class="sxs-lookup"><span data-stu-id="83eaa-106"> addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="83eaa-107">簡化的組態</span><span class="sxs-lookup"><span data-stu-id="83eaa-107">Simplified Configuration</span></span>  
 <span data-ttu-id="83eaa-108">在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務組態檔中，<`system.serviceModel`> 區段會針對每一項裝載的服務包含一個 <`service`> 項目。</span><span class="sxs-lookup"><span data-stu-id="83eaa-108">In [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="83eaa-109"><`service`> 項目包含 <`endpoint`> 項目的集合，這些項目可指定對每一項服務公開的端點，以及一組選擇性的服務行為。</span><span class="sxs-lookup"><span data-stu-id="83eaa-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="83eaa-110"><`endpoint`> 項目會指定端點公開的位址、繫結和合約，以及選擇性的繫結組態和端點行為。</span><span class="sxs-lookup"><span data-stu-id="83eaa-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="83eaa-111"><`system.serviceModel`> 區段還包含 <`behaviors`> 項目，可讓您指定服務或端點行為。</span><span class="sxs-lookup"><span data-stu-id="83eaa-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="83eaa-112">下列範例顯示組態檔的 <`system.serviceModel`> 區段。</span><span class="sxs-lookup"><span data-stu-id="83eaa-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="83eaa-113"> 會透過免除對 <[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]> 項目的需求，讓設定 `service` 服務更為容易。</span><span class="sxs-lookup"><span data-stu-id="83eaa-113"> makes configuring a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="83eaa-114">如果您沒有加入 <`service`> 區段，或在 <`service`> 區段中加入任何端點，而且您的服務並未以程式設計方式定義任何端點，則會自動將一組預設端點加入至服務，而且每個服務基底位址和服務實作的每個合約都會有一個端點。</span><span class="sxs-lookup"><span data-stu-id="83eaa-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="83eaa-115">每一個端點中的端點位置都會對應至基底位址，繫結是由基底位址配置所決定，而合約則是服務實作的合約。</span><span class="sxs-lookup"><span data-stu-id="83eaa-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="83eaa-116">如果您不需要指定任何端點或服務行為，或是進行任何繫結設定變更，就不需要指定服務組態檔。</span><span class="sxs-lookup"><span data-stu-id="83eaa-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="83eaa-117">如果服務實作兩個合約，而且主機同時啟用 HTTP 和 TCP 傳輸，服務主機就會建立四個預設端點，使用各個傳輸的每一個合約都會有一個端點。</span><span class="sxs-lookup"><span data-stu-id="83eaa-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="83eaa-118">若要建立預設端點，服務主機必須知道要使用哪些繫結。</span><span class="sxs-lookup"><span data-stu-id="83eaa-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="83eaa-119">這些設定是在 <`protocolMappings`> 區段內的 <`system.serviceModel`> 區段中指定。</span><span class="sxs-lookup"><span data-stu-id="83eaa-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="83eaa-120"><`protocolMappings`> 區段包含傳輸通訊協定配置的清單，這些配置會對應至繫結型別。</span><span class="sxs-lookup"><span data-stu-id="83eaa-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="83eaa-121">服務主機會使用傳遞至主機本身的基底位址判斷要使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="83eaa-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="83eaa-122">下列範例使用 <`protocolMappings`> 項目。</span><span class="sxs-lookup"><span data-stu-id="83eaa-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="83eaa-123">變更預設組態項目 (例如繫結或行為) 可能會影響定義於組態階層架構中較低層級的服務，因為它們可能會使用這些預設繫結和行為。</span><span class="sxs-lookup"><span data-stu-id="83eaa-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="83eaa-124">因此，變更預設繫結和行為的所有人員都必須注意，這些變更可能會影響階層中的其他服務。</span><span class="sxs-lookup"><span data-stu-id="83eaa-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83eaa-125">Internet Information Services (IIS) 或 Windows 處理序啟用服務 (WAS) 底下裝載的服務會使用虛擬目錄做為其基底位址。</span><span class="sxs-lookup"><span data-stu-id="83eaa-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="83eaa-126">在上面的範例中，基底位址開頭為 "http" 配置的端點會使用 <xref:System.ServiceModel.BasicHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="83eaa-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="83eaa-127">基底位置開頭為 "net.tcp" 配置的端點則會使用 <xref:System.ServiceModel.NetTcpBinding>。</span><span class="sxs-lookup"><span data-stu-id="83eaa-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="83eaa-128">您可以覆寫本機 App.config 或 Web.config 檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="83eaa-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="83eaa-129"><`protocolMappings`> 區段內的每一個項目都必須指定配置和繫結。</span><span class="sxs-lookup"><span data-stu-id="83eaa-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="83eaa-130">每個項目也可以選擇性地指定 `bindingConfiguration` 屬性，該屬性會指定組態檔之 <`bindings`> 區段內的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="83eaa-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="83eaa-131">如果未指定 `bindingConfiguration`，則會使用適當繫結型別的匿名繫結組態。</span><span class="sxs-lookup"><span data-stu-id="83eaa-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="83eaa-132">預設端點的服務行為會使用 <`behavior`> 區段內的匿名 <`serviceBehaviors`> 區段設定。</span><span class="sxs-lookup"><span data-stu-id="83eaa-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="83eaa-133"><`behavior`> 內任何未命名的 <`serviceBehaviors`> 項目都會用來設定服務行為。</span><span class="sxs-lookup"><span data-stu-id="83eaa-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="83eaa-134">例如，下列組態檔會啟用主機內所有服務的服務中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="83eaa-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 <span data-ttu-id="83eaa-135">端點行為是使用 <`behavior`> 區段內的匿名 <`serviceBehaviors`> 區段設定。</span><span class="sxs-lookup"><span data-stu-id="83eaa-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="83eaa-136">下列範例的組態檔相當於本主題開頭的組態檔，使用的是簡化的組態模型。</span><span class="sxs-lookup"><span data-stu-id="83eaa-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <bindings>  
       <basicHttpBinding>  
          <binding maxBufferSize="100"  
                   maxReceiveBufferSize="100" />  
       </basicHttpBinding>  
    </bindings>    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->  
    <!-- The service behavior with name="" will be picked up by the service -->  
    <protocolMapping>  
      <add scheme="http"     binding="basicHttpBinding" / </protocolMapping>  
  </system.serviceModel>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="83eaa-137">此功能只涉及 WCF 服務組態，不是用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="83eaa-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="83eaa-138">大多數時候，WCF 用戶端組態會以 svcutil.exe 之類的工具產生，或從 Visual Studio 新增服務參考。</span><span class="sxs-lookup"><span data-stu-id="83eaa-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="83eaa-139">如果您要手動設定 WCF 用戶端必須新增\<用戶端 > 組態項目，並指定您想要呼叫的任何端點。</span><span class="sxs-lookup"><span data-stu-id="83eaa-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83eaa-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83eaa-140">See Also</span></span>  
 [<span data-ttu-id="83eaa-141">使用設定檔設定服務</span><span class="sxs-lookup"><span data-stu-id="83eaa-141">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="83eaa-142">設定服務的繫結</span><span class="sxs-lookup"><span data-stu-id="83eaa-142">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [<span data-ttu-id="83eaa-143">設定系統提供繫結</span><span class="sxs-lookup"><span data-stu-id="83eaa-143">Configuring System-Provided Bindings</span></span>](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="83eaa-144">設定服務</span><span class="sxs-lookup"><span data-stu-id="83eaa-144">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="83eaa-145">設定 Windows Communication Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="83eaa-145">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="83eaa-146">在程式碼中設定 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="83eaa-146">Configuring WCF Services in Code</span></span>](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
