---
title: <issuedTokenAuthentication> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400363"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="0e853-102">\<serviceCredentials > 的\<n ></span><span class="sxs-lookup"><span data-stu-id="0e853-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="0e853-103">指定發行為服務認證的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="0e853-103">Specifies a custom token issued as a service credential.</span></span>  
  
<span data-ttu-id="0e853-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0e853-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0e853-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0e853-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0e853-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0e853-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="0e853-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0e853-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="0e853-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0e853-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="0e853-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="0e853-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="0e853-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<n >**</span><span class="sxs-lookup"><span data-stu-id="0e853-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e853-111">語法</span><span class="sxs-lookup"><span data-stu-id="0e853-111">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e853-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0e853-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0e853-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="0e853-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e853-114">屬性</span><span class="sxs-lookup"><span data-stu-id="0e853-114">Attributes</span></span>  
  
|<span data-ttu-id="0e853-115">屬性</span><span class="sxs-lookup"><span data-stu-id="0e853-115">Attribute</span></span>|<span data-ttu-id="0e853-116">描述</span><span class="sxs-lookup"><span data-stu-id="0e853-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="0e853-117">取得目標 URI 的集合，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣該 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="0e853-117">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="0e853-118">如需使用這個屬性的詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>。</span><span class="sxs-lookup"><span data-stu-id="0e853-118">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="0e853-119">布林值，指定是否允許使用未受信任的 RSA 憑證簽發者。</span><span class="sxs-lookup"><span data-stu-id="0e853-119">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="0e853-120">憑證是由憑證授權單位 (CA) 簽署，以確認真實性。</span><span class="sxs-lookup"><span data-stu-id="0e853-120">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="0e853-121">未受信任的簽發者，是指未指定為可信任進行簽署憑證的 CA。</span><span class="sxs-lookup"><span data-stu-id="0e853-121">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="0e853-122">取得值，這個值會指定是否應驗證 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖的 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition>。</span><span class="sxs-lookup"><span data-stu-id="0e853-122">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="0e853-123">這個值的型別為 <xref:System.IdentityModel.Selectors.AudienceUriMode>。</span><span class="sxs-lookup"><span data-stu-id="0e853-123">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="0e853-124">如需使用這個屬性的詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="0e853-124">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="0e853-125">設定憑證驗證模式。</span><span class="sxs-lookup"><span data-stu-id="0e853-125">Sets the certificate validation mode.</span></span> <span data-ttu-id="0e853-126"><xref:System.ServiceModel.Security.X509CertificateValidationMode> 的其中一個有效值。</span><span class="sxs-lookup"><span data-stu-id="0e853-126">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="0e853-127">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="0e853-127">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="0e853-128">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="0e853-128">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="0e853-129">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="0e853-129">Optional string.</span></span> <span data-ttu-id="0e853-130">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="0e853-130">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="0e853-131">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="0e853-131">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="0e853-132">設定撤銷模式，這個模式會指定是否進行撤銷檢查，並且指定以線上或離線的方式執行。</span><span class="sxs-lookup"><span data-stu-id="0e853-132">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="0e853-133">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="0e853-133">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="0e853-134">選用性字串屬性，指定用於服務認證之 SamlSerializer 的型別。</span><span class="sxs-lookup"><span data-stu-id="0e853-134">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="0e853-135">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="0e853-135">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="0e853-136">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="0e853-136">Optional enumeration.</span></span> <span data-ttu-id="0e853-137">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="0e853-137">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e853-138">子元素</span><span class="sxs-lookup"><span data-stu-id="0e853-138">Child Elements</span></span>  
  
|<span data-ttu-id="0e853-139">項目</span><span class="sxs-lookup"><span data-stu-id="0e853-139">Element</span></span>|<span data-ttu-id="0e853-140">說明</span><span class="sxs-lookup"><span data-stu-id="0e853-140">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="0e853-141">指定 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> 項目的集合，這個集合會指定服務認證的受信任簽發者。</span><span class="sxs-lookup"><span data-stu-id="0e853-141">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e853-142">父項目</span><span class="sxs-lookup"><span data-stu-id="0e853-142">Parent Elements</span></span>  
  
|<span data-ttu-id="0e853-143">項目</span><span class="sxs-lookup"><span data-stu-id="0e853-143">Element</span></span>|<span data-ttu-id="0e853-144">說明</span><span class="sxs-lookup"><span data-stu-id="0e853-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e853-145">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="0e853-145">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="0e853-146">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="0e853-146">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e853-147">備註</span><span class="sxs-lookup"><span data-stu-id="0e853-147">Remarks</span></span>  
 <span data-ttu-id="0e853-148">發行之權杖的情況有三個階段。</span><span class="sxs-lookup"><span data-stu-id="0e853-148">The issued token scenario has three stages.</span></span> <span data-ttu-id="0e853-149">在第一個階段中，嘗試存取服務的用戶端稱為「*安全權杖服務*」。</span><span class="sxs-lookup"><span data-stu-id="0e853-149">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="0e853-150">此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。</span><span class="sxs-lookup"><span data-stu-id="0e853-150">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="0e853-151">用戶端接著會以權杖傳回服務。</span><span class="sxs-lookup"><span data-stu-id="0e853-151">The client then returns to the service with the token.</span></span> <span data-ttu-id="0e853-152">此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="0e853-152">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="0e853-153">若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。</span><span class="sxs-lookup"><span data-stu-id="0e853-153">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="0e853-154">這個項目是任何此類安全權杖服務憑證的存放庫。</span><span class="sxs-lookup"><span data-stu-id="0e853-154">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="0e853-155">若要新增憑證，請使用[ \<knownCertificates >](knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="0e853-155">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="0e853-156">為每個憑證插入「 [新增>，如下列範例所示。\< ](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="0e853-156">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="0e853-157">根據預設，必須從安全權杖服務取得憑證。</span><span class="sxs-lookup"><span data-stu-id="0e853-157">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="0e853-158">這些「已知的」憑證可確保只有合法的用戶端可以存取服務。</span><span class="sxs-lookup"><span data-stu-id="0e853-158">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="0e853-159">如需使用此設定元素的詳細資訊， [請參閱如何：在同盟服務](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)上設定認證。</span><span class="sxs-lookup"><span data-stu-id="0e853-159">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e853-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e853-160">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="0e853-161">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="0e853-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0e853-162">如何：在同盟服務上設定認證</span><span class="sxs-lookup"><span data-stu-id="0e853-162">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
