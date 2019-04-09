---
title: <endpoint> 項目
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 667086cda010daf51cb92116d636b9b526b4b34b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163406"
---
# <a name="endpoint-element"></a><span data-ttu-id="17685-102">\<結束點 > 項目</span><span class="sxs-lookup"><span data-stu-id="17685-102">\<endpoint> element</span></span>
<span data-ttu-id="17685-103">指定服務端點的繫結、合約和位址屬性，以用於公開服務。</span><span class="sxs-lookup"><span data-stu-id="17685-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="17685-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="17685-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="17685-105">\<service></span><span class="sxs-lookup"><span data-stu-id="17685-105">\<service></span></span>  
<span data-ttu-id="17685-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="17685-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17685-107">語法</span><span class="sxs-lookup"><span data-stu-id="17685-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17685-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="17685-108">Attributes and Elements</span></span>  
 <span data-ttu-id="17685-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="17685-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17685-110">屬性</span><span class="sxs-lookup"><span data-stu-id="17685-110">Attributes</span></span>  
  
|<span data-ttu-id="17685-111">屬性</span><span class="sxs-lookup"><span data-stu-id="17685-111">Attribute</span></span>|<span data-ttu-id="17685-112">描述</span><span class="sxs-lookup"><span data-stu-id="17685-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17685-113">位址</span><span class="sxs-lookup"><span data-stu-id="17685-113">address</span></span>|<span data-ttu-id="17685-114">包含端點位址的字串。</span><span class="sxs-lookup"><span data-stu-id="17685-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="17685-115">位址可以指定為絕對或相對位址。</span><span class="sxs-lookup"><span data-stu-id="17685-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="17685-116">如果提供相對位址，主機必須為繫結中使用的傳輸配置提供適當的基底位址。</span><span class="sxs-lookup"><span data-stu-id="17685-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="17685-117">如果沒有設定位址，會將基底位址假設為該端點的位址。</span><span class="sxs-lookup"><span data-stu-id="17685-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="17685-118">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="17685-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="17685-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="17685-119">behaviorConfiguration</span></span>|<span data-ttu-id="17685-120">字串，其中包含端點中所使用行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="17685-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="17685-121">繫結</span><span class="sxs-lookup"><span data-stu-id="17685-121">binding</span></span>|<span data-ttu-id="17685-122">必要的字串屬性，其中指定要使用的繫結型別。</span><span class="sxs-lookup"><span data-stu-id="17685-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="17685-123">此型別必須要有註冊的組態區段，才能加以參考。</span><span class="sxs-lookup"><span data-stu-id="17685-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="17685-124">型別是以區段名稱進行註冊，而非以繫結的型別名稱進行註冊。</span><span class="sxs-lookup"><span data-stu-id="17685-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="17685-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="17685-125">bindingConfiguration</span></span>|<span data-ttu-id="17685-126">字串，指定在產生端點時所使用繫結的繫結名稱。</span><span class="sxs-lookup"><span data-stu-id="17685-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="17685-127">繫結名稱必須在定義端點之處的範圍內。</span><span class="sxs-lookup"><span data-stu-id="17685-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="17685-128">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="17685-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="17685-129">這個屬性用於搭配 `binding` 使用，以參考組態檔中特定的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="17685-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="17685-130">如果您要嘗試使用自訂繫結，請設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="17685-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="17685-131">否則，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="17685-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="17685-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="17685-132">bindingName</span></span>|<span data-ttu-id="17685-133">字串，指定透過 WSDL 匯出定義之繫結的唯一限定名稱。</span><span class="sxs-lookup"><span data-stu-id="17685-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="17685-134">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="17685-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="17685-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="17685-135">bindingNamespace</span></span>|<span data-ttu-id="17685-136">字串，指定透過 WSDL 匯出定義之繫結的命名空間限定名稱。</span><span class="sxs-lookup"><span data-stu-id="17685-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="17685-137">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="17685-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="17685-138">Contract - 合約</span><span class="sxs-lookup"><span data-stu-id="17685-138">contract</span></span>|<span data-ttu-id="17685-139">指示這個端點要公開 (Expose) 之合約的字串。</span><span class="sxs-lookup"><span data-stu-id="17685-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="17685-140">組件必須實作合約類型。</span><span class="sxs-lookup"><span data-stu-id="17685-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="17685-141">如果服務實作實作單一合約類型，便可省略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="17685-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="17685-142">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="17685-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="17685-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="17685-143">endpointConfiguration</span></span>|<span data-ttu-id="17685-144">字串，這個字串會指定 `kind` 屬性所設定的標準端點名稱，該屬性會參考這個標準端點的其他組態資訊。</span><span class="sxs-lookup"><span data-stu-id="17685-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="17685-145">必須在 `<standardEndpoints>` 區段中定義相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="17685-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="17685-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="17685-146">isSystemEndpoint</span></span>|<span data-ttu-id="17685-147">布林值，用於指定端點是否為基礎結構端點。</span><span class="sxs-lookup"><span data-stu-id="17685-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="17685-148">kind</span><span class="sxs-lookup"><span data-stu-id="17685-148">kind</span></span>|<span data-ttu-id="17685-149">字串，這個字串會指定所套用之標準端點的型別。</span><span class="sxs-lookup"><span data-stu-id="17685-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="17685-150">型別必須要在 `<extensions>` 區段或 machine.config 中註冊。如果未指定任何內容，則會建立一般服務端點。</span><span class="sxs-lookup"><span data-stu-id="17685-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="17685-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="17685-151">listenUriMode</span></span>|<span data-ttu-id="17685-152">指定傳輸如何處理提供給服務接聽的 `ListenUri`。</span><span class="sxs-lookup"><span data-stu-id="17685-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="17685-153">有效值為</span><span class="sxs-lookup"><span data-stu-id="17685-153">Valid values are</span></span><br /><br /> <span data-ttu-id="17685-154">-   Explicit</span><span class="sxs-lookup"><span data-stu-id="17685-154">-   Explicit</span></span><br /><span data-ttu-id="17685-155">唯一</span><span class="sxs-lookup"><span data-stu-id="17685-155">-   Unique</span></span><br /><br /> <span data-ttu-id="17685-156">預設值為 Explicit。</span><span class="sxs-lookup"><span data-stu-id="17685-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="17685-157">listenUri</span><span class="sxs-lookup"><span data-stu-id="17685-157">listenUri</span></span>|<span data-ttu-id="17685-158">字串，指定服務端點接聽的 URI。</span><span class="sxs-lookup"><span data-stu-id="17685-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="17685-159">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="17685-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="17685-160">名稱</span><span class="sxs-lookup"><span data-stu-id="17685-160">name</span></span>|<span data-ttu-id="17685-161">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="17685-161">Optional attribute.</span></span> <span data-ttu-id="17685-162">指定服務端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="17685-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="17685-163">預設值是繫結名稱和合約描述名稱的串連。</span><span class="sxs-lookup"><span data-stu-id="17685-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="17685-164">服務可能會有多個端點，因此端點的 `name` 屬性會與服務的名稱有所區別。</span><span class="sxs-lookup"><span data-stu-id="17685-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17685-165">子元素</span><span class="sxs-lookup"><span data-stu-id="17685-165">Child Elements</span></span>  
  
|<span data-ttu-id="17685-166">項目</span><span class="sxs-lookup"><span data-stu-id="17685-166">Element</span></span>|<span data-ttu-id="17685-167">描述</span><span class="sxs-lookup"><span data-stu-id="17685-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17685-168">\<headers></span><span class="sxs-lookup"><span data-stu-id="17685-168">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="17685-169">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="17685-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="17685-170">\<identity></span><span class="sxs-lookup"><span data-stu-id="17685-170">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="17685-171">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="17685-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17685-172">父項目</span><span class="sxs-lookup"><span data-stu-id="17685-172">Parent Elements</span></span>  
  
|<span data-ttu-id="17685-173">項目</span><span class="sxs-lookup"><span data-stu-id="17685-173">Element</span></span>|<span data-ttu-id="17685-174">描述</span><span class="sxs-lookup"><span data-stu-id="17685-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17685-175">\<service></span><span class="sxs-lookup"><span data-stu-id="17685-175">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="17685-176">組態區段，它會定義用戶端可以連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="17685-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17685-177">範例</span><span class="sxs-lookup"><span data-stu-id="17685-177">Example</span></span>  
 <span data-ttu-id="17685-178">這是服務端點組態的範例。</span><span class="sxs-lookup"><span data-stu-id="17685-178">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="17685-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17685-179">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="17685-180">端點：位址、繫結和合約</span><span class="sxs-lookup"><span data-stu-id="17685-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="17685-181">HOW TO：在組態中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="17685-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
