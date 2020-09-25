---
title: <add> 項目的 <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 28777ecac130295a8ba82a8e4d67cc519d088d8a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195138"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="22b70-102">\<add> 項目的 \<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="22b70-102">\<add> of \<scopedCertificates> Element</span></span>

<span data-ttu-id="22b70-103">將 X.509 憑證加入至範圍憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="22b70-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="22b70-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="22b70-104">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22b70-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="22b70-105">Attributes and Elements</span></span>  

 <span data-ttu-id="22b70-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="22b70-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22b70-107">屬性</span><span class="sxs-lookup"><span data-stu-id="22b70-107">Attributes</span></span>  
  
|<span data-ttu-id="22b70-108">屬性</span><span class="sxs-lookup"><span data-stu-id="22b70-108">Attribute</span></span>|<span data-ttu-id="22b70-109">描述</span><span class="sxs-lookup"><span data-stu-id="22b70-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22b70-110">targetUri</span><span class="sxs-lookup"><span data-stu-id="22b70-110">targetUri</span></span>|<span data-ttu-id="22b70-111">字串。</span><span class="sxs-lookup"><span data-stu-id="22b70-111">String.</span></span> <span data-ttu-id="22b70-112">指定與憑證相關聯的服務之 URI。</span><span class="sxs-lookup"><span data-stu-id="22b70-112">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="22b70-113">findValue</span><span class="sxs-lookup"><span data-stu-id="22b70-113">findValue</span></span>|<span data-ttu-id="22b70-114">字串。</span><span class="sxs-lookup"><span data-stu-id="22b70-114">String.</span></span> <span data-ttu-id="22b70-115">要搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="22b70-115">The value to search for.</span></span>|  
|<span data-ttu-id="22b70-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="22b70-116">x509FindType</span></span>|<span data-ttu-id="22b70-117">列舉。</span><span class="sxs-lookup"><span data-stu-id="22b70-117">Enumeration.</span></span> <span data-ttu-id="22b70-118">要搜尋的其中一個憑證欄位。</span><span class="sxs-lookup"><span data-stu-id="22b70-118">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="22b70-119">storeLocation</span><span class="sxs-lookup"><span data-stu-id="22b70-119">storeLocation</span></span>|<span data-ttu-id="22b70-120">列舉。</span><span class="sxs-lookup"><span data-stu-id="22b70-120">Enumeration.</span></span> <span data-ttu-id="22b70-121">搜尋兩個存放位置中的一個。</span><span class="sxs-lookup"><span data-stu-id="22b70-121">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="22b70-122">storeName</span><span class="sxs-lookup"><span data-stu-id="22b70-122">storeName</span></span>|<span data-ttu-id="22b70-123">列舉。</span><span class="sxs-lookup"><span data-stu-id="22b70-123">Enumeration.</span></span> <span data-ttu-id="22b70-124">搜尋的其中一個系統存放區。</span><span class="sxs-lookup"><span data-stu-id="22b70-124">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="22b70-125">findValue 屬性</span><span class="sxs-lookup"><span data-stu-id="22b70-125">findValue Attribute</span></span>  
  
|<span data-ttu-id="22b70-126">值</span><span class="sxs-lookup"><span data-stu-id="22b70-126">Value</span></span>|<span data-ttu-id="22b70-127">描述</span><span class="sxs-lookup"><span data-stu-id="22b70-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="22b70-128">String</span><span class="sxs-lookup"><span data-stu-id="22b70-128">String</span></span>|<span data-ttu-id="22b70-129">這個值取決於要搜尋的欄位 (由 X509FindType 屬性指定)。</span><span class="sxs-lookup"><span data-stu-id="22b70-129">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="22b70-130">例如，如果搜尋指紋，則此值必須是十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="22b70-130">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="22b70-131">x509FindType 屬性</span><span class="sxs-lookup"><span data-stu-id="22b70-131">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="22b70-132">值</span><span class="sxs-lookup"><span data-stu-id="22b70-132">Value</span></span>|<span data-ttu-id="22b70-133">描述</span><span class="sxs-lookup"><span data-stu-id="22b70-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="22b70-134">列舉型別</span><span class="sxs-lookup"><span data-stu-id="22b70-134">Enumeration</span></span>|<span data-ttu-id="22b70-135">值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage、FindBySubjectKeyIdentifier。</span><span class="sxs-lookup"><span data-stu-id="22b70-135">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="22b70-136">storeLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="22b70-136">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="22b70-137">值</span><span class="sxs-lookup"><span data-stu-id="22b70-137">Value</span></span>|<span data-ttu-id="22b70-138">描述</span><span class="sxs-lookup"><span data-stu-id="22b70-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="22b70-139">列舉型別</span><span class="sxs-lookup"><span data-stu-id="22b70-139">Enumeration</span></span>|<span data-ttu-id="22b70-140">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="22b70-140">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="22b70-141">storeName 屬性</span><span class="sxs-lookup"><span data-stu-id="22b70-141">storeName Attribute</span></span>  
  
|<span data-ttu-id="22b70-142">值</span><span class="sxs-lookup"><span data-stu-id="22b70-142">Value</span></span>|<span data-ttu-id="22b70-143">描述</span><span class="sxs-lookup"><span data-stu-id="22b70-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="22b70-144">列舉型別</span><span class="sxs-lookup"><span data-stu-id="22b70-144">Enumeration</span></span>|<span data-ttu-id="22b70-145">值包括：AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="22b70-145">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22b70-146">子元素</span><span class="sxs-lookup"><span data-stu-id="22b70-146">Child Elements</span></span>  

 <span data-ttu-id="22b70-147">無。</span><span class="sxs-lookup"><span data-stu-id="22b70-147">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22b70-148">父項目</span><span class="sxs-lookup"><span data-stu-id="22b70-148">Parent Elements</span></span>  
  
|<span data-ttu-id="22b70-149">項目</span><span class="sxs-lookup"><span data-stu-id="22b70-149">Element</span></span>|<span data-ttu-id="22b70-150">描述</span><span class="sxs-lookup"><span data-stu-id="22b70-150">Description</span></span>|  
|-------------|-----------------|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="22b70-151">表示特定服務 (範圍服務) 為驗證所提供之 X.509 憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="22b70-151">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22b70-152">備註</span><span class="sxs-lookup"><span data-stu-id="22b70-152">Remarks</span></span>  

 <span data-ttu-id="22b70-153">這個項目可讓用戶端根據與其進行通訊之服務的 URL 設定要使用的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="22b70-153">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="22b70-154">在用戶端可以與多重服務 (終端服務以及中繼安全性權杖服務) 進行通訊的已核發權杖情況中，這個屬性特別有用。</span><span class="sxs-lookup"><span data-stu-id="22b70-154">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="22b70-155">對於使用以憑證為基礎之訊息安全性的繫結，這個憑證會用來加密傳送給服務的訊息，而且預期會被服務用來簽署對用戶端的回覆。</span><span class="sxs-lookup"><span data-stu-id="22b70-155">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="22b70-156">如果繫結需要服務的憑證，但是在 ScopedCertificates 中找不到服務 URL 的專屬憑證，則會使用預設的憑證。</span><span class="sxs-lookup"><span data-stu-id="22b70-156">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="22b70-157">如需詳細資訊，請參閱 [如何：建立同盟用戶端](../../../wcf/feature-details/how-to-create-a-federated-client.md)的「範圍憑證」一節。</span><span class="sxs-lookup"><span data-stu-id="22b70-157">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22b70-158">範例</span><span class="sxs-lookup"><span data-stu-id="22b70-158">Example</span></span>  

 <span data-ttu-id="22b70-159">下列範例會將 X.509 憑證新增至集合。</span><span class="sxs-lookup"><span data-stu-id="22b70-159">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22b70-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22b70-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="22b70-161">作法：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="22b70-161">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="22b70-162">使用憑證</span><span class="sxs-lookup"><span data-stu-id="22b70-162">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="22b70-163">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="22b70-163">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="22b70-164">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="22b70-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
