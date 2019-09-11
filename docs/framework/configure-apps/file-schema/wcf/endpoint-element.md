---
title: <endpoint> 項目
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855388"
---
# <a name="endpoint-element"></a><span data-ttu-id="38b37-102">\<端點 > 元素</span><span class="sxs-lookup"><span data-stu-id="38b37-102">\<endpoint> element</span></span>
<span data-ttu-id="38b37-103">指定服務端點的繫結、合約和位址屬性，以用於公開服務。</span><span class="sxs-lookup"><span data-stu-id="38b37-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
<span data-ttu-id="38b37-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38b37-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38b37-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="38b37-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="38b37-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="38b37-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="38b37-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<服務 >** ](service.md)</span><span class="sxs-lookup"><span data-stu-id="38b37-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="38b37-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<端點 >**</span><span class="sxs-lookup"><span data-stu-id="38b37-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b37-109">語法</span><span class="sxs-lookup"><span data-stu-id="38b37-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38b37-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38b37-110">Attributes and Elements</span></span>  
 <span data-ttu-id="38b37-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="38b37-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38b37-112">屬性</span><span class="sxs-lookup"><span data-stu-id="38b37-112">Attributes</span></span>  
  
|<span data-ttu-id="38b37-113">屬性</span><span class="sxs-lookup"><span data-stu-id="38b37-113">Attribute</span></span>|<span data-ttu-id="38b37-114">說明</span><span class="sxs-lookup"><span data-stu-id="38b37-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38b37-115">位址</span><span class="sxs-lookup"><span data-stu-id="38b37-115">address</span></span>|<span data-ttu-id="38b37-116">包含端點位址的字串。</span><span class="sxs-lookup"><span data-stu-id="38b37-116">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="38b37-117">位址可以指定為絕對或相對位址。</span><span class="sxs-lookup"><span data-stu-id="38b37-117">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="38b37-118">如果提供相對位址，主機必須為繫結中使用的傳輸配置提供適當的基底位址。</span><span class="sxs-lookup"><span data-stu-id="38b37-118">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="38b37-119">如果沒有設定位址，會將基底位址假設為該端點的位址。</span><span class="sxs-lookup"><span data-stu-id="38b37-119">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="38b37-120">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="38b37-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="38b37-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="38b37-121">behaviorConfiguration</span></span>|<span data-ttu-id="38b37-122">字串，其中包含端點中所使用行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="38b37-122">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="38b37-123">繫結</span><span class="sxs-lookup"><span data-stu-id="38b37-123">binding</span></span>|<span data-ttu-id="38b37-124">必要的字串屬性，其中指定要使用的繫結型別。</span><span class="sxs-lookup"><span data-stu-id="38b37-124">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="38b37-125">此型別必須要有註冊的組態區段，才能加以參考。</span><span class="sxs-lookup"><span data-stu-id="38b37-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="38b37-126">型別是以區段名稱進行註冊，而非以繫結的型別名稱進行註冊。</span><span class="sxs-lookup"><span data-stu-id="38b37-126">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="38b37-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="38b37-127">bindingConfiguration</span></span>|<span data-ttu-id="38b37-128">字串，指定在產生端點時所使用繫結的繫結名稱。</span><span class="sxs-lookup"><span data-stu-id="38b37-128">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="38b37-129">繫結名稱必須在定義端點之處的範圍內。</span><span class="sxs-lookup"><span data-stu-id="38b37-129">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="38b37-130">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="38b37-130">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="38b37-131">這個屬性用於搭配 `binding` 使用，以參考組態檔中特定的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="38b37-131">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="38b37-132">如果您要嘗試使用自訂繫結，請設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="38b37-132">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="38b37-133">否則，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="38b37-133">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="38b37-134">bindingName</span><span class="sxs-lookup"><span data-stu-id="38b37-134">bindingName</span></span>|<span data-ttu-id="38b37-135">字串，指定透過 WSDL 匯出定義之繫結的唯一限定名稱。</span><span class="sxs-lookup"><span data-stu-id="38b37-135">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="38b37-136">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="38b37-136">The default is an empty string.</span></span>|  
|<span data-ttu-id="38b37-137">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="38b37-137">bindingNamespace</span></span>|<span data-ttu-id="38b37-138">字串，指定透過 WSDL 匯出定義之繫結的命名空間限定名稱。</span><span class="sxs-lookup"><span data-stu-id="38b37-138">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="38b37-139">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="38b37-139">The default is an empty string.</span></span>|  
|<span data-ttu-id="38b37-140">合約</span><span class="sxs-lookup"><span data-stu-id="38b37-140">contract</span></span>|<span data-ttu-id="38b37-141">指示這個端點要公開 (Expose) 之合約的字串。</span><span class="sxs-lookup"><span data-stu-id="38b37-141">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="38b37-142">組件必須實作合約類型。</span><span class="sxs-lookup"><span data-stu-id="38b37-142">The assembly must implement the contract type.</span></span> <span data-ttu-id="38b37-143">如果服務實作實作單一合約類型，便可省略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="38b37-143">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="38b37-144">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="38b37-144">The default is an empty string.</span></span>|  
|<span data-ttu-id="38b37-145">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="38b37-145">endpointConfiguration</span></span>|<span data-ttu-id="38b37-146">字串，這個字串會指定 `kind` 屬性所設定的標準端點名稱，該屬性會參考這個標準端點的其他組態資訊。</span><span class="sxs-lookup"><span data-stu-id="38b37-146">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="38b37-147">必須在 `<standardEndpoints>` 區段中定義相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="38b37-147">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="38b37-148">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="38b37-148">isSystemEndpoint</span></span>|<span data-ttu-id="38b37-149">布林值，用於指定端點是否為基礎結構端點。</span><span class="sxs-lookup"><span data-stu-id="38b37-149">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="38b37-150">kind</span><span class="sxs-lookup"><span data-stu-id="38b37-150">kind</span></span>|<span data-ttu-id="38b37-151">字串，這個字串會指定所套用之標準端點的型別。</span><span class="sxs-lookup"><span data-stu-id="38b37-151">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="38b37-152">型別必須要在 `<extensions>` 區段或 machine.config 中註冊。如果未指定任何內容，則會建立一般服務端點。</span><span class="sxs-lookup"><span data-stu-id="38b37-152">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="38b37-153">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="38b37-153">listenUriMode</span></span>|<span data-ttu-id="38b37-154">指定傳輸如何處理提供給服務接聽的 `ListenUri`。</span><span class="sxs-lookup"><span data-stu-id="38b37-154">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="38b37-155">有效值為</span><span class="sxs-lookup"><span data-stu-id="38b37-155">Valid values are</span></span><br /><br /> <span data-ttu-id="38b37-156">-Explicit</span><span class="sxs-lookup"><span data-stu-id="38b37-156">-   Explicit</span></span><br /><span data-ttu-id="38b37-157">-唯一</span><span class="sxs-lookup"><span data-stu-id="38b37-157">-   Unique</span></span><br /><br /> <span data-ttu-id="38b37-158">預設值為 Explicit。</span><span class="sxs-lookup"><span data-stu-id="38b37-158">The default value is Explicit.</span></span>|  
|<span data-ttu-id="38b37-159">listenUri</span><span class="sxs-lookup"><span data-stu-id="38b37-159">listenUri</span></span>|<span data-ttu-id="38b37-160">字串，指定服務端點接聽的 URI。</span><span class="sxs-lookup"><span data-stu-id="38b37-160">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="38b37-161">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="38b37-161">The default is an empty string.</span></span>|  
|<span data-ttu-id="38b37-162">NAME</span><span class="sxs-lookup"><span data-stu-id="38b37-162">name</span></span>|<span data-ttu-id="38b37-163">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="38b37-163">Optional attribute.</span></span> <span data-ttu-id="38b37-164">指定服務端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="38b37-164">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="38b37-165">預設值是繫結名稱和合約描述名稱的串連。</span><span class="sxs-lookup"><span data-stu-id="38b37-165">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="38b37-166">服務可能會有多個端點，因此端點的 `name` 屬性會與服務的名稱有所區別。</span><span class="sxs-lookup"><span data-stu-id="38b37-166">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38b37-167">子元素</span><span class="sxs-lookup"><span data-stu-id="38b37-167">Child Elements</span></span>  
  
|<span data-ttu-id="38b37-168">項目</span><span class="sxs-lookup"><span data-stu-id="38b37-168">Element</span></span>|<span data-ttu-id="38b37-169">描述</span><span class="sxs-lookup"><span data-stu-id="38b37-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38b37-170">\<headers></span><span class="sxs-lookup"><span data-stu-id="38b37-170">\<headers></span></span>](headers.md)|<span data-ttu-id="38b37-171">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="38b37-171">A collection of address headers.</span></span>|  
|[<span data-ttu-id="38b37-172">\<identity></span><span class="sxs-lookup"><span data-stu-id="38b37-172">\<identity></span></span>](identity.md)|<span data-ttu-id="38b37-173">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="38b37-173">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="38b37-174">父項目</span><span class="sxs-lookup"><span data-stu-id="38b37-174">Parent Elements</span></span>  
  
|<span data-ttu-id="38b37-175">項目</span><span class="sxs-lookup"><span data-stu-id="38b37-175">Element</span></span>|<span data-ttu-id="38b37-176">描述</span><span class="sxs-lookup"><span data-stu-id="38b37-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38b37-177">\<service></span><span class="sxs-lookup"><span data-stu-id="38b37-177">\<service></span></span>](service.md)|<span data-ttu-id="38b37-178">組態區段，它會定義用戶端可以連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="38b37-178">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="38b37-179">範例</span><span class="sxs-lookup"><span data-stu-id="38b37-179">Example</span></span>  
 <span data-ttu-id="38b37-180">這是服務端點組態的範例。</span><span class="sxs-lookup"><span data-stu-id="38b37-180">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38b37-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38b37-181">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="38b37-182">終點位址、系結和合約</span><span class="sxs-lookup"><span data-stu-id="38b37-182">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="38b37-183">如何：在設定中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="38b37-183">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
