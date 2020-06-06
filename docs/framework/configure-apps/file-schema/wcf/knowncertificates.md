---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400328"
---
# \<knownCertificates>
<span data-ttu-id="5f1b5-101">表示 X.509 憑證的集合，這些憑證是用來驗證由安全性權杖服務 (STS) 發行的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-101">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="5f1b5-102">語法</span><span class="sxs-lookup"><span data-stu-id="5f1b5-102">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f1b5-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f1b5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5f1b5-104">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="5f1b5-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f1b5-105">屬性</span><span class="sxs-lookup"><span data-stu-id="5f1b5-105">Attributes</span></span>  
 <span data-ttu-id="5f1b5-106">無。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f1b5-107">子元素</span><span class="sxs-lookup"><span data-stu-id="5f1b5-107">Child Elements</span></span>  
  
|<span data-ttu-id="5f1b5-108">元素</span><span class="sxs-lookup"><span data-stu-id="5f1b5-108">Element</span></span>|<span data-ttu-id="5f1b5-109">描述</span><span class="sxs-lookup"><span data-stu-id="5f1b5-109">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|<span data-ttu-id="5f1b5-110">將 X.509 憑證加入至集合。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-110">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f1b5-111">父項目</span><span class="sxs-lookup"><span data-stu-id="5f1b5-111">Parent Elements</span></span>  
  
|<span data-ttu-id="5f1b5-112">元素</span><span class="sxs-lookup"><span data-stu-id="5f1b5-112">Element</span></span>|<span data-ttu-id="5f1b5-113">描述</span><span class="sxs-lookup"><span data-stu-id="5f1b5-113">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="5f1b5-114">指定發行為服務認證的權杖。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-114">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f1b5-115">備註</span><span class="sxs-lookup"><span data-stu-id="5f1b5-115">Remarks</span></span>  
 <span data-ttu-id="5f1b5-116">發行之權杖的情況有三個階段。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-116">The issued token scenario has three stages.</span></span> <span data-ttu-id="5f1b5-117">在第一個階段中，嘗試存取服務的用戶端稱為「*安全權杖服務*」。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-117">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="5f1b5-118">此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-118">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="5f1b5-119">用戶端接著會以權杖傳回服務。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-119">The client then returns to the service with the token.</span></span> <span data-ttu-id="5f1b5-120">此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-120">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="5f1b5-121">若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-121">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="5f1b5-122">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)元素是任何此類安全權杖服務憑證的存放庫。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-122">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="5f1b5-123">若要新增憑證，請使用[ \<knownCertificates> 元素](knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-123">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="5f1b5-124">為 [\<add>](add-of-knowncertificates.md) 每個憑證插入，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-124">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="5f1b5-125">根據預設，必須從安全權杖服務取得憑證。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-125">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="5f1b5-126">這些「已知的」憑證可確保只有合法的用戶端可以存取服務。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-126">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="5f1b5-127">若要檢查同盟服務驗證用戶端所需的條件，以及使用此設定元素的詳細資訊，請參閱[如何：在同盟服務上設定認證](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-127">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="5f1b5-128">如需聯合案例的詳細資訊，請參閱[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-128">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="5f1b5-129">如需示範如何在設定中填入集合的範例，請參閱 [\<add>](add-of-knowncertificates.md) 。</span><span class="sxs-lookup"><span data-stu-id="5f1b5-129">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f1b5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f1b5-130">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="5f1b5-131">安全性行為</span><span class="sxs-lookup"><span data-stu-id="5f1b5-131">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5f1b5-132">HOW TO：設定聯合服務的認證</span><span class="sxs-lookup"><span data-stu-id="5f1b5-132">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="5f1b5-133">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="5f1b5-133">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="5f1b5-134">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="5f1b5-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [<span data-ttu-id="5f1b5-135">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="5f1b5-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
