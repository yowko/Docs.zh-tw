---
title: <add> 的 <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 3eb5bf74f909e6036154b7f5f7c6181b09fefbff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077715"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="cc826-102">\<add> of \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="cc826-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="cc826-103">將 X.509 憑證加入至已知憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="cc826-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="cc826-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cc826-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cc826-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="cc826-105">\<behaviors></span></span>  
<span data-ttu-id="cc826-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cc826-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cc826-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="cc826-107">\<behavior></span></span>  
<span data-ttu-id="cc826-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="cc826-108">\<serviceCredentials></span></span>  
<span data-ttu-id="cc826-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="cc826-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="cc826-110">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="cc826-110">\<knownCertificates></span></span>  
<span data-ttu-id="cc826-111">\<add></span><span class="sxs-lookup"><span data-stu-id="cc826-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc826-112">語法</span><span class="sxs-lookup"><span data-stu-id="cc826-112">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc826-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cc826-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cc826-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cc826-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc826-115">屬性</span><span class="sxs-lookup"><span data-stu-id="cc826-115">Attributes</span></span>  
  
|<span data-ttu-id="cc826-116">屬性</span><span class="sxs-lookup"><span data-stu-id="cc826-116">Attribute</span></span>|<span data-ttu-id="cc826-117">描述</span><span class="sxs-lookup"><span data-stu-id="cc826-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc826-118">findValue</span><span class="sxs-lookup"><span data-stu-id="cc826-118">findValue</span></span>|<span data-ttu-id="cc826-119">字串。</span><span class="sxs-lookup"><span data-stu-id="cc826-119">String.</span></span> <span data-ttu-id="cc826-120">要搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="cc826-120">The value to search for.</span></span>|  
|<span data-ttu-id="cc826-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="cc826-121">storeLocation</span></span>|<span data-ttu-id="cc826-122">列舉。</span><span class="sxs-lookup"><span data-stu-id="cc826-122">Enumeration.</span></span> <span data-ttu-id="cc826-123">搜尋兩個存放位置中的一個。</span><span class="sxs-lookup"><span data-stu-id="cc826-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="cc826-124">storeName</span><span class="sxs-lookup"><span data-stu-id="cc826-124">storeName</span></span>|<span data-ttu-id="cc826-125">列舉。</span><span class="sxs-lookup"><span data-stu-id="cc826-125">Enumeration.</span></span> <span data-ttu-id="cc826-126">搜尋的其中一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="cc826-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="cc826-127">x509FindType</span><span class="sxs-lookup"><span data-stu-id="cc826-127">x509FindType</span></span>|<span data-ttu-id="cc826-128">列舉。</span><span class="sxs-lookup"><span data-stu-id="cc826-128">Enumeration.</span></span> <span data-ttu-id="cc826-129">要搜尋的其中一個憑證欄位。</span><span class="sxs-lookup"><span data-stu-id="cc826-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="cc826-130">findValue 屬性</span><span class="sxs-lookup"><span data-stu-id="cc826-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="cc826-131">值</span><span class="sxs-lookup"><span data-stu-id="cc826-131">Value</span></span>|<span data-ttu-id="cc826-132">描述</span><span class="sxs-lookup"><span data-stu-id="cc826-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cc826-133">String</span><span class="sxs-lookup"><span data-stu-id="cc826-133">String</span></span>|<span data-ttu-id="cc826-134">這個值取決於要搜尋的欄位 (由 X509FindType 屬性指定)。</span><span class="sxs-lookup"><span data-stu-id="cc826-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="cc826-135">例如，如果搜尋指紋，則此值必須是十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="cc826-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="cc826-136">x509FindType 屬性</span><span class="sxs-lookup"><span data-stu-id="cc826-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="cc826-137">值</span><span class="sxs-lookup"><span data-stu-id="cc826-137">Value</span></span>|<span data-ttu-id="cc826-138">描述</span><span class="sxs-lookup"><span data-stu-id="cc826-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cc826-139">列舉</span><span class="sxs-lookup"><span data-stu-id="cc826-139">Enumeration</span></span>|<span data-ttu-id="cc826-140">這些值包括：FindByThumbprint、 FindBySubjectName、 FindBySubjectDistinguishedName、 FindByIssuerName、 FindByIssuerDistinguishedName、 FindBySerialNumber、 FindByTimeValid、 FindByTimeNotYetValid、 FindBySerialNumber、 FindByTimeExpired、 FindByTemplateNameFindByApplicationPolicy、 FindByCertificatePolicy、 FindByExtension、 FindByKeyUsage、 FindBySubjectKeyIdentifier。</span><span class="sxs-lookup"><span data-stu-id="cc826-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="cc826-141">storeLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="cc826-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="cc826-142">值</span><span class="sxs-lookup"><span data-stu-id="cc826-142">Value</span></span>|<span data-ttu-id="cc826-143">描述</span><span class="sxs-lookup"><span data-stu-id="cc826-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cc826-144">列舉</span><span class="sxs-lookup"><span data-stu-id="cc826-144">Enumeration</span></span>|<span data-ttu-id="cc826-145">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="cc826-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="cc826-146">storeName 屬性</span><span class="sxs-lookup"><span data-stu-id="cc826-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="cc826-147">值</span><span class="sxs-lookup"><span data-stu-id="cc826-147">Value</span></span>|<span data-ttu-id="cc826-148">描述</span><span class="sxs-lookup"><span data-stu-id="cc826-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cc826-149">列舉</span><span class="sxs-lookup"><span data-stu-id="cc826-149">Enumeration</span></span>|<span data-ttu-id="cc826-150">這些值包括：AddressBook、 AuthRoot、 CertificateAuthority、 Disallowed、 My、 Root、 TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="cc826-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc826-151">子元素</span><span class="sxs-lookup"><span data-stu-id="cc826-151">Child Elements</span></span>  
 <span data-ttu-id="cc826-152">無。</span><span class="sxs-lookup"><span data-stu-id="cc826-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc826-153">父項目</span><span class="sxs-lookup"><span data-stu-id="cc826-153">Parent Elements</span></span>  
  
|<span data-ttu-id="cc826-154">項目</span><span class="sxs-lookup"><span data-stu-id="cc826-154">Element</span></span>|<span data-ttu-id="cc826-155">描述</span><span class="sxs-lookup"><span data-stu-id="cc826-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc826-156">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="cc826-156">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|<span data-ttu-id="cc826-157">表示 X.509 憑證的集合，這些憑證是由安全性權杖服務 (STS) 提供的，可用來驗證安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="cc826-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc826-158">備註</span><span class="sxs-lookup"><span data-stu-id="cc826-158">Remarks</span></span>  
 <span data-ttu-id="cc826-159">發行之權杖的情況有三個階段。</span><span class="sxs-lookup"><span data-stu-id="cc826-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="cc826-160">在第一個階段中，嘗試存取服務的用戶端指*安全權杖服務*。</span><span class="sxs-lookup"><span data-stu-id="cc826-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="cc826-161">此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。</span><span class="sxs-lookup"><span data-stu-id="cc826-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="cc826-162">用戶端接著會以權杖傳回服務。</span><span class="sxs-lookup"><span data-stu-id="cc826-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="cc826-163">此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="cc826-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="cc826-164">若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。</span><span class="sxs-lookup"><span data-stu-id="cc826-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="cc826-165">[ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)項目是任何此類安全權杖服務憑證的存放庫。</span><span class="sxs-lookup"><span data-stu-id="cc826-165">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="cc826-166">若要新增的憑證，請使用[ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="cc826-166">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="cc826-167">插入[\<新增 > 項目\<knownCertificates > 項目](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)為每個憑證，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cc826-167">Insert an [\<add> element \<knownCertificates> Element](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="cc826-168">根據預設，必須從安全權杖服務取得憑證。</span><span class="sxs-lookup"><span data-stu-id="cc826-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="cc826-169">這些「已知的」憑證可確保只有合法的用戶端可以存取服務。</span><span class="sxs-lookup"><span data-stu-id="cc826-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="cc826-170">若要檢閱由聯合的服務，以及更多有關使用這個組態項目驗證用戶端所需的條件，請參閱[How to:Federation Service 上設定認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="cc826-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="cc826-171">如需聯合案例的詳細資訊，請參閱[聯合與發行權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="cc826-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc826-172">範例</span><span class="sxs-lookup"><span data-stu-id="cc826-172">Example</span></span>  
 <span data-ttu-id="cc826-173">下列範例會將憑證加入至任何 STS 憑證的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="cc826-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="cc826-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc826-174">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="cc826-175">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="cc826-175">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)
- [<span data-ttu-id="cc826-176">使用憑證</span><span class="sxs-lookup"><span data-stu-id="cc826-176">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="cc826-177">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="cc826-177">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="cc826-178">HOW TO：設定同盟服務的認證</span><span class="sxs-lookup"><span data-stu-id="cc826-178">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="cc826-179">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="cc826-179">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
