---
title: WCF 中的安全性行為
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 4e8452d2beb93c9ae59ef6535f45445352a48e22
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288329"
---
# <a name="security-behaviors-in-wcf"></a><span data-ttu-id="8e4b7-102">WCF 中的安全性行為</span><span class="sxs-lookup"><span data-stu-id="8e4b7-102">Security Behaviors in WCF</span></span>

<span data-ttu-id="8e4b7-103">在 Windows Communication Foundation (WCF) 中，行為會修改服務層級或端點層級的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-103">In Windows Communication Foundation (WCF), behaviors modify run-time behavior at the service level or at the endpoint level.</span></span> <span data-ttu-id="8e4b7-104"> (如需有關一般行為的詳細資訊，請參閱 [指定服務 Run-Time 行為](../specifying-service-run-time-behavior.md)。 ) *安全性行為* 允許控制認證、驗證、授權和審核記錄。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-104">(For more information about behaviors in general, see [Specifying Service Run-Time Behavior](../specifying-service-run-time-behavior.md).) *Security behaviors* allow control over credentials, authentication, authorization, and auditing logs.</span></span> <span data-ttu-id="8e4b7-105">您可以藉由程式設計的方式或透過組態的方式使用這些行為。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-105">You can use behaviors either by programming or through configuration.</span></span> <span data-ttu-id="8e4b7-106">本主題將著重於設定下列與安全性功能相關的行為：</span><span class="sxs-lookup"><span data-stu-id="8e4b7-106">This topic focuses on configuring the following behaviors related to security functions:</span></span>  
  
- <span data-ttu-id="8e4b7-107">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="8e4b7-107">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
- <span data-ttu-id="8e4b7-108">[\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="8e4b7-108">[\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).</span></span>  
  
- <span data-ttu-id="8e4b7-109">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).</span><span class="sxs-lookup"><span data-stu-id="8e4b7-109">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).</span></span>  
  
- <span data-ttu-id="8e4b7-110">[\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).</span><span class="sxs-lookup"><span data-stu-id="8e4b7-110">[\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).</span></span>  
  
- <span data-ttu-id="8e4b7-111">[\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md)，也可讓您指定用戶端可以存取中繼資料的安全端點。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-111">[\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md), which also enables you to specify a secure endpoint that clients can access for metadata.</span></span>  
  
## <a name="setting-credentials-with-behaviors"></a><span data-ttu-id="8e4b7-112">設定認證與行為</span><span class="sxs-lookup"><span data-stu-id="8e4b7-112">Setting Credentials with Behaviors</span></span>  

 <span data-ttu-id="8e4b7-113">使用 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 和 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) 來設定服務或用戶端的認證值。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-113">Use the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) and [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) to set credential values for a service or client.</span></span> <span data-ttu-id="8e4b7-114">基礎繫結組態會判斷是否必須設定認證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-114">The underlying binding configuration determines whether a credential has to be set.</span></span> <span data-ttu-id="8e4b7-115">例如，若安全性模式設定為 `None`，則用戶端和服務不需互相驗證彼此，也不需要任何類型的認證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-115">For example, if the security mode is set to `None`, both clients and services do not authenticate each other and require no credentials of any type.</span></span>  
  
 <span data-ttu-id="8e4b7-116">另一方面，服務繫結程序可以要求用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-116">On the other hand, the service binding can require a client credential type.</span></span> <span data-ttu-id="8e4b7-117">在這種情況下，您必須使用行為設定認證值</span><span class="sxs-lookup"><span data-stu-id="8e4b7-117">In that case, you may have to set a credential value using a behavior.</span></span> <span data-ttu-id="8e4b7-118"> (如需有關可能的認證類型的詳細資訊，請參閱 [選取認證類型](selecting-a-credential-type.md)。在某些情況下 ) ，例如使用 Windows 認證進行驗證時，環境會自動建立實際的認證值，而且您不需要明確地設定認證值 (除非您想要指定不同的認證集) 。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-118">(For more information about the possible types of credentials, see [Selecting a Credential Type](selecting-a-credential-type.md).) In some cases, such as when Windows credentials are used to authenticate, the environment automatically establishes the actual credential value and you do not need to explicitly set the credential value (unless you want to specify a different set of credentials).</span></span>  
  
 <span data-ttu-id="8e4b7-119">所有服務認證都可作為的子項目 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-119">All service credentials are found as child elements of the [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md).</span></span> <span data-ttu-id="8e4b7-120">下列範例示範當成服務認證使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-120">The following example shows a certificate used as a service credential.</span></span>  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a><span data-ttu-id="8e4b7-121">服務認證</span><span class="sxs-lookup"><span data-stu-id="8e4b7-121">Service Credentials</span></span>  

 <span data-ttu-id="8e4b7-122">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md)包含四個子項目。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-122">The [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) contains four child elements.</span></span> <span data-ttu-id="8e4b7-123">下列各章節將討論這些項目及其使用方法。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-123">The elements and their usages are discussed in the following sections.</span></span>  
  
### <a name="servicecertificate-element"></a><span data-ttu-id="8e4b7-124">\<serviceCertificate> 項目</span><span class="sxs-lookup"><span data-stu-id="8e4b7-124">\<serviceCertificate> Element</span></span>  

 <span data-ttu-id="8e4b7-125">使用此項目指定 X.509 憑證，而該憑證將用以驗證使用訊息安全性模式的用戶端服務。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-125">Use this element to specify an X.509 certificate that is used to authenticate the service to clients using Message security mode.</span></span> <span data-ttu-id="8e4b7-126">如果您是使用會定期更新的憑證，則其指紋將會變更。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-126">If you are using a certificate that is periodically renewed, then its thumbprint changes.</span></span> <span data-ttu-id="8e4b7-127">在這種情況下，請使用主體名稱當成 `X509FindType`，因為憑證可以使用相同的主體名稱重新發出。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-127">In that case, use the subject name as the `X509FindType` because the certificate can be reissued with the same subject name.</span></span>  
  
 <span data-ttu-id="8e4b7-128">如需使用元素的詳細資訊，請參閱 [如何：指定用戶端認證值](../how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-128">For more information about using the element, see [How to: Specify Client Credential Values](../how-to-specify-client-credential-values.md).</span></span>  
  
### <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="8e4b7-129">\<certificate> 項目的 \<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="8e4b7-129">\<certificate> of \<clientCertificate> Element</span></span>  

 <span data-ttu-id="8e4b7-130">[\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)當服務必須具有用戶端的憑證，才能與用戶端安全地進行通訊時，請使用元素。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-130">Use the [\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) element when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="8e4b7-131">這種情況發生在使用雙工通訊模式時。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-131">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="8e4b7-132">在較為典型的要求-回覆模式下，用戶端會在要求中納入其憑證，以便讓服務使用此憑證安全地將回覆傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-132">In the more typical request-reply pattern, the client includes its certificate in the request, which the service uses to secure its response back to the client.</span></span> <span data-ttu-id="8e4b7-133">不過，雙工通訊模式便沒有要求和回覆。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-133">The duplex communication pattern, however, has no requests and replies.</span></span> <span data-ttu-id="8e4b7-134">由於服務無法從通訊中推斷用戶端的憑證，服務即需要用戶端的憑證，以便與用戶端安全地傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-134">The service cannot infer the client's certificate from the communication and therefore the service requires the client's certificate in advance to secure the messages to the client.</span></span> <span data-ttu-id="8e4b7-135">您必須以頻外的方式來取得用戶端的憑證，並使用此元素來指定憑證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-135">You must obtain the client's certificate in an out-of-band manner and specify the certificate using this element.</span></span> <span data-ttu-id="8e4b7-136">如需雙工服務的詳細資訊，請參閱 [如何：建立雙工合約](how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-136">For more information about duplex services, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
### <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="8e4b7-137">\<authentication> 項目的 \<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="8e4b7-137">\<authentication> of \<clientCertificate> Element</span></span>  

 <span data-ttu-id="8e4b7-138">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)元素可讓您自訂用戶端的驗證方式。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-138">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) element enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="8e4b7-139">您可以將 `CertificateValidationMode` 屬性 (Attribute) 設定為 `None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust` 或 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-139">You can set the `CertificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="8e4b7-140">根據預設，層級會設為 `ChainTrust` ，指定每個憑證都必須在鏈頂端以 *根授權* 單位結尾的憑證階層中找到。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-140">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="8e4b7-141">這是最安全的模式。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-141">This is the most secure mode.</span></span> <span data-ttu-id="8e4b7-142">您也可以將值設定為 `PeerOrChainTrust`，指定可接受自行發出的憑證 (對等信任)，以及信任鏈結內的憑證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-142">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="8e4b7-143">這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-143">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="8e4b7-144">部署用戶端時，請改用 `ChainTrust` 值。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-144">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="8e4b7-145">您也可以將值設定為 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-145">You can also set the value to `Custom`.</span></span> <span data-ttu-id="8e4b7-146">設定為 `Custom` 值時，您還必須將 `CustomCertificateValidatorType` 屬性設定為可用來驗證憑證的組件與型別。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-146">When set to the `Custom` value, you must also set the `CustomCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="8e4b7-147">若要建立自己的自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-147">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
### <a name="issuedtokenauthentication-element"></a><span data-ttu-id="8e4b7-148">\<issuedTokenAuthentication> 項目</span><span class="sxs-lookup"><span data-stu-id="8e4b7-148">\<issuedTokenAuthentication> Element</span></span>  

 <span data-ttu-id="8e4b7-149">發行之權杖的情況有三個階段。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-149">The issued token scenario has three stages.</span></span> <span data-ttu-id="8e4b7-150">在第一個階段中，嘗試存取服務的用戶端是指 (STS) 的 *安全權杖服務* 。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-150">In the first stage, a client trying to access a service is referred to a *secure token service* (STS).</span></span> <span data-ttu-id="8e4b7-151">此 STS 接著會驗證用戶端，隨後並對用戶端發出權杖，通常是安全性判斷提示標記語言 (SAML) 權杖。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-151">The STS then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="8e4b7-152">用戶端接著會以權杖傳回服務。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-152">The client then returns to the service with the token.</span></span> <span data-ttu-id="8e4b7-153">此服務會檢查資料的權杖，使服務能夠驗證權杖，因此也能夠驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-153">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="8e4b7-154">若要驗證權杖，安全權杖服務所使用的憑證必須讓服務知道。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-154">To authenticate the token, the certificate that the secure token service uses must be known to the service.</span></span> <span data-ttu-id="8e4b7-155">[\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)元素是任何這類安全權杖服務憑證的存放庫。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-155">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="8e4b7-156">若要加入憑證，請使用 [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md) 。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-156">To add certificates, use the [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="8e4b7-157">為 [\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md) 每個憑證插入，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-157">Insert an [\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"
           storeLocation="LocalMachine" storeName="My"
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="8e4b7-158">根據預設，必須從安全權杖服務取得憑證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-158">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="8e4b7-159">這些「已知的」憑證可確保只有合法的用戶端可以存取服務。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-159">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="8e4b7-160">您應該在使用 [\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md) *安全權杖服務* 的同盟應用程式中使用集合， (STS) 來發出 `SamlSecurityToken` 安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-160">You should use the [\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md) collection in a federated application that utilizes a *secure token service* (STS) that issues `SamlSecurityToken` security tokens.</span></span> <span data-ttu-id="8e4b7-161">當 STS 發出安全性權杖時，它可以將 `SamlAudienceRestrictionCondition` 加入至安全性權杖中，以便指定此安全性權杖適用之 Web 服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-161">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a `SamlAudienceRestrictionCondition` to the security token.</span></span> <span data-ttu-id="8e4b7-162">如此便可讓接收端 Web 服務的 `SamlSecurityTokenAuthenticator` 驗證發出的安全性權杖是否適用於此 Web 服務，而驗證的方法則是指定這項檢查應該透過執行下列動作來進行：</span><span class="sxs-lookup"><span data-stu-id="8e4b7-162">That allows the `SamlSecurityTokenAuthenticator` for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="8e4b7-163">將的 `audienceUriMode` 屬性設定 [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) 為 `Always` 或 `BearerKeyOnly` 。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-163">Set the `audienceUriMode` attribute of [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) to `Always` or `BearerKeyOnly`.</span></span>  
  
- <span data-ttu-id="8e4b7-164">將 URI 加入此集合，以指定有效的 URI 集合。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-164">Specify the set of valid URIs, by adding the URIs to this collection.</span></span> <span data-ttu-id="8e4b7-165">若要這樣做，請 [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) 為每個 URI 插入</span><span class="sxs-lookup"><span data-stu-id="8e4b7-165">To do this, insert an [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) for each URI</span></span>  
  
 <span data-ttu-id="8e4b7-166">如需詳細資訊，請參閱<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-166">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="8e4b7-167">如需使用此設定元素的詳細資訊，請參閱 [如何：在同盟服務上設定認證](how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-167">For more information about using this configuration element, see [How to: Configure Credentials on a Federation Service](how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
#### <a name="allowing-anonymous-cardspace-users"></a><span data-ttu-id="8e4b7-168">允許匿名的 CardSpace 使用者</span><span class="sxs-lookup"><span data-stu-id="8e4b7-168">Allowing Anonymous CardSpace Users</span></span>  

 <span data-ttu-id="8e4b7-169">將 `AllowUntrustedRsaIssuers` 項目的 `<IssuedTokenAuthentication>` 屬性設定為 `true`，以明確地允許任何用戶端提出以任一 RSA 金鑰組所簽署之自行發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-169">Setting the `AllowUntrustedRsaIssuers` attribute of the `<IssuedTokenAuthentication>` element to `true` explicitly allows any client to present a self-issued token signed with an arbitrary RSA key pair.</span></span> <span data-ttu-id="8e4b7-170">簽發者未 *受信任* ，因為金鑰沒有相關聯的簽發者資料。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-170">The issuer is *untrusted* because the key has no issuer data associated with it.</span></span> <span data-ttu-id="8e4b7-171">CardSpace 使用者可以建立自我發行的卡片，其中包含自我提供的身分識別宣告。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-171">A CardSpace user can create a self-issued card that includes self-provided claims of identity.</span></span> <span data-ttu-id="8e4b7-172">使用這個功能時必須要很小心。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-172">Use this capability with caution.</span></span> <span data-ttu-id="8e4b7-173">若要使用此功能，請考慮使用 RSA 公開金鑰做為更安全的密碼，這個金鑰應該與使用者名稱一起儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-173">To use this feature, think of the RSA public key as a more secure password that should be stored in a database along with a user name.</span></span> <span data-ttu-id="8e4b7-174">允許用戶端存取服務之前，請確認用戶端所提出的 RSA 公開金鑰，此動作可透過將用戶端所提出的 RSA 公開金鑰與所呈現之使用者名稱對應的儲存公開金鑰進行比較來達成。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-174">Before allowing a client access to the service, verify the client-presented RSA public key by comparing it with the stored public key for the presented user name.</span></span> <span data-ttu-id="8e4b7-175">這個情況是假設您已建立註冊程式，以便讓使用者註冊其使用者名稱，並將其與自行發行的 RSA 公開金鑰產生關聯。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-175">This presumes that you have established a registration process whereby users can register their user names and associate them with the self-issued RSA public keys.</span></span>  
  
## <a name="client-credentials"></a><span data-ttu-id="8e4b7-176">用戶端認證</span><span class="sxs-lookup"><span data-stu-id="8e4b7-176">Client Credentials</span></span>  

 <span data-ttu-id="8e4b7-177">在需要雙向驗證的情況下，用戶端認證可用於驗證服務的用戶端。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-177">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="8e4b7-178">在用戶端必須以服務的憑證保護傳遞給服務的訊息時，您可以使用此章節的說明指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-178">You can use the section to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
 <span data-ttu-id="8e4b7-179">您也可以將用戶端設定為同盟案例的一部分，以便從安全權杖服務或權杖的本機簽發者使用發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-179">You can also configure a client as part of a federation scenario to use issued tokens from a secure token service or a local issuer of tokens.</span></span> <span data-ttu-id="8e4b7-180">如需同盟案例的詳細資訊，請參閱 [同盟和已發行的權杖](federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-180">For more information about federated scenarios, see [Federation and Issued Tokens](federation-and-issued-tokens.md).</span></span> <span data-ttu-id="8e4b7-181">中的所有用戶端認證都可以在底下找到 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) ，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-181">All client credentials are found under the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md), as shown in the following code.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
#### <a name="clientcertificate-element"></a><span data-ttu-id="8e4b7-182">\<clientCertificate> 項目</span><span class="sxs-lookup"><span data-stu-id="8e4b7-182">\<clientCertificate> Element</span></span>  

 <span data-ttu-id="8e4b7-183">使用此項目來設定用以驗證用戶端的憑證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-183">Set the certificate used to authenticate the client with this element.</span></span> <span data-ttu-id="8e4b7-184">如需詳細資訊，請參閱 [如何：指定用戶端認證值](../how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-184">For more information, see [How to: Specify Client Credential Values](../how-to-specify-client-credential-values.md).</span></span>  
  
#### \<httpDigest>  

 <span data-ttu-id="8e4b7-185">此功能必須與 Windows 和 Internet Information Services (IIS) 上的 Active Directory 一起啟用。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-185">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="8e4b7-186">如需詳細資訊，請參閱 [IIS 6.0 中的摘要式驗證](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-186">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
#### <a name="issuedtoken-element"></a><span data-ttu-id="8e4b7-187">\<issuedToken> 項目</span><span class="sxs-lookup"><span data-stu-id="8e4b7-187">\<issuedToken> Element</span></span>  

 <span data-ttu-id="8e4b7-188">[\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md)包含用來設定權杖之本機簽發者的專案，或搭配安全性權杖服務使用的行為。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-188">The [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="8e4b7-189">如需將用戶端設定為使用本機簽發者的指示，請參閱 [如何：設定本機簽發者](how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-189">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](how-to-configure-a-local-issuer.md).</span></span>  
  
#### \<localIssuerAddress>  

 <span data-ttu-id="8e4b7-190">指定預設的安全性權杖服務位址。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-190">Specifies a default security token service address.</span></span> <span data-ttu-id="8e4b7-191">當 <xref:System.ServiceModel.WSFederationHttpBinding> 未提供安全性權杖服務的 URL，或同盟系結的簽發者位址為或時，就會使用這個 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` 。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-191">This is used when the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="8e4b7-192">在這種情形下，<xref:System.ServiceModel.Description.ClientCredentials> 必須設定本機簽發者的位址，以及用於與該簽發者進行通訊的繫結。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-192">In such cases, the <xref:System.ServiceModel.Description.ClientCredentials> must be configured with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
#### \<issuerChannelBehaviors>  

 <span data-ttu-id="8e4b7-193">使用 [\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) 加入與安全性權杖服務通訊時所使用的 WCF 用戶端行為。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-193">Use the [\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) to add WCF client behaviors used when communicating with a security token service.</span></span> <span data-ttu-id="8e4b7-194">在區段中定義用戶端行為 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-194">Define client behaviors in the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) section.</span></span> <span data-ttu-id="8e4b7-195">若要使用定義的行為，請將 <`add`> 元素加入 `<issuerChannelBehaviors>` 具有兩個屬性的專案。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-195">To use a defined behavior, add an <`add`> element to the `<issuerChannelBehaviors>` element with two attributes.</span></span> <span data-ttu-id="8e4b7-196">將 `issuerAddress` 設定為安全性權杖服務的 URL，並將 `behaviorConfiguration` 屬性設定為已定義之端點行為的名稱，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-196">Set the `issuerAddress` to the URL of the security token service and set the `behaviorConfiguration` attribute to the name of the defined endpoint behavior, as shown in the following example.</span></span>  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
      </issuerChannelBehaviors>  
   </issuedToken>  
</clientCredentials>
```  
  
#### <a name="servicecertificate-element"></a><span data-ttu-id="8e4b7-197">\<serviceCertificate> 項目</span><span class="sxs-lookup"><span data-stu-id="8e4b7-197">\<serviceCertificate> Element</span></span>  

 <span data-ttu-id="8e4b7-198">使用此項目控制服務憑證的驗證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-198">Use this element to control authentication of service certificates.</span></span>  
  
 <span data-ttu-id="8e4b7-199">[\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md)當服務未指定憑證時，元素可以儲存使用的單一憑證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-199">The [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) element can store a single certificate used when the service specifies no certificate.</span></span>  
  
 <span data-ttu-id="8e4b7-200">使用 [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) 和 [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) 來設定與特定服務相關聯的服務憑證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-200">Use the [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) and [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) to set service certificates that are associated with specific services.</span></span> <span data-ttu-id="8e4b7-201">`<add>` 項目包含 `targetUri` 屬性，此屬性是用於將憑證與服務產生關聯。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-201">The `<add>` element includes a `targetUri` attribute that is used to associate the certificate with the service.</span></span>  
  
 <span data-ttu-id="8e4b7-202">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)元素會指定用來驗證憑證的信任層級。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-202">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="8e4b7-203">根據預設，層級會設為 "ChainTrust"，指定每一個憑證必須出現在鏈結頂端以受信任的憑證授權單位為結尾的憑證階層中。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-203">By default, the level is set to "ChainTrust," which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="8e4b7-204">這是最安全的模式。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-204">This is the most secure mode.</span></span> <span data-ttu-id="8e4b7-205">您也可以將其值設定為 "PeerOrChainTrust"，指定可接受自行簽發的憑證 (對等信任)，以及信任鏈結內的憑證。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-205">You can also set the value to "PeerOrChainTrust", which specifies that self-issued certificates (peer trust) are accepted, as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="8e4b7-206">這個值會在開發及偵錯用戶端和服務時使用，因為自行發出的憑證不需要從受信任的授權單位購買。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-206">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="8e4b7-207">部署用戶端時，請改用 "ChainTrust" 值。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-207">When deploying a client, use the "ChainTrust" value instead.</span></span> <span data-ttu-id="8e4b7-208">您也可以將值設定為 "Custom" 或 "None"。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-208">You can also set the value to "Custom" or "None."</span></span> <span data-ttu-id="8e4b7-209">若要使用 "Custom" 值，您必須同時將 `CustomCertificateValidatorType` 屬性設為可用來驗證憑證的組件與型別。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-209">To use the "Custom" value, you must also set the `CustomCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="8e4b7-210">若要建立自己的自訂驗證程式，您必須繼承自抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 類別。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-210">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="8e4b7-211">如需詳細資訊，請參閱 [如何：建立採用自訂憑證驗證程式的服務](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-211">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="8e4b7-212">專案 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) 包含 `RevocationMode` 屬性，該屬性會指定如何檢查憑證的撤銷。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-212">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element includes a `RevocationMode` attribute that specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="8e4b7-213">預設為 "online"，指出會自動檢查該憑證是否已被撤銷。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-213">The default is "online", which indicates that certificates are automatically checked for revocation.</span></span> <span data-ttu-id="8e4b7-214">如需詳細資訊，請參閱 [使用憑證](working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-214">For more information, see [Working with Certificates](working-with-certificates.md).</span></span>  
  
## <a name="serviceauthorization"></a><span data-ttu-id="8e4b7-215">ServiceAuthorization</span><span class="sxs-lookup"><span data-stu-id="8e4b7-215">ServiceAuthorization</span></span>  

 <span data-ttu-id="8e4b7-216">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)元素包含會影響授權、自訂角色提供者和模擬的元素。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-216">The [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) element contains elements that affect authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="8e4b7-217"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 類別會套用至服務方法。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-217">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> class is applied to a service method.</span></span> <span data-ttu-id="8e4b7-218">屬性會指定使用者群組，以便在對保護的方法進行授權使用時使用。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-218">The attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="8e4b7-219">預設值為 "UseWindowsGroups"，指定在 Windows 群組 (例如 "Administrators" 或 "Users") 中搜尋嘗試存取資源的身分識別。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-219">The default value is "UseWindowsGroups" and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="8e4b7-220">您也可以指定 "UseAspNetRoles"，以使用在 <> 元素下設定的自訂角色提供者 `system.web` ，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-220">You can also specify "UseAspNetRoles" to use a custom role provider that is configured under the <`system.web` > element, as shown in the following code.</span></span>  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add
          name="SqlProvider"
          type="System.Web.Security.SqlMembershipProvider"
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 <span data-ttu-id="8e4b7-221">下列程式碼示範搭配 `roleProviderName` 屬性使用的 `principalPermissionMode`。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-221">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                        roleProviderName ="SqlProvider" />  
</behavior>
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a><span data-ttu-id="8e4b7-222">設定安全性稽核</span><span class="sxs-lookup"><span data-stu-id="8e4b7-222">Configuring Security Audits</span></span>  

 <span data-ttu-id="8e4b7-223">使用 [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) 指定寫入的記錄檔，以及要記錄的事件種類。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-223">Use the [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) to specify the log written to, and what types of events to log.</span></span> <span data-ttu-id="8e4b7-224">如需詳細資訊，請參閱「 [審核](auditing-security-events.md)」。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-224">For more information, see [Auditing](auditing-security-events.md).</span></span>  
  
```xml  
<behaviors>
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"
             messageAuthenticationAuditLevel="Success" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a><span data-ttu-id="8e4b7-225">安全的中繼資料交換</span><span class="sxs-lookup"><span data-stu-id="8e4b7-225">Secure Metadata Exchange</span></span>  

 <span data-ttu-id="8e4b7-226">將中繼資料匯出至用戶端對於服務和用戶端的開發人員來說是很方便的，因為如此一來便可以下載設定和用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-226">Exporting metadata to clients is convenient for service and client developers, as it enables downloads of configuration and client code.</span></span> <span data-ttu-id="8e4b7-227">若要降低將服務暴露給惡意使用者的機會，可以使用 SSL over HTTP (HTTPS) 機制來進行安全的傳輸。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-227">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="8e4b7-228">若要這麼做，您必須先將適當的 X.509 憑證，繫結至裝載服務之電腦上的特定連接埠 </span><span class="sxs-lookup"><span data-stu-id="8e4b7-228">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="8e4b7-229"> (需詳細資訊，請參閱 [使用憑證](working-with-certificates.md)。 ) 其次，將加入 [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) 至服務設定，並將 `HttpsGetEnabled` 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-229">(For more information, see [Working with Certificates](working-with-certificates.md).) Second, add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) to the service configuration and set the `HttpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="8e4b7-230">最後，將 `HttpsGetUrl` 屬性設定為服務中繼資料端點的 URL，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8e4b7-230">Finally, set the `HttpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e4b7-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e4b7-231">See also</span></span>

- [<span data-ttu-id="8e4b7-232">稽核</span><span class="sxs-lookup"><span data-stu-id="8e4b7-232">Auditing</span></span>](auditing-security-events.md)
- <span data-ttu-id="8e4b7-233">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8e4b7-233">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
