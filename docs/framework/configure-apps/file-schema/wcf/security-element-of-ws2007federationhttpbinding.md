---
title: <security> 的 <ws2007FederationHttpBinding> 項目
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738730"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="90638-102">\<security> 的 \<ws2007FederationHttpBinding> 項目</span><span class="sxs-lookup"><span data-stu-id="90638-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="90638-103">定義元素的安全性設定 [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="90638-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="90638-104">語法</span><span class="sxs-lookup"><span data-stu-id="90638-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90638-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="90638-105">Attributes and Elements</span></span>  
 <span data-ttu-id="90638-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="90638-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90638-107">屬性</span><span class="sxs-lookup"><span data-stu-id="90638-107">Attributes</span></span>  
  
|<span data-ttu-id="90638-108">屬性</span><span class="sxs-lookup"><span data-stu-id="90638-108">Attribute</span></span>|<span data-ttu-id="90638-109">描述</span><span class="sxs-lookup"><span data-stu-id="90638-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="90638-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="90638-110">Optional.</span></span> <span data-ttu-id="90638-111">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="90638-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="90638-112">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="90638-112">The default value is `Message`.</span></span> <span data-ttu-id="90638-113">此屬性的型別為 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="90638-113">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="90638-114">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="90638-114">mode Attribute</span></span>  
  
|<span data-ttu-id="90638-115">值</span><span class="sxs-lookup"><span data-stu-id="90638-115">Value</span></span>|<span data-ttu-id="90638-116">描述</span><span class="sxs-lookup"><span data-stu-id="90638-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="90638-117">None</span><span class="sxs-lookup"><span data-stu-id="90638-117">None</span></span>|<span data-ttu-id="90638-118">傳輸期間的 SOAP 訊息是不安全的。</span><span class="sxs-lookup"><span data-stu-id="90638-118">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="90638-119">訊息</span><span class="sxs-lookup"><span data-stu-id="90638-119">Message</span></span>|<span data-ttu-id="90638-120">完整性、機密性、伺服器驗證與用戶端驗證都可透過 SOAP 訊息安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="90638-120">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="90638-121">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="90638-121">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="90638-122">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="90638-122">The service must be configured with a certificate.</span></span> <span data-ttu-id="90638-123">用戶端驗證係以安全性權杖服務對用戶端發行的權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="90638-123">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="90638-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="90638-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="90638-125">完整性、機密性與伺服器驗證都是經由 HTTPS 來提供。</span><span class="sxs-lookup"><span data-stu-id="90638-125">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="90638-126">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="90638-126">The service must be configured with a certificate.</span></span> <span data-ttu-id="90638-127">用戶端驗證係透過 SOAP 訊息安全性方式提供，並以安全性權杖服務發行給用戶端之權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="90638-127">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90638-128">子元素</span><span class="sxs-lookup"><span data-stu-id="90638-128">Child Elements</span></span>  
  
|<span data-ttu-id="90638-129">元素</span><span class="sxs-lookup"><span data-stu-id="90638-129">Element</span></span>|<span data-ttu-id="90638-130">描述</span><span class="sxs-lookup"><span data-stu-id="90638-130">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="90638-131">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="90638-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="90638-132">此項目的型別為 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>。</span><span class="sxs-lookup"><span data-stu-id="90638-132">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90638-133">父項目</span><span class="sxs-lookup"><span data-stu-id="90638-133">Parent Elements</span></span>  
  
|<span data-ttu-id="90638-134">元素</span><span class="sxs-lookup"><span data-stu-id="90638-134">Element</span></span>|<span data-ttu-id="90638-135">描述</span><span class="sxs-lookup"><span data-stu-id="90638-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="90638-136">定義的所有系結功能 [\<wsDualHttpBinding>](wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="90638-136">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90638-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90638-137">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="90638-138">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="90638-138">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="90638-139">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="90638-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="90638-140">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="90638-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="90638-141">繫結</span><span class="sxs-lookup"><span data-stu-id="90638-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="90638-142">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="90638-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="90638-143">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="90638-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
