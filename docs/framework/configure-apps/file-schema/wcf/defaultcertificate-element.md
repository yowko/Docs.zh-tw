---
title: <defaultCertificate> 項目
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: c94531d10b7c0ef5ca0ee1f2d5683d0a259a2537
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100596"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="68979-102">\<defaultCertificate > 項目</span><span class="sxs-lookup"><span data-stu-id="68979-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="68979-103">指定服務或 STS 不透過交涉通訊協定提供憑證時要使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="68979-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="68979-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="68979-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="68979-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="68979-105">\<behaviors></span></span>  
<span data-ttu-id="68979-106">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="68979-106">endpointBehaviors section</span></span>  
<span data-ttu-id="68979-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="68979-107">\<behavior></span></span>  
<span data-ttu-id="68979-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="68979-108">\<clientCredentials></span></span>  
<span data-ttu-id="68979-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="68979-109">\<serviceCertificate></span></span>  
<span data-ttu-id="68979-110">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="68979-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68979-111">語法</span><span class="sxs-lookup"><span data-stu-id="68979-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68979-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="68979-112">Attributes and Elements</span></span>  
 <span data-ttu-id="68979-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="68979-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68979-114">屬性</span><span class="sxs-lookup"><span data-stu-id="68979-114">Attributes</span></span>  
  
|<span data-ttu-id="68979-115">屬性</span><span class="sxs-lookup"><span data-stu-id="68979-115">Attribute</span></span>|<span data-ttu-id="68979-116">描述</span><span class="sxs-lookup"><span data-stu-id="68979-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68979-117">findValue</span><span class="sxs-lookup"><span data-stu-id="68979-117">findValue</span></span>|<span data-ttu-id="68979-118">字串。</span><span class="sxs-lookup"><span data-stu-id="68979-118">String.</span></span> <span data-ttu-id="68979-119">要搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="68979-119">The value to search for.</span></span>|  
|<span data-ttu-id="68979-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="68979-120">x509FindType</span></span>|<span data-ttu-id="68979-121">列舉。</span><span class="sxs-lookup"><span data-stu-id="68979-121">Enumeration.</span></span> <span data-ttu-id="68979-122">要搜尋的其中一個憑證欄位。</span><span class="sxs-lookup"><span data-stu-id="68979-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="68979-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="68979-123">storeLocation</span></span>|<span data-ttu-id="68979-124">列舉。</span><span class="sxs-lookup"><span data-stu-id="68979-124">Enumeration.</span></span> <span data-ttu-id="68979-125">搜尋兩個系統存放位置中的一個。</span><span class="sxs-lookup"><span data-stu-id="68979-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="68979-126">storeName</span><span class="sxs-lookup"><span data-stu-id="68979-126">storeName</span></span>|<span data-ttu-id="68979-127">列舉。</span><span class="sxs-lookup"><span data-stu-id="68979-127">Enumeration.</span></span> <span data-ttu-id="68979-128">搜尋的其中一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="68979-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="68979-129">findValue 屬性</span><span class="sxs-lookup"><span data-stu-id="68979-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="68979-130">值</span><span class="sxs-lookup"><span data-stu-id="68979-130">Value</span></span>|<span data-ttu-id="68979-131">描述</span><span class="sxs-lookup"><span data-stu-id="68979-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68979-132">String</span><span class="sxs-lookup"><span data-stu-id="68979-132">String</span></span>|<span data-ttu-id="68979-133">這個值取決於要搜尋的欄位 (由 X509FindType 屬性指定)。</span><span class="sxs-lookup"><span data-stu-id="68979-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="68979-134">例如，如果搜尋指紋，則此值必須是十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="68979-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="68979-135">x509FindType 屬性</span><span class="sxs-lookup"><span data-stu-id="68979-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="68979-136">值</span><span class="sxs-lookup"><span data-stu-id="68979-136">Value</span></span>|<span data-ttu-id="68979-137">描述</span><span class="sxs-lookup"><span data-stu-id="68979-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68979-138">列舉</span><span class="sxs-lookup"><span data-stu-id="68979-138">Enumeration</span></span>|<span data-ttu-id="68979-139">這些值包括：FindByThumbprint、 FindBySubjectName、 FindBySubjectDistinguishedName、 FindByIssuerName、 FindByIssuerDistinguishedName、 FindBySerialNumber、 FindByTimeValid、 FindByTimeNotYetValid、 FindBySerialNumber、 FindByTimeExpired、 FindByTemplateNameFindByApplicationPolicy、 FindByCertificatePolicy、 FindByExtension、 FindByKeyUsage、 FindBySubjectKeyIdentifier。</span><span class="sxs-lookup"><span data-stu-id="68979-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="68979-140">storeLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="68979-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="68979-141">值</span><span class="sxs-lookup"><span data-stu-id="68979-141">Value</span></span>|<span data-ttu-id="68979-142">描述</span><span class="sxs-lookup"><span data-stu-id="68979-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68979-143">列舉</span><span class="sxs-lookup"><span data-stu-id="68979-143">Enumeration</span></span>|<span data-ttu-id="68979-144">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="68979-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="68979-145">storeName 屬性</span><span class="sxs-lookup"><span data-stu-id="68979-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="68979-146">值</span><span class="sxs-lookup"><span data-stu-id="68979-146">Value</span></span>|<span data-ttu-id="68979-147">描述</span><span class="sxs-lookup"><span data-stu-id="68979-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68979-148">列舉</span><span class="sxs-lookup"><span data-stu-id="68979-148">Enumeration</span></span>|<span data-ttu-id="68979-149">這些值包括：AddressBook、 AuthRoot、 CertificateAuthority、 Disallowed、 My、 Root、 TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="68979-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68979-150">子元素</span><span class="sxs-lookup"><span data-stu-id="68979-150">Child Elements</span></span>  
 <span data-ttu-id="68979-151">無。</span><span class="sxs-lookup"><span data-stu-id="68979-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68979-152">父項目</span><span class="sxs-lookup"><span data-stu-id="68979-152">Parent Elements</span></span>  
  
|<span data-ttu-id="68979-153">項目</span><span class="sxs-lookup"><span data-stu-id="68979-153">Element</span></span>|<span data-ttu-id="68979-154">描述</span><span class="sxs-lookup"><span data-stu-id="68979-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68979-155">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="68979-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="68979-156">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="68979-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68979-157">備註</span><span class="sxs-lookup"><span data-stu-id="68979-157">Remarks</span></span>  
 <span data-ttu-id="68979-158">對於使用以憑證為基礎之訊息安全性的繫結，這個組態項目指定的憑證會用來加密傳送給服務的訊息，而且預期會由服務用來簽署對用戶端的回覆。</span><span class="sxs-lookup"><span data-stu-id="68979-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="68979-159">它會儲存當服務未指定憑證時所要使用的單一憑證。</span><span class="sxs-lookup"><span data-stu-id="68979-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68979-160">範例</span><span class="sxs-lookup"><span data-stu-id="68979-160">Example</span></span>  
 <span data-ttu-id="68979-161">下列範例會指定要用於的端點 URI 開頭憑證 `http://www.contoso.com` 和要針對所有其他不執行憑證交涉的端點使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="68979-161">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="68979-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68979-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="68979-163">使用憑證</span><span class="sxs-lookup"><span data-stu-id="68979-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="68979-164">\<authentication></span><span class="sxs-lookup"><span data-stu-id="68979-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="68979-165">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="68979-165">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="68979-166">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="68979-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
