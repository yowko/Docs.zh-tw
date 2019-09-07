---
title: <add> 的 <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400614"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="ac649-102">\<新增 knownCertificates > \<的 ></span><span class="sxs-lookup"><span data-stu-id="ac649-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="ac649-103">將 X.509 憑證加入至已知憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="ac649-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
<span data-ttu-id="ac649-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ac649-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ac649-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ac649-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ac649-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ac649-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ac649-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ac649-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="ac649-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ac649-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="ac649-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="ac649-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="ac649-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<n >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="ac649-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="ac649-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<knownCertificates >** ](knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="ac649-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)</span></span>\
<span data-ttu-id="ac649-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="ac649-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac649-113">語法</span><span class="sxs-lookup"><span data-stu-id="ac649-113">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac649-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ac649-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ac649-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ac649-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac649-116">屬性</span><span class="sxs-lookup"><span data-stu-id="ac649-116">Attributes</span></span>  
  
|<span data-ttu-id="ac649-117">屬性</span><span class="sxs-lookup"><span data-stu-id="ac649-117">Attribute</span></span>|<span data-ttu-id="ac649-118">描述</span><span class="sxs-lookup"><span data-stu-id="ac649-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac649-119">findValue</span><span class="sxs-lookup"><span data-stu-id="ac649-119">findValue</span></span>|<span data-ttu-id="ac649-120">字串。</span><span class="sxs-lookup"><span data-stu-id="ac649-120">String.</span></span> <span data-ttu-id="ac649-121">要搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="ac649-121">The value to search for.</span></span>|  
|<span data-ttu-id="ac649-122">storeLocation</span><span class="sxs-lookup"><span data-stu-id="ac649-122">storeLocation</span></span>|<span data-ttu-id="ac649-123">列舉。</span><span class="sxs-lookup"><span data-stu-id="ac649-123">Enumeration.</span></span> <span data-ttu-id="ac649-124">搜尋兩個存放位置中的一個。</span><span class="sxs-lookup"><span data-stu-id="ac649-124">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="ac649-125">storeName</span><span class="sxs-lookup"><span data-stu-id="ac649-125">storeName</span></span>|<span data-ttu-id="ac649-126">列舉。</span><span class="sxs-lookup"><span data-stu-id="ac649-126">Enumeration.</span></span> <span data-ttu-id="ac649-127">搜尋的其中一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="ac649-127">One of the system stores to search.</span></span>|  
|<span data-ttu-id="ac649-128">x509FindType</span><span class="sxs-lookup"><span data-stu-id="ac649-128">x509FindType</span></span>|<span data-ttu-id="ac649-129">列舉。</span><span class="sxs-lookup"><span data-stu-id="ac649-129">Enumeration.</span></span> <span data-ttu-id="ac649-130">要搜尋的其中一個憑證欄位。</span><span class="sxs-lookup"><span data-stu-id="ac649-130">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="ac649-131">findValue 屬性</span><span class="sxs-lookup"><span data-stu-id="ac649-131">findValue Attribute</span></span>  
  
|<span data-ttu-id="ac649-132">值</span><span class="sxs-lookup"><span data-stu-id="ac649-132">Value</span></span>|<span data-ttu-id="ac649-133">描述</span><span class="sxs-lookup"><span data-stu-id="ac649-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac649-134">String</span><span class="sxs-lookup"><span data-stu-id="ac649-134">String</span></span>|<span data-ttu-id="ac649-135">這個值取決於要搜尋的欄位 (由 X509FindType 屬性指定)。</span><span class="sxs-lookup"><span data-stu-id="ac649-135">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="ac649-136">例如，如果搜尋指紋，則此值必須是十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="ac649-136">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="ac649-137">x509FindType 屬性</span><span class="sxs-lookup"><span data-stu-id="ac649-137">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="ac649-138">值</span><span class="sxs-lookup"><span data-stu-id="ac649-138">Value</span></span>|<span data-ttu-id="ac649-139">描述</span><span class="sxs-lookup"><span data-stu-id="ac649-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac649-140">列舉</span><span class="sxs-lookup"><span data-stu-id="ac649-140">Enumeration</span></span>|<span data-ttu-id="ac649-141">這些值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="ac649-141">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="ac649-142">storeLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="ac649-142">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="ac649-143">值</span><span class="sxs-lookup"><span data-stu-id="ac649-143">Value</span></span>|<span data-ttu-id="ac649-144">描述</span><span class="sxs-lookup"><span data-stu-id="ac649-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac649-145">列舉</span><span class="sxs-lookup"><span data-stu-id="ac649-145">Enumeration</span></span>|<span data-ttu-id="ac649-146">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="ac649-146">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="ac649-147">storeName 屬性</span><span class="sxs-lookup"><span data-stu-id="ac649-147">storeName Attribute</span></span>  
  
|<span data-ttu-id="ac649-148">值</span><span class="sxs-lookup"><span data-stu-id="ac649-148">Value</span></span>|<span data-ttu-id="ac649-149">描述</span><span class="sxs-lookup"><span data-stu-id="ac649-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ac649-150">列舉</span><span class="sxs-lookup"><span data-stu-id="ac649-150">Enumeration</span></span>|<span data-ttu-id="ac649-151">這些值包括：通訊錄、AuthRoot、CertificateAuthority、不允許、My、Root、TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="ac649-151">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac649-152">子元素</span><span class="sxs-lookup"><span data-stu-id="ac649-152">Child Elements</span></span>  
 <span data-ttu-id="ac649-153">無。</span><span class="sxs-lookup"><span data-stu-id="ac649-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac649-154">父項目</span><span class="sxs-lookup"><span data-stu-id="ac649-154">Parent Elements</span></span>  
  
|<span data-ttu-id="ac649-155">項目</span><span class="sxs-lookup"><span data-stu-id="ac649-155">Element</span></span>|<span data-ttu-id="ac649-156">描述</span><span class="sxs-lookup"><span data-stu-id="ac649-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac649-157">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="ac649-157">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="ac649-158">表示 X.509 憑證的集合，這些憑證是由安全性權杖服務 (STS) 提供的，可用來驗證安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="ac649-158">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac649-159">備註</span><span class="sxs-lookup"><span data-stu-id="ac649-159">Remarks</span></span>  
 <span data-ttu-id="ac649-160">發行之權杖的情況有三個階段。</span><span class="sxs-lookup"><span data-stu-id="ac649-160">The issued token scenario has three stages.</span></span> <span data-ttu-id="ac649-161">在第一個階段中，嘗試存取服務的用戶端稱為「*安全權杖服務*」。</span><span class="sxs-lookup"><span data-stu-id="ac649-161">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="ac649-162">此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。</span><span class="sxs-lookup"><span data-stu-id="ac649-162">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="ac649-163">用戶端接著會以權杖傳回服務。</span><span class="sxs-lookup"><span data-stu-id="ac649-163">The client then returns to the service with the token.</span></span> <span data-ttu-id="ac649-164">此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="ac649-164">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="ac649-165">若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。</span><span class="sxs-lookup"><span data-stu-id="ac649-165">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="ac649-166">N > 元素是任何此類安全權杖服務憑證的存放庫。 [ \< ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="ac649-166">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="ac649-167">若要新增憑證，請使用[ \<knownCertificates >](knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="ac649-167">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="ac649-168">插入每個憑證的[ \<add > 元素 knownCertificates > 元素，如下列範例所示。 \< ](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="ac649-168">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ac649-169">根據預設，必須從安全權杖服務取得憑證。</span><span class="sxs-lookup"><span data-stu-id="ac649-169">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="ac649-170">這些「已知的」憑證可確保只有合法的用戶端可以存取服務。</span><span class="sxs-lookup"><span data-stu-id="ac649-170">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="ac649-171">若要檢查同盟服務驗證用戶端所需的條件，以及使用此設定元素的詳細資訊，請參閱[如何：在同盟服務](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)上設定認證。</span><span class="sxs-lookup"><span data-stu-id="ac649-171">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="ac649-172">如需聯合案例的詳細資訊，請參閱[同盟和發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="ac649-172">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac649-173">範例</span><span class="sxs-lookup"><span data-stu-id="ac649-173">Example</span></span>  
 <span data-ttu-id="ac649-174">下列範例會將憑證加入至任何 STS 憑證的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="ac649-174">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac649-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac649-175">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="ac649-176">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="ac649-176">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="ac649-177">使用憑證</span><span class="sxs-lookup"><span data-stu-id="ac649-177">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ac649-178">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="ac649-178">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ac649-179">如何：在同盟服務上設定認證</span><span class="sxs-lookup"><span data-stu-id="ac649-179">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="ac649-180">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="ac649-180">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
