---
title: '&lt;ws2007FederationHttpBinding&gt; 的 &lt;security&gt; 項目'
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 87f8f3cf296aeb30cd19c7579887ef94e0992ba7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194977"
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="13e5b-102">&lt;ws2007FederationHttpBinding&gt; 的 &lt;security&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="13e5b-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="13e5b-103">定義的安全性設定[ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="13e5b-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="13e5b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="13e5b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="13e5b-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="13e5b-105">\<bindings></span></span>  
<span data-ttu-id="13e5b-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="13e5b-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="13e5b-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="13e5b-107">\<binding></span></span>  
<span data-ttu-id="13e5b-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="13e5b-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e5b-109">語法</span><span class="sxs-lookup"><span data-stu-id="13e5b-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13e5b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="13e5b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="13e5b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="13e5b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13e5b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="13e5b-112">Attributes</span></span>  
  
|<span data-ttu-id="13e5b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="13e5b-113">Attribute</span></span>|<span data-ttu-id="13e5b-114">描述</span><span class="sxs-lookup"><span data-stu-id="13e5b-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="13e5b-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="13e5b-115">Optional.</span></span> <span data-ttu-id="13e5b-116">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="13e5b-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="13e5b-117">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="13e5b-117">The default value is `Message`.</span></span> <span data-ttu-id="13e5b-118">此屬性的型別為 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="13e5b-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="13e5b-119">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="13e5b-119">mode Attribute</span></span>  
  
|<span data-ttu-id="13e5b-120">值</span><span class="sxs-lookup"><span data-stu-id="13e5b-120">Value</span></span>|<span data-ttu-id="13e5b-121">描述</span><span class="sxs-lookup"><span data-stu-id="13e5b-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13e5b-122">無</span><span class="sxs-lookup"><span data-stu-id="13e5b-122">None</span></span>|<span data-ttu-id="13e5b-123">傳輸期間的 SOAP 訊息是不安全的。</span><span class="sxs-lookup"><span data-stu-id="13e5b-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="13e5b-124">訊息</span><span class="sxs-lookup"><span data-stu-id="13e5b-124">Message</span></span>|<span data-ttu-id="13e5b-125">完整性、機密性、伺服器驗證與用戶端驗證都可透過 SOAP 訊息安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="13e5b-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="13e5b-126">根據預設，本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="13e5b-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="13e5b-127">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="13e5b-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="13e5b-128">用戶端驗證係以安全性權杖服務對用戶端發行的權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="13e5b-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="13e5b-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="13e5b-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="13e5b-130">完整性、機密性與伺服器驗證都是經由 HTTPS 來提供。</span><span class="sxs-lookup"><span data-stu-id="13e5b-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="13e5b-131">服務必須使用憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="13e5b-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="13e5b-132">用戶端驗證係透過 SOAP 訊息安全性方式提供，並以安全性權杖服務發行給用戶端之權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="13e5b-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13e5b-133">子元素</span><span class="sxs-lookup"><span data-stu-id="13e5b-133">Child Elements</span></span>  
  
|<span data-ttu-id="13e5b-134">項目</span><span class="sxs-lookup"><span data-stu-id="13e5b-134">Element</span></span>|<span data-ttu-id="13e5b-135">描述</span><span class="sxs-lookup"><span data-stu-id="13e5b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13e5b-136">\<message></span><span class="sxs-lookup"><span data-stu-id="13e5b-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="13e5b-137">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="13e5b-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="13e5b-138">此項目的型別為 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>。</span><span class="sxs-lookup"><span data-stu-id="13e5b-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13e5b-139">父項目</span><span class="sxs-lookup"><span data-stu-id="13e5b-139">Parent Elements</span></span>  
  
|<span data-ttu-id="13e5b-140">項目</span><span class="sxs-lookup"><span data-stu-id="13e5b-140">Element</span></span>|<span data-ttu-id="13e5b-141">描述</span><span class="sxs-lookup"><span data-stu-id="13e5b-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13e5b-142">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="13e5b-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="13e5b-143">定義的所有繫結功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="13e5b-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13e5b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13e5b-144">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="13e5b-145">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="13e5b-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="13e5b-146">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="13e5b-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="13e5b-147">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="13e5b-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="13e5b-148">繫結</span><span class="sxs-lookup"><span data-stu-id="13e5b-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="13e5b-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="13e5b-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="13e5b-150">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="13e5b-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="13e5b-151">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="13e5b-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
