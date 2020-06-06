---
title: <defaultCertificate> 項目
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400421"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="5f7db-102">\<defaultCertificate> 項目</span><span class="sxs-lookup"><span data-stu-id="5f7db-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="5f7db-103">指定服務或 STS 不透過交涉通訊協定提供憑證時要使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="5f7db-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="5f7db-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f7db-104">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f7db-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f7db-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5f7db-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="5f7db-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f7db-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5f7db-107">Attributes</span></span>  
  
|<span data-ttu-id="5f7db-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5f7db-108">Attribute</span></span>|<span data-ttu-id="5f7db-109">描述</span><span class="sxs-lookup"><span data-stu-id="5f7db-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f7db-110">findValue</span><span class="sxs-lookup"><span data-stu-id="5f7db-110">findValue</span></span>|<span data-ttu-id="5f7db-111">字串。</span><span class="sxs-lookup"><span data-stu-id="5f7db-111">String.</span></span> <span data-ttu-id="5f7db-112">要搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="5f7db-112">The value to search for.</span></span>|  
|<span data-ttu-id="5f7db-113">x509FindType</span><span class="sxs-lookup"><span data-stu-id="5f7db-113">x509FindType</span></span>|<span data-ttu-id="5f7db-114">列舉。</span><span class="sxs-lookup"><span data-stu-id="5f7db-114">Enumeration.</span></span> <span data-ttu-id="5f7db-115">要搜尋的其中一個憑證欄位。</span><span class="sxs-lookup"><span data-stu-id="5f7db-115">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="5f7db-116">storeLocation</span><span class="sxs-lookup"><span data-stu-id="5f7db-116">storeLocation</span></span>|<span data-ttu-id="5f7db-117">列舉。</span><span class="sxs-lookup"><span data-stu-id="5f7db-117">Enumeration.</span></span> <span data-ttu-id="5f7db-118">搜尋兩個系統存放位置中的一個。</span><span class="sxs-lookup"><span data-stu-id="5f7db-118">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="5f7db-119">storeName</span><span class="sxs-lookup"><span data-stu-id="5f7db-119">storeName</span></span>|<span data-ttu-id="5f7db-120">列舉。</span><span class="sxs-lookup"><span data-stu-id="5f7db-120">Enumeration.</span></span> <span data-ttu-id="5f7db-121">搜尋的其中一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="5f7db-121">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="5f7db-122">findValue 屬性</span><span class="sxs-lookup"><span data-stu-id="5f7db-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="5f7db-123">值</span><span class="sxs-lookup"><span data-stu-id="5f7db-123">Value</span></span>|<span data-ttu-id="5f7db-124">描述</span><span class="sxs-lookup"><span data-stu-id="5f7db-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5f7db-125">String</span><span class="sxs-lookup"><span data-stu-id="5f7db-125">String</span></span>|<span data-ttu-id="5f7db-126">這個值取決於要搜尋的欄位 (由 X509FindType 屬性指定)。</span><span class="sxs-lookup"><span data-stu-id="5f7db-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="5f7db-127">例如，如果搜尋指紋，則此值必須是十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="5f7db-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="5f7db-128">x509FindType 屬性</span><span class="sxs-lookup"><span data-stu-id="5f7db-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="5f7db-129">值</span><span class="sxs-lookup"><span data-stu-id="5f7db-129">Value</span></span>|<span data-ttu-id="5f7db-130">描述</span><span class="sxs-lookup"><span data-stu-id="5f7db-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5f7db-131">列舉型別</span><span class="sxs-lookup"><span data-stu-id="5f7db-131">Enumeration</span></span>|<span data-ttu-id="5f7db-132">值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage、FindBySubjectKeyIdentifier。</span><span class="sxs-lookup"><span data-stu-id="5f7db-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="5f7db-133">storeLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="5f7db-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="5f7db-134">值</span><span class="sxs-lookup"><span data-stu-id="5f7db-134">Value</span></span>|<span data-ttu-id="5f7db-135">描述</span><span class="sxs-lookup"><span data-stu-id="5f7db-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5f7db-136">列舉型別</span><span class="sxs-lookup"><span data-stu-id="5f7db-136">Enumeration</span></span>|<span data-ttu-id="5f7db-137">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="5f7db-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="5f7db-138">storeName 屬性</span><span class="sxs-lookup"><span data-stu-id="5f7db-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="5f7db-139">值</span><span class="sxs-lookup"><span data-stu-id="5f7db-139">Value</span></span>|<span data-ttu-id="5f7db-140">描述</span><span class="sxs-lookup"><span data-stu-id="5f7db-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5f7db-141">列舉型別</span><span class="sxs-lookup"><span data-stu-id="5f7db-141">Enumeration</span></span>|<span data-ttu-id="5f7db-142">值包括：AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="5f7db-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f7db-143">子元素</span><span class="sxs-lookup"><span data-stu-id="5f7db-143">Child Elements</span></span>  
 <span data-ttu-id="5f7db-144">無。</span><span class="sxs-lookup"><span data-stu-id="5f7db-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f7db-145">父項目</span><span class="sxs-lookup"><span data-stu-id="5f7db-145">Parent Elements</span></span>  
  
|<span data-ttu-id="5f7db-146">元素</span><span class="sxs-lookup"><span data-stu-id="5f7db-146">Element</span></span>|<span data-ttu-id="5f7db-147">描述</span><span class="sxs-lookup"><span data-stu-id="5f7db-147">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="5f7db-148">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="5f7db-148">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f7db-149">備註</span><span class="sxs-lookup"><span data-stu-id="5f7db-149">Remarks</span></span>  
 <span data-ttu-id="5f7db-150">對於使用以憑證為基礎之訊息安全性的繫結，這個組態項目指定的憑證會用來加密傳送給服務的訊息，而且預期會由服務用來簽署對用戶端的回覆。</span><span class="sxs-lookup"><span data-stu-id="5f7db-150">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="5f7db-151">它會儲存當服務未指定憑證時所要使用的單一憑證。</span><span class="sxs-lookup"><span data-stu-id="5f7db-151">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f7db-152">範例</span><span class="sxs-lookup"><span data-stu-id="5f7db-152">Example</span></span>  
 <span data-ttu-id="5f7db-153">下列範例會指定一個憑證，以用於 URI 開頭為的端點 `http://www.contoso.com` ，另一個憑證用於不會執行憑證協商的其他所有端點。</span><span class="sxs-lookup"><span data-stu-id="5f7db-153">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f7db-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f7db-154">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="5f7db-155">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="5f7db-155">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="5f7db-156">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="5f7db-156">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="5f7db-157">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="5f7db-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
