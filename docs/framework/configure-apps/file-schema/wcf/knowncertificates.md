---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 1210e6282a7dd6c40198693d4948a89efe841d59
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913532"
---
# <a name="knowncertificates"></a><span data-ttu-id="a26bf-101">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="a26bf-101">\<knownCertificates></span></span>
<span data-ttu-id="a26bf-102">表示 X.509 憑證的集合，這些憑證是用來驗證由安全性權杖服務 (STS) 發行的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="a26bf-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="a26bf-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a26bf-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a26bf-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="a26bf-104">\<behaviors></span></span>  
<span data-ttu-id="a26bf-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a26bf-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="a26bf-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="a26bf-106">\<behavior></span></span>  
<span data-ttu-id="a26bf-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a26bf-107">\<serviceCredentials></span></span>  
<span data-ttu-id="a26bf-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="a26bf-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="a26bf-109">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="a26bf-109">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a26bf-110">語法</span><span class="sxs-lookup"><span data-stu-id="a26bf-110">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a26bf-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a26bf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a26bf-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="a26bf-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a26bf-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a26bf-113">Attributes</span></span>  
 <span data-ttu-id="a26bf-114">無。</span><span class="sxs-lookup"><span data-stu-id="a26bf-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a26bf-115">子元素</span><span class="sxs-lookup"><span data-stu-id="a26bf-115">Child Elements</span></span>  
  
|<span data-ttu-id="a26bf-116">項目</span><span class="sxs-lookup"><span data-stu-id="a26bf-116">Element</span></span>|<span data-ttu-id="a26bf-117">描述</span><span class="sxs-lookup"><span data-stu-id="a26bf-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a26bf-118">\<add></span><span class="sxs-lookup"><span data-stu-id="a26bf-118">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="a26bf-119">將 X.509 憑證加入至集合。</span><span class="sxs-lookup"><span data-stu-id="a26bf-119">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a26bf-120">父項目</span><span class="sxs-lookup"><span data-stu-id="a26bf-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a26bf-121">項目</span><span class="sxs-lookup"><span data-stu-id="a26bf-121">Element</span></span>|<span data-ttu-id="a26bf-122">描述</span><span class="sxs-lookup"><span data-stu-id="a26bf-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a26bf-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="a26bf-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="a26bf-124">指定發行為服務認證的權杖。</span><span class="sxs-lookup"><span data-stu-id="a26bf-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a26bf-125">備註</span><span class="sxs-lookup"><span data-stu-id="a26bf-125">Remarks</span></span>  
 <span data-ttu-id="a26bf-126">發行之權杖的情況有三個階段。</span><span class="sxs-lookup"><span data-stu-id="a26bf-126">The issued token scenario has three stages.</span></span> <span data-ttu-id="a26bf-127">在第一個階段中, 嘗試存取服務的用戶端稱為「*安全權杖服務*」。</span><span class="sxs-lookup"><span data-stu-id="a26bf-127">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="a26bf-128">此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。</span><span class="sxs-lookup"><span data-stu-id="a26bf-128">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="a26bf-129">用戶端接著會以權杖傳回服務。</span><span class="sxs-lookup"><span data-stu-id="a26bf-129">The client then returns to the service with the token.</span></span> <span data-ttu-id="a26bf-130">此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="a26bf-130">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="a26bf-131">若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。</span><span class="sxs-lookup"><span data-stu-id="a26bf-131">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="a26bf-132">N > 元素是任何此類安全權杖服務憑證的存放庫。 [ \< ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="a26bf-132">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="a26bf-133">若要新增憑證, 請使用[ \<knownCertificates > 元素](knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="a26bf-133">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="a26bf-134">為每個憑證插入「 [新增>,如下列範例所示。\< ](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="a26bf-134">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a26bf-135">根據預設，必須從安全權杖服務取得憑證。</span><span class="sxs-lookup"><span data-stu-id="a26bf-135">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="a26bf-136">這些「已知的」憑證可確保只有合法的用戶端可以存取服務。</span><span class="sxs-lookup"><span data-stu-id="a26bf-136">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="a26bf-137">若要檢查同盟服務驗證用戶端所需的條件, 以及使用此設定元素的詳細資訊, 請參閱[如何:在同盟服務](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)上設定認證。</span><span class="sxs-lookup"><span data-stu-id="a26bf-137">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="a26bf-138">如需聯合案例的詳細資訊, 請參閱[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="a26bf-138">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="a26bf-139">如需示範如何在設定中填入集合的範例, 請參閱[ \<add >](add-of-knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="a26bf-139">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a26bf-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a26bf-140">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="a26bf-141">\<add></span><span class="sxs-lookup"><span data-stu-id="a26bf-141">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="a26bf-142">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="a26bf-142">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="a26bf-143">安全性行為</span><span class="sxs-lookup"><span data-stu-id="a26bf-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a26bf-144">如何：在同盟服務上設定認證</span><span class="sxs-lookup"><span data-stu-id="a26bf-144">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="a26bf-145">使用憑證</span><span class="sxs-lookup"><span data-stu-id="a26bf-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a26bf-146">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="a26bf-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a26bf-147">\<add></span><span class="sxs-lookup"><span data-stu-id="a26bf-147">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="a26bf-148">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a26bf-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
