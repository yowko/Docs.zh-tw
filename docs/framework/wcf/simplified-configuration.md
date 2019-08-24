---
title: 簡化的組態
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: cdb5d819ce3af372ce44ee2c038556c1383acfe3
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987214"
---
# <a name="simplified-configuration"></a><span data-ttu-id="b4722-102">簡化的組態</span><span class="sxs-lookup"><span data-stu-id="b4722-102">Simplified Configuration</span></span>
<span data-ttu-id="b4722-103">設定 Windows Communication Foundation (WCF) 服務可能是一項複雜的工作。</span><span class="sxs-lookup"><span data-stu-id="b4722-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="b4722-104">這項工作不但包含許多不同的選項，而且判斷需要哪些設定往往絕非易事。</span><span class="sxs-lookup"><span data-stu-id="b4722-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="b4722-105">雖然設定檔會增加 WCF 服務的彈性, 但它們也是許多難以發現問題的來源。</span><span class="sxs-lookup"><span data-stu-id="b4722-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="b4722-106">能夠解決這些問題，並且提供可讓使用者降低服務組態大小與複雜度的方式。</span><span class="sxs-lookup"><span data-stu-id="b4722-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="b4722-107">簡化的組態</span><span class="sxs-lookup"><span data-stu-id="b4722-107">Simplified Configuration</span></span>  
 <span data-ttu-id="b4722-108">在 WCF 服務設定檔中, <`system.serviceModel`> 區段會針對每`service`個裝載的服務包含 < 的 > 元素。</span><span class="sxs-lookup"><span data-stu-id="b4722-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="b4722-109"><`service`> 元素包含 <`endpoint`> 專案的集合, 這些專案會指定為每個服務公開的端點, 以及選擇性的一組服務行為。</span><span class="sxs-lookup"><span data-stu-id="b4722-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="b4722-110"><`endpoint`> 元素會指定端點所公開的位址、系結和合約, 以及選擇性地系結設定和端點行為。</span><span class="sxs-lookup"><span data-stu-id="b4722-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="b4722-111"><`system.serviceModel`> 區段也包含 <`behaviors`的 > 元素, 可讓您指定服務或端點行為。</span><span class="sxs-lookup"><span data-stu-id="b4722-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="b4722-112">下列範例會顯示設定檔`system.serviceModel`的 < > 區段。</span><span class="sxs-lookup"><span data-stu-id="b4722-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="b4722-113">藉由移除 <`service`> 元素的需求, 讓您更輕鬆地設定 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="b4722-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="b4722-114">如果您未在 <`service` `service`> 區段中加入 < > 區段或加入任何端點, 而且您的服務不會以程式設計方式定義任何端點, 則會自動將一組預設端點新增至您的服務, 每一個服務基底位址, 以及服務所執行之每個合約的。</span><span class="sxs-lookup"><span data-stu-id="b4722-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="b4722-115">每一個端點中的端點位置都會對應至基底位址，繫結是由基底位址配置所決定，而合約則是服務實作的合約。</span><span class="sxs-lookup"><span data-stu-id="b4722-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="b4722-116">如果您不需要指定任何端點或服務行為，或是進行任何繫結設定變更，就不需要指定服務組態檔。</span><span class="sxs-lookup"><span data-stu-id="b4722-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="b4722-117">如果服務實作兩個合約，而且主機同時啟用 HTTP 和 TCP 傳輸，服務主機就會建立四個預設端點，使用各個傳輸的每一個合約都會有一個端點。</span><span class="sxs-lookup"><span data-stu-id="b4722-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="b4722-118">若要建立預設端點，服務主機必須知道要使用哪些繫結。</span><span class="sxs-lookup"><span data-stu-id="b4722-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="b4722-119">這些設定是在 [<`protocolMappings` `system.serviceModel`>] 區段內的 [< >] 區段中指定。</span><span class="sxs-lookup"><span data-stu-id="b4722-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="b4722-120"><`protocolMappings`> 區段包含對應至系結類型的傳輸通訊協定配置清單。</span><span class="sxs-lookup"><span data-stu-id="b4722-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="b4722-121">服務主機會使用傳遞至主機本身的基底位址判斷要使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="b4722-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="b4722-122">下列範例會使用 <`protocolMappings`> 元素。</span><span class="sxs-lookup"><span data-stu-id="b4722-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b4722-123">變更預設組態項目 (例如繫結或行為) 可能會影響定義於組態階層架構中較低層級的服務，因為它們可能會使用這些預設繫結和行為。</span><span class="sxs-lookup"><span data-stu-id="b4722-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="b4722-124">因此，變更預設繫結和行為的所有人員都必須注意，這些變更可能會影響階層中的其他服務。</span><span class="sxs-lookup"><span data-stu-id="b4722-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4722-125">Internet Information Services (IIS) 或 Windows 處理序啟用服務 (WAS) 底下裝載的服務會使用虛擬目錄做為其基底位址。</span><span class="sxs-lookup"><span data-stu-id="b4722-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="b4722-126">在上面的範例中，基底位址開頭為 "http" 配置的端點會使用 <xref:System.ServiceModel.BasicHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="b4722-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="b4722-127">基底位置開頭為 "net.tcp" 配置的端點則會使用 <xref:System.ServiceModel.NetTcpBinding>。</span><span class="sxs-lookup"><span data-stu-id="b4722-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="b4722-128">您可以覆寫本機 App.config 或 Web.config 檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="b4722-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="b4722-129"><`protocolMappings`> 區段中的每個元素都必須指定配置和系結。</span><span class="sxs-lookup"><span data-stu-id="b4722-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="b4722-130">您可以選擇性地指定`bindingConfiguration`屬性, 以指定設定檔的 <`bindings`> 區段內的系結設定。</span><span class="sxs-lookup"><span data-stu-id="b4722-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="b4722-131">如果未指定 `bindingConfiguration`，則會使用適當繫結型別的匿名繫結組態。</span><span class="sxs-lookup"><span data-stu-id="b4722-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="b4722-132">系統會使用 <`behavior` `serviceBehaviors`> 區段內的匿名 < > 區段, 為預設端點設定服務行為。</span><span class="sxs-lookup"><span data-stu-id="b4722-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="b4722-133">`behavior` <`serviceBehaviors`> 內任何未命名的 < > 元素, 都是用來設定服務行為。</span><span class="sxs-lookup"><span data-stu-id="b4722-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="b4722-134">例如，下列組態檔會啟用主機內所有服務的服務中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="b4722-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
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
  
 <span data-ttu-id="b4722-135">端點行為是使用 <`behavior` `serviceBehaviors`> 區段內的匿名 < > 區段來設定。</span><span class="sxs-lookup"><span data-stu-id="b4722-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="b4722-136">下列範例的組態檔相當於本主題開頭的組態檔，使用的是簡化的組態模型。</span><span class="sxs-lookup"><span data-stu-id="b4722-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> <span data-ttu-id="b4722-137">此功能只涉及 WCF 服務組態，不是用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="b4722-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="b4722-138">大多數時候，WCF 用戶端組態會以 svcutil.exe 之類的工具產生，或從 Visual Studio 新增服務參考。</span><span class="sxs-lookup"><span data-stu-id="b4722-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="b4722-139">如果您要手動設定 WCF 用戶端, 您必須將\<用戶端 > 元素新增至設定, 並指定您想要呼叫的任何端點。</span><span class="sxs-lookup"><span data-stu-id="b4722-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4722-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4722-140">See also</span></span>

- [<span data-ttu-id="b4722-141">使用設定檔設定服務</span><span class="sxs-lookup"><span data-stu-id="b4722-141">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [<span data-ttu-id="b4722-142">設定服務的繫結</span><span class="sxs-lookup"><span data-stu-id="b4722-142">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="b4722-143">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="b4722-143">Configuring System-Provided Bindings</span></span>](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b4722-144">設定服務</span><span class="sxs-lookup"><span data-stu-id="b4722-144">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)
- [<span data-ttu-id="b4722-145">設定 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="b4722-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="b4722-146">在程式碼中設定 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="b4722-146">Configuring WCF Services in Code</span></span>](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
