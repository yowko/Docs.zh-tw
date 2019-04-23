---
title: <authentication> 項目的 <clientCertificate>
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: e232cde8f6838de734e37aeee3f52cd7f7e7502d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221198"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="6dfee-102">\<驗證 > 的\<clientCertificate > 項目</span><span class="sxs-lookup"><span data-stu-id="6dfee-102">\<authentication> of \<clientCertificate> Element</span></span>
<span data-ttu-id="6dfee-103">指定服務所使用之用戶端憑證的驗證行為。</span><span class="sxs-lookup"><span data-stu-id="6dfee-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
 <span data-ttu-id="6dfee-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6dfee-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6dfee-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="6dfee-105">\<behaviors></span></span>  
<span data-ttu-id="6dfee-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6dfee-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6dfee-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="6dfee-107">\<behavior></span></span>  
<span data-ttu-id="6dfee-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="6dfee-108">\<serviceCredentials></span></span>  
<span data-ttu-id="6dfee-109">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="6dfee-109">\<clientCertificate></span></span>  
<span data-ttu-id="6dfee-110">\<驗證 ></span><span class="sxs-lookup"><span data-stu-id="6dfee-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dfee-111">語法</span><span class="sxs-lookup"><span data-stu-id="6dfee-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6dfee-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6dfee-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6dfee-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="6dfee-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6dfee-114">屬性</span><span class="sxs-lookup"><span data-stu-id="6dfee-114">Attributes</span></span>  
  
|<span data-ttu-id="6dfee-115">屬性</span><span class="sxs-lookup"><span data-stu-id="6dfee-115">Attribute</span></span>|<span data-ttu-id="6dfee-116">描述</span><span class="sxs-lookup"><span data-stu-id="6dfee-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6dfee-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="6dfee-117">customCertificateValidatorType</span></span>|<span data-ttu-id="6dfee-118">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="6dfee-118">Optional string.</span></span> <span data-ttu-id="6dfee-119">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="6dfee-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="6dfee-120">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="6dfee-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="6dfee-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="6dfee-121">certificateValidationMode</span></span>|<span data-ttu-id="6dfee-122">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="6dfee-122">Optional enumeration.</span></span> <span data-ttu-id="6dfee-123">指定用來驗證認證的其中一個模式。</span><span class="sxs-lookup"><span data-stu-id="6dfee-123">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="6dfee-124">此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="6dfee-124">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="6dfee-125">如果設定為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="6dfee-125">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="6dfee-126">預設為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6dfee-126">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="6dfee-127">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="6dfee-127">includeWindowsGroups</span></span>|<span data-ttu-id="6dfee-128">選擇性布林值。</span><span class="sxs-lookup"><span data-stu-id="6dfee-128">Optional Boolean.</span></span> <span data-ttu-id="6dfee-129">指定 Windows 群組是否包含在安全性內容中。</span><span class="sxs-lookup"><span data-stu-id="6dfee-129">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="6dfee-130">將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。</span><span class="sxs-lookup"><span data-stu-id="6dfee-130">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="6dfee-131">如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6dfee-131">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="6dfee-132">mapClientCertificateToWindowsAcccount</span><span class="sxs-lookup"><span data-stu-id="6dfee-132">mapClientCertificateToWindowsAcccount</span></span>|<span data-ttu-id="6dfee-133">布林值。</span><span class="sxs-lookup"><span data-stu-id="6dfee-133">Boolean.</span></span> <span data-ttu-id="6dfee-134">指定是否能夠使用憑證將用戶端對應至 Windows 身分識別。</span><span class="sxs-lookup"><span data-stu-id="6dfee-134">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="6dfee-135">必須啟用 Active Directory 才能這麼做。</span><span class="sxs-lookup"><span data-stu-id="6dfee-135">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="6dfee-136">revocationMode</span><span class="sxs-lookup"><span data-stu-id="6dfee-136">revocationMode</span></span>|<span data-ttu-id="6dfee-137">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="6dfee-137">Optional enumeration.</span></span> <span data-ttu-id="6dfee-138">用於檢查撤銷憑證清單 (RCL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="6dfee-138">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="6dfee-139">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="6dfee-139">The default is `Online`.</span></span> <span data-ttu-id="6dfee-140">使用 HTTP 傳輸安全性時，將忽略此值。</span><span class="sxs-lookup"><span data-stu-id="6dfee-140">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="6dfee-141">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="6dfee-141">trustedStoreLocation</span></span>|<span data-ttu-id="6dfee-142">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="6dfee-142">Optional enumeration.</span></span> <span data-ttu-id="6dfee-143">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="6dfee-143">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="6dfee-144">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="6dfee-144">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="6dfee-145">針對執行驗證**受信任的人**將儲存在指定的存放區位置。</span><span class="sxs-lookup"><span data-stu-id="6dfee-145">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="6dfee-146">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="6dfee-146">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="6dfee-147">customCertificateValidatorType 屬性</span><span class="sxs-lookup"><span data-stu-id="6dfee-147">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="6dfee-148">值</span><span class="sxs-lookup"><span data-stu-id="6dfee-148">Value</span></span>|<span data-ttu-id="6dfee-149">描述</span><span class="sxs-lookup"><span data-stu-id="6dfee-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6dfee-150">String</span><span class="sxs-lookup"><span data-stu-id="6dfee-150">String</span></span>|<span data-ttu-id="6dfee-151">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="6dfee-151">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="6dfee-152">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="6dfee-152">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="6dfee-153">值</span><span class="sxs-lookup"><span data-stu-id="6dfee-153">Value</span></span>|<span data-ttu-id="6dfee-154">描述</span><span class="sxs-lookup"><span data-stu-id="6dfee-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6dfee-155">列舉</span><span class="sxs-lookup"><span data-stu-id="6dfee-155">Enumeration</span></span>|<span data-ttu-id="6dfee-156">下列其中一個值：None、 PeerTrust、 ChainTrust、 PeerOrChainTrust、 Custom。</span><span class="sxs-lookup"><span data-stu-id="6dfee-156">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="6dfee-157">如需詳細資訊，請參閱 < [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="6dfee-157">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="6dfee-158">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="6dfee-158">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="6dfee-159">值</span><span class="sxs-lookup"><span data-stu-id="6dfee-159">Value</span></span>|<span data-ttu-id="6dfee-160">描述</span><span class="sxs-lookup"><span data-stu-id="6dfee-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6dfee-161">列舉</span><span class="sxs-lookup"><span data-stu-id="6dfee-161">Enumeration</span></span>|<span data-ttu-id="6dfee-162">下列其中一個值：NoCheck、 Online、 Offline。</span><span class="sxs-lookup"><span data-stu-id="6dfee-162">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="6dfee-163">如需詳細資訊，請參閱 < [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="6dfee-163">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="6dfee-164">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="6dfee-164">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="6dfee-165">值</span><span class="sxs-lookup"><span data-stu-id="6dfee-165">Value</span></span>|<span data-ttu-id="6dfee-166">描述</span><span class="sxs-lookup"><span data-stu-id="6dfee-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6dfee-167">列舉</span><span class="sxs-lookup"><span data-stu-id="6dfee-167">Enumeration</span></span>|<span data-ttu-id="6dfee-168">下列其中一個值：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="6dfee-168">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="6dfee-169">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="6dfee-169">The default is `CurrentUser`.</span></span> <span data-ttu-id="6dfee-170">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。</span><span class="sxs-lookup"><span data-stu-id="6dfee-170">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="6dfee-171">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="6dfee-171">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6dfee-172">子元素</span><span class="sxs-lookup"><span data-stu-id="6dfee-172">Child Elements</span></span>  
 <span data-ttu-id="6dfee-173">無。</span><span class="sxs-lookup"><span data-stu-id="6dfee-173">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6dfee-174">父項目</span><span class="sxs-lookup"><span data-stu-id="6dfee-174">Parent Elements</span></span>  
  
|<span data-ttu-id="6dfee-175">項目</span><span class="sxs-lookup"><span data-stu-id="6dfee-175">Element</span></span>|<span data-ttu-id="6dfee-176">描述</span><span class="sxs-lookup"><span data-stu-id="6dfee-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6dfee-177">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="6dfee-177">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="6dfee-178">定義用於向服務驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="6dfee-178">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dfee-179">備註</span><span class="sxs-lookup"><span data-stu-id="6dfee-179">Remarks</span></span>  
 <span data-ttu-id="6dfee-180">`<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 類別。</span><span class="sxs-lookup"><span data-stu-id="6dfee-180">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="6dfee-181">它可讓您自訂驗證用戶端的方法。</span><span class="sxs-lookup"><span data-stu-id="6dfee-181">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="6dfee-182">您可以將 `certificateValidationMode` 屬性 (Attribute) 設定為 `None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust` 或 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="6dfee-182">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="6dfee-183">根據預設，層級設定為`ChainTrust`，指定每個憑證必須位於結尾中的憑證階層*根授權單位*在鏈結頂端。</span><span class="sxs-lookup"><span data-stu-id="6dfee-183">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="6dfee-184">這是最安全的模式。</span><span class="sxs-lookup"><span data-stu-id="6dfee-184">This is the most secure mode.</span></span> <span data-ttu-id="6dfee-185">您也可以將值設定為 `PeerOrChainTrust`，指定可接受自行發出的憑證 (對等信任)，以及信任鏈結內的憑證。</span><span class="sxs-lookup"><span data-stu-id="6dfee-185">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="6dfee-186">這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。</span><span class="sxs-lookup"><span data-stu-id="6dfee-186">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="6dfee-187">部署用戶端時，請改用 `ChainTrust` 值。</span><span class="sxs-lookup"><span data-stu-id="6dfee-187">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="6dfee-188">您也可以將值設定為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="6dfee-188">You can also set the value to `Custom`.</span></span> <span data-ttu-id="6dfee-189">設定為 `Custom` 值時，您還必須將 `customCertificateValidatorType` 屬性設定為可用來驗證憑證的組件與型別。</span><span class="sxs-lookup"><span data-stu-id="6dfee-189">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="6dfee-190">若要建立自己的自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。</span><span class="sxs-lookup"><span data-stu-id="6dfee-190">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="6dfee-191">如需詳細資訊，請參閱[如何：建立使用自訂憑證驗證程式服務](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。</span><span class="sxs-lookup"><span data-stu-id="6dfee-191">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dfee-192">範例</span><span class="sxs-lookup"><span data-stu-id="6dfee-192">Example</span></span>  
 <span data-ttu-id="6dfee-193">下列程式碼會在 `<authentication>` 項目中指定 X.509 憑證和自訂驗證類型。</span><span class="sxs-lookup"><span data-stu-id="6dfee-193">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="6dfee-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dfee-194">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="6dfee-195">安全性行為</span><span class="sxs-lookup"><span data-stu-id="6dfee-195">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6dfee-196">如何：建立使用自訂憑證驗證程式服務</span><span class="sxs-lookup"><span data-stu-id="6dfee-196">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="6dfee-197">使用憑證</span><span class="sxs-lookup"><span data-stu-id="6dfee-197">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
