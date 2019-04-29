---
title: <issuerMetadata> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: e46e56c6285af24941a550b2c4f7dec3b441db69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764097"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="46176-102">\<issuerMetadata> of \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="46176-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>
<span data-ttu-id="46176-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="46176-103">\<system.serviceModel></span></span>  
<span data-ttu-id="46176-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="46176-104">\<bindings></span></span>  
<span data-ttu-id="46176-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="46176-105">\<customBinding></span></span>  
<span data-ttu-id="46176-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="46176-106">\<binding></span></span>  
<span data-ttu-id="46176-107">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="46176-107">\<security></span></span>  
<span data-ttu-id="46176-108">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="46176-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="46176-109">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="46176-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46176-110">語法</span><span class="sxs-lookup"><span data-stu-id="46176-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46176-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="46176-111">Attributes and Elements</span></span>  
 <span data-ttu-id="46176-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="46176-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46176-113">屬性</span><span class="sxs-lookup"><span data-stu-id="46176-113">Attributes</span></span>  
  
|<span data-ttu-id="46176-114">屬性</span><span class="sxs-lookup"><span data-stu-id="46176-114">Attribute</span></span>|<span data-ttu-id="46176-115">描述</span><span class="sxs-lookup"><span data-stu-id="46176-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46176-116">位址</span><span class="sxs-lookup"><span data-stu-id="46176-116">address</span></span>|<span data-ttu-id="46176-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="46176-117">Required.</span></span> <span data-ttu-id="46176-118">指定端點位址的字串。</span><span class="sxs-lookup"><span data-stu-id="46176-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="46176-119">位址必須是絕對 URI。</span><span class="sxs-lookup"><span data-stu-id="46176-119">The address must be an absolute URI.</span></span> <span data-ttu-id="46176-120">預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="46176-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46176-121">子元素</span><span class="sxs-lookup"><span data-stu-id="46176-121">Child Elements</span></span>  
  
|<span data-ttu-id="46176-122">項目</span><span class="sxs-lookup"><span data-stu-id="46176-122">Element</span></span>|<span data-ttu-id="46176-123">描述</span><span class="sxs-lookup"><span data-stu-id="46176-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46176-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="46176-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="46176-125">位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="46176-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="46176-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="46176-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="46176-127">身分識別，可讓其他端點與此端點交換訊息，以啟用端點的驗證。</span><span class="sxs-lookup"><span data-stu-id="46176-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46176-128">父項目</span><span class="sxs-lookup"><span data-stu-id="46176-128">Parent Elements</span></span>  
  
|<span data-ttu-id="46176-129">項目</span><span class="sxs-lookup"><span data-stu-id="46176-129">Element</span></span>|<span data-ttu-id="46176-130">描述</span><span class="sxs-lookup"><span data-stu-id="46176-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46176-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="46176-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="46176-132">指定在聯合安全性案例中核發之安全性權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="46176-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46176-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46176-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="46176-134">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="46176-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="46176-135">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="46176-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="46176-136">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="46176-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="46176-137">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="46176-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="46176-138">繫結</span><span class="sxs-lookup"><span data-stu-id="46176-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="46176-139">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="46176-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="46176-140">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="46176-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="46176-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="46176-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="46176-142">如何：建立自訂繫結使用 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="46176-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="46176-143">自訂繫結安全性</span><span class="sxs-lookup"><span data-stu-id="46176-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
