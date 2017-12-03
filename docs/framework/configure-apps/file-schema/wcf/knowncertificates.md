---
title: '&lt;knownCertificates&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f62a43f1f8d3d025f62efca341c35e4af590abd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltknowncertificatesgt"></a><span data-ttu-id="724d5-102">&lt;knownCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="724d5-102">&lt;knownCertificates&gt;</span></span>
<span data-ttu-id="724d5-103">表示 X.509 憑證的集合，這些憑證是用來驗證由安全性權杖服務 (STS) 發行的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="724d5-103">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="724d5-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="724d5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="724d5-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="724d5-105">\<behaviors></span></span>  
<span data-ttu-id="724d5-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="724d5-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="724d5-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="724d5-107">\<behavior></span></span>  
<span data-ttu-id="724d5-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="724d5-108">\<serviceCredentials></span></span>  
<span data-ttu-id="724d5-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="724d5-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="724d5-110">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="724d5-110">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="724d5-111">語法</span><span class="sxs-lookup"><span data-stu-id="724d5-111">Syntax</span></span>  
  
```xml  
<knownCertificates>   
      <add findValue="String"  
         storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
           x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="724d5-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="724d5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="724d5-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="724d5-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="724d5-114">屬性</span><span class="sxs-lookup"><span data-stu-id="724d5-114">Attributes</span></span>  
 <span data-ttu-id="724d5-115">無。</span><span class="sxs-lookup"><span data-stu-id="724d5-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="724d5-116">子項目</span><span class="sxs-lookup"><span data-stu-id="724d5-116">Child Elements</span></span>  
  
|<span data-ttu-id="724d5-117">項目</span><span class="sxs-lookup"><span data-stu-id="724d5-117">Element</span></span>|<span data-ttu-id="724d5-118">描述</span><span class="sxs-lookup"><span data-stu-id="724d5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="724d5-119">\<add></span><span class="sxs-lookup"><span data-stu-id="724d5-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="724d5-120">將 X.509 憑證加入至集合。</span><span class="sxs-lookup"><span data-stu-id="724d5-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="724d5-121">父項目</span><span class="sxs-lookup"><span data-stu-id="724d5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="724d5-122">項目</span><span class="sxs-lookup"><span data-stu-id="724d5-122">Element</span></span>|<span data-ttu-id="724d5-123">說明</span><span class="sxs-lookup"><span data-stu-id="724d5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="724d5-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="724d5-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="724d5-125">指定發行為服務認證的權杖。</span><span class="sxs-lookup"><span data-stu-id="724d5-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="724d5-126">備註</span><span class="sxs-lookup"><span data-stu-id="724d5-126">Remarks</span></span>  
 <span data-ttu-id="724d5-127">發行之權杖的情況有三個階段。</span><span class="sxs-lookup"><span data-stu-id="724d5-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="724d5-128">在第一個階段中，用戶端會嘗試存取的服務指*安全權杖服務*。</span><span class="sxs-lookup"><span data-stu-id="724d5-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="724d5-129">此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。</span><span class="sxs-lookup"><span data-stu-id="724d5-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="724d5-130">用戶端接著會以權杖傳回服務。</span><span class="sxs-lookup"><span data-stu-id="724d5-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="724d5-131">此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="724d5-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="724d5-132">若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。</span><span class="sxs-lookup"><span data-stu-id="724d5-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="724d5-133">[ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)項目是任何此類安全權杖服務憑證的存放庫。</span><span class="sxs-lookup"><span data-stu-id="724d5-133">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="724d5-134">若要新增的憑證，請使用[ \<a d d > 項目](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="724d5-134">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="724d5-135">插入[\<新增 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)每個憑證，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="724d5-135">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="724d5-136">根據預設，必須從安全權杖服務取得憑證。</span><span class="sxs-lookup"><span data-stu-id="724d5-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="724d5-137">這些「已知的」憑證可確保只有合法的用戶端可以存取服務。</span><span class="sxs-lookup"><span data-stu-id="724d5-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="724d5-138">若要檢閱要由同盟的服務，如需有關使用這個組態項目驗證用戶端所需的條件，請參閱[How to： 設定聯合服務的認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="724d5-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="724d5-139">如需聯合案例的詳細資訊，請參閱[同盟和發出的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="724d5-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="724d5-140">如需示範如何在組態中的集合中填入的範例，請參閱[\<新增 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="724d5-140">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724d5-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="724d5-141">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [<span data-ttu-id="724d5-142">\<add></span><span class="sxs-lookup"><span data-stu-id="724d5-142">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="724d5-143">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="724d5-143">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="724d5-144">安全性行為</span><span class="sxs-lookup"><span data-stu-id="724d5-144">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="724d5-145">如何： 設定聯合服務認證</span><span class="sxs-lookup"><span data-stu-id="724d5-145">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="724d5-146">使用憑證</span><span class="sxs-lookup"><span data-stu-id="724d5-146">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="724d5-147">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="724d5-147">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="724d5-148">\<add></span><span class="sxs-lookup"><span data-stu-id="724d5-148">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="724d5-149">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="724d5-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
