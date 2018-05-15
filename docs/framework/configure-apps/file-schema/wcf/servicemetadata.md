---
title: '&lt;serviceMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: 3c59a47f8a45fbccb05eb1f385215fe2aa739836
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicemetadatagt"></a><span data-ttu-id="6d2a4-102">&lt;serviceMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="6d2a4-102">&lt;serviceMetadata&gt;</span></span>
<span data-ttu-id="6d2a4-103">指定服務中繼資料和相關資訊的發行。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-103">Specifies the publication of service metadata and associated information.</span></span>  
  
<span data-ttu-id="6d2a4-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6d2a4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6d2a4-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="6d2a4-105">\<behaviors></span></span>  
<span data-ttu-id="6d2a4-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6d2a4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6d2a4-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="6d2a4-107">\<behavior></span></span>  
<span data-ttu-id="6d2a4-108">\<serviceMetadata ></span><span class="sxs-lookup"><span data-stu-id="6d2a4-108">\<serviceMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d2a4-109">語法</span><span class="sxs-lookup"><span data-stu-id="6d2a4-109">Syntax</span></span>  
  
```xml
<serviceMetadata externalMetadataLocation="String"  
                 httpGetBinding="String" 
                 httpGetBindingConfiguration="String"  
                 httpGetEnabled="Boolean" 
                 httpGetUrl="String" 
                 httpsGetBinding="String" 
                 httpsGetBindingConfiguration="String"  
                 httpsGetEnabled="Boolean"   
                 httpsGetUrl="String"  
                 policyVersion="Policy12/Policy15" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d2a4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6d2a4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6d2a4-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d2a4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6d2a4-112">Attributes</span></span>  
  
|<span data-ttu-id="6d2a4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6d2a4-113">Attribute</span></span>|<span data-ttu-id="6d2a4-114">描述</span><span class="sxs-lookup"><span data-stu-id="6d2a4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d2a4-115">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="6d2a4-115">externalMetadataLocation</span></span>|<span data-ttu-id="6d2a4-116">包含 WSDL 檔案位置的 URI，此位置會傳回給使用者，以回應 WSDL 和 MEX 要求，而非自動產生的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-116">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="6d2a4-117">如果未設定這個屬性，則會傳回預設 WSDL。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-117">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="6d2a4-118">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="6d2a4-119">httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="6d2a4-119">httpGetBinding</span></span>|<span data-ttu-id="6d2a4-120">字串，這個字串會指定透過 HTTP GET 擷取中繼資料所要使用之繫結的型別。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-120">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="6d2a4-121">這是選擇性的設定。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-121">This setting is optional.</span></span> <span data-ttu-id="6d2a4-122">如果未指定這個設定，則會使用預設的繫結。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-122">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="6d2a4-123">只有當繫結的內部繫結項目支援 <xref:System.ServiceModel.Channels.IReplyChannel> 時，這些繫結才會受到支援。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-123">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="6d2a4-124">此外，該繫結的 <xref:System.ServiceModel.Channels.MessageVersion> 屬性 (Property) 必須是 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-124">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="6d2a4-125">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6d2a4-125">httpGetBindingConfiguration</span></span>|<span data-ttu-id="6d2a4-126">字串，這個字串會設定在 `httpGetBinding` 屬性中指定之繫結的名稱，該屬性會參考這個繫結中的其他組態資訊。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-126">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="6d2a4-127">必須在 `<bindings>` 區段中定義相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-127">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="6d2a4-128">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="6d2a4-128">httpGetEnabled</span></span>|<span data-ttu-id="6d2a4-129">布林值，指定是否發行服務中繼資料以使用 HTTP/Get 要求進行擷取。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-129">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="6d2a4-130">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-130">The default is `false`.</span></span><br /><br /> <span data-ttu-id="6d2a4-131">如果未指定 httpGetUrl 屬性，則中繼資料的發行位址會是服務位址加上 "?wsdl"。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-131">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="6d2a4-132">例如，如果服務位址是"http://localhost:8080/CalculatorService"，HTTP/Get 中繼資料位址為"http://localhost:8080/CalculatorService?wsdl"。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-132">For example, if the service address is "http://localhost:8080/CalculatorService", the HTTP/Get metadata address is "http://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="6d2a4-133">如果這個屬性是`false`，或服務的位址並非根據 HTTP 或 HTTPS，"？ wsdl"會被忽略。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-133">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="6d2a4-134">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="6d2a4-134">httpGetUrl</span></span>|<span data-ttu-id="6d2a4-135">布林值，指定中繼資料的發行位址以使用 HTTP/Get 要求進行擷取。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-135">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="6d2a4-136">如果已指定相對 URI，則視為相對於服務的基底位址。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-136">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="6d2a4-137">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="6d2a4-137">httpsGetBinding</span></span>|<span data-ttu-id="6d2a4-138">字串，這個字串會指定透過 HTTPS GET 擷取中繼資料所要使用之繫結的型別。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-138">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="6d2a4-139">這是選擇性的設定。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-139">This setting is optional.</span></span> <span data-ttu-id="6d2a4-140">如果未指定這個設定，則會使用預設的繫結。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-140">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="6d2a4-141">只有當繫結的內部繫結項目支援 <xref:System.ServiceModel.Channels.IReplyChannel> 時，這些繫結才會受到支援。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-141">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="6d2a4-142">此外，該繫結的 <xref:System.ServiceModel.Channels.MessageVersion> 屬性 (Property) 必須是 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-142">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="6d2a4-143">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6d2a4-143">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="6d2a4-144">字串，這個字串會設定在 `httpsGetBinding` 屬性中指定之繫結的名稱，該屬性會參考這個繫結中的其他組態資訊。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-144">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="6d2a4-145">必須在 `<bindings>` 區段中定義相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-145">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="6d2a4-146">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="6d2a4-146">httpsGetEnabled</span></span>|<span data-ttu-id="6d2a4-147">布林值，指定是否發行服務中繼資料以使用 HTTPS/Get 要求進行擷取。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-147">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="6d2a4-148">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="6d2a4-149">如果未指定 httpsGetUrl 屬性，則中繼資料的發行位址會是服務位址加上 "?wsdl"。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-149">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="6d2a4-150">例如，如果服務位址是"https://localhost:8080/CalculatorService"，HTTP/Get 中繼資料位址為"https://localhost:8080/CalculatorService?wsdl"。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-150">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="6d2a4-151">如果這個屬性是`false`，或服務的位址並非根據 HTTP 或 HTTPS，"？ wsdl"會被忽略。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-151">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="6d2a4-152">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="6d2a4-152">httpsGetUrl</span></span>|<span data-ttu-id="6d2a4-153">URI，指定中繼資料的發行位址以使用 HTTPS/Get 要求進行擷取。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-153">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="6d2a4-154">policyVersion</span><span class="sxs-lookup"><span data-stu-id="6d2a4-154">policyVersion</span></span>|<span data-ttu-id="6d2a4-155">字串，指定所要使用的 WS-Policy 規格版本。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-155">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="6d2a4-156">此屬性的型別為 <xref:System.ServiceModel.Description.PolicyVersion>。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-156">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d2a4-157">子項目</span><span class="sxs-lookup"><span data-stu-id="6d2a4-157">Child Elements</span></span>  
 <span data-ttu-id="6d2a4-158">無</span><span class="sxs-lookup"><span data-stu-id="6d2a4-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d2a4-159">父項目</span><span class="sxs-lookup"><span data-stu-id="6d2a4-159">Parent Elements</span></span>  
  
|<span data-ttu-id="6d2a4-160">項目</span><span class="sxs-lookup"><span data-stu-id="6d2a4-160">Element</span></span>|<span data-ttu-id="6d2a4-161">描述</span><span class="sxs-lookup"><span data-stu-id="6d2a4-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d2a4-162">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="6d2a4-162">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="6d2a4-163">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-163">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d2a4-164">備註</span><span class="sxs-lookup"><span data-stu-id="6d2a4-164">Remarks</span></span>  
 <span data-ttu-id="6d2a4-165">這個組態項目可讓您控制服務的中繼資料發行功能。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-165">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="6d2a4-166">若要避免意外洩露潛在的敏感服務中繼資料，Windows Communication Foundation (WCF) 服務的預設組態會停用中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-166">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="6d2a4-167">這個行為依預設為安全行為，但也表示您無法使用中繼資料匯入工具 (例如 Svcutil.exe) 來產生呼叫服務所需的用戶端程式碼，除非組態中已明確啟用服務的中繼發行行為。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-167">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="6d2a4-168">使用這個組態項目，您就可以為服務啟用此發行行為。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-168">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="6d2a4-169">設定此行為的詳細範例，請參閱[中繼資料發行行為](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-169">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="6d2a4-170">選用的 `httpGetBinding` 和 `httpsGetBinding` 屬性可讓您設定透過 HTTP GET (或 HTTPS GET) 擷取中繼資料時所使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-170">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="6d2a4-171">如果未指定這些繫結，則會依適當情形，使用預設的繫結 (使用 HTTP 時為 `HttpTransportBindingElement`，使用 HTTPS 時則為 `HttpsTransportBindingElement`) 擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-171">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="6d2a4-172">請注意，這些屬性 (Attribute) 無法搭配內建的 WCF 繫結使用。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-172">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="6d2a4-173">只有當繫結的內部繫結項目支援 <xref:System.ServiceModel.Channels.IReplyChannel> 時，這些繫結才會受到支援。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-173">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="6d2a4-174">此外，該繫結的 <xref:System.ServiceModel.Channels.MessageVersion> 屬性 (Property) 必須是 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-174">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="6d2a4-175">若要降低將服務暴露給惡意使用者的機會，可以使用 SSL over HTTP (HTTPS) 機制來進行安全的傳輸。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-175">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="6d2a4-176">若要這麼做，您必須先將適當的 X.509 憑證，繫結至裝載服務之電腦上的特定連接埠 </span><span class="sxs-lookup"><span data-stu-id="6d2a4-176">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="6d2a4-177">(如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。)其次，將這個項目加入至服務組態，並將 `httpsGetEnabled` 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-177">(For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="6d2a4-178">最後，將 `httpsGetUrl` 屬性設定為服務中繼資料端點的 URL，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-178">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml
<behaviors>  
  <serviceBehaviors>  
    <behavior name="NewBehavior">  
      <serviceMetadata httpsGetEnabled="true"   
                       httpsGetUrl="https://myComputerName/myEndpoint" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="example"></a><span data-ttu-id="6d2a4-179">範例</span><span class="sxs-lookup"><span data-stu-id="6d2a4-179">Example</span></span>  
 <span data-ttu-id="6d2a4-180">下列範例設定服務以公開中繼資料使用\<serviceMetadata > 項目。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-180">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="6d2a4-181">它也設定了一個端點，將 `IMetadataExchange` 合約公開做為 WS-MetadataExchange (MEX) 通訊協定的實作。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-181">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="6d2a4-182">此範例使用 `mexHttpBinding`，這個方便的標準繫結，相當於將安全性模式設定為 `wsHttpBinding` 的 `None`。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-182">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="6d2a4-183">"Mex"的相對位址用於端點中，當解析服務基底位址的端點位址http://localhost/servicemodelsamples/service.svc/mex。</span><span class="sxs-lookup"><span data-stu-id="6d2a4-183">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService" 
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex   
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <!-- The serviceMetadata behavior publishes metadata through   
               the IMetadataExchange contract. When this behavior is   
               present, you can expose this contract through an endpoint   
               as shown above. Setting httpGetEnabled to true publishes   
               the service's WSDL at the <baseaddress>?wsdl  
               eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d2a4-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d2a4-184">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="6d2a4-185">安全性行為</span><span class="sxs-lookup"><span data-stu-id="6d2a4-185">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="6d2a4-186">中繼資料發行行為</span><span class="sxs-lookup"><span data-stu-id="6d2a4-186">Metadata Publishing Behavior</span></span>](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
