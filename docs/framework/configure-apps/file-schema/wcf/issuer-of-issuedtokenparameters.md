---
title: '&lt;issuedTokenParameters&gt; 的 &lt;issuer&gt;'
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: aa647f448bad74e25ffce4a5622c7489274996c7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151133"
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="74689-102">&lt;issuedTokenParameters&gt; 的 &lt;issuer&gt;</span><span class="sxs-lookup"><span data-stu-id="74689-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="74689-103">指定發行安全性權杖的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="74689-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="74689-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="74689-104">\<system.serviceModel></span></span>  
<span data-ttu-id="74689-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="74689-105">\<bindings></span></span>  
<span data-ttu-id="74689-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="74689-106">\<customBinding></span></span>  
<span data-ttu-id="74689-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="74689-107">\<binding></span></span>  
<span data-ttu-id="74689-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="74689-108">\<security></span></span>  
<span data-ttu-id="74689-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="74689-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="74689-110">\<簽發者 ></span><span class="sxs-lookup"><span data-stu-id="74689-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74689-111">語法</span><span class="sxs-lookup"><span data-stu-id="74689-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74689-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="74689-112">Attributes and Elements</span></span>  
 <span data-ttu-id="74689-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="74689-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74689-114">屬性</span><span class="sxs-lookup"><span data-stu-id="74689-114">Attributes</span></span>  
  
|<span data-ttu-id="74689-115">屬性</span><span class="sxs-lookup"><span data-stu-id="74689-115">Attribute</span></span>|<span data-ttu-id="74689-116">描述</span><span class="sxs-lookup"><span data-stu-id="74689-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74689-117">address</span><span class="sxs-lookup"><span data-stu-id="74689-117">address</span></span>|<span data-ttu-id="74689-118">必要的字串。</span><span class="sxs-lookup"><span data-stu-id="74689-118">Required string.</span></span> <span data-ttu-id="74689-119">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="74689-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74689-120">子元素</span><span class="sxs-lookup"><span data-stu-id="74689-120">Child Elements</span></span>  
  
|<span data-ttu-id="74689-121">項目</span><span class="sxs-lookup"><span data-stu-id="74689-121">Element</span></span>|<span data-ttu-id="74689-122">描述</span><span class="sxs-lookup"><span data-stu-id="74689-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74689-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="74689-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="74689-124">建置器可建立之端點的位址標頭集合。</span><span class="sxs-lookup"><span data-stu-id="74689-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="74689-125">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="74689-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="74689-126">使用發行的權杖時，指定可讓用戶端驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="74689-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74689-127">父項目</span><span class="sxs-lookup"><span data-stu-id="74689-127">Parent Elements</span></span>  
  
|<span data-ttu-id="74689-128">項目</span><span class="sxs-lookup"><span data-stu-id="74689-128">Element</span></span>|<span data-ttu-id="74689-129">描述</span><span class="sxs-lookup"><span data-stu-id="74689-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74689-130">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="74689-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="74689-131">指定目前發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="74689-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74689-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74689-132">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="74689-133">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="74689-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="74689-134">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="74689-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="74689-135">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="74689-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="74689-136">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="74689-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="74689-137">繫結</span><span class="sxs-lookup"><span data-stu-id="74689-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="74689-138">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="74689-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="74689-139">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="74689-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="74689-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="74689-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="74689-141">如何：建立自訂繫結使用 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="74689-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="74689-142">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="74689-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
