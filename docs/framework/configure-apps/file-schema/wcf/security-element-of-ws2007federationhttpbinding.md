---
title: <security> 的 <ws2007FederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738730"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="66641-102">\<ws2007FederationHttpBinding 的 \<安全性 > 元素 ></span><span class="sxs-lookup"><span data-stu-id="66641-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="66641-103">定義[\<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md)元素的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="66641-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="66641-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="66641-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="66641-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="66641-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="66641-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="66641-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="66641-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="66641-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="66641-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="66641-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="66641-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="66641-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66641-110">語法</span><span class="sxs-lookup"><span data-stu-id="66641-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66641-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="66641-111">Attributes and Elements</span></span>  
 <span data-ttu-id="66641-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="66641-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66641-113">屬性</span><span class="sxs-lookup"><span data-stu-id="66641-113">Attributes</span></span>  
  
|<span data-ttu-id="66641-114">屬性</span><span class="sxs-lookup"><span data-stu-id="66641-114">Attribute</span></span>|<span data-ttu-id="66641-115">描述</span><span class="sxs-lookup"><span data-stu-id="66641-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="66641-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="66641-116">Optional.</span></span> <span data-ttu-id="66641-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="66641-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="66641-118">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="66641-118">The default value is `Message`.</span></span> <span data-ttu-id="66641-119">此屬性的型別為 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="66641-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="66641-120">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="66641-120">mode Attribute</span></span>  
  
|<span data-ttu-id="66641-121">值</span><span class="sxs-lookup"><span data-stu-id="66641-121">Value</span></span>|<span data-ttu-id="66641-122">描述</span><span class="sxs-lookup"><span data-stu-id="66641-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="66641-123">None</span><span class="sxs-lookup"><span data-stu-id="66641-123">None</span></span>|<span data-ttu-id="66641-124">傳輸期間的 SOAP 訊息是不安全的。</span><span class="sxs-lookup"><span data-stu-id="66641-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="66641-125">訊息</span><span class="sxs-lookup"><span data-stu-id="66641-125">Message</span></span>|<span data-ttu-id="66641-126">完整性、機密性、伺服器驗證與用戶端驗證都可透過 SOAP 訊息安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="66641-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="66641-127">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="66641-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="66641-128">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="66641-128">The service must be configured with a certificate.</span></span> <span data-ttu-id="66641-129">用戶端驗證係以安全性權杖服務對用戶端發行的權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="66641-129">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="66641-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="66641-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="66641-131">完整性、機密性與伺服器驗證都是經由 HTTPS 來提供。</span><span class="sxs-lookup"><span data-stu-id="66641-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="66641-132">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="66641-132">The service must be configured with a certificate.</span></span> <span data-ttu-id="66641-133">用戶端驗證係透過 SOAP 訊息安全性方式提供，並以安全性權杖服務發行給用戶端之權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="66641-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66641-134">子項目</span><span class="sxs-lookup"><span data-stu-id="66641-134">Child Elements</span></span>  
  
|<span data-ttu-id="66641-135">項目</span><span class="sxs-lookup"><span data-stu-id="66641-135">Element</span></span>|<span data-ttu-id="66641-136">描述</span><span class="sxs-lookup"><span data-stu-id="66641-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66641-137">\<message ></span><span class="sxs-lookup"><span data-stu-id="66641-137">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="66641-138">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="66641-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="66641-139">此項目的型別為 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>。</span><span class="sxs-lookup"><span data-stu-id="66641-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66641-140">父項目</span><span class="sxs-lookup"><span data-stu-id="66641-140">Parent Elements</span></span>  
  
|<span data-ttu-id="66641-141">項目</span><span class="sxs-lookup"><span data-stu-id="66641-141">Element</span></span>|<span data-ttu-id="66641-142">描述</span><span class="sxs-lookup"><span data-stu-id="66641-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66641-143">\<binding ></span><span class="sxs-lookup"><span data-stu-id="66641-143">\<binding></span></span>](bindings.md)|<span data-ttu-id="66641-144">定義[\<wsDualHttpBinding >](wsdualhttpbinding.md)的所有系結功能。</span><span class="sxs-lookup"><span data-stu-id="66641-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66641-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="66641-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="66641-146">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="66641-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="66641-147">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="66641-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="66641-148">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="66641-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="66641-149">繫結</span><span class="sxs-lookup"><span data-stu-id="66641-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="66641-150">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="66641-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="66641-151">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="66641-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="66641-152">\<binding ></span><span class="sxs-lookup"><span data-stu-id="66641-152">\<binding></span></span>](bindings.md)
