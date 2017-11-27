---
title: "&lt;serviceCredentials&gt; 的 &lt;issuedTokenAuthentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d8e3c7df0108c6f8656827c6c0795dcb9fe3a9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuedtokenauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="f1a98-102">&lt;serviceCredentials&gt; 的 &lt;issuedTokenAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="f1a98-102">&lt;issuedTokenAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="f1a98-103">指定發行為服務認證的自訂權杖。</span><span class="sxs-lookup"><span data-stu-id="f1a98-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="f1a98-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f1a98-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1a98-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="f1a98-105">\<behaviors></span></span>  
<span data-ttu-id="f1a98-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f1a98-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f1a98-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="f1a98-107">\<behavior></span></span>  
<span data-ttu-id="f1a98-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f1a98-108">\<serviceCredentials></span></span>  
<span data-ttu-id="f1a98-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f1a98-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a98-110">語法</span><span class="sxs-lookup"><span data-stu-id="f1a98-110">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1a98-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f1a98-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f1a98-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="f1a98-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1a98-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f1a98-113">Attributes</span></span>  
  
|<span data-ttu-id="f1a98-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f1a98-114">Attribute</span></span>|<span data-ttu-id="f1a98-115">描述</span><span class="sxs-lookup"><span data-stu-id="f1a98-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="f1a98-116">取得目標 URI 的集合，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣該 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="f1a98-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="f1a98-117">如需使用這個屬性的詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>。</span><span class="sxs-lookup"><span data-stu-id="f1a98-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="f1a98-118">布林值，指定是否允許使用未受信任的 RSA 憑證簽發者。</span><span class="sxs-lookup"><span data-stu-id="f1a98-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="f1a98-119">憑證是由憑證授權單位 (CA) 簽署，以確認真實性。</span><span class="sxs-lookup"><span data-stu-id="f1a98-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="f1a98-120">未受信任的簽發者，是指未指定為可信任進行簽署憑證的 CA。</span><span class="sxs-lookup"><span data-stu-id="f1a98-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="f1a98-121">取得值，這個值會指定是否應驗證 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖的 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition>。</span><span class="sxs-lookup"><span data-stu-id="f1a98-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="f1a98-122">這個值的型別為 <xref:System.IdentityModel.Selectors.AudienceUriMode>。</span><span class="sxs-lookup"><span data-stu-id="f1a98-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="f1a98-123">如需使用這個屬性的詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="f1a98-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="f1a98-124">設定憑證驗證模式。</span><span class="sxs-lookup"><span data-stu-id="f1a98-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="f1a98-125"><xref:System.ServiceModel.Security.X509CertificateValidationMode> 的其中一個有效值。</span><span class="sxs-lookup"><span data-stu-id="f1a98-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="f1a98-126">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="f1a98-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="f1a98-127">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="f1a98-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="f1a98-128">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="f1a98-128">Optional string.</span></span> <span data-ttu-id="f1a98-129">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="f1a98-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="f1a98-130">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="f1a98-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="f1a98-131">設定撤銷模式，這個模式會指定是否進行撤銷檢查，並且指定以線上或離線的方式執行。</span><span class="sxs-lookup"><span data-stu-id="f1a98-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="f1a98-132">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="f1a98-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="f1a98-133">選用性字串屬性，指定用於服務認證之 SamlSerializer 的型別。</span><span class="sxs-lookup"><span data-stu-id="f1a98-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="f1a98-134">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="f1a98-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="f1a98-135">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="f1a98-135">Optional enumeration.</span></span> <span data-ttu-id="f1a98-136">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="f1a98-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1a98-137">子元素</span><span class="sxs-lookup"><span data-stu-id="f1a98-137">Child Elements</span></span>  
  
|<span data-ttu-id="f1a98-138">項目</span><span class="sxs-lookup"><span data-stu-id="f1a98-138">Element</span></span>|<span data-ttu-id="f1a98-139">描述</span><span class="sxs-lookup"><span data-stu-id="f1a98-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="f1a98-140">指定 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> 項目的集合，這個集合會指定服務認證的受信任簽發者。</span><span class="sxs-lookup"><span data-stu-id="f1a98-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1a98-141">父項目</span><span class="sxs-lookup"><span data-stu-id="f1a98-141">Parent Elements</span></span>  
  
|<span data-ttu-id="f1a98-142">項目</span><span class="sxs-lookup"><span data-stu-id="f1a98-142">Element</span></span>|<span data-ttu-id="f1a98-143">說明</span><span class="sxs-lookup"><span data-stu-id="f1a98-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1a98-144">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f1a98-144">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="f1a98-145">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="f1a98-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1a98-146">備註</span><span class="sxs-lookup"><span data-stu-id="f1a98-146">Remarks</span></span>  
 <span data-ttu-id="f1a98-147">發行之權杖的情況有三個階段。</span><span class="sxs-lookup"><span data-stu-id="f1a98-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="f1a98-148">在第一個階段中，用戶端會嘗試存取的服務指*安全權杖服務*。</span><span class="sxs-lookup"><span data-stu-id="f1a98-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="f1a98-149">此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。</span><span class="sxs-lookup"><span data-stu-id="f1a98-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="f1a98-150">用戶端接著會以權杖傳回服務。</span><span class="sxs-lookup"><span data-stu-id="f1a98-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="f1a98-151">此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="f1a98-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="f1a98-152">若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。</span><span class="sxs-lookup"><span data-stu-id="f1a98-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="f1a98-153">這個項目是任何此類安全權杖服務憑證的存放庫。</span><span class="sxs-lookup"><span data-stu-id="f1a98-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="f1a98-154">若要新增的憑證，請使用[ \<a d d >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="f1a98-154">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="f1a98-155">插入[\<新增 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)每個憑證，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f1a98-155">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="f1a98-156">根據預設，必須從安全權杖服務取得憑證。</span><span class="sxs-lookup"><span data-stu-id="f1a98-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="f1a98-157">這些「已知的」憑證可確保只有合法的用戶端可以存取服務。</span><span class="sxs-lookup"><span data-stu-id="f1a98-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="f1a98-158">如需有關如何使用這個組態項目的詳細資訊，請參閱[How to： 設定聯合服務的認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="f1a98-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a98-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1a98-159">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
 [<span data-ttu-id="f1a98-160">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="f1a98-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f1a98-161">如何： 設定聯合服務認證</span><span class="sxs-lookup"><span data-stu-id="f1a98-161">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
