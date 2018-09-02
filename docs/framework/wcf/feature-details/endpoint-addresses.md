---
title: 端點位址
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: cc81e7ad45c308f5ecf476641dfd65fe47b36098
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404563"
---
# <a name="endpoint-addresses"></a><span data-ttu-id="ee397-102">端點位址</span><span class="sxs-lookup"><span data-stu-id="ee397-102">Endpoint Addresses</span></span>
<span data-ttu-id="ee397-103">每個端點都有與其相關聯的位址，以便用來找出並識別端點。</span><span class="sxs-lookup"><span data-stu-id="ee397-103">Every endpoint has an address associated with it, which is used to locate and identify the endpoint.</span></span> <span data-ttu-id="ee397-104">這個位址主要包含一個可指定端點位置的統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="ee397-104">This address consists primarily of a Uniform Resource Identifier (URI), which specifies the location of the endpoint.</span></span> <span data-ttu-id="ee397-105">在由 Windows Communication Foundation (WCF) 程式設計模型中表示端點位址<xref:System.ServiceModel.EndpointAddress>類別，其中包含選擇性<xref:System.ServiceModel.EndpointAddress.Identity%2A>屬性可讓其他端點之端點的驗證，交換訊息，以及一組選擇性的<xref:System.ServiceModel.EndpointAddress.Headers%2A>屬性，定義取用服務時所需任何其他 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="ee397-105">The endpoint address is represented in the Windows Communication Foundation (WCF) programming model by the <xref:System.ServiceModel.EndpointAddress> class, which contains an optional <xref:System.ServiceModel.EndpointAddress.Identity%2A> property that enables the authentication of the endpoint by other endpoints that exchange messages with it, and a set of optional <xref:System.ServiceModel.EndpointAddress.Headers%2A> properties, which define any other SOAP headers required to reach the service.</span></span> <span data-ttu-id="ee397-106">選擇性標頭會提供額外與更詳細的定址資訊，以便識別端點或與服務端點互動。</span><span class="sxs-lookup"><span data-stu-id="ee397-106">The optional headers provide additional and more detailed addressing information to identify or interact with the service endpoint.</span></span> <span data-ttu-id="ee397-107">端點位址會在網路上表示為 WS-Addressing 端點參考 (EPR)。</span><span class="sxs-lookup"><span data-stu-id="ee397-107">The address of an endpoint is represented on the wire as a WS-Addressing endpoint reference (EPR).</span></span>  
  
## <a name="uri-structure-of-an-address"></a><span data-ttu-id="ee397-108">位址的 URI 結構</span><span class="sxs-lookup"><span data-stu-id="ee397-108">URI Structure of an Address</span></span>  
 <span data-ttu-id="ee397-109">大部分傳輸的位址 URI 具有四個部分。</span><span class="sxs-lookup"><span data-stu-id="ee397-109">The address URI for most transports has four parts.</span></span> <span data-ttu-id="ee397-110">例如，URI 的四個部分 http://www.fabrikam.com:322/mathservice.svc/secureEndpoint可以分項列出，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ee397-110">For example, the four parts of the URI http://www.fabrikam.com:322/mathservice.svc/secureEndpoint can be itemized as follows:</span></span>  
  
-   <span data-ttu-id="ee397-111">配置：http:</span><span class="sxs-lookup"><span data-stu-id="ee397-111">Scheme: http:</span></span>  
  
-   <span data-ttu-id="ee397-112">電腦： `www.fabrikam.com`</span><span class="sxs-lookup"><span data-stu-id="ee397-112">Machine: `www.fabrikam.com`</span></span>  
  
-   <span data-ttu-id="ee397-113">(選擇性) 連接埠：322</span><span class="sxs-lookup"><span data-stu-id="ee397-113">(optional) Port: 322</span></span>  
  
-   <span data-ttu-id="ee397-114">路徑：/mathservice.svc/secureEndpoint</span><span class="sxs-lookup"><span data-stu-id="ee397-114">Path: /mathservice.svc/secureEndpoint</span></span>  
  
## <a name="defining-an-address-for-a-service"></a><span data-ttu-id="ee397-115">定義服務的位址</span><span class="sxs-lookup"><span data-stu-id="ee397-115">Defining an Address for a Service</span></span>  
 <span data-ttu-id="ee397-116">您可以強制使用程式碼，或是透過組態以宣告的形式來指定服務的端點位址。</span><span class="sxs-lookup"><span data-stu-id="ee397-116">The endpoint address for a service can be specified either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="ee397-117">在程式碼中定義端點通常不太實用，因為部署之服務的繫結和位址通常與開發服務時所使用的繫結和位址不同。</span><span class="sxs-lookup"><span data-stu-id="ee397-117">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="ee397-118">一般來說，透過組態來定義服務端點會比透過程式碼來得實際一些。</span><span class="sxs-lookup"><span data-stu-id="ee397-118">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="ee397-119">如果將繫結和定址資訊留在程式碼外面，就可以讓您變更這些資訊，而且不需要重新編譯或重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="ee397-119">Keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
### <a name="defining-an-address-in-configuration"></a><span data-ttu-id="ee397-120">在組態中定義位址</span><span class="sxs-lookup"><span data-stu-id="ee397-120">Defining an Address in Configuration</span></span>  
 <span data-ttu-id="ee397-121">若要在組態檔中定義端點，請使用[\<端點 >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="ee397-121">To define an endpoint in a configuration file, use the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="ee397-122">如需詳細資訊和範例，請參閱 <<c0> [ 指定端點位址](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="ee397-122">For details and an example, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
### <a name="defining-an-address-in-code"></a><span data-ttu-id="ee397-123">在程式碼中定義位址</span><span class="sxs-lookup"><span data-stu-id="ee397-123">Defining an Address in Code</span></span>  
 <span data-ttu-id="ee397-124">您可以使用 <xref:System.ServiceModel.EndpointAddress> 類別，在程式碼中建立端點位址。</span><span class="sxs-lookup"><span data-stu-id="ee397-124">An endpoint address can be created in code with the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="ee397-125">如需詳細資訊和範例，請參閱 <<c0> [ 指定端點位址](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="ee397-125">For details and an example, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
### <a name="endpoints-in-wsdl"></a><span data-ttu-id="ee397-126">WSDL 中的端點</span><span class="sxs-lookup"><span data-stu-id="ee397-126">Endpoints in WSDL</span></span>  
 <span data-ttu-id="ee397-127">您也可以在對應端點的 `wsdl:port` 項目中，透過 WSDL 將端點位址表示為 WS-Addressing EPR 項目。</span><span class="sxs-lookup"><span data-stu-id="ee397-127">An endpoint address can also be represented in WSDL as a WS-Addressing EPR element inside the corresponding endpoint's `wsdl:port` element.</span></span> <span data-ttu-id="ee397-128">EPR 包含端點的位址以及任何位址屬性。</span><span class="sxs-lookup"><span data-stu-id="ee397-128">The EPR contains the endpoint's address as well as any address properties.</span></span> <span data-ttu-id="ee397-129">如需詳細資訊和範例，請參閱 <<c0> [ 指定端點位址](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="ee397-129">For details and an example, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a><span data-ttu-id="ee397-130">多個 IIS 繫結支援.NET Framework 3.5 中</span><span class="sxs-lookup"><span data-stu-id="ee397-130">Multiple IIS Binding Support in .NET Framework 3.5</span></span>  
 <span data-ttu-id="ee397-131">網際網路服務提供者通常會在相同的伺服器與網站上裝載許多應用程式，以增加網站密度並降低整體經營成本，</span><span class="sxs-lookup"><span data-stu-id="ee397-131">Internet service providers often host many applications on the same server and site to increase the site density and lower total cost of ownership.</span></span> <span data-ttu-id="ee397-132">而這些應用程式通常會繫結至不同的基底位址。</span><span class="sxs-lookup"><span data-stu-id="ee397-132">These applications are typically bound to different base addresses.</span></span> <span data-ttu-id="ee397-133">網際網路資訊服務 (IIS) 網站可以包含多個應用程式，</span><span class="sxs-lookup"><span data-stu-id="ee397-133">An Internet Information Services (IIS) Web site can contain multiple applications.</span></span> <span data-ttu-id="ee397-134">網站中的應用程式則可以透過一或多個 IIS 繫結來存取。</span><span class="sxs-lookup"><span data-stu-id="ee397-134">The applications in a site can be accessed through one or more IIS bindings.</span></span>  
  
 <span data-ttu-id="ee397-135">IIS 繫結提供繫結通訊協定和繫結這兩項資訊。</span><span class="sxs-lookup"><span data-stu-id="ee397-135">IIS bindings provide two pieces of information: a binding protocol, and binding information.</span></span> <span data-ttu-id="ee397-136">繫結通訊協定會定義產生通訊的配置，而繫結資訊則是用來存取網站的資訊。</span><span class="sxs-lookup"><span data-stu-id="ee397-136">The binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span>  
  
 <span data-ttu-id="ee397-137">下列範例示範 IIS 繫結中可能存在的元件：</span><span class="sxs-lookup"><span data-stu-id="ee397-137">The following example shows the components that can be present in an IIS binding:</span></span>  
  
-   <span data-ttu-id="ee397-138">繫結通訊協定：HTTP</span><span class="sxs-lookup"><span data-stu-id="ee397-138">Binding protocol: HTTP</span></span>  
  
-   <span data-ttu-id="ee397-139">繫結資訊：IP 位址、連接埠、主機標頭</span><span class="sxs-lookup"><span data-stu-id="ee397-139">Binding Information: IP Address, Port, Host header</span></span>  
  
 <span data-ttu-id="ee397-140">IIS 可以為每個網站指定多個繫結，讓每個配置都有多個基底位址。</span><span class="sxs-lookup"><span data-stu-id="ee397-140">IIS can specify multiple bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="ee397-141">之前[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]，WCF 會不支援多個位址的結構描述，和指定，會擲回<xref:System.ArgumentException>在啟用期間。</span><span class="sxs-lookup"><span data-stu-id="ee397-141">Prior to [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], WCF did not support multiple addresses for a schema and, if they were specified, threw a <xref:System.ArgumentException> during activation.</span></span>  
  
 <span data-ttu-id="ee397-142">[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 可讓網際網路服務提供者在同一個網站上裝載多個應用程式，而且同一個配置中可以有不同的基底位址。</span><span class="sxs-lookup"><span data-stu-id="ee397-142">The [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] enables Internet service providers to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="ee397-143">例如，網站可能包含下列基底位址：</span><span class="sxs-lookup"><span data-stu-id="ee397-143">For example, a site could contain the following base addresses:</span></span>  
  
-   http://payroll.myorg.com/Service.svc  
  
-   http://shipping.myorg.com/Service.svc  
  
 <span data-ttu-id="ee397-144">有了 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]，您就可以透過組態檔在 AppDomain 層級指定前置詞篩選條件。</span><span class="sxs-lookup"><span data-stu-id="ee397-144">With [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], you specify a prefix filter at the AppDomain level in the configuration file.</span></span> <span data-ttu-id="ee397-145">即可達到這個[ \<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)元素，其中包含的前置詞清單。</span><span class="sxs-lookup"><span data-stu-id="ee397-145">You do this with the [\<baseAddressPrefixFilters>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) element, which contains a list of prefixes.</span></span> <span data-ttu-id="ee397-146">IIS 提供的傳入基底位址會依據選擇性的前置詞清單經過篩選。</span><span class="sxs-lookup"><span data-stu-id="ee397-146">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list.</span></span> <span data-ttu-id="ee397-147">根據預設，如果沒有指定前置詞，則所有位址都會通過。</span><span class="sxs-lookup"><span data-stu-id="ee397-147">By default, when a prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="ee397-148">如果指定前置詞，則只會產生相符的基底位址讓該配置通過。</span><span class="sxs-lookup"><span data-stu-id="ee397-148">Specifying the prefix results in only the matching base address for that scheme to be passed through.</span></span>  
  
 <span data-ttu-id="ee397-149">下列示範使用前置詞篩選條件的組態程式碼。</span><span class="sxs-lookup"><span data-stu-id="ee397-149">The following is an example of configuration code that uses the prefix filters.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="ee397-150">在上述範例中，//payroll.myorg.com: 8000 和 http://shipping.myorg.com:8000會的唯一基底位址，對於其各自的結構描述，都會通過。</span><span class="sxs-lookup"><span data-stu-id="ee397-150">In the preceding example, net.tcp://payroll.myorg.com:8000 and http://shipping.myorg.com:8000 are the only base addresses, for their respective schemes, which are passed through.</span></span>  
  
 <span data-ttu-id="ee397-151">`baseAddressPrefixFilter` 不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ee397-151">The `baseAddressPrefixFilter` does not support wildcards.</span></span>  
  
 <span data-ttu-id="ee397-152">IIS 提供的基底位址可能會有繫結至其他配置，但 `baseAddressPrefixFilters` 清單中不存在的位址，</span><span class="sxs-lookup"><span data-stu-id="ee397-152">The base addresses supplied by IIS may have addresses bound to other schemes not present in `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="ee397-153">而且這些位址尚未經過篩選。</span><span class="sxs-lookup"><span data-stu-id="ee397-153">These addresses are not filtered out.</span></span>  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a><span data-ttu-id="ee397-154">.NET Framework 4 及更新版本中的多重 IIS 繫結支援</span><span class="sxs-lookup"><span data-stu-id="ee397-154">Multiple IIS Binding Support in .NET Framework 4 and later</span></span>  
 <span data-ttu-id="ee397-155">從 .NET 4 開始，您就可以將 <xref:System.ServiceModel.ServiceHostingEnvironment> 的 <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> 設定設為 true，藉以啟用 IIS 的多重繫結支援，而不需要挑選單一基底位址。</span><span class="sxs-lookup"><span data-stu-id="ee397-155">Starting in .NET 4, you can enable support for multiple bindings in IIS without having to pick a single base address, by setting <xref:System.ServiceModel.ServiceHostingEnvironment>’s <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> setting to true.</span></span> <span data-ttu-id="ee397-156">這項支援僅限 HTTP 通訊協定配置。</span><span class="sxs-lookup"><span data-stu-id="ee397-156">This support is limited to HTTP protocol schemes.</span></span>  
  
 <span data-ttu-id="ee397-157">以下是使用 multipleSiteBindingsEnabled 的組態程式碼範例[ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)。</span><span class="sxs-lookup"><span data-stu-id="ee397-157">The following is an example of configuration code that uses multipleSiteBindingsEnabled on [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="ee397-158">使用這項設定來啟用多重網站繫結時，系統會針對 HTTP 和非 HTTP 通訊協定忽略任何 baseAddressPrefixFilters 設定。</span><span class="sxs-lookup"><span data-stu-id="ee397-158">Any baseAddressPrefixFilters settings are ignored, for both HTTP and non-HTTP protocols, when multiple site bindings are enabled using this setting.</span></span>  
  
 <span data-ttu-id="ee397-159">如需詳細資訊和範例，請參閱 <<c0> [ 支援多重 IIS 網站繫結](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md)和<xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>。</span><span class="sxs-lookup"><span data-stu-id="ee397-159">For details and examples, see [Supporting Multiple IIS Site Bindings](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) and <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.</span></span>  
  
## <a name="extending-addressing-in-wcf-services"></a><span data-ttu-id="ee397-160">擴充 WCF 服務中的定址</span><span class="sxs-lookup"><span data-stu-id="ee397-160">Extending Addressing in WCF Services</span></span>  
 <span data-ttu-id="ee397-161">預設定址模型之 WCF 服務使用的端點位址 URI 用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="ee397-161">The default addressing model of WCF services uses the endpoint address URI for the following purposes:</span></span>  
  
-   <span data-ttu-id="ee397-162">指定服務接聽位址，亦即端點接聽訊息時的位置。</span><span class="sxs-lookup"><span data-stu-id="ee397-162">To specify the service listening address, the location at which the endpoint listens for messages,</span></span>  
  
-   <span data-ttu-id="ee397-163">指定 SOAP 位址篩選條件，亦即端點需要它成為 SOAP 標頭的位址。</span><span class="sxs-lookup"><span data-stu-id="ee397-163">To specify the SOAP address filter, the address an endpoint expects as a SOAP header.</span></span>  
  
 <span data-ttu-id="ee397-164">您可以針對每個用途個別指定所屬的值，充分延伸定址功能，應付各種實用情況：</span><span class="sxs-lookup"><span data-stu-id="ee397-164">The values for each of these purposes can be specified separately, allowing several extensions of addressing that cover useful scenarios:</span></span>  
  
-   <span data-ttu-id="ee397-165">SOAP 媒介：用戶端所傳送的訊息會周遊一或多個其他服務，這些服務則會在訊息抵達最後目的地之前處理訊息。</span><span class="sxs-lookup"><span data-stu-id="ee397-165">SOAP intermediaries: a message sent by a client traverses one or more additional services that process the message before it reaches its final destination.</span></span> <span data-ttu-id="ee397-166">SOAP 媒介可以執行不同的工作，例如快取、傳送、負載平衡，或是針對訊息進行結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="ee397-166">SOAP intermediaries can perform various tasks, such as caching, routing, load-balancing, or schema validation on the messages.</span></span> <span data-ttu-id="ee397-167">將要抵達媒介的訊息傳送至個別實體位址 (`via`)，而不只是傳送要抵達最終目的地的邏輯位址 (`wsa:To`)，即可完成這種情況。</span><span class="sxs-lookup"><span data-stu-id="ee397-167">This scenario is accomplished by sending messages to a separate physical address (`via`) that targets the intermediary rather than just to a logical address (`wsa:To`) that targets the ultimate destination.</span></span>  
  
-   <span data-ttu-id="ee397-168">端點的接聽位址是私用 URI，而且已設為不同於本身 `listenURI` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ee397-168">The listening address of the endpoint is a private URI and is set to a different value than its `listenURI` property.</span></span>  
  
 <span data-ttu-id="ee397-169">`via` 指定的傳輸位址，是指訊息在前往由服務所在位置 `to` 參數指定的某個其他遠端位址途中，一開始要傳送到的位置。</span><span class="sxs-lookup"><span data-stu-id="ee397-169">The transport address that the `via` specifies is the location to which a message should initially be sent on its way to some other remote address specified by the `to` parameter at which the service is located.</span></span> <span data-ttu-id="ee397-170">在網際網路用途方面，`via` URI 大多與服務最終 <xref:System.ServiceModel.EndpointAddress.Uri%2A> 位址的 `to` 屬性相同。</span><span class="sxs-lookup"><span data-stu-id="ee397-170">In most Internet scenarios, the `via` URI is the same as the <xref:System.ServiceModel.EndpointAddress.Uri%2A> property of the final `to` address of the service.</span></span> <span data-ttu-id="ee397-171">當您必須手動執行路由傳送時，才需要區分這兩個位址。</span><span class="sxs-lookup"><span data-stu-id="ee397-171">You only distinguish between these two addresses when you must do manual routing.</span></span>  
  
### <a name="addressing-headers"></a><span data-ttu-id="ee397-172">定址標頭</span><span class="sxs-lookup"><span data-stu-id="ee397-172">Addressing Headers</span></span>  
 <span data-ttu-id="ee397-173">端點除了可以由其基本 URI 定址之外，還可由一個或多個 SOAP 標頭定址。</span><span class="sxs-lookup"><span data-stu-id="ee397-173">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="ee397-174">有些情況適用這種方式，例如 SOAP 媒介，此時端點需要此端點的用戶端加入目標為媒介的 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="ee397-174">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span>  
  
 <span data-ttu-id="ee397-175">使用程式碼或組態這兩種方式的其中一種，您就可以定義自訂位址標頭：</span><span class="sxs-lookup"><span data-stu-id="ee397-175">You can define custom address headers in two ways—by using either code or configuration:</span></span>  
  
-   <span data-ttu-id="ee397-176">在程式碼中，可以使用 <xref:System.ServiceModel.Channels.AddressHeader> 類別來建立自訂位址標頭，然後用來建構 <xref:System.ServiceModel.EndpointAddress>。</span><span class="sxs-lookup"><span data-stu-id="ee397-176">In code, create custom address headers by using the <xref:System.ServiceModel.Channels.AddressHeader> class, and then used in the construction of an <xref:System.ServiceModel.EndpointAddress>.</span></span>  
  
-   <span data-ttu-id="ee397-177">在組態中，自訂[\<標頭 >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)指定為的子系[\<端點 >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)項目。</span><span class="sxs-lookup"><span data-stu-id="ee397-177">In configuration, custom [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) are specified as children of the [\<endpoint>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
 <span data-ttu-id="ee397-178">與程式碼相較之下，建議您使用組態，因為程式碼可讓您在部署後變更標頭。</span><span class="sxs-lookup"><span data-stu-id="ee397-178">Configuration is generally preferable to code, as it allows you to change the headers after deployment.</span></span>  
  
### <a name="custom-listening-addresses"></a><span data-ttu-id="ee397-179">自訂接聽位址</span><span class="sxs-lookup"><span data-stu-id="ee397-179">Custom Listening Addresses</span></span>  
 <span data-ttu-id="ee397-180">您可以將接聽位址設為端點 URI 以外的值。</span><span class="sxs-lookup"><span data-stu-id="ee397-180">You can set the listening address to a different value than the endpoint’s URI.</span></span> <span data-ttu-id="ee397-181">如果要公開的 SOAP 位址是屬於公用 SOAP 媒介的位址，而端點實際接聽的位址是私用網路位址，則這種方式就很實用。</span><span class="sxs-lookup"><span data-stu-id="ee397-181">This is useful in intermediary scenarios where the SOAP address to be exposed is that of a public SOAP intermediary, whereas the address where the endpoint actually listens is a private network address.</span></span>  
  
 <span data-ttu-id="ee397-182">您可以使用程式碼或組態來指定自訂接聽位址：</span><span class="sxs-lookup"><span data-stu-id="ee397-182">You can specify a custom listening address by using either code or configuration:</span></span>  
  
-   <span data-ttu-id="ee397-183">在程式碼中，可以將 <xref:System.ServiceModel.Description.ClientViaBehavior> 類別新增至端點的行為集合中，以指定自訂接聽位址。</span><span class="sxs-lookup"><span data-stu-id="ee397-183">In code, specify a custom listening address by adding a <xref:System.ServiceModel.Description.ClientViaBehavior> class to the endpoint’s behavior collection.</span></span>  
  
-   <span data-ttu-id="ee397-184">在組態中，指定 使用自訂接聽位址`ListenUri`的服務屬性[\<端點 >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)項目。</span><span class="sxs-lookup"><span data-stu-id="ee397-184">In configuration, specify a custom listening address with the `ListenUri` attribute of the service [\<endpoint>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
### <a name="custom-soap-address-filter"></a><span data-ttu-id="ee397-185">自訂 SOAP 位址篩選條件</span><span class="sxs-lookup"><span data-stu-id="ee397-185">Custom SOAP Address Filter</span></span>  
 <span data-ttu-id="ee397-186"><xref:System.ServiceModel.EndpointAddress.Uri%2A> 可以與任何 <xref:System.ServiceModel.EndpointAddress.Headers%2A> 屬性搭配使用，以定義端點的 SOAP 位址篩選條件 (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>)。</span><span class="sxs-lookup"><span data-stu-id="ee397-186">The <xref:System.ServiceModel.EndpointAddress.Uri%2A> is used in conjunction with any <xref:System.ServiceModel.EndpointAddress.Headers%2A> property to define an endpoint’s SOAP address filter (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>).</span></span> <span data-ttu-id="ee397-187">根據預設，這項篩選條件會確認傳入訊息所包含的 `To` 訊息標頭符合端點 URI，而且所有必要的端點標頭都出現在訊息中。</span><span class="sxs-lookup"><span data-stu-id="ee397-187">By default, this filter verifies that an incoming message has a `To` message header that matches the endpoint’s URI and that all of the required endpoint headers are present in the message.</span></span>  
  
 <span data-ttu-id="ee397-188">在某些情況中，端點會接收抵達基礎傳輸的所有訊息，而不只有包含適當 `To` 標頭的訊息。</span><span class="sxs-lookup"><span data-stu-id="ee397-188">In some scenarios, an endpoint receives all messages that arrive on the underlying transport, and not just those with the appropriate `To` header.</span></span> <span data-ttu-id="ee397-189">若要啟用這項功能，使用者可以使用 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> 類別。</span><span class="sxs-lookup"><span data-stu-id="ee397-189">To enable this, the user can use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee397-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee397-190">See Also</span></span>  
 [<span data-ttu-id="ee397-191">指定端點位址</span><span class="sxs-lookup"><span data-stu-id="ee397-191">Specifying an Endpoint Address</span></span>](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 [<span data-ttu-id="ee397-192">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="ee397-192">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
