---
title: "&lt;issuedTokenParameters&gt; 的 &lt;issuerMetadata&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e8df1ffb74c59bfed2b9fa2f1e87e7669fe3ad9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="7e3d9-102">&lt;issuedTokenParameters&gt; 的 &lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="7e3d9-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="7e3d9-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7e3d9-103">\<system.serviceModel></span></span>  
<span data-ttu-id="7e3d9-104">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7e3d9-104">\<bindings></span></span>  
<span data-ttu-id="7e3d9-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7e3d9-105">\<customBinding></span></span>  
<span data-ttu-id="7e3d9-106">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7e3d9-106">\<binding></span></span>  
<span data-ttu-id="7e3d9-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="7e3d9-107">\<security></span></span>  
<span data-ttu-id="7e3d9-108">\<></span><span class="sxs-lookup"><span data-stu-id="7e3d9-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="7e3d9-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="7e3d9-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e3d9-110">語法</span><span class="sxs-lookup"><span data-stu-id="7e3d9-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e3d9-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7e3d9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7e3d9-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7e3d9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e3d9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7e3d9-113">Attributes</span></span>  
  
|<span data-ttu-id="7e3d9-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7e3d9-114">Attribute</span></span>|<span data-ttu-id="7e3d9-115">描述</span><span class="sxs-lookup"><span data-stu-id="7e3d9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e3d9-116">address</span><span class="sxs-lookup"><span data-stu-id="7e3d9-116">address</span></span>|<span data-ttu-id="7e3d9-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="7e3d9-117">Required.</span></span> <span data-ttu-id="7e3d9-118">指定端點位址的字串。</span><span class="sxs-lookup"><span data-stu-id="7e3d9-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="7e3d9-119">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="7e3d9-119">The address must be an absolute URI.</span></span> <span data-ttu-id="7e3d9-120">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="7e3d9-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e3d9-121">子元素</span><span class="sxs-lookup"><span data-stu-id="7e3d9-121">Child Elements</span></span>  
  
|<span data-ttu-id="7e3d9-122">項目</span><span class="sxs-lookup"><span data-stu-id="7e3d9-122">Element</span></span>|<span data-ttu-id="7e3d9-123">說明</span><span class="sxs-lookup"><span data-stu-id="7e3d9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e3d9-124">\<標頭 ></span><span class="sxs-lookup"><span data-stu-id="7e3d9-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="7e3d9-125">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="7e3d9-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="7e3d9-126">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="7e3d9-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="7e3d9-127">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="7e3d9-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e3d9-128">父項目</span><span class="sxs-lookup"><span data-stu-id="7e3d9-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7e3d9-129">項目</span><span class="sxs-lookup"><span data-stu-id="7e3d9-129">Element</span></span>|<span data-ttu-id="7e3d9-130">說明</span><span class="sxs-lookup"><span data-stu-id="7e3d9-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e3d9-131">\<></span><span class="sxs-lookup"><span data-stu-id="7e3d9-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="7e3d9-132">指定在聯合安全性案例中核發之安全性權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="7e3d9-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e3d9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e3d9-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="7e3d9-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="7e3d9-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="7e3d9-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7e3d9-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="7e3d9-136">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="7e3d9-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="7e3d9-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="7e3d9-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="7e3d9-138">繫結</span><span class="sxs-lookup"><span data-stu-id="7e3d9-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7e3d9-139">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="7e3d9-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="7e3d9-140">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="7e3d9-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="7e3d9-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7e3d9-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="7e3d9-142">如何： 建立自訂繫結使用 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7e3d9-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="7e3d9-143">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="7e3d9-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
