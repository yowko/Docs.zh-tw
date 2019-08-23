---
title: <issuerMetadata> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: d9d7d41277eff1de43f717816b35fdc10d52192e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928882"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="6113b-102">\<issuermetadata > 的\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="6113b-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>
<span data-ttu-id="6113b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6113b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="6113b-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6113b-104">\<bindings></span></span>  
<span data-ttu-id="6113b-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6113b-105">\<customBinding></span></span>  
<span data-ttu-id="6113b-106">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="6113b-106">\<binding></span></span>  
<span data-ttu-id="6113b-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="6113b-107">\<security></span></span>  
<span data-ttu-id="6113b-108">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="6113b-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="6113b-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="6113b-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6113b-110">語法</span><span class="sxs-lookup"><span data-stu-id="6113b-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6113b-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6113b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6113b-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6113b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6113b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6113b-113">Attributes</span></span>  
  
|<span data-ttu-id="6113b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="6113b-114">Attribute</span></span>|<span data-ttu-id="6113b-115">描述</span><span class="sxs-lookup"><span data-stu-id="6113b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6113b-116">位址</span><span class="sxs-lookup"><span data-stu-id="6113b-116">address</span></span>|<span data-ttu-id="6113b-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="6113b-117">Required.</span></span> <span data-ttu-id="6113b-118">指定端點位址的字串。</span><span class="sxs-lookup"><span data-stu-id="6113b-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="6113b-119">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="6113b-119">The address must be an absolute URI.</span></span> <span data-ttu-id="6113b-120">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="6113b-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6113b-121">子元素</span><span class="sxs-lookup"><span data-stu-id="6113b-121">Child Elements</span></span>  
  
|<span data-ttu-id="6113b-122">項目</span><span class="sxs-lookup"><span data-stu-id="6113b-122">Element</span></span>|<span data-ttu-id="6113b-123">說明</span><span class="sxs-lookup"><span data-stu-id="6113b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6113b-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="6113b-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="6113b-125">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="6113b-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="6113b-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="6113b-126">\<identity></span></span>](identity.md)|<span data-ttu-id="6113b-127">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="6113b-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6113b-128">父項目</span><span class="sxs-lookup"><span data-stu-id="6113b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="6113b-129">項目</span><span class="sxs-lookup"><span data-stu-id="6113b-129">Element</span></span>|<span data-ttu-id="6113b-130">描述</span><span class="sxs-lookup"><span data-stu-id="6113b-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6113b-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="6113b-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="6113b-132">指定在聯合安全性案例中核發之安全性權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="6113b-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6113b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6113b-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6113b-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="6113b-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6113b-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="6113b-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6113b-136">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="6113b-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="6113b-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="6113b-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6113b-138">繫結</span><span class="sxs-lookup"><span data-stu-id="6113b-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6113b-139">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="6113b-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6113b-140">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="6113b-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="6113b-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6113b-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="6113b-142">如何：使用 SecurityBindingElement 建立自訂系結</span><span class="sxs-lookup"><span data-stu-id="6113b-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="6113b-143">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="6113b-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
