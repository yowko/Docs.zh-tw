---
title: <issuer> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 411fd1addb41822043d72de1edffee9f8733bc08
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256637"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="caa2a-102">\<issuer> of \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="caa2a-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="caa2a-103">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="caa2a-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="caa2a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="caa2a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="caa2a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="caa2a-105">\<bindings></span></span>  
<span data-ttu-id="caa2a-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="caa2a-106">\<customBinding></span></span>  
<span data-ttu-id="caa2a-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="caa2a-107">\<binding></span></span>  
<span data-ttu-id="caa2a-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="caa2a-108">\<security></span></span>  
<span data-ttu-id="caa2a-109">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="caa2a-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="caa2a-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="caa2a-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa2a-111">語法</span><span class="sxs-lookup"><span data-stu-id="caa2a-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="caa2a-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="caa2a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="caa2a-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="caa2a-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="caa2a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="caa2a-114">Attributes</span></span>  
  
|<span data-ttu-id="caa2a-115">屬性</span><span class="sxs-lookup"><span data-stu-id="caa2a-115">Attribute</span></span>|<span data-ttu-id="caa2a-116">描述</span><span class="sxs-lookup"><span data-stu-id="caa2a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="caa2a-117">address</span><span class="sxs-lookup"><span data-stu-id="caa2a-117">address</span></span>|<span data-ttu-id="caa2a-118">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="caa2a-118">Required string.</span></span> <span data-ttu-id="caa2a-119">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="caa2a-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="caa2a-120">子元素</span><span class="sxs-lookup"><span data-stu-id="caa2a-120">Child Elements</span></span>  
  
|<span data-ttu-id="caa2a-121">項目</span><span class="sxs-lookup"><span data-stu-id="caa2a-121">Element</span></span>|<span data-ttu-id="caa2a-122">描述</span><span class="sxs-lookup"><span data-stu-id="caa2a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="caa2a-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="caa2a-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="caa2a-124">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="caa2a-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="caa2a-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="caa2a-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="caa2a-126">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="caa2a-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="caa2a-127">父項目</span><span class="sxs-lookup"><span data-stu-id="caa2a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="caa2a-128">項目</span><span class="sxs-lookup"><span data-stu-id="caa2a-128">Element</span></span>|<span data-ttu-id="caa2a-129">描述</span><span class="sxs-lookup"><span data-stu-id="caa2a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="caa2a-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="caa2a-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="caa2a-131">指定目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="caa2a-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="caa2a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caa2a-132">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="caa2a-133">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="caa2a-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="caa2a-134">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="caa2a-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="caa2a-135">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="caa2a-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="caa2a-136">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="caa2a-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="caa2a-137">繫結</span><span class="sxs-lookup"><span data-stu-id="caa2a-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="caa2a-138">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="caa2a-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="caa2a-139">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="caa2a-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="caa2a-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="caa2a-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="caa2a-141">如何：建立自訂繫結使用 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="caa2a-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="caa2a-142">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="caa2a-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
