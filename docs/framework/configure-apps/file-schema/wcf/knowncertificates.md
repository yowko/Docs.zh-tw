---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400328"
---
# <a name="knowncertificates"></a><span data-ttu-id="16a42-101">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="16a42-101">\<knownCertificates></span></span>
<span data-ttu-id="16a42-102">表示 X.509 憑證的集合，這些憑證是用來驗證由安全性權杖服務 (STS) 發行的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="16a42-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
<span data-ttu-id="16a42-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="16a42-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="16a42-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="16a42-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="16a42-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="16a42-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="16a42-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="16a42-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="16a42-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="16a42-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="16a42-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="16a42-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="16a42-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<n >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="16a42-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="16a42-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownCertificates >**</span><span class="sxs-lookup"><span data-stu-id="16a42-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16a42-111">語法</span><span class="sxs-lookup"><span data-stu-id="16a42-111">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16a42-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="16a42-112">Attributes and Elements</span></span>  
 <span data-ttu-id="16a42-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="16a42-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16a42-114">屬性</span><span class="sxs-lookup"><span data-stu-id="16a42-114">Attributes</span></span>  
 <span data-ttu-id="16a42-115">無。</span><span class="sxs-lookup"><span data-stu-id="16a42-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="16a42-116">子元素</span><span class="sxs-lookup"><span data-stu-id="16a42-116">Child Elements</span></span>  
  
|<span data-ttu-id="16a42-117">項目</span><span class="sxs-lookup"><span data-stu-id="16a42-117">Element</span></span>|<span data-ttu-id="16a42-118">描述</span><span class="sxs-lookup"><span data-stu-id="16a42-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16a42-119">\<add></span><span class="sxs-lookup"><span data-stu-id="16a42-119">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="16a42-120">將 X.509 憑證加入至集合。</span><span class="sxs-lookup"><span data-stu-id="16a42-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16a42-121">父項目</span><span class="sxs-lookup"><span data-stu-id="16a42-121">Parent Elements</span></span>  
  
|<span data-ttu-id="16a42-122">項目</span><span class="sxs-lookup"><span data-stu-id="16a42-122">Element</span></span>|<span data-ttu-id="16a42-123">描述</span><span class="sxs-lookup"><span data-stu-id="16a42-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16a42-124">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="16a42-124">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="16a42-125">指定發行為服務認證的權杖。</span><span class="sxs-lookup"><span data-stu-id="16a42-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16a42-126">備註</span><span class="sxs-lookup"><span data-stu-id="16a42-126">Remarks</span></span>  
 <span data-ttu-id="16a42-127">發行之權杖的情況有三個階段。</span><span class="sxs-lookup"><span data-stu-id="16a42-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="16a42-128">在第一個階段中，嘗試存取服務的用戶端稱為「*安全權杖服務*」。</span><span class="sxs-lookup"><span data-stu-id="16a42-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="16a42-129">此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。</span><span class="sxs-lookup"><span data-stu-id="16a42-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="16a42-130">用戶端接著會以權杖傳回服務。</span><span class="sxs-lookup"><span data-stu-id="16a42-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="16a42-131">此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="16a42-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="16a42-132">若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。</span><span class="sxs-lookup"><span data-stu-id="16a42-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="16a42-133">N > 元素是任何此類安全權杖服務憑證的存放庫。 [ \< ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="16a42-133">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="16a42-134">若要新增憑證，請使用[ \<knownCertificates > 元素](knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="16a42-134">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="16a42-135">為每個憑證插入「 [新增>，如下列範例所示。\< ](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="16a42-135">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="16a42-136">根據預設，必須從安全權杖服務取得憑證。</span><span class="sxs-lookup"><span data-stu-id="16a42-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="16a42-137">這些「已知的」憑證可確保只有合法的用戶端可以存取服務。</span><span class="sxs-lookup"><span data-stu-id="16a42-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="16a42-138">若要檢查同盟服務驗證用戶端所需的條件，以及使用此設定元素的詳細資訊，請參閱[如何：在同盟服務](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)上設定認證。</span><span class="sxs-lookup"><span data-stu-id="16a42-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="16a42-139">如需聯合案例的詳細資訊，請參閱[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="16a42-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="16a42-140">如需示範如何在設定中填入集合的範例，請參閱[ \<add >](add-of-knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="16a42-140">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a42-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16a42-141">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="16a42-142">\<add></span><span class="sxs-lookup"><span data-stu-id="16a42-142">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="16a42-143">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="16a42-143">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="16a42-144">安全性行為</span><span class="sxs-lookup"><span data-stu-id="16a42-144">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="16a42-145">如何：在同盟服務上設定認證</span><span class="sxs-lookup"><span data-stu-id="16a42-145">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="16a42-146">使用憑證</span><span class="sxs-lookup"><span data-stu-id="16a42-146">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="16a42-147">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="16a42-147">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="16a42-148">\<add></span><span class="sxs-lookup"><span data-stu-id="16a42-148">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="16a42-149">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="16a42-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
