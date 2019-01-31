---
title: <security> 的 <ws2007FederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: d533a930bfa57f523d7800205c230583559cb141
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272886"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="378ef-102">\<安全性 > 項目\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="378ef-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="378ef-103">定義的安全性設定[ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="378ef-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="378ef-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="378ef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="378ef-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="378ef-105">\<bindings></span></span>  
<span data-ttu-id="378ef-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="378ef-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="378ef-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="378ef-107">\<binding></span></span>  
<span data-ttu-id="378ef-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="378ef-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="378ef-109">語法</span><span class="sxs-lookup"><span data-stu-id="378ef-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="378ef-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="378ef-110">Attributes and Elements</span></span>  
 <span data-ttu-id="378ef-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="378ef-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="378ef-112">屬性</span><span class="sxs-lookup"><span data-stu-id="378ef-112">Attributes</span></span>  
  
|<span data-ttu-id="378ef-113">屬性</span><span class="sxs-lookup"><span data-stu-id="378ef-113">Attribute</span></span>|<span data-ttu-id="378ef-114">描述</span><span class="sxs-lookup"><span data-stu-id="378ef-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="378ef-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="378ef-115">Optional.</span></span> <span data-ttu-id="378ef-116">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="378ef-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="378ef-117">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="378ef-117">The default value is `Message`.</span></span> <span data-ttu-id="378ef-118">此屬性的型別為 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="378ef-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="378ef-119">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="378ef-119">mode Attribute</span></span>  
  
|<span data-ttu-id="378ef-120">值</span><span class="sxs-lookup"><span data-stu-id="378ef-120">Value</span></span>|<span data-ttu-id="378ef-121">描述</span><span class="sxs-lookup"><span data-stu-id="378ef-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="378ef-122">無</span><span class="sxs-lookup"><span data-stu-id="378ef-122">None</span></span>|<span data-ttu-id="378ef-123">傳輸期間的 SOAP 訊息是不安全的。</span><span class="sxs-lookup"><span data-stu-id="378ef-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="378ef-124">訊息</span><span class="sxs-lookup"><span data-stu-id="378ef-124">Message</span></span>|<span data-ttu-id="378ef-125">完整性、機密性、伺服器驗證與用戶端驗證都可透過 SOAP 訊息安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="378ef-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="378ef-126">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="378ef-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="378ef-127">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="378ef-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="378ef-128">用戶端驗證係以安全性權杖服務對用戶端發行的權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="378ef-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="378ef-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="378ef-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="378ef-130">完整性、機密性與伺服器驗證都是經由 HTTPS 來提供。</span><span class="sxs-lookup"><span data-stu-id="378ef-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="378ef-131">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="378ef-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="378ef-132">用戶端驗證係透過 SOAP 訊息安全性方式提供，並以安全性權杖服務發行給用戶端之權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="378ef-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="378ef-133">子元素</span><span class="sxs-lookup"><span data-stu-id="378ef-133">Child Elements</span></span>  
  
|<span data-ttu-id="378ef-134">項目</span><span class="sxs-lookup"><span data-stu-id="378ef-134">Element</span></span>|<span data-ttu-id="378ef-135">描述</span><span class="sxs-lookup"><span data-stu-id="378ef-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="378ef-136">\<message></span><span class="sxs-lookup"><span data-stu-id="378ef-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="378ef-137">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="378ef-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="378ef-138">此項目的型別為 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>。</span><span class="sxs-lookup"><span data-stu-id="378ef-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="378ef-139">父項目</span><span class="sxs-lookup"><span data-stu-id="378ef-139">Parent Elements</span></span>  
  
|<span data-ttu-id="378ef-140">項目</span><span class="sxs-lookup"><span data-stu-id="378ef-140">Element</span></span>|<span data-ttu-id="378ef-141">描述</span><span class="sxs-lookup"><span data-stu-id="378ef-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="378ef-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="378ef-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="378ef-143">定義的所有繫結功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="378ef-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="378ef-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="378ef-144">See also</span></span>
- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="378ef-145">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="378ef-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="378ef-146">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="378ef-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="378ef-147">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="378ef-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="378ef-148">繫結</span><span class="sxs-lookup"><span data-stu-id="378ef-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="378ef-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="378ef-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="378ef-150">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="378ef-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="378ef-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="378ef-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
