---
title: <endpoint> 的 <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855313"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="75ec0-102">\<用戶端 > \<的端點 ></span><span class="sxs-lookup"><span data-stu-id="75ec0-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="75ec0-103">指定通道端點的合約、繫結和位址屬性，用戶端會使用該通道端點連線至伺服器上的服務端點。</span><span class="sxs-lookup"><span data-stu-id="75ec0-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
<span data-ttu-id="75ec0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="75ec0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75ec0-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="75ec0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="75ec0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<用戶端 >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="75ec0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="75ec0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<端點 >**</span><span class="sxs-lookup"><span data-stu-id="75ec0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75ec0-108">語法</span><span class="sxs-lookup"><span data-stu-id="75ec0-108">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75ec0-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="75ec0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="75ec0-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="75ec0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75ec0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="75ec0-111">Attributes</span></span>  
  
|<span data-ttu-id="75ec0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="75ec0-112">Attribute</span></span>|<span data-ttu-id="75ec0-113">描述</span><span class="sxs-lookup"><span data-stu-id="75ec0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75ec0-114">位址</span><span class="sxs-lookup"><span data-stu-id="75ec0-114">address</span></span>|<span data-ttu-id="75ec0-115">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="75ec0-115">Required string attribute.</span></span><br /><br /> <span data-ttu-id="75ec0-116">指定端點的位址。</span><span class="sxs-lookup"><span data-stu-id="75ec0-116">Specifies the address of the endpoint.</span></span> <span data-ttu-id="75ec0-117">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="75ec0-117">The default is an empty string.</span></span> <span data-ttu-id="75ec0-118">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="75ec0-118">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="75ec0-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="75ec0-119">behaviorConfiguration</span></span>|<span data-ttu-id="75ec0-120">字串，其中包含要用於產生端點之行為的行為名稱。</span><span class="sxs-lookup"><span data-stu-id="75ec0-120">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="75ec0-121">行為名稱必須在定義服務之處的範圍內。</span><span class="sxs-lookup"><span data-stu-id="75ec0-121">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="75ec0-122">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="75ec0-122">The default is an empty string.</span></span>|  
|<span data-ttu-id="75ec0-123">繫結</span><span class="sxs-lookup"><span data-stu-id="75ec0-123">binding</span></span>|<span data-ttu-id="75ec0-124">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="75ec0-124">Required string attribute.</span></span><br /><br /> <span data-ttu-id="75ec0-125">字串，指出要使用的繫結型別。</span><span class="sxs-lookup"><span data-stu-id="75ec0-125">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="75ec0-126">此型別必須要有註冊的組態區段，才能加以參考。</span><span class="sxs-lookup"><span data-stu-id="75ec0-126">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="75ec0-127">型別是以區段名稱進行註冊，而非以繫結的型別名稱進行註冊。</span><span class="sxs-lookup"><span data-stu-id="75ec0-127">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="75ec0-128">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="75ec0-128">bindingConfiguration</span></span>|<span data-ttu-id="75ec0-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="75ec0-129">Optional.</span></span> <span data-ttu-id="75ec0-130">字串，其中包含在產生端點時使用的繫結組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="75ec0-130">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="75ec0-131">繫結組態必須在定義端點之處的範圍內。</span><span class="sxs-lookup"><span data-stu-id="75ec0-131">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="75ec0-132">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="75ec0-132">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="75ec0-133">這個屬性用於搭配 `binding` 使用，以參考組態檔中特定的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="75ec0-133">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="75ec0-134">如果您要嘗試使用自訂繫結，請設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="75ec0-134">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="75ec0-135">否則，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="75ec0-135">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="75ec0-136">合約</span><span class="sxs-lookup"><span data-stu-id="75ec0-136">contract</span></span>|<span data-ttu-id="75ec0-137">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="75ec0-137">Required string attribute.</span></span><br /><br /> <span data-ttu-id="75ec0-138">指示這個端點要公開 (Expose) 之合約的字串。</span><span class="sxs-lookup"><span data-stu-id="75ec0-138">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="75ec0-139">組件必須實作合約類型。</span><span class="sxs-lookup"><span data-stu-id="75ec0-139">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="75ec0-140">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="75ec0-140">endpointConfiguration</span></span>|<span data-ttu-id="75ec0-141">字串，這個字串會指定 `kind` 屬性所設定的標準端點名稱，該屬性會參考這個標準端點的其他組態資訊。</span><span class="sxs-lookup"><span data-stu-id="75ec0-141">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="75ec0-142">必須在 `<standardEndpoints>` 區段中定義相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="75ec0-142">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="75ec0-143">kind</span><span class="sxs-lookup"><span data-stu-id="75ec0-143">kind</span></span>|<span data-ttu-id="75ec0-144">字串，這個字串會指定所套用之標準端點的型別。</span><span class="sxs-lookup"><span data-stu-id="75ec0-144">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="75ec0-145">型別必須要在 `<extensions>` 區段或 machine.config 中註冊。如果未指定任何內容，則會建立一般通道端點。</span><span class="sxs-lookup"><span data-stu-id="75ec0-145">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="75ec0-146">NAME</span><span class="sxs-lookup"><span data-stu-id="75ec0-146">name</span></span>|<span data-ttu-id="75ec0-147">選擇性字串屬性。</span><span class="sxs-lookup"><span data-stu-id="75ec0-147">Optional string attribute.</span></span> <span data-ttu-id="75ec0-148">這個屬性可唯一識別指定合約的端點。</span><span class="sxs-lookup"><span data-stu-id="75ec0-148">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="75ec0-149">您可以為指定的合約類型定義多個用戶端。</span><span class="sxs-lookup"><span data-stu-id="75ec0-149">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="75ec0-150">每個定義必須使用唯一組態名稱來區別。</span><span class="sxs-lookup"><span data-stu-id="75ec0-150">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="75ec0-151">如果省略這個屬性，就會使用對應端點做為與所指定合約類型相關聯的預設端點。</span><span class="sxs-lookup"><span data-stu-id="75ec0-151">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="75ec0-152">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="75ec0-152">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="75ec0-153">繫結的 `name` 屬性用於透過 WSDL 進行的定義匯出。</span><span class="sxs-lookup"><span data-stu-id="75ec0-153">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75ec0-154">子元素</span><span class="sxs-lookup"><span data-stu-id="75ec0-154">Child Elements</span></span>  
  
|<span data-ttu-id="75ec0-155">項目</span><span class="sxs-lookup"><span data-stu-id="75ec0-155">Element</span></span>|<span data-ttu-id="75ec0-156">說明</span><span class="sxs-lookup"><span data-stu-id="75ec0-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75ec0-157">\<headers></span><span class="sxs-lookup"><span data-stu-id="75ec0-157">\<headers></span></span>](headers.md)|<span data-ttu-id="75ec0-158">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="75ec0-158">A collection of address headers.</span></span>|  
|[<span data-ttu-id="75ec0-159">\<identity></span><span class="sxs-lookup"><span data-stu-id="75ec0-159">\<identity></span></span>](identity.md)|<span data-ttu-id="75ec0-160">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="75ec0-160">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="75ec0-161">父項目</span><span class="sxs-lookup"><span data-stu-id="75ec0-161">Parent Elements</span></span>  
  
|<span data-ttu-id="75ec0-162">項目</span><span class="sxs-lookup"><span data-stu-id="75ec0-162">Element</span></span>|<span data-ttu-id="75ec0-163">說明</span><span class="sxs-lookup"><span data-stu-id="75ec0-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75ec0-164">\<client></span><span class="sxs-lookup"><span data-stu-id="75ec0-164">\<client></span></span>](client.md)|<span data-ttu-id="75ec0-165">組態區段，它會定義用戶端可以連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="75ec0-165">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="75ec0-166">範例</span><span class="sxs-lookup"><span data-stu-id="75ec0-166">Example</span></span>  
 <span data-ttu-id="75ec0-167">這是通道端點組態的範例。</span><span class="sxs-lookup"><span data-stu-id="75ec0-167">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="75ec0-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75ec0-168">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="75ec0-169">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="75ec0-169">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="75ec0-170">用戶端</span><span class="sxs-lookup"><span data-stu-id="75ec0-170">Clients</span></span>](../../../wcf/feature-details/clients.md)
