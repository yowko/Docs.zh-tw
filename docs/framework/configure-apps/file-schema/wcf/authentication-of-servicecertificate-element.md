---
title: <authentication> 項目的 <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398232"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="4c5ea-102">\<serviceCertificate > 元素\<的驗證 ></span><span class="sxs-lookup"><span data-stu-id="4c5ea-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="4c5ea-103">指定用戶端 Proxy 用來驗證服務憑證的設定，而這份憑證是使用 SSL/TLS 交涉所取得。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
<span data-ttu-id="4c5ea-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4c5ea-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4c5ea-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4c5ea-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4c5ea-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4c5ea-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="4c5ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4c5ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="4c5ea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4c5ea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="4c5ea-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="4c5ea-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="4c5ea-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="4c5ea-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="4c5ea-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<驗證 >**</span><span class="sxs-lookup"><span data-stu-id="4c5ea-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c5ea-112">語法</span><span class="sxs-lookup"><span data-stu-id="4c5ea-112">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c5ea-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4c5ea-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4c5ea-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="4c5ea-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c5ea-115">屬性</span><span class="sxs-lookup"><span data-stu-id="4c5ea-115">Attributes</span></span>  
  
|<span data-ttu-id="4c5ea-116">屬性</span><span class="sxs-lookup"><span data-stu-id="4c5ea-116">Attribute</span></span>|<span data-ttu-id="4c5ea-117">描述</span><span class="sxs-lookup"><span data-stu-id="4c5ea-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c5ea-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="4c5ea-118">customCertificateValidatorType</span></span>|<span data-ttu-id="4c5ea-119">字串。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-119">String.</span></span> <span data-ttu-id="4c5ea-120">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-120">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="4c5ea-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="4c5ea-121">certificateValidationMode</span></span>|<span data-ttu-id="4c5ea-122">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="4c5ea-123">如果設定為 `Custom`，也必須提供 customCertificateValidator。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-123">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="4c5ea-124">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-124">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="4c5ea-125">revocationMode</span><span class="sxs-lookup"><span data-stu-id="4c5ea-125">revocationMode</span></span>|<span data-ttu-id="4c5ea-126">用於檢查撤銷憑證清單 (CRL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="4c5ea-127">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-127">The default is `Online`.</span></span>|  
|<span data-ttu-id="4c5ea-128">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="4c5ea-128">trustedStoreLocation</span></span>|<span data-ttu-id="4c5ea-129">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="4c5ea-130">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="4c5ea-131">會針對指定存放區位置中的「**受信任的人**」存放區執行驗證。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="4c5ea-132">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="4c5ea-133">customCertificateValidator 屬性</span><span class="sxs-lookup"><span data-stu-id="4c5ea-133">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="4c5ea-134">值</span><span class="sxs-lookup"><span data-stu-id="4c5ea-134">Value</span></span>|<span data-ttu-id="4c5ea-135">描述</span><span class="sxs-lookup"><span data-stu-id="4c5ea-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c5ea-136">String</span><span class="sxs-lookup"><span data-stu-id="4c5ea-136">String</span></span>|<span data-ttu-id="4c5ea-137">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-137">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="4c5ea-138">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="4c5ea-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="4c5ea-139">值</span><span class="sxs-lookup"><span data-stu-id="4c5ea-139">Value</span></span>|<span data-ttu-id="4c5ea-140">說明</span><span class="sxs-lookup"><span data-stu-id="4c5ea-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c5ea-141">列舉</span><span class="sxs-lookup"><span data-stu-id="4c5ea-141">Enumeration</span></span>|<span data-ttu-id="4c5ea-142">下列其中一個值：None、PeerTrust、ChainTrust、PeerOrChainTrust、Custom。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-142">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="4c5ea-143">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="4c5ea-144">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="4c5ea-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="4c5ea-145">值</span><span class="sxs-lookup"><span data-stu-id="4c5ea-145">Value</span></span>|<span data-ttu-id="4c5ea-146">描述</span><span class="sxs-lookup"><span data-stu-id="4c5ea-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c5ea-147">列舉</span><span class="sxs-lookup"><span data-stu-id="4c5ea-147">Enumeration</span></span>|<span data-ttu-id="4c5ea-148">下列其中一個值：NoCheck，線上，離線。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-148">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="4c5ea-149">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="4c5ea-150">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="4c5ea-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="4c5ea-151">值</span><span class="sxs-lookup"><span data-stu-id="4c5ea-151">Value</span></span>|<span data-ttu-id="4c5ea-152">描述</span><span class="sxs-lookup"><span data-stu-id="4c5ea-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c5ea-153">列舉</span><span class="sxs-lookup"><span data-stu-id="4c5ea-153">Enumeration</span></span>|<span data-ttu-id="4c5ea-154">下列其中一個值：LocalMachine 或 CurrentUser。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-154">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="4c5ea-155">預設為 CurrentUser。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-155">The default is CurrentUser.</span></span> <span data-ttu-id="4c5ea-156">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 LocalMachine 之下。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-156">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="4c5ea-157">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 CurrentUser 中。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-157">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c5ea-158">子元素</span><span class="sxs-lookup"><span data-stu-id="4c5ea-158">Child Elements</span></span>  
 <span data-ttu-id="4c5ea-159">無。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c5ea-160">父項目</span><span class="sxs-lookup"><span data-stu-id="4c5ea-160">Parent Elements</span></span>  
  
|<span data-ttu-id="4c5ea-161">項目</span><span class="sxs-lookup"><span data-stu-id="4c5ea-161">Element</span></span>|<span data-ttu-id="4c5ea-162">描述</span><span class="sxs-lookup"><span data-stu-id="4c5ea-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c5ea-163">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4c5ea-163">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="4c5ea-164">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-164">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c5ea-165">備註</span><span class="sxs-lookup"><span data-stu-id="4c5ea-165">Remarks</span></span>  
 <span data-ttu-id="4c5ea-166">這個組態項目的 `certificateValidationMode` 屬性會指定用來驗證憑證的信任層級。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-166">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="4c5ea-167">根據預設，層級會設為 `ChainTrust`，指定每一個憑證必須出現在鏈結頂端以受信任的憑證授權單位為結尾的憑證階層中。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-167">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="4c5ea-168">這是最安全的模式。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-168">This is the most secure mode.</span></span> <span data-ttu-id="4c5ea-169">您也可以將值設定為 `PeerOrChainTrust`，指定可接受自行發出的憑證 (對等信任)，以及信任鏈結內的憑證。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-169">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="4c5ea-170">這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-170">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="4c5ea-171">部署用戶端時，請改用 `ChainTrust` 值。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-171">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="4c5ea-172">您也可以將值設為 `Custom` 或 `None`。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-172">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="4c5ea-173">若要使用 `Custom` 值，您必須同時將 `customCertificateValidator` 屬性 (Attribute) 設為可用來驗證憑證的組件與型別。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-173">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="4c5ea-174">若要建立自己的自訂驗證程式，您必須繼承自抽象 X509CertificateValidator 類別。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-174">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="4c5ea-175">如需詳細資訊，請參閱[如何：建立採用自訂憑證驗證](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)程式的服務。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-175">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="4c5ea-176">`revocationMode` 屬性會指定檢查憑證是否已被撤銷的方法。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-176">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="4c5ea-177">預設為 `online`，表示會自動檢查該憑證是否已被撤銷。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-177">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="4c5ea-178">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-178">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c5ea-179">範例</span><span class="sxs-lookup"><span data-stu-id="4c5ea-179">Example</span></span>  
 <span data-ttu-id="4c5ea-180">下列範例會執行兩個工作。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-180">The following example does two tasks.</span></span> <span data-ttu-id="4c5ea-181">它會先指定服務憑證，讓用戶端在與其功能變數名稱是`www.contoso.com`透過 HTTP 通訊協定的端點進行通訊時使用。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-181">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="4c5ea-182">第二，指定驗證時使用的撤銷模式和存放區位置。</span><span class="sxs-lookup"><span data-stu-id="4c5ea-182">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4c5ea-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c5ea-183">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="4c5ea-184">安全性行為</span><span class="sxs-lookup"><span data-stu-id="4c5ea-184">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="4c5ea-185">使用憑證</span><span class="sxs-lookup"><span data-stu-id="4c5ea-185">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="4c5ea-186">如何：建立採用自訂憑證驗證程式的服務</span><span class="sxs-lookup"><span data-stu-id="4c5ea-186">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="4c5ea-187">\<authentication></span><span class="sxs-lookup"><span data-stu-id="4c5ea-187">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="4c5ea-188">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="4c5ea-188">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="4c5ea-189">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="4c5ea-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
