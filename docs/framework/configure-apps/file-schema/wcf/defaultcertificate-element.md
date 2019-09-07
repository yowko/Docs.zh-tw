---
title: <defaultCertificate> 項目
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400421"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="dfa81-102">\<defaultCertificate > 元素</span><span class="sxs-lookup"><span data-stu-id="dfa81-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="dfa81-103">指定服務或 STS 不透過交涉通訊協定提供憑證時要使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="dfa81-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
<span data-ttu-id="dfa81-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dfa81-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dfa81-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dfa81-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dfa81-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dfa81-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="dfa81-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dfa81-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="dfa81-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dfa81-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="dfa81-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="dfa81-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="dfa81-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="dfa81-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="dfa81-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultCertificate >**</span><span class="sxs-lookup"><span data-stu-id="dfa81-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa81-112">語法</span><span class="sxs-lookup"><span data-stu-id="dfa81-112">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfa81-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dfa81-113">Attributes and Elements</span></span>  
 <span data-ttu-id="dfa81-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="dfa81-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfa81-115">屬性</span><span class="sxs-lookup"><span data-stu-id="dfa81-115">Attributes</span></span>  
  
|<span data-ttu-id="dfa81-116">屬性</span><span class="sxs-lookup"><span data-stu-id="dfa81-116">Attribute</span></span>|<span data-ttu-id="dfa81-117">說明</span><span class="sxs-lookup"><span data-stu-id="dfa81-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dfa81-118">findValue</span><span class="sxs-lookup"><span data-stu-id="dfa81-118">findValue</span></span>|<span data-ttu-id="dfa81-119">字串。</span><span class="sxs-lookup"><span data-stu-id="dfa81-119">String.</span></span> <span data-ttu-id="dfa81-120">要搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="dfa81-120">The value to search for.</span></span>|  
|<span data-ttu-id="dfa81-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="dfa81-121">x509FindType</span></span>|<span data-ttu-id="dfa81-122">列舉。</span><span class="sxs-lookup"><span data-stu-id="dfa81-122">Enumeration.</span></span> <span data-ttu-id="dfa81-123">要搜尋的其中一個憑證欄位。</span><span class="sxs-lookup"><span data-stu-id="dfa81-123">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="dfa81-124">storeLocation</span><span class="sxs-lookup"><span data-stu-id="dfa81-124">storeLocation</span></span>|<span data-ttu-id="dfa81-125">列舉。</span><span class="sxs-lookup"><span data-stu-id="dfa81-125">Enumeration.</span></span> <span data-ttu-id="dfa81-126">搜尋兩個系統存放位置中的一個。</span><span class="sxs-lookup"><span data-stu-id="dfa81-126">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="dfa81-127">storeName</span><span class="sxs-lookup"><span data-stu-id="dfa81-127">storeName</span></span>|<span data-ttu-id="dfa81-128">列舉。</span><span class="sxs-lookup"><span data-stu-id="dfa81-128">Enumeration.</span></span> <span data-ttu-id="dfa81-129">搜尋的其中一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="dfa81-129">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="dfa81-130">findValue 屬性</span><span class="sxs-lookup"><span data-stu-id="dfa81-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="dfa81-131">值</span><span class="sxs-lookup"><span data-stu-id="dfa81-131">Value</span></span>|<span data-ttu-id="dfa81-132">描述</span><span class="sxs-lookup"><span data-stu-id="dfa81-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dfa81-133">String</span><span class="sxs-lookup"><span data-stu-id="dfa81-133">String</span></span>|<span data-ttu-id="dfa81-134">這個值取決於要搜尋的欄位 (由 X509FindType 屬性指定)。</span><span class="sxs-lookup"><span data-stu-id="dfa81-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="dfa81-135">例如，如果搜尋指紋，則此值必須是十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="dfa81-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="dfa81-136">x509FindType 屬性</span><span class="sxs-lookup"><span data-stu-id="dfa81-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="dfa81-137">值</span><span class="sxs-lookup"><span data-stu-id="dfa81-137">Value</span></span>|<span data-ttu-id="dfa81-138">描述</span><span class="sxs-lookup"><span data-stu-id="dfa81-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dfa81-139">列舉</span><span class="sxs-lookup"><span data-stu-id="dfa81-139">Enumeration</span></span>|<span data-ttu-id="dfa81-140">這些值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="dfa81-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="dfa81-141">storeLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="dfa81-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="dfa81-142">值</span><span class="sxs-lookup"><span data-stu-id="dfa81-142">Value</span></span>|<span data-ttu-id="dfa81-143">說明</span><span class="sxs-lookup"><span data-stu-id="dfa81-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dfa81-144">列舉</span><span class="sxs-lookup"><span data-stu-id="dfa81-144">Enumeration</span></span>|<span data-ttu-id="dfa81-145">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="dfa81-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="dfa81-146">storeName 屬性</span><span class="sxs-lookup"><span data-stu-id="dfa81-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="dfa81-147">值</span><span class="sxs-lookup"><span data-stu-id="dfa81-147">Value</span></span>|<span data-ttu-id="dfa81-148">描述</span><span class="sxs-lookup"><span data-stu-id="dfa81-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dfa81-149">列舉</span><span class="sxs-lookup"><span data-stu-id="dfa81-149">Enumeration</span></span>|<span data-ttu-id="dfa81-150">這些值包括：通訊錄、AuthRoot、CertificateAuthority、不允許、My、Root、TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="dfa81-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfa81-151">子元素</span><span class="sxs-lookup"><span data-stu-id="dfa81-151">Child Elements</span></span>  
 <span data-ttu-id="dfa81-152">無。</span><span class="sxs-lookup"><span data-stu-id="dfa81-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dfa81-153">父項目</span><span class="sxs-lookup"><span data-stu-id="dfa81-153">Parent Elements</span></span>  
  
|<span data-ttu-id="dfa81-154">項目</span><span class="sxs-lookup"><span data-stu-id="dfa81-154">Element</span></span>|<span data-ttu-id="dfa81-155">描述</span><span class="sxs-lookup"><span data-stu-id="dfa81-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfa81-156">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="dfa81-156">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="dfa81-157">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="dfa81-157">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfa81-158">備註</span><span class="sxs-lookup"><span data-stu-id="dfa81-158">Remarks</span></span>  
 <span data-ttu-id="dfa81-159">對於使用以憑證為基礎之訊息安全性的繫結，這個組態項目指定的憑證會用來加密傳送給服務的訊息，而且預期會由服務用來簽署對用戶端的回覆。</span><span class="sxs-lookup"><span data-stu-id="dfa81-159">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="dfa81-160">它會儲存當服務未指定憑證時所要使用的單一憑證。</span><span class="sxs-lookup"><span data-stu-id="dfa81-160">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfa81-161">範例</span><span class="sxs-lookup"><span data-stu-id="dfa81-161">Example</span></span>  
 <span data-ttu-id="dfa81-162">下列範例會指定要用於的端點 URI 開頭憑證 `http://www.contoso.com` 和要針對所有其他不執行憑證交涉的端點使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="dfa81-162">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dfa81-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfa81-163">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="dfa81-164">使用憑證</span><span class="sxs-lookup"><span data-stu-id="dfa81-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="dfa81-165">\<authentication></span><span class="sxs-lookup"><span data-stu-id="dfa81-165">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="dfa81-166">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="dfa81-166">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="dfa81-167">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="dfa81-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
