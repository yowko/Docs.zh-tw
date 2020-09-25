---
title: <add> 的 <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 453593918de15613edb801cca8a16c9dbf71aa90
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176080"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="a0004-102">\<add> 的 \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="a0004-102">\<add> of \<knownCertificates></span></span>

<span data-ttu-id="a0004-103">將 X.509 憑證加入至已知憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="a0004-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="a0004-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a0004-104">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0004-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a0004-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a0004-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a0004-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0004-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a0004-107">Attributes</span></span>  
  
|<span data-ttu-id="a0004-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a0004-108">Attribute</span></span>|<span data-ttu-id="a0004-109">描述</span><span class="sxs-lookup"><span data-stu-id="a0004-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0004-110">findValue</span><span class="sxs-lookup"><span data-stu-id="a0004-110">findValue</span></span>|<span data-ttu-id="a0004-111">字串。</span><span class="sxs-lookup"><span data-stu-id="a0004-111">String.</span></span> <span data-ttu-id="a0004-112">要搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="a0004-112">The value to search for.</span></span>|  
|<span data-ttu-id="a0004-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="a0004-113">storeLocation</span></span>|<span data-ttu-id="a0004-114">列舉。</span><span class="sxs-lookup"><span data-stu-id="a0004-114">Enumeration.</span></span> <span data-ttu-id="a0004-115">搜尋兩個存放位置中的一個。</span><span class="sxs-lookup"><span data-stu-id="a0004-115">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="a0004-116">storeName</span><span class="sxs-lookup"><span data-stu-id="a0004-116">storeName</span></span>|<span data-ttu-id="a0004-117">列舉。</span><span class="sxs-lookup"><span data-stu-id="a0004-117">Enumeration.</span></span> <span data-ttu-id="a0004-118">搜尋的其中一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="a0004-118">One of the system stores to search.</span></span>|  
|<span data-ttu-id="a0004-119">x509FindType</span><span class="sxs-lookup"><span data-stu-id="a0004-119">x509FindType</span></span>|<span data-ttu-id="a0004-120">列舉。</span><span class="sxs-lookup"><span data-stu-id="a0004-120">Enumeration.</span></span> <span data-ttu-id="a0004-121">要搜尋的其中一個憑證欄位。</span><span class="sxs-lookup"><span data-stu-id="a0004-121">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="a0004-122">findValue 屬性</span><span class="sxs-lookup"><span data-stu-id="a0004-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="a0004-123">值</span><span class="sxs-lookup"><span data-stu-id="a0004-123">Value</span></span>|<span data-ttu-id="a0004-124">描述</span><span class="sxs-lookup"><span data-stu-id="a0004-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0004-125">String</span><span class="sxs-lookup"><span data-stu-id="a0004-125">String</span></span>|<span data-ttu-id="a0004-126">這個值取決於要搜尋的欄位 (由 X509FindType 屬性指定)。</span><span class="sxs-lookup"><span data-stu-id="a0004-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="a0004-127">例如，如果搜尋指紋，則此值必須是十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="a0004-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="a0004-128">x509FindType 屬性</span><span class="sxs-lookup"><span data-stu-id="a0004-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="a0004-129">值</span><span class="sxs-lookup"><span data-stu-id="a0004-129">Value</span></span>|<span data-ttu-id="a0004-130">描述</span><span class="sxs-lookup"><span data-stu-id="a0004-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0004-131">列舉型別</span><span class="sxs-lookup"><span data-stu-id="a0004-131">Enumeration</span></span>|<span data-ttu-id="a0004-132">值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage、FindBySubjectKeyIdentifier。</span><span class="sxs-lookup"><span data-stu-id="a0004-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="a0004-133">storeLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="a0004-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="a0004-134">值</span><span class="sxs-lookup"><span data-stu-id="a0004-134">Value</span></span>|<span data-ttu-id="a0004-135">描述</span><span class="sxs-lookup"><span data-stu-id="a0004-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0004-136">列舉型別</span><span class="sxs-lookup"><span data-stu-id="a0004-136">Enumeration</span></span>|<span data-ttu-id="a0004-137">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="a0004-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="a0004-138">storeName 屬性</span><span class="sxs-lookup"><span data-stu-id="a0004-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="a0004-139">值</span><span class="sxs-lookup"><span data-stu-id="a0004-139">Value</span></span>|<span data-ttu-id="a0004-140">描述</span><span class="sxs-lookup"><span data-stu-id="a0004-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0004-141">列舉型別</span><span class="sxs-lookup"><span data-stu-id="a0004-141">Enumeration</span></span>|<span data-ttu-id="a0004-142">值包括：AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="a0004-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0004-143">子元素</span><span class="sxs-lookup"><span data-stu-id="a0004-143">Child Elements</span></span>  

 <span data-ttu-id="a0004-144">無。</span><span class="sxs-lookup"><span data-stu-id="a0004-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0004-145">父項目</span><span class="sxs-lookup"><span data-stu-id="a0004-145">Parent Elements</span></span>  
  
|<span data-ttu-id="a0004-146">項目</span><span class="sxs-lookup"><span data-stu-id="a0004-146">Element</span></span>|<span data-ttu-id="a0004-147">描述</span><span class="sxs-lookup"><span data-stu-id="a0004-147">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="a0004-148">表示 X.509 憑證的集合，這些憑證是由安全性權杖服務 (STS) 提供的，可用來驗證安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="a0004-148">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0004-149">備註</span><span class="sxs-lookup"><span data-stu-id="a0004-149">Remarks</span></span>  

 <span data-ttu-id="a0004-150">發行之權杖的情況有三個階段。</span><span class="sxs-lookup"><span data-stu-id="a0004-150">The issued token scenario has three stages.</span></span> <span data-ttu-id="a0004-151">在第一個階段中，嘗試存取服務的用戶端稱為「 *安全權杖服務*」。</span><span class="sxs-lookup"><span data-stu-id="a0004-151">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="a0004-152">此安全權杖服務接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。</span><span class="sxs-lookup"><span data-stu-id="a0004-152">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="a0004-153">用戶端接著會以權杖傳回服務。</span><span class="sxs-lookup"><span data-stu-id="a0004-153">The client then returns to the service with the token.</span></span> <span data-ttu-id="a0004-154">此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="a0004-154">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="a0004-155">若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。</span><span class="sxs-lookup"><span data-stu-id="a0004-155">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="a0004-156">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)元素是任何這類安全權杖服務憑證的存放庫。</span><span class="sxs-lookup"><span data-stu-id="a0004-156">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="a0004-157">若要加入憑證，請使用 [\<knownCertificates>](knowncertificates.md) 。</span><span class="sxs-lookup"><span data-stu-id="a0004-157">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="a0004-158">為每個憑證插入[ \<add> 元素 \<knownCertificates> 元素](add-of-knowncertificates.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a0004-158">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a0004-159">根據預設，必須從安全權杖服務取得憑證。</span><span class="sxs-lookup"><span data-stu-id="a0004-159">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="a0004-160">這些「已知的」憑證可確保只有合法的用戶端可以存取服務。</span><span class="sxs-lookup"><span data-stu-id="a0004-160">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="a0004-161">若要檢查同盟服務驗證用戶端所需的條件，以及使用此設定專案的詳細資訊，請參閱 [如何：在同盟服務上設定認證](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="a0004-161">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="a0004-162">如需同盟案例的詳細資訊，請參閱 [同盟和已發行的權杖](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="a0004-162">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0004-163">範例</span><span class="sxs-lookup"><span data-stu-id="a0004-163">Example</span></span>  

 <span data-ttu-id="a0004-164">下列範例會將憑證加入至任何 STS 憑證的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="a0004-164">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a0004-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0004-165">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="a0004-166">使用憑證</span><span class="sxs-lookup"><span data-stu-id="a0004-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a0004-167">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="a0004-167">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a0004-168">作法：設定同盟服務的認證</span><span class="sxs-lookup"><span data-stu-id="a0004-168">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="a0004-169">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a0004-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
