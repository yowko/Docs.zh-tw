---
title: "&lt;serviceCertificate&gt; 項目的 &lt;authentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cb2f567b47f66b378cc6e0a5d5e96441ea65c1ac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a><span data-ttu-id="e2760-102">&lt;serviceCertificate&gt; 項目的 &lt;authentication&gt;</span><span class="sxs-lookup"><span data-stu-id="e2760-102">&lt;authentication&gt; of &lt;serviceCertificate&gt; Element</span></span>
<span data-ttu-id="e2760-103">指定用戶端 Proxy 用來驗證服務憑證的設定，而這份憑證是使用 SSL/TLS 交涉所取得。</span><span class="sxs-lookup"><span data-stu-id="e2760-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="e2760-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e2760-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e2760-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e2760-105">\<behaviors></span></span>  
<span data-ttu-id="e2760-106">endpointBehaviors 區段</span><span class="sxs-lookup"><span data-stu-id="e2760-106">endpointBehaviors section</span></span>  
<span data-ttu-id="e2760-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e2760-107">\<behavior></span></span>  
<span data-ttu-id="e2760-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="e2760-108">\<clientCredentials></span></span>  
<span data-ttu-id="e2760-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="e2760-109">\<serviceCertificate></span></span>  
<span data-ttu-id="e2760-110">\<驗證 ></span><span class="sxs-lookup"><span data-stu-id="e2760-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2760-111">語法</span><span class="sxs-lookup"><span data-stu-id="e2760-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2760-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e2760-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e2760-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="e2760-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2760-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e2760-114">Attributes</span></span>  
  
|<span data-ttu-id="e2760-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e2760-115">Attribute</span></span>|<span data-ttu-id="e2760-116">描述</span><span class="sxs-lookup"><span data-stu-id="e2760-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2760-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="e2760-117">customCertificateValidatorType</span></span>|<span data-ttu-id="e2760-118">字串。</span><span class="sxs-lookup"><span data-stu-id="e2760-118">String.</span></span> <span data-ttu-id="e2760-119">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="e2760-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="e2760-120">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="e2760-120">certificateValidationMode</span></span>|<span data-ttu-id="e2760-121">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="e2760-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="e2760-122">如果設定為 `Custom`，也必須提供 customCertificateValidator。</span><span class="sxs-lookup"><span data-stu-id="e2760-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="e2760-123">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="e2760-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="e2760-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="e2760-124">revocationMode</span></span>|<span data-ttu-id="e2760-125">用於檢查撤銷憑證清單 (CRL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="e2760-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="e2760-126">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="e2760-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="e2760-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="e2760-127">trustedStoreLocation</span></span>|<span data-ttu-id="e2760-128">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="e2760-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="e2760-129">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="e2760-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="e2760-130">針對執行驗證**受信任的人**將儲存在指定的存放區位置。</span><span class="sxs-lookup"><span data-stu-id="e2760-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="e2760-131">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="e2760-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="e2760-132">customCertificateValidator 屬性</span><span class="sxs-lookup"><span data-stu-id="e2760-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="e2760-133">值</span><span class="sxs-lookup"><span data-stu-id="e2760-133">Value</span></span>|<span data-ttu-id="e2760-134">描述</span><span class="sxs-lookup"><span data-stu-id="e2760-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e2760-135">String</span><span class="sxs-lookup"><span data-stu-id="e2760-135">String</span></span>|<span data-ttu-id="e2760-136">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="e2760-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="e2760-137">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="e2760-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="e2760-138">值</span><span class="sxs-lookup"><span data-stu-id="e2760-138">Value</span></span>|<span data-ttu-id="e2760-139">描述</span><span class="sxs-lookup"><span data-stu-id="e2760-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e2760-140">列舉</span><span class="sxs-lookup"><span data-stu-id="e2760-140">Enumeration</span></span>|<span data-ttu-id="e2760-141">下列其中一個值：None、PeerTrust、ChainTrust、PeerOrChainTrust、Custom。</span><span class="sxs-lookup"><span data-stu-id="e2760-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="e2760-142">如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="e2760-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="e2760-143">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="e2760-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="e2760-144">值</span><span class="sxs-lookup"><span data-stu-id="e2760-144">Value</span></span>|<span data-ttu-id="e2760-145">描述</span><span class="sxs-lookup"><span data-stu-id="e2760-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e2760-146">列舉</span><span class="sxs-lookup"><span data-stu-id="e2760-146">Enumeration</span></span>|<span data-ttu-id="e2760-147">下列其中一個值：NoCheck、Online、Offline。</span><span class="sxs-lookup"><span data-stu-id="e2760-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="e2760-148">如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="e2760-148">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="e2760-149">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="e2760-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="e2760-150">值</span><span class="sxs-lookup"><span data-stu-id="e2760-150">Value</span></span>|<span data-ttu-id="e2760-151">描述</span><span class="sxs-lookup"><span data-stu-id="e2760-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e2760-152">列舉</span><span class="sxs-lookup"><span data-stu-id="e2760-152">Enumeration</span></span>|<span data-ttu-id="e2760-153">下列其中一個值：LocalMachine 或 CurrentUser。</span><span class="sxs-lookup"><span data-stu-id="e2760-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="e2760-154">預設為 CurrentUser。</span><span class="sxs-lookup"><span data-stu-id="e2760-154">The default is CurrentUser.</span></span> <span data-ttu-id="e2760-155">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 LocalMachine 之下。</span><span class="sxs-lookup"><span data-stu-id="e2760-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="e2760-156">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 CurrentUser 中。</span><span class="sxs-lookup"><span data-stu-id="e2760-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2760-157">子元素</span><span class="sxs-lookup"><span data-stu-id="e2760-157">Child Elements</span></span>  
 <span data-ttu-id="e2760-158">無。</span><span class="sxs-lookup"><span data-stu-id="e2760-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2760-159">父項目</span><span class="sxs-lookup"><span data-stu-id="e2760-159">Parent Elements</span></span>  
  
|<span data-ttu-id="e2760-160">項目</span><span class="sxs-lookup"><span data-stu-id="e2760-160">Element</span></span>|<span data-ttu-id="e2760-161">說明</span><span class="sxs-lookup"><span data-stu-id="e2760-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2760-162">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="e2760-162">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="e2760-163">指定對用戶端驗證服務時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="e2760-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2760-164">備註</span><span class="sxs-lookup"><span data-stu-id="e2760-164">Remarks</span></span>  
 <span data-ttu-id="e2760-165">這個組態項目的 `certificateValidationMode` 屬性會指定用來驗證憑證的信任層級。</span><span class="sxs-lookup"><span data-stu-id="e2760-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="e2760-166">根據預設，層級會設為 `ChainTrust`，指定每一個憑證必須出現在鏈結頂端以受信任的憑證授權單位為結尾的憑證階層中。</span><span class="sxs-lookup"><span data-stu-id="e2760-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="e2760-167">這是最安全的模式。</span><span class="sxs-lookup"><span data-stu-id="e2760-167">This is the most secure mode.</span></span> <span data-ttu-id="e2760-168">您也可以將值設定為 `PeerOrChainTrust`，指定可接受自行發出的憑證 (對等信任)，以及信任鏈結內的憑證。</span><span class="sxs-lookup"><span data-stu-id="e2760-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="e2760-169">這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。</span><span class="sxs-lookup"><span data-stu-id="e2760-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="e2760-170">部署用戶端時，請改用 `ChainTrust` 值。</span><span class="sxs-lookup"><span data-stu-id="e2760-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="e2760-171">您也可以將值設為 `Custom` 或 `None`。</span><span class="sxs-lookup"><span data-stu-id="e2760-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="e2760-172">若要使用 `Custom` 值，您必須同時將 `customCertificateValidator` 屬性 (Attribute) 設為可用來驗證憑證的組件與型別。</span><span class="sxs-lookup"><span data-stu-id="e2760-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="e2760-173">若要建立自己的自訂驗證程式，您必須繼承自抽象 X509CertificateValidator 類別。</span><span class="sxs-lookup"><span data-stu-id="e2760-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="e2760-174">如需詳細資訊，請參閱[How to： 建立採用自訂憑證驗證程式服務](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。</span><span class="sxs-lookup"><span data-stu-id="e2760-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="e2760-175">`revocationMode` 屬性會指定檢查憑證是否已被撤銷的方法。</span><span class="sxs-lookup"><span data-stu-id="e2760-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="e2760-176">預設為 `online`，表示會自動檢查該憑證是否已被撤銷。</span><span class="sxs-lookup"><span data-stu-id="e2760-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="e2760-177">如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="e2760-177">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2760-178">範例</span><span class="sxs-lookup"><span data-stu-id="e2760-178">Example</span></span>  
 <span data-ttu-id="e2760-179">下列範例會執行兩個工作。</span><span class="sxs-lookup"><span data-stu-id="e2760-179">The following example does two tasks.</span></span> <span data-ttu-id="e2760-180">第一，指定當用戶端以 HTTP 通訊協定與網域名稱為 www.contoso.com 的端點通訊時，使用的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="e2760-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is www.contoso.com over the HTTP protocol.</span></span> <span data-ttu-id="e2760-181">第二，指定驗證時使用的撤銷模式和存放區位置。</span><span class="sxs-lookup"><span data-stu-id="e2760-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2760-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2760-182">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [<span data-ttu-id="e2760-183">安全性行為</span><span class="sxs-lookup"><span data-stu-id="e2760-183">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="e2760-184">使用憑證</span><span class="sxs-lookup"><span data-stu-id="e2760-184">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="e2760-185">如何： 建立採用自訂憑證驗證程式服務</span><span class="sxs-lookup"><span data-stu-id="e2760-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="e2760-186">\<驗證 ></span><span class="sxs-lookup"><span data-stu-id="e2760-186">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="e2760-187">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="e2760-187">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="e2760-188">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="e2760-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
