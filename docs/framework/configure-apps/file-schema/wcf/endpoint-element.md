---
title: <endpoint> 項目
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855388"
---
# <a name="endpoint-element"></a><span data-ttu-id="43fd4-102">\<endpoint> 項目</span><span class="sxs-lookup"><span data-stu-id="43fd4-102">\<endpoint> element</span></span>
<span data-ttu-id="43fd4-103">指定服務端點的繫結、合約和位址屬性，以用於公開服務。</span><span class="sxs-lookup"><span data-stu-id="43fd4-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="43fd4-104">語法</span><span class="sxs-lookup"><span data-stu-id="43fd4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43fd4-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="43fd4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="43fd4-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="43fd4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43fd4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="43fd4-107">Attributes</span></span>  
  
|<span data-ttu-id="43fd4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="43fd4-108">Attribute</span></span>|<span data-ttu-id="43fd4-109">描述</span><span class="sxs-lookup"><span data-stu-id="43fd4-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43fd4-110">address</span><span class="sxs-lookup"><span data-stu-id="43fd4-110">address</span></span>|<span data-ttu-id="43fd4-111">包含端點位址的字串。</span><span class="sxs-lookup"><span data-stu-id="43fd4-111">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="43fd4-112">位址可以指定為絕對或相對位址。</span><span class="sxs-lookup"><span data-stu-id="43fd4-112">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="43fd4-113">如果提供相對位址，主機必須為繫結中使用的傳輸配置提供適當的基底位址。</span><span class="sxs-lookup"><span data-stu-id="43fd4-113">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="43fd4-114">如果沒有設定位址，會將基底位址假設為該端點的位址。</span><span class="sxs-lookup"><span data-stu-id="43fd4-114">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="43fd4-115">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="43fd4-115">The default is an empty string.</span></span>|  
|<span data-ttu-id="43fd4-116">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="43fd4-116">behaviorConfiguration</span></span>|<span data-ttu-id="43fd4-117">字串，其中包含端點中所使用行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="43fd4-117">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="43fd4-118">繫結</span><span class="sxs-lookup"><span data-stu-id="43fd4-118">binding</span></span>|<span data-ttu-id="43fd4-119">必要的字串屬性，其中指定要使用的繫結型別。</span><span class="sxs-lookup"><span data-stu-id="43fd4-119">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="43fd4-120">此型別必須要有註冊的組態區段，才能加以參考。</span><span class="sxs-lookup"><span data-stu-id="43fd4-120">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="43fd4-121">型別是以區段名稱進行註冊，而非以繫結的型別名稱進行註冊。</span><span class="sxs-lookup"><span data-stu-id="43fd4-121">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="43fd4-122">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="43fd4-122">bindingConfiguration</span></span>|<span data-ttu-id="43fd4-123">字串，指定在產生端點時所使用繫結的繫結名稱。</span><span class="sxs-lookup"><span data-stu-id="43fd4-123">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="43fd4-124">繫結名稱必須在定義端點之處的範圍內。</span><span class="sxs-lookup"><span data-stu-id="43fd4-124">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="43fd4-125">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="43fd4-125">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="43fd4-126">這個屬性用於搭配 `binding` 使用，以參考組態檔中特定的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="43fd4-126">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="43fd4-127">如果您要嘗試使用自訂繫結，請設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="43fd4-127">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="43fd4-128">否則，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="43fd4-128">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="43fd4-129">bindingName</span><span class="sxs-lookup"><span data-stu-id="43fd4-129">bindingName</span></span>|<span data-ttu-id="43fd4-130">字串，指定透過 WSDL 匯出定義之繫結的唯一限定名稱。</span><span class="sxs-lookup"><span data-stu-id="43fd4-130">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="43fd4-131">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="43fd4-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="43fd4-132">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="43fd4-132">bindingNamespace</span></span>|<span data-ttu-id="43fd4-133">字串，指定透過 WSDL 匯出定義之繫結的命名空間限定名稱。</span><span class="sxs-lookup"><span data-stu-id="43fd4-133">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="43fd4-134">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="43fd4-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="43fd4-135">合約</span><span class="sxs-lookup"><span data-stu-id="43fd4-135">contract</span></span>|<span data-ttu-id="43fd4-136">指示這個端點要公開 (Expose) 之合約的字串。</span><span class="sxs-lookup"><span data-stu-id="43fd4-136">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="43fd4-137">組件必須實作合約類型。</span><span class="sxs-lookup"><span data-stu-id="43fd4-137">The assembly must implement the contract type.</span></span> <span data-ttu-id="43fd4-138">如果服務實作實作單一合約類型，便可省略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="43fd4-138">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="43fd4-139">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="43fd4-139">The default is an empty string.</span></span>|  
|<span data-ttu-id="43fd4-140">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="43fd4-140">endpointConfiguration</span></span>|<span data-ttu-id="43fd4-141">字串，這個字串會指定 `kind` 屬性所設定的標準端點名稱，該屬性會參考這個標準端點的其他組態資訊。</span><span class="sxs-lookup"><span data-stu-id="43fd4-141">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="43fd4-142">必須在 `<standardEndpoints>` 區段中定義相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="43fd4-142">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="43fd4-143">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="43fd4-143">isSystemEndpoint</span></span>|<span data-ttu-id="43fd4-144">布林值，用於指定端點是否為基礎結構端點。</span><span class="sxs-lookup"><span data-stu-id="43fd4-144">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="43fd4-145">kind</span><span class="sxs-lookup"><span data-stu-id="43fd4-145">kind</span></span>|<span data-ttu-id="43fd4-146">字串，這個字串會指定所套用之標準端點的型別。</span><span class="sxs-lookup"><span data-stu-id="43fd4-146">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="43fd4-147">類型必須在區段或 machine.config 中註冊 `<extensions>` 。如果未指定任何內容，則會建立一般服務端點。</span><span class="sxs-lookup"><span data-stu-id="43fd4-147">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="43fd4-148">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="43fd4-148">listenUriMode</span></span>|<span data-ttu-id="43fd4-149">指定傳輸如何處理提供給服務接聽的 `ListenUri`。</span><span class="sxs-lookup"><span data-stu-id="43fd4-149">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="43fd4-150">有效值為</span><span class="sxs-lookup"><span data-stu-id="43fd4-150">Valid values are</span></span><br /><br /> <span data-ttu-id="43fd4-151">-Explicit</span><span class="sxs-lookup"><span data-stu-id="43fd4-151">-   Explicit</span></span><br /><span data-ttu-id="43fd4-152">-唯一</span><span class="sxs-lookup"><span data-stu-id="43fd4-152">-   Unique</span></span><br /><br /> <span data-ttu-id="43fd4-153">預設值為 Explicit。</span><span class="sxs-lookup"><span data-stu-id="43fd4-153">The default value is Explicit.</span></span>|  
|<span data-ttu-id="43fd4-154">listenUri</span><span class="sxs-lookup"><span data-stu-id="43fd4-154">listenUri</span></span>|<span data-ttu-id="43fd4-155">字串，指定服務端點接聽的 URI。</span><span class="sxs-lookup"><span data-stu-id="43fd4-155">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="43fd4-156">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="43fd4-156">The default is an empty string.</span></span>|  
|<span data-ttu-id="43fd4-157">NAME</span><span class="sxs-lookup"><span data-stu-id="43fd4-157">name</span></span>|<span data-ttu-id="43fd4-158">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="43fd4-158">Optional attribute.</span></span> <span data-ttu-id="43fd4-159">指定服務端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="43fd4-159">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="43fd4-160">預設值是繫結名稱和合約描述名稱的串連。</span><span class="sxs-lookup"><span data-stu-id="43fd4-160">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="43fd4-161">服務可能會有多個端點，因此端點的 `name` 屬性會與服務的名稱有所區別。</span><span class="sxs-lookup"><span data-stu-id="43fd4-161">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43fd4-162">子元素</span><span class="sxs-lookup"><span data-stu-id="43fd4-162">Child Elements</span></span>  
  
|<span data-ttu-id="43fd4-163">元素</span><span class="sxs-lookup"><span data-stu-id="43fd4-163">Element</span></span>|<span data-ttu-id="43fd4-164">描述</span><span class="sxs-lookup"><span data-stu-id="43fd4-164">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="43fd4-165">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="43fd4-165">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="43fd4-166">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="43fd4-166">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43fd4-167">父項目</span><span class="sxs-lookup"><span data-stu-id="43fd4-167">Parent Elements</span></span>  
  
|<span data-ttu-id="43fd4-168">元素</span><span class="sxs-lookup"><span data-stu-id="43fd4-168">Element</span></span>|<span data-ttu-id="43fd4-169">描述</span><span class="sxs-lookup"><span data-stu-id="43fd4-169">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="43fd4-170">組態區段，它會定義用戶端可以連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="43fd4-170">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43fd4-171">範例</span><span class="sxs-lookup"><span data-stu-id="43fd4-171">Example</span></span>  
 <span data-ttu-id="43fd4-172">這是服務端點組態的範例。</span><span class="sxs-lookup"><span data-stu-id="43fd4-172">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43fd4-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43fd4-173">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="43fd4-174">端點：位址、繫結和合約</span><span class="sxs-lookup"><span data-stu-id="43fd4-174">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="43fd4-175">HOW TO：在組態中建立服務端點</span><span class="sxs-lookup"><span data-stu-id="43fd4-175">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
