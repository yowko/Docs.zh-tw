---
title: "&lt;clientCertificate&gt; 的 &lt;authentication&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4eb125727d68d1618b32d21612ecfac28eaa5b6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a><span data-ttu-id="38a87-102">&lt;clientCertificate&gt; 的 &lt;authentication&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="38a87-102">&lt;authentication&gt; of &lt;clientCertificate&gt; Element</span></span>
<span data-ttu-id="38a87-103">指定服務所使用之用戶端憑證的驗證行為。</span><span class="sxs-lookup"><span data-stu-id="38a87-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
 <span data-ttu-id="38a87-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="38a87-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="38a87-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="38a87-105">\<behaviors></span></span>  
<span data-ttu-id="38a87-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="38a87-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="38a87-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="38a87-107">\<behavior></span></span>  
<span data-ttu-id="38a87-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="38a87-108">\<serviceCredentials></span></span>  
<span data-ttu-id="38a87-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="38a87-109">\<clientCertificate></span></span>  
<span data-ttu-id="38a87-110">\<驗證 ></span><span class="sxs-lookup"><span data-stu-id="38a87-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38a87-111">語法</span><span class="sxs-lookup"><span data-stu-id="38a87-111">Syntax</span></span>  
  
```xml  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38a87-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38a87-112">Attributes and Elements</span></span>  
 <span data-ttu-id="38a87-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="38a87-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38a87-114">屬性</span><span class="sxs-lookup"><span data-stu-id="38a87-114">Attributes</span></span>  
  
|<span data-ttu-id="38a87-115">屬性</span><span class="sxs-lookup"><span data-stu-id="38a87-115">Attribute</span></span>|<span data-ttu-id="38a87-116">描述</span><span class="sxs-lookup"><span data-stu-id="38a87-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38a87-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="38a87-117">customCertificateValidatorType</span></span>|<span data-ttu-id="38a87-118">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="38a87-118">Optional string.</span></span> <span data-ttu-id="38a87-119">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="38a87-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="38a87-120">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="38a87-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="38a87-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="38a87-121">certificateValidationMode</span></span>|<span data-ttu-id="38a87-122">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="38a87-122">Optional enumeration.</span></span> <span data-ttu-id="38a87-123">指定用來驗證認證的其中一個模式。</span><span class="sxs-lookup"><span data-stu-id="38a87-123">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="38a87-124">此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="38a87-124">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="38a87-125">如果設定為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="38a87-125">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="38a87-126">預設為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="38a87-126">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="38a87-127">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="38a87-127">includeWindowsGroups</span></span>|<span data-ttu-id="38a87-128">選擇性布林值。</span><span class="sxs-lookup"><span data-stu-id="38a87-128">Optional Boolean.</span></span> <span data-ttu-id="38a87-129">指定 Windows 群組是否包含在安全性內容中。</span><span class="sxs-lookup"><span data-stu-id="38a87-129">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="38a87-130">將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。</span><span class="sxs-lookup"><span data-stu-id="38a87-130">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="38a87-131">如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="38a87-131">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="38a87-132">mapClientCertificateToWindowsAcccount</span><span class="sxs-lookup"><span data-stu-id="38a87-132">mapClientCertificateToWindowsAcccount</span></span>|<span data-ttu-id="38a87-133">布林值。</span><span class="sxs-lookup"><span data-stu-id="38a87-133">Boolean.</span></span> <span data-ttu-id="38a87-134">指定是否能夠使用憑證將用戶端對應至 Windows 身分識別。</span><span class="sxs-lookup"><span data-stu-id="38a87-134">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="38a87-135">必須啟用 Active Directory 才能這麼做。</span><span class="sxs-lookup"><span data-stu-id="38a87-135">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="38a87-136">revocationMode</span><span class="sxs-lookup"><span data-stu-id="38a87-136">revocationMode</span></span>|<span data-ttu-id="38a87-137">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="38a87-137">Optional enumeration.</span></span> <span data-ttu-id="38a87-138">用於檢查撤銷憑證清單 (RCL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="38a87-138">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="38a87-139">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="38a87-139">The default is `Online`.</span></span> <span data-ttu-id="38a87-140">使用 HTTP 傳輸安全性時，將忽略此值。</span><span class="sxs-lookup"><span data-stu-id="38a87-140">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="38a87-141">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="38a87-141">trustedStoreLocation</span></span>|<span data-ttu-id="38a87-142">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="38a87-142">Optional enumeration.</span></span> <span data-ttu-id="38a87-143">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="38a87-143">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="38a87-144">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="38a87-144">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="38a87-145">針對執行驗證**受信任的人**將儲存在指定的存放區位置。</span><span class="sxs-lookup"><span data-stu-id="38a87-145">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="38a87-146">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="38a87-146">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="38a87-147">customCertificateValidatorType 屬性</span><span class="sxs-lookup"><span data-stu-id="38a87-147">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="38a87-148">值</span><span class="sxs-lookup"><span data-stu-id="38a87-148">Value</span></span>|<span data-ttu-id="38a87-149">描述</span><span class="sxs-lookup"><span data-stu-id="38a87-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38a87-150">String</span><span class="sxs-lookup"><span data-stu-id="38a87-150">String</span></span>|<span data-ttu-id="38a87-151">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="38a87-151">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="38a87-152">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="38a87-152">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="38a87-153">值</span><span class="sxs-lookup"><span data-stu-id="38a87-153">Value</span></span>|<span data-ttu-id="38a87-154">描述</span><span class="sxs-lookup"><span data-stu-id="38a87-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38a87-155">列舉</span><span class="sxs-lookup"><span data-stu-id="38a87-155">Enumeration</span></span>|<span data-ttu-id="38a87-156">下列其中一個值：None、PeerTrust、ChainTrust、PeerOrChainTrust、Custom。</span><span class="sxs-lookup"><span data-stu-id="38a87-156">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="38a87-157">如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="38a87-157">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="38a87-158">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="38a87-158">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="38a87-159">值</span><span class="sxs-lookup"><span data-stu-id="38a87-159">Value</span></span>|<span data-ttu-id="38a87-160">描述</span><span class="sxs-lookup"><span data-stu-id="38a87-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38a87-161">列舉</span><span class="sxs-lookup"><span data-stu-id="38a87-161">Enumeration</span></span>|<span data-ttu-id="38a87-162">下列其中一個值：NoCheck、Online、Offline。</span><span class="sxs-lookup"><span data-stu-id="38a87-162">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="38a87-163">如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="38a87-163">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="38a87-164">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="38a87-164">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="38a87-165">值</span><span class="sxs-lookup"><span data-stu-id="38a87-165">Value</span></span>|<span data-ttu-id="38a87-166">描述</span><span class="sxs-lookup"><span data-stu-id="38a87-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38a87-167">列舉</span><span class="sxs-lookup"><span data-stu-id="38a87-167">Enumeration</span></span>|<span data-ttu-id="38a87-168">下列其中一個值：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="38a87-168">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="38a87-169">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="38a87-169">The default is `CurrentUser`.</span></span> <span data-ttu-id="38a87-170">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。</span><span class="sxs-lookup"><span data-stu-id="38a87-170">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="38a87-171">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="38a87-171">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38a87-172">子元素</span><span class="sxs-lookup"><span data-stu-id="38a87-172">Child Elements</span></span>  
 <span data-ttu-id="38a87-173">無。</span><span class="sxs-lookup"><span data-stu-id="38a87-173">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38a87-174">父項目</span><span class="sxs-lookup"><span data-stu-id="38a87-174">Parent Elements</span></span>  
  
|<span data-ttu-id="38a87-175">項目</span><span class="sxs-lookup"><span data-stu-id="38a87-175">Element</span></span>|<span data-ttu-id="38a87-176">說明</span><span class="sxs-lookup"><span data-stu-id="38a87-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38a87-177">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="38a87-177">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="38a87-178">定義用於向服務驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="38a87-178">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38a87-179">備註</span><span class="sxs-lookup"><span data-stu-id="38a87-179">Remarks</span></span>  
 <span data-ttu-id="38a87-180">`<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 類別。</span><span class="sxs-lookup"><span data-stu-id="38a87-180">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="38a87-181">它可讓您自訂驗證用戶端的方法。</span><span class="sxs-lookup"><span data-stu-id="38a87-181">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="38a87-182">您可以將 `certificateValidationMode` 屬性 (Attribute) 設定為 `None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust` 或 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="38a87-182">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="38a87-183">根據預設，層級設為`ChainTrust`，指定的每個憑證必須出現在結尾中的憑證階層中*根授權*在鏈結頂端。</span><span class="sxs-lookup"><span data-stu-id="38a87-183">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="38a87-184">這是最安全的模式。</span><span class="sxs-lookup"><span data-stu-id="38a87-184">This is the most secure mode.</span></span> <span data-ttu-id="38a87-185">您也可以將值設定為 `PeerOrChainTrust`，指定可接受自行發出的憑證 (對等信任)，以及信任鏈結內的憑證。</span><span class="sxs-lookup"><span data-stu-id="38a87-185">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="38a87-186">這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。</span><span class="sxs-lookup"><span data-stu-id="38a87-186">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="38a87-187">部署用戶端時，請改用 `ChainTrust` 值。</span><span class="sxs-lookup"><span data-stu-id="38a87-187">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="38a87-188">您也可以將值設定為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="38a87-188">You can also set the value to `Custom`.</span></span> <span data-ttu-id="38a87-189">設定為 `Custom` 值時，您還必須將 `customCertificateValidatorType` 屬性設定為可用來驗證憑證的組件與型別。</span><span class="sxs-lookup"><span data-stu-id="38a87-189">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="38a87-190">若要建立自己的自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。</span><span class="sxs-lookup"><span data-stu-id="38a87-190">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="38a87-191">如需詳細資訊，請參閱[How to： 建立採用自訂憑證驗證程式服務](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。</span><span class="sxs-lookup"><span data-stu-id="38a87-191">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38a87-192">範例</span><span class="sxs-lookup"><span data-stu-id="38a87-192">Example</span></span>  
 <span data-ttu-id="38a87-193">下列程式碼會在 `<authentication>` 項目中指定 X.509 憑證和自訂驗證類型。</span><span class="sxs-lookup"><span data-stu-id="38a87-193">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
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
  
## <a name="see-also"></a><span data-ttu-id="38a87-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38a87-194">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>  
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>  
 [<span data-ttu-id="38a87-195">安全性行為</span><span class="sxs-lookup"><span data-stu-id="38a87-195">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="38a87-196">如何： 建立採用自訂憑證驗證程式服務</span><span class="sxs-lookup"><span data-stu-id="38a87-196">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="38a87-197">使用憑證</span><span class="sxs-lookup"><span data-stu-id="38a87-197">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
