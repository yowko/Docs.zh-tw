---
title: 簡化的組態
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249626"
---
# <a name="simplified-configuration"></a><span data-ttu-id="a4a66-102">簡化的組態</span><span class="sxs-lookup"><span data-stu-id="a4a66-102">Simplified Configuration</span></span>
<span data-ttu-id="a4a66-103">配置 Windows 通信基礎 （WCF） 服務可能是一項複雜的任務。</span><span class="sxs-lookup"><span data-stu-id="a4a66-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="a4a66-104">這項工作不但包含許多不同的選項，而且判斷需要哪些設定往往絕非易事。</span><span class="sxs-lookup"><span data-stu-id="a4a66-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="a4a66-105">雖然設定檔提高了 WCF 服務的靈活性，但它們也是許多難以發現問題的根源。</span><span class="sxs-lookup"><span data-stu-id="a4a66-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a4a66-106">能夠解決這些問題，並且提供可讓使用者降低服務組態大小與複雜度的方式。</span><span class="sxs-lookup"><span data-stu-id="a4a66-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="a4a66-107">簡化的組態</span><span class="sxs-lookup"><span data-stu-id="a4a66-107">Simplified Configuration</span></span>  
 <span data-ttu-id="a4a66-108">在 WCF 服務設定檔中，<>`system.serviceModel`部分包含託管的每個`service`服務<>元素。</span><span class="sxs-lookup"><span data-stu-id="a4a66-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="a4a66-109"><>`service`元素包含一個<>`endpoint`元素的集合，這些元素指定每個服務公開的終結點，並可以選擇一組服務行為。</span><span class="sxs-lookup"><span data-stu-id="a4a66-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="a4a66-110"><>`endpoint`元素指定終結點公開的位址、綁定和協定，以及可選的綁定配置和終結點行為。</span><span class="sxs-lookup"><span data-stu-id="a4a66-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="a4a66-111"><>`system.serviceModel`部分還包含一個<>`behaviors`元素，允許您指定服務或終結點行為。</span><span class="sxs-lookup"><span data-stu-id="a4a66-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="a4a66-112">下面的示例顯示了設定檔<>`system.serviceModel`部分。</span><span class="sxs-lookup"><span data-stu-id="a4a66-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="a4a66-113">通過刪除<>`service`元素的要求，使配置 WCF 服務變得更加容易。</span><span class="sxs-lookup"><span data-stu-id="a4a66-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="a4a66-114">如果不在<>`service`節中添加`service`<>節或添加任何終結點，並且服務未以程式設計方式定義任何終結點，則會自動將一組預設終結點添加到服務中，每個服務基底位址和服務實現的每個協定都添加一個終結點。</span><span class="sxs-lookup"><span data-stu-id="a4a66-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="a4a66-115">每一個端點中的端點位置都會對應至基底位址，繫結是由基底位址配置所決定，而合約則是服務實作的合約。</span><span class="sxs-lookup"><span data-stu-id="a4a66-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="a4a66-116">如果您不需要指定任何端點或服務行為，或是進行任何繫結設定變更，就不需要指定服務組態檔。</span><span class="sxs-lookup"><span data-stu-id="a4a66-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="a4a66-117">如果服務實作兩個合約，而且主機同時啟用 HTTP 和 TCP 傳輸，服務主機就會建立四個預設端點，使用各個傳輸的每一個合約都會有一個端點。</span><span class="sxs-lookup"><span data-stu-id="a4a66-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="a4a66-118">若要建立預設端點，服務主機必須知道要使用哪些繫結。</span><span class="sxs-lookup"><span data-stu-id="a4a66-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="a4a66-119">這些設置在<>`protocolMappings``system.serviceModel`節中的<>部分中指定。</span><span class="sxs-lookup"><span data-stu-id="a4a66-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="a4a66-120"><>`protocolMappings`部分包含映射到綁定類型的傳輸協議方案的清單。</span><span class="sxs-lookup"><span data-stu-id="a4a66-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="a4a66-121">服務主機會使用傳遞至主機本身的基底位址判斷要使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="a4a66-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="a4a66-122">下面的示例使用<>`protocolMappings`元素。</span><span class="sxs-lookup"><span data-stu-id="a4a66-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a4a66-123">變更預設組態項目 (例如繫結或行為) 可能會影響定義於組態階層架構中較低層級的服務，因為它們可能會使用這些預設繫結和行為。</span><span class="sxs-lookup"><span data-stu-id="a4a66-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="a4a66-124">因此，變更預設繫結和行為的所有人員都必須注意，這些變更可能會影響階層中的其他服務。</span><span class="sxs-lookup"><span data-stu-id="a4a66-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4a66-125">Internet Information Services (IIS) 或 Windows 處理序啟用服務 (WAS) 底下裝載的服務會使用虛擬目錄做為其基底位址。</span><span class="sxs-lookup"><span data-stu-id="a4a66-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="a4a66-126">在上面的範例中，基底位址開頭為 "http" 配置的端點會使用 <xref:System.ServiceModel.BasicHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="a4a66-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="a4a66-127">基底位置開頭為 "net.tcp" 配置的端點則會使用 <xref:System.ServiceModel.NetTcpBinding>。</span><span class="sxs-lookup"><span data-stu-id="a4a66-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="a4a66-128">您可以覆寫本機 App.config 或 Web.config 檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="a4a66-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="a4a66-129"><>`protocolMappings`部分中的每個元素必須指定方案和綁定。</span><span class="sxs-lookup"><span data-stu-id="a4a66-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="a4a66-130">或者，它可以指定一個`bindingConfiguration`屬性，該屬性在設定檔的<>`bindings`部分中指定綁定配置。</span><span class="sxs-lookup"><span data-stu-id="a4a66-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="a4a66-131">如果未指定 `bindingConfiguration`，則會使用適當繫結型別的匿名繫結組態。</span><span class="sxs-lookup"><span data-stu-id="a4a66-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="a4a66-132">通過使用<>`behavior``serviceBehaviors`節中的匿名<>部分，為預設終結點佈建服務行為。</span><span class="sxs-lookup"><span data-stu-id="a4a66-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="a4a66-133"><>`serviceBehaviors`中任何`behavior`未命名的<>元素都用於佈建服務行為。</span><span class="sxs-lookup"><span data-stu-id="a4a66-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="a4a66-134">例如，下列組態檔會啟用主機內所有服務的服務中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="a4a66-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
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
  
 <span data-ttu-id="a4a66-135">終結點行為通過使用<>`behavior``serviceBehaviors`節中的匿名<>部分進行配置。</span><span class="sxs-lookup"><span data-stu-id="a4a66-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="a4a66-136">下列範例的組態檔相當於本主題開頭的組態檔，使用的是簡化的組態模型。</span><span class="sxs-lookup"><span data-stu-id="a4a66-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
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
> <span data-ttu-id="a4a66-137">此功能只涉及 WCF 服務組態，不是用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="a4a66-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="a4a66-138">大多數時候，WCF 用戶端組態會以 svcutil.exe 之類的工具產生，或從 Visual Studio 新增服務參考。</span><span class="sxs-lookup"><span data-stu-id="a4a66-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="a4a66-139">如果要手動設定 WCF 用戶端，則需要向配置中添加\<用戶端>元素，並指定要調用的任何終結點。</span><span class="sxs-lookup"><span data-stu-id="a4a66-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a66-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4a66-140">See also</span></span>

- [<span data-ttu-id="a4a66-141">使用組態檔設定服務</span><span class="sxs-lookup"><span data-stu-id="a4a66-141">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="a4a66-142">設定服務的繫結</span><span class="sxs-lookup"><span data-stu-id="a4a66-142">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="a4a66-143">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a4a66-143">Configuring System-Provided Bindings</span></span>](./feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a4a66-144">設定服務</span><span class="sxs-lookup"><span data-stu-id="a4a66-144">Configuring Services</span></span>](configuring-services.md)
- [<span data-ttu-id="a4a66-145">配置 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="a4a66-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="a4a66-146">在程式碼中設定 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="a4a66-146">Configuring WCF Services in Code</span></span>](configuring-wcf-services-in-code.md)
