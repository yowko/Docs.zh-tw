---
title: "&lt;client&gt; 的 &lt;endpoint&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec959a9eeea82c56d6a2ae5ec3a7befce67676e3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltendpointgt-of-ltclientgt"></a><span data-ttu-id="57d93-102">&lt;client&gt; 的 &lt;endpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="57d93-102">&lt;endpoint&gt; of &lt;client&gt;</span></span>
<span data-ttu-id="57d93-103">指定通道端點的合約、繫結和位址屬性，用戶端會使用該通道端點連線至伺服器上的服務端點。</span><span class="sxs-lookup"><span data-stu-id="57d93-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="57d93-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="57d93-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="57d93-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="57d93-105">\<client></span></span>  
<span data-ttu-id="57d93-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="57d93-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57d93-107">語法</span><span class="sxs-lookup"><span data-stu-id="57d93-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   contract="String"   endpointConfiguration="String"   kind="String"  
   name="String"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57d93-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="57d93-108">Attributes and Elements</span></span>  
 <span data-ttu-id="57d93-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="57d93-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57d93-110">屬性</span><span class="sxs-lookup"><span data-stu-id="57d93-110">Attributes</span></span>  
  
|<span data-ttu-id="57d93-111">屬性</span><span class="sxs-lookup"><span data-stu-id="57d93-111">Attribute</span></span>|<span data-ttu-id="57d93-112">描述</span><span class="sxs-lookup"><span data-stu-id="57d93-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57d93-113">address</span><span class="sxs-lookup"><span data-stu-id="57d93-113">address</span></span>|<span data-ttu-id="57d93-114">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="57d93-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="57d93-115">指定端點的位址。</span><span class="sxs-lookup"><span data-stu-id="57d93-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="57d93-116">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="57d93-116">The default is an empty string.</span></span> <span data-ttu-id="57d93-117">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="57d93-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="57d93-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="57d93-118">behaviorConfiguration</span></span>|<span data-ttu-id="57d93-119">字串，其中包含要用於產生端點之行為的行為名稱。</span><span class="sxs-lookup"><span data-stu-id="57d93-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="57d93-120">行為名稱必須在定義服務之處的範圍內。</span><span class="sxs-lookup"><span data-stu-id="57d93-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="57d93-121">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="57d93-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="57d93-122">繫結</span><span class="sxs-lookup"><span data-stu-id="57d93-122">binding</span></span>|<span data-ttu-id="57d93-123">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="57d93-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="57d93-124">字串，指出要使用的繫結型別。</span><span class="sxs-lookup"><span data-stu-id="57d93-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="57d93-125">此型別必須要有註冊的組態區段，才能加以參考。</span><span class="sxs-lookup"><span data-stu-id="57d93-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="57d93-126">型別是以區段名稱進行註冊，而非以繫結的型別名稱進行註冊。</span><span class="sxs-lookup"><span data-stu-id="57d93-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="57d93-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="57d93-127">bindingConfiguration</span></span>|<span data-ttu-id="57d93-128">選擇項。</span><span class="sxs-lookup"><span data-stu-id="57d93-128">Optional.</span></span> <span data-ttu-id="57d93-129">字串，其中包含在產生端點時使用的繫結組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="57d93-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="57d93-130">繫結組態必須在定義端點之處的範圍內。</span><span class="sxs-lookup"><span data-stu-id="57d93-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="57d93-131">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="57d93-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="57d93-132">這個屬性用於搭配 `binding` 使用，以參考組態檔中特定的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="57d93-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="57d93-133">如果您要嘗試使用自訂繫結，請設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="57d93-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="57d93-134">否則，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="57d93-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="57d93-135">Contract - 合約</span><span class="sxs-lookup"><span data-stu-id="57d93-135">contract</span></span>|<span data-ttu-id="57d93-136">必要的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="57d93-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="57d93-137">指示這個端點要公開 (Expose) 之合約的字串。</span><span class="sxs-lookup"><span data-stu-id="57d93-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="57d93-138">組件必須實作合約類型。</span><span class="sxs-lookup"><span data-stu-id="57d93-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="57d93-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="57d93-139">endpointConfiguration</span></span>|<span data-ttu-id="57d93-140">字串，這個字串會指定 `kind` 屬性所設定的標準端點名稱，該屬性會參考這個標準端點的其他組態資訊。</span><span class="sxs-lookup"><span data-stu-id="57d93-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="57d93-141">必須在 `<standardEndpoints>` 區段中定義相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="57d93-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="57d93-142">kind</span><span class="sxs-lookup"><span data-stu-id="57d93-142">kind</span></span>|<span data-ttu-id="57d93-143">字串，這個字串會指定所套用之標準端點的型別。</span><span class="sxs-lookup"><span data-stu-id="57d93-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="57d93-144">型別必須要在 `<extensions>` 區段或 machine.config 中註冊。如果未指定任何內容，則會建立一般通道端點。</span><span class="sxs-lookup"><span data-stu-id="57d93-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="57d93-145">name</span><span class="sxs-lookup"><span data-stu-id="57d93-145">name</span></span>|<span data-ttu-id="57d93-146">選擇性字串屬性。</span><span class="sxs-lookup"><span data-stu-id="57d93-146">Optional string attribute.</span></span> <span data-ttu-id="57d93-147">這個屬性可唯一識別指定合約的端點。</span><span class="sxs-lookup"><span data-stu-id="57d93-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="57d93-148">您可以為指定的合約類型定義多個用戶端。</span><span class="sxs-lookup"><span data-stu-id="57d93-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="57d93-149">每個定義必須使用唯一組態名稱來區別。</span><span class="sxs-lookup"><span data-stu-id="57d93-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="57d93-150">如果省略這個屬性，就會使用對應端點做為與所指定合約類型相關聯的預設端點。</span><span class="sxs-lookup"><span data-stu-id="57d93-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="57d93-151">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="57d93-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="57d93-152">繫結的 `name` 屬性用於透過 WSDL 進行的定義匯出。</span><span class="sxs-lookup"><span data-stu-id="57d93-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57d93-153">子元素</span><span class="sxs-lookup"><span data-stu-id="57d93-153">Child Elements</span></span>  
  
|<span data-ttu-id="57d93-154">項目</span><span class="sxs-lookup"><span data-stu-id="57d93-154">Element</span></span>|<span data-ttu-id="57d93-155">說明</span><span class="sxs-lookup"><span data-stu-id="57d93-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57d93-156">\<標頭 ></span><span class="sxs-lookup"><span data-stu-id="57d93-156">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="57d93-157">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="57d93-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="57d93-158">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="57d93-158">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="57d93-159">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="57d93-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57d93-160">父項目</span><span class="sxs-lookup"><span data-stu-id="57d93-160">Parent Elements</span></span>  
  
|<span data-ttu-id="57d93-161">項目</span><span class="sxs-lookup"><span data-stu-id="57d93-161">Element</span></span>|<span data-ttu-id="57d93-162">說明</span><span class="sxs-lookup"><span data-stu-id="57d93-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57d93-163">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="57d93-163">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="57d93-164">組態區段，它會定義用戶端可以連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="57d93-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="57d93-165">範例</span><span class="sxs-lookup"><span data-stu-id="57d93-165">Example</span></span>  
 <span data-ttu-id="57d93-166">這是通道端點組態的範例。</span><span class="sxs-lookup"><span data-stu-id="57d93-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    name="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
</endpoint>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57d93-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57d93-167">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>  
 <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 [<span data-ttu-id="57d93-168">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="57d93-168">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="57d93-169">用戶端</span><span class="sxs-lookup"><span data-stu-id="57d93-169">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
