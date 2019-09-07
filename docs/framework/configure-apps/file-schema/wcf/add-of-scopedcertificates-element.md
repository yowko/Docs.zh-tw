---
title: <add> 項目的 <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: b00a342108beca69a906fbf6212915768e98778f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398338"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="d7b77-102">\<新增 scopedCertificates > \<元素的 ></span><span class="sxs-lookup"><span data-stu-id="d7b77-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="d7b77-103">將 X.509 憑證加入至範圍憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="d7b77-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
<span data-ttu-id="d7b77-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d7b77-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d7b77-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d7b77-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d7b77-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d7b77-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="d7b77-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d7b77-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="d7b77-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d7b77-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="d7b77-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="d7b77-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="d7b77-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="d7b77-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="d7b77-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<scopedCertificates >** ](scopedcertificates-element.md)</span><span class="sxs-lookup"><span data-stu-id="d7b77-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)</span></span>\
<span data-ttu-id="d7b77-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="d7b77-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7b77-113">語法</span><span class="sxs-lookup"><span data-stu-id="d7b77-113">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7b77-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d7b77-114">Attributes and Elements</span></span>  
 <span data-ttu-id="d7b77-115">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="d7b77-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7b77-116">屬性</span><span class="sxs-lookup"><span data-stu-id="d7b77-116">Attributes</span></span>  
  
|<span data-ttu-id="d7b77-117">屬性</span><span class="sxs-lookup"><span data-stu-id="d7b77-117">Attribute</span></span>|<span data-ttu-id="d7b77-118">描述</span><span class="sxs-lookup"><span data-stu-id="d7b77-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7b77-119">targetUri</span><span class="sxs-lookup"><span data-stu-id="d7b77-119">targetUri</span></span>|<span data-ttu-id="d7b77-120">字串。</span><span class="sxs-lookup"><span data-stu-id="d7b77-120">String.</span></span> <span data-ttu-id="d7b77-121">指定與憑證相關聯的服務之 URI。</span><span class="sxs-lookup"><span data-stu-id="d7b77-121">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="d7b77-122">findValue</span><span class="sxs-lookup"><span data-stu-id="d7b77-122">findValue</span></span>|<span data-ttu-id="d7b77-123">字串。</span><span class="sxs-lookup"><span data-stu-id="d7b77-123">String.</span></span> <span data-ttu-id="d7b77-124">要搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="d7b77-124">The value to search for.</span></span>|  
|<span data-ttu-id="d7b77-125">x509FindType</span><span class="sxs-lookup"><span data-stu-id="d7b77-125">x509FindType</span></span>|<span data-ttu-id="d7b77-126">列舉。</span><span class="sxs-lookup"><span data-stu-id="d7b77-126">Enumeration.</span></span> <span data-ttu-id="d7b77-127">要搜尋的其中一個憑證欄位。</span><span class="sxs-lookup"><span data-stu-id="d7b77-127">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="d7b77-128">storeLocation</span><span class="sxs-lookup"><span data-stu-id="d7b77-128">storeLocation</span></span>|<span data-ttu-id="d7b77-129">列舉。</span><span class="sxs-lookup"><span data-stu-id="d7b77-129">Enumeration.</span></span> <span data-ttu-id="d7b77-130">搜尋兩個存放位置中的一個。</span><span class="sxs-lookup"><span data-stu-id="d7b77-130">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="d7b77-131">storeName</span><span class="sxs-lookup"><span data-stu-id="d7b77-131">storeName</span></span>|<span data-ttu-id="d7b77-132">列舉。</span><span class="sxs-lookup"><span data-stu-id="d7b77-132">Enumeration.</span></span> <span data-ttu-id="d7b77-133">搜尋的其中一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="d7b77-133">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="d7b77-134">findValue 屬性</span><span class="sxs-lookup"><span data-stu-id="d7b77-134">findValue Attribute</span></span>  
  
|<span data-ttu-id="d7b77-135">值</span><span class="sxs-lookup"><span data-stu-id="d7b77-135">Value</span></span>|<span data-ttu-id="d7b77-136">描述</span><span class="sxs-lookup"><span data-stu-id="d7b77-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7b77-137">String</span><span class="sxs-lookup"><span data-stu-id="d7b77-137">String</span></span>|<span data-ttu-id="d7b77-138">這個值取決於要搜尋的欄位 (由 X509FindType 屬性指定)。</span><span class="sxs-lookup"><span data-stu-id="d7b77-138">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="d7b77-139">例如，如果搜尋指紋，則此值必須是十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="d7b77-139">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="d7b77-140">x509FindType 屬性</span><span class="sxs-lookup"><span data-stu-id="d7b77-140">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="d7b77-141">值</span><span class="sxs-lookup"><span data-stu-id="d7b77-141">Value</span></span>|<span data-ttu-id="d7b77-142">說明</span><span class="sxs-lookup"><span data-stu-id="d7b77-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7b77-143">列舉</span><span class="sxs-lookup"><span data-stu-id="d7b77-143">Enumeration</span></span>|<span data-ttu-id="d7b77-144">這些值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="d7b77-144">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="d7b77-145">storeLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="d7b77-145">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="d7b77-146">值</span><span class="sxs-lookup"><span data-stu-id="d7b77-146">Value</span></span>|<span data-ttu-id="d7b77-147">說明</span><span class="sxs-lookup"><span data-stu-id="d7b77-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7b77-148">列舉</span><span class="sxs-lookup"><span data-stu-id="d7b77-148">Enumeration</span></span>|<span data-ttu-id="d7b77-149">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="d7b77-149">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="d7b77-150">storeName 屬性</span><span class="sxs-lookup"><span data-stu-id="d7b77-150">storeName Attribute</span></span>  
  
|<span data-ttu-id="d7b77-151">值</span><span class="sxs-lookup"><span data-stu-id="d7b77-151">Value</span></span>|<span data-ttu-id="d7b77-152">描述</span><span class="sxs-lookup"><span data-stu-id="d7b77-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7b77-153">列舉</span><span class="sxs-lookup"><span data-stu-id="d7b77-153">Enumeration</span></span>|<span data-ttu-id="d7b77-154">這些值包括：通訊錄、AuthRoot、CertificateAuthority、不允許、My、Root、TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="d7b77-154">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7b77-155">子元素</span><span class="sxs-lookup"><span data-stu-id="d7b77-155">Child Elements</span></span>  
 <span data-ttu-id="d7b77-156">無。</span><span class="sxs-lookup"><span data-stu-id="d7b77-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7b77-157">父項目</span><span class="sxs-lookup"><span data-stu-id="d7b77-157">Parent Elements</span></span>  
  
|<span data-ttu-id="d7b77-158">項目</span><span class="sxs-lookup"><span data-stu-id="d7b77-158">Element</span></span>|<span data-ttu-id="d7b77-159">說明</span><span class="sxs-lookup"><span data-stu-id="d7b77-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7b77-160">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="d7b77-160">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="d7b77-161">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="d7b77-161">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7b77-162">備註</span><span class="sxs-lookup"><span data-stu-id="d7b77-162">Remarks</span></span>  
 <span data-ttu-id="d7b77-163">這個項目可讓用戶端根據與其進行通訊之服務的 URL 設定要使用的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="d7b77-163">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="d7b77-164">在用戶端可以與多重服務 (終端服務以及中繼安全性權杖服務) 進行通訊的已核發權杖情況中，這個屬性特別有用。</span><span class="sxs-lookup"><span data-stu-id="d7b77-164">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="d7b77-165">對於使用以憑證為基礎之訊息安全性的繫結，這個憑證會用來加密傳送給服務的訊息，而且預期會被服務用來簽署對用戶端的回覆。</span><span class="sxs-lookup"><span data-stu-id="d7b77-165">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="d7b77-166">如果繫結需要服務的憑證，但是在 ScopedCertificates 中找不到服務 URL 的專屬憑證，則會使用預設的憑證。</span><span class="sxs-lookup"><span data-stu-id="d7b77-166">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="d7b77-167">如需詳細資訊，請參閱[如何：建立同盟用戶端](../../../wcf/feature-details/how-to-create-a-federated-client.md)。</span><span class="sxs-lookup"><span data-stu-id="d7b77-167">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7b77-168">範例</span><span class="sxs-lookup"><span data-stu-id="d7b77-168">Example</span></span>  
 <span data-ttu-id="d7b77-169">下列範例會將 X.509 憑證新增至集合。</span><span class="sxs-lookup"><span data-stu-id="d7b77-169">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7b77-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7b77-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="d7b77-171">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="d7b77-171">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="d7b77-172">使用憑證</span><span class="sxs-lookup"><span data-stu-id="d7b77-172">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d7b77-173">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="d7b77-173">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="d7b77-174">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="d7b77-174">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
