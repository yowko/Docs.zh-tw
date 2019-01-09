---
title: '&lt;issuedTokenParameters&gt; 的 &lt;issuerMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 76956c54739219bbde78f378a12d59563ab785c4
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148743"
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="b75c5-102">&lt;issuedTokenParameters&gt; 的 &lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="b75c5-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="b75c5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b75c5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="b75c5-104">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="b75c5-104">\<bindings></span></span>  
<span data-ttu-id="b75c5-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b75c5-105">\<customBinding></span></span>  
<span data-ttu-id="b75c5-106">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="b75c5-106">\<binding></span></span>  
<span data-ttu-id="b75c5-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="b75c5-107">\<security></span></span>  
<span data-ttu-id="b75c5-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="b75c5-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="b75c5-109">\<s ></span><span class="sxs-lookup"><span data-stu-id="b75c5-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b75c5-110">語法</span><span class="sxs-lookup"><span data-stu-id="b75c5-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b75c5-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b75c5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b75c5-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b75c5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b75c5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b75c5-113">Attributes</span></span>  
  
|<span data-ttu-id="b75c5-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b75c5-114">Attribute</span></span>|<span data-ttu-id="b75c5-115">描述</span><span class="sxs-lookup"><span data-stu-id="b75c5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b75c5-116">address</span><span class="sxs-lookup"><span data-stu-id="b75c5-116">address</span></span>|<span data-ttu-id="b75c5-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="b75c5-117">Required.</span></span> <span data-ttu-id="b75c5-118">指定端點位址的字串。</span><span class="sxs-lookup"><span data-stu-id="b75c5-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="b75c5-119">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="b75c5-119">The address must be an absolute URI.</span></span> <span data-ttu-id="b75c5-120">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="b75c5-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b75c5-121">子元素</span><span class="sxs-lookup"><span data-stu-id="b75c5-121">Child Elements</span></span>  
  
|<span data-ttu-id="b75c5-122">項目</span><span class="sxs-lookup"><span data-stu-id="b75c5-122">Element</span></span>|<span data-ttu-id="b75c5-123">描述</span><span class="sxs-lookup"><span data-stu-id="b75c5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b75c5-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="b75c5-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="b75c5-125">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="b75c5-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="b75c5-126">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="b75c5-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b75c5-127">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="b75c5-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b75c5-128">父項目</span><span class="sxs-lookup"><span data-stu-id="b75c5-128">Parent Elements</span></span>  
  
|<span data-ttu-id="b75c5-129">項目</span><span class="sxs-lookup"><span data-stu-id="b75c5-129">Element</span></span>|<span data-ttu-id="b75c5-130">描述</span><span class="sxs-lookup"><span data-stu-id="b75c5-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b75c5-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="b75c5-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="b75c5-132">指定在聯合安全性案例中核發之安全性權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="b75c5-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b75c5-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b75c5-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="b75c5-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="b75c5-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b75c5-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="b75c5-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b75c5-136">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="b75c5-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="b75c5-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="b75c5-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b75c5-138">繫結</span><span class="sxs-lookup"><span data-stu-id="b75c5-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b75c5-139">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="b75c5-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b75c5-140">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="b75c5-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b75c5-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b75c5-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="b75c5-142">如何：建立自訂繫結使用 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b75c5-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="b75c5-143">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="b75c5-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
