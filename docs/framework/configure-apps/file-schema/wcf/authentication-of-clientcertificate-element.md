---
title: <authentication> 項目的 <clientCertificate>
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 99084f6b7afbdd8586ee706cd6ec44b349d81ff2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398259"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="e6021-102">\<clientCertificate > 元素\<的驗證 ></span><span class="sxs-lookup"><span data-stu-id="e6021-102">\<authentication> of \<clientCertificate> Element</span></span>
<span data-ttu-id="e6021-103">指定服務所使用之用戶端憑證的驗證行為。</span><span class="sxs-lookup"><span data-stu-id="e6021-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
<span data-ttu-id="e6021-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e6021-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e6021-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e6021-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e6021-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6021-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e6021-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6021-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="e6021-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e6021-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="e6021-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e6021-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="e6021-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCertificate >** ](clientcertificate-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e6021-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)</span></span>\
<span data-ttu-id="e6021-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<驗證 >**</span><span class="sxs-lookup"><span data-stu-id="e6021-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6021-112">語法</span><span class="sxs-lookup"><span data-stu-id="e6021-112">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6021-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6021-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e6021-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="e6021-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6021-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e6021-115">Attributes</span></span>  
  
|<span data-ttu-id="e6021-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e6021-116">Attribute</span></span>|<span data-ttu-id="e6021-117">描述</span><span class="sxs-lookup"><span data-stu-id="e6021-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6021-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="e6021-118">customCertificateValidatorType</span></span>|<span data-ttu-id="e6021-119">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="e6021-119">Optional string.</span></span> <span data-ttu-id="e6021-120">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="e6021-120">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="e6021-121">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="e6021-121">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="e6021-122">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="e6021-122">certificateValidationMode</span></span>|<span data-ttu-id="e6021-123">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="e6021-123">Optional enumeration.</span></span> <span data-ttu-id="e6021-124">指定用來驗證認證的其中一個模式。</span><span class="sxs-lookup"><span data-stu-id="e6021-124">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="e6021-125">此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="e6021-125">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="e6021-126">如果設定為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="e6021-126">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="e6021-127">預設為 <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e6021-127">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="e6021-128">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="e6021-128">includeWindowsGroups</span></span>|<span data-ttu-id="e6021-129">選擇性布林值。</span><span class="sxs-lookup"><span data-stu-id="e6021-129">Optional Boolean.</span></span> <span data-ttu-id="e6021-130">指定 Windows 群組是否包含在安全性內容中。</span><span class="sxs-lookup"><span data-stu-id="e6021-130">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="e6021-131">將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。</span><span class="sxs-lookup"><span data-stu-id="e6021-131">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="e6021-132">如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="e6021-132">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="e6021-133">mapClientCertificateToWindowsAccount</span><span class="sxs-lookup"><span data-stu-id="e6021-133">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="e6021-134">布林值。</span><span class="sxs-lookup"><span data-stu-id="e6021-134">Boolean.</span></span> <span data-ttu-id="e6021-135">指定是否能夠使用憑證將用戶端對應至 Windows 身分識別。</span><span class="sxs-lookup"><span data-stu-id="e6021-135">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="e6021-136">必須啟用 Active Directory 才能這麼做。</span><span class="sxs-lookup"><span data-stu-id="e6021-136">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="e6021-137">revocationMode</span><span class="sxs-lookup"><span data-stu-id="e6021-137">revocationMode</span></span>|<span data-ttu-id="e6021-138">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="e6021-138">Optional enumeration.</span></span> <span data-ttu-id="e6021-139">用於檢查撤銷憑證清單 (RCL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="e6021-139">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="e6021-140">預設為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="e6021-140">The default is `Online`.</span></span> <span data-ttu-id="e6021-141">使用 HTTP 傳輸安全性時，將忽略此值。</span><span class="sxs-lookup"><span data-stu-id="e6021-141">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="e6021-142">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="e6021-142">trustedStoreLocation</span></span>|<span data-ttu-id="e6021-143">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="e6021-143">Optional enumeration.</span></span> <span data-ttu-id="e6021-144">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="e6021-144">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="e6021-145">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="e6021-145">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="e6021-146">會針對指定存放區位置中的「**受信任的人**」存放區執行驗證。</span><span class="sxs-lookup"><span data-stu-id="e6021-146">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="e6021-147">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="e6021-147">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="e6021-148">customCertificateValidatorType 屬性</span><span class="sxs-lookup"><span data-stu-id="e6021-148">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="e6021-149">值</span><span class="sxs-lookup"><span data-stu-id="e6021-149">Value</span></span>|<span data-ttu-id="e6021-150">描述</span><span class="sxs-lookup"><span data-stu-id="e6021-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6021-151">String</span><span class="sxs-lookup"><span data-stu-id="e6021-151">String</span></span>|<span data-ttu-id="e6021-152">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="e6021-152">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="e6021-153">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="e6021-153">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="e6021-154">值</span><span class="sxs-lookup"><span data-stu-id="e6021-154">Value</span></span>|<span data-ttu-id="e6021-155">描述</span><span class="sxs-lookup"><span data-stu-id="e6021-155">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6021-156">列舉</span><span class="sxs-lookup"><span data-stu-id="e6021-156">Enumeration</span></span>|<span data-ttu-id="e6021-157">下列其中一個值：None、PeerTrust、ChainTrust、PeerOrChainTrust、Custom。</span><span class="sxs-lookup"><span data-stu-id="e6021-157">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="e6021-158">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="e6021-158">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="e6021-159">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="e6021-159">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="e6021-160">值</span><span class="sxs-lookup"><span data-stu-id="e6021-160">Value</span></span>|<span data-ttu-id="e6021-161">說明</span><span class="sxs-lookup"><span data-stu-id="e6021-161">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6021-162">列舉</span><span class="sxs-lookup"><span data-stu-id="e6021-162">Enumeration</span></span>|<span data-ttu-id="e6021-163">下列其中一個值：NoCheck，線上，離線。</span><span class="sxs-lookup"><span data-stu-id="e6021-163">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="e6021-164">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="e6021-164">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="e6021-165">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="e6021-165">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="e6021-166">值</span><span class="sxs-lookup"><span data-stu-id="e6021-166">Value</span></span>|<span data-ttu-id="e6021-167">描述</span><span class="sxs-lookup"><span data-stu-id="e6021-167">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6021-168">列舉</span><span class="sxs-lookup"><span data-stu-id="e6021-168">Enumeration</span></span>|<span data-ttu-id="e6021-169">下列其中一個值：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="e6021-169">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="e6021-170">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="e6021-170">The default is `CurrentUser`.</span></span> <span data-ttu-id="e6021-171">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。</span><span class="sxs-lookup"><span data-stu-id="e6021-171">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="e6021-172">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="e6021-172">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6021-173">子元素</span><span class="sxs-lookup"><span data-stu-id="e6021-173">Child Elements</span></span>  
 <span data-ttu-id="e6021-174">無。</span><span class="sxs-lookup"><span data-stu-id="e6021-174">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6021-175">父項目</span><span class="sxs-lookup"><span data-stu-id="e6021-175">Parent Elements</span></span>  
  
|<span data-ttu-id="e6021-176">項目</span><span class="sxs-lookup"><span data-stu-id="e6021-176">Element</span></span>|<span data-ttu-id="e6021-177">描述</span><span class="sxs-lookup"><span data-stu-id="e6021-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6021-178">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="e6021-178">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="e6021-179">定義用於向服務驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="e6021-179">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6021-180">備註</span><span class="sxs-lookup"><span data-stu-id="e6021-180">Remarks</span></span>  
 <span data-ttu-id="e6021-181">`<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 類別。</span><span class="sxs-lookup"><span data-stu-id="e6021-181">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="e6021-182">它可讓您自訂驗證用戶端的方法。</span><span class="sxs-lookup"><span data-stu-id="e6021-182">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="e6021-183">您可以將 `certificateValidationMode` 屬性 (Attribute) 設定為 `None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust` 或 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="e6021-183">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="e6021-184">根據預設，層級會設定為`ChainTrust`，這會指定每個憑證都必須在鏈頂端以*根授權*單位結尾的憑證階層中找到。</span><span class="sxs-lookup"><span data-stu-id="e6021-184">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="e6021-185">這是最安全的模式。</span><span class="sxs-lookup"><span data-stu-id="e6021-185">This is the most secure mode.</span></span> <span data-ttu-id="e6021-186">您也可以將值設定為 `PeerOrChainTrust`，指定可接受自行發出的憑證 (對等信任)，以及信任鏈結內的憑證。</span><span class="sxs-lookup"><span data-stu-id="e6021-186">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="e6021-187">這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。</span><span class="sxs-lookup"><span data-stu-id="e6021-187">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="e6021-188">部署用戶端時，請改用 `ChainTrust` 值。</span><span class="sxs-lookup"><span data-stu-id="e6021-188">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="e6021-189">您也可以將值設定為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="e6021-189">You can also set the value to `Custom`.</span></span> <span data-ttu-id="e6021-190">設定為 `Custom` 值時，您還必須將 `customCertificateValidatorType` 屬性設定為可用來驗證憑證的組件與型別。</span><span class="sxs-lookup"><span data-stu-id="e6021-190">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="e6021-191">若要建立自己的自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。</span><span class="sxs-lookup"><span data-stu-id="e6021-191">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="e6021-192">如需詳細資訊，請參閱[如何：建立採用自訂憑證驗證](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)程式的服務。</span><span class="sxs-lookup"><span data-stu-id="e6021-192">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6021-193">範例</span><span class="sxs-lookup"><span data-stu-id="e6021-193">Example</span></span>  
 <span data-ttu-id="e6021-194">下列程式碼會在 `<authentication>` 項目中指定 X.509 憑證和自訂驗證類型。</span><span class="sxs-lookup"><span data-stu-id="e6021-194">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6021-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6021-195">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="e6021-196">安全性行為</span><span class="sxs-lookup"><span data-stu-id="e6021-196">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e6021-197">如何：建立採用自訂憑證驗證程式的服務</span><span class="sxs-lookup"><span data-stu-id="e6021-197">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="e6021-198">使用憑證</span><span class="sxs-lookup"><span data-stu-id="e6021-198">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
