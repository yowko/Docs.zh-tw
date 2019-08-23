---
title: <add> 項目的 <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 9756d37527fcf888cad930b24677ae8e6a2c8fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920048"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="11a5b-102">\<新增 scopedCertificates > \<元素的 ></span><span class="sxs-lookup"><span data-stu-id="11a5b-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="11a5b-103">將 X.509 憑證加入至範圍憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="11a5b-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="11a5b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="11a5b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="11a5b-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="11a5b-105">\<behaviors></span></span>  
<span data-ttu-id="11a5b-106">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="11a5b-106">endpointBehaviors section</span></span>  
<span data-ttu-id="11a5b-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="11a5b-107">\<behavior></span></span>  
<span data-ttu-id="11a5b-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="11a5b-108">\<clientCredentials></span></span>  
<span data-ttu-id="11a5b-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="11a5b-109">\<serviceCertificate></span></span>  
<span data-ttu-id="11a5b-110">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="11a5b-110">\<scopedCertificates></span></span>  
<span data-ttu-id="11a5b-111">\<新增 scopedCertificates > 的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="11a5b-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a5b-112">語法</span><span class="sxs-lookup"><span data-stu-id="11a5b-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11a5b-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="11a5b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="11a5b-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="11a5b-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11a5b-115">屬性</span><span class="sxs-lookup"><span data-stu-id="11a5b-115">Attributes</span></span>  
  
|<span data-ttu-id="11a5b-116">屬性</span><span class="sxs-lookup"><span data-stu-id="11a5b-116">Attribute</span></span>|<span data-ttu-id="11a5b-117">描述</span><span class="sxs-lookup"><span data-stu-id="11a5b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11a5b-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="11a5b-118">targetUri</span></span>|<span data-ttu-id="11a5b-119">字串。</span><span class="sxs-lookup"><span data-stu-id="11a5b-119">String.</span></span> <span data-ttu-id="11a5b-120">指定與憑證相關聯的服務之 URI。</span><span class="sxs-lookup"><span data-stu-id="11a5b-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="11a5b-121">findValue</span><span class="sxs-lookup"><span data-stu-id="11a5b-121">findValue</span></span>|<span data-ttu-id="11a5b-122">字串。</span><span class="sxs-lookup"><span data-stu-id="11a5b-122">String.</span></span> <span data-ttu-id="11a5b-123">要搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="11a5b-123">The value to search for.</span></span>|  
|<span data-ttu-id="11a5b-124">x509FindType</span><span class="sxs-lookup"><span data-stu-id="11a5b-124">x509FindType</span></span>|<span data-ttu-id="11a5b-125">列舉。</span><span class="sxs-lookup"><span data-stu-id="11a5b-125">Enumeration.</span></span> <span data-ttu-id="11a5b-126">要搜尋的其中一個憑證欄位。</span><span class="sxs-lookup"><span data-stu-id="11a5b-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="11a5b-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="11a5b-127">storeLocation</span></span>|<span data-ttu-id="11a5b-128">列舉。</span><span class="sxs-lookup"><span data-stu-id="11a5b-128">Enumeration.</span></span> <span data-ttu-id="11a5b-129">搜尋兩個存放位置中的一個。</span><span class="sxs-lookup"><span data-stu-id="11a5b-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="11a5b-130">storeName</span><span class="sxs-lookup"><span data-stu-id="11a5b-130">storeName</span></span>|<span data-ttu-id="11a5b-131">列舉。</span><span class="sxs-lookup"><span data-stu-id="11a5b-131">Enumeration.</span></span> <span data-ttu-id="11a5b-132">搜尋的其中一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="11a5b-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="11a5b-133">findValue 屬性</span><span class="sxs-lookup"><span data-stu-id="11a5b-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="11a5b-134">值</span><span class="sxs-lookup"><span data-stu-id="11a5b-134">Value</span></span>|<span data-ttu-id="11a5b-135">描述</span><span class="sxs-lookup"><span data-stu-id="11a5b-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11a5b-136">String</span><span class="sxs-lookup"><span data-stu-id="11a5b-136">String</span></span>|<span data-ttu-id="11a5b-137">這個值取決於要搜尋的欄位 (由 X509FindType 屬性指定)。</span><span class="sxs-lookup"><span data-stu-id="11a5b-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="11a5b-138">例如，如果搜尋指紋，則此值必須是十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="11a5b-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="11a5b-139">x509FindType 屬性</span><span class="sxs-lookup"><span data-stu-id="11a5b-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="11a5b-140">值</span><span class="sxs-lookup"><span data-stu-id="11a5b-140">Value</span></span>|<span data-ttu-id="11a5b-141">說明</span><span class="sxs-lookup"><span data-stu-id="11a5b-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11a5b-142">列舉</span><span class="sxs-lookup"><span data-stu-id="11a5b-142">Enumeration</span></span>|<span data-ttu-id="11a5b-143">這些值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="11a5b-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="11a5b-144">storeLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="11a5b-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="11a5b-145">值</span><span class="sxs-lookup"><span data-stu-id="11a5b-145">Value</span></span>|<span data-ttu-id="11a5b-146">描述</span><span class="sxs-lookup"><span data-stu-id="11a5b-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11a5b-147">列舉</span><span class="sxs-lookup"><span data-stu-id="11a5b-147">Enumeration</span></span>|<span data-ttu-id="11a5b-148">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="11a5b-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="11a5b-149">storeName 屬性</span><span class="sxs-lookup"><span data-stu-id="11a5b-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="11a5b-150">值</span><span class="sxs-lookup"><span data-stu-id="11a5b-150">Value</span></span>|<span data-ttu-id="11a5b-151">描述</span><span class="sxs-lookup"><span data-stu-id="11a5b-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11a5b-152">列舉</span><span class="sxs-lookup"><span data-stu-id="11a5b-152">Enumeration</span></span>|<span data-ttu-id="11a5b-153">這些值包括：通訊錄、AuthRoot、CertificateAuthority、不允許、My、Root、TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="11a5b-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11a5b-154">子元素</span><span class="sxs-lookup"><span data-stu-id="11a5b-154">Child Elements</span></span>  
 <span data-ttu-id="11a5b-155">無。</span><span class="sxs-lookup"><span data-stu-id="11a5b-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11a5b-156">父項目</span><span class="sxs-lookup"><span data-stu-id="11a5b-156">Parent Elements</span></span>  
  
|<span data-ttu-id="11a5b-157">項目</span><span class="sxs-lookup"><span data-stu-id="11a5b-157">Element</span></span>|<span data-ttu-id="11a5b-158">說明</span><span class="sxs-lookup"><span data-stu-id="11a5b-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11a5b-159">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="11a5b-159">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="11a5b-160">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="11a5b-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11a5b-161">備註</span><span class="sxs-lookup"><span data-stu-id="11a5b-161">Remarks</span></span>  
 <span data-ttu-id="11a5b-162">這個項目可讓用戶端根據與其進行通訊之服務的 URL 設定要使用的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="11a5b-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="11a5b-163">在用戶端可以與多重服務 (終端服務以及中繼安全性權杖服務) 進行通訊的已核發權杖情況中，這個屬性特別有用。</span><span class="sxs-lookup"><span data-stu-id="11a5b-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="11a5b-164">對於使用以憑證為基礎之訊息安全性的繫結，這個憑證會用來加密傳送給服務的訊息，而且預期會被服務用來簽署對用戶端的回覆。</span><span class="sxs-lookup"><span data-stu-id="11a5b-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="11a5b-165">如果繫結需要服務的憑證，但是在 ScopedCertificates 中找不到服務 URL 的專屬憑證，則會使用預設的憑證。</span><span class="sxs-lookup"><span data-stu-id="11a5b-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="11a5b-166">如需詳細資訊, 請參閱[如何:建立同盟用戶端](../../../wcf/feature-details/how-to-create-a-federated-client.md)。</span><span class="sxs-lookup"><span data-stu-id="11a5b-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="11a5b-167">範例</span><span class="sxs-lookup"><span data-stu-id="11a5b-167">Example</span></span>  
 <span data-ttu-id="11a5b-168">下列範例會將 X.509 憑證新增至集合。</span><span class="sxs-lookup"><span data-stu-id="11a5b-168">The following example adds an X.509 certificate the collection.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="11a5b-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11a5b-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="11a5b-170">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="11a5b-170">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="11a5b-171">使用憑證</span><span class="sxs-lookup"><span data-stu-id="11a5b-171">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="11a5b-172">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="11a5b-172">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="11a5b-173">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="11a5b-173">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
