---
title: "&lt;messageSenderAuthentication&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20d452a6aa9047032d989d62d6c1121d7edc5ee3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagesenderauthenticationgt-element"></a><span data-ttu-id="1ac2f-102">&lt;messageSenderAuthentication&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="1ac2f-102">&lt;messageSenderAuthentication&gt; element</span></span>
<span data-ttu-id="1ac2f-103">指定對等訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="1ac2f-104">如需端對端程式設計的詳細資訊，請參閱[對等網路](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="1ac2f-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1ac2f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ac2f-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="1ac2f-106">\<behaviors></span></span>  
<span data-ttu-id="1ac2f-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1ac2f-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="1ac2f-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1ac2f-108">\<behavior></span></span>  
<span data-ttu-id="1ac2f-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="1ac2f-109">\<clientCredentials></span></span>  
<span data-ttu-id="1ac2f-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="1ac2f-110">\<peer></span></span>  
<span data-ttu-id="1ac2f-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="1ac2f-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac2f-112">語法</span><span class="sxs-lookup"><span data-stu-id="1ac2f-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ac2f-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1ac2f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1ac2f-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="1ac2f-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ac2f-115">屬性</span><span class="sxs-lookup"><span data-stu-id="1ac2f-115">Attributes</span></span>  
  
|<span data-ttu-id="1ac2f-116">屬性</span><span class="sxs-lookup"><span data-stu-id="1ac2f-116">Attribute</span></span>|<span data-ttu-id="1ac2f-117">描述</span><span class="sxs-lookup"><span data-stu-id="1ac2f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ac2f-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="1ac2f-118">customCertificateValidatorType</span></span>|<span data-ttu-id="1ac2f-119">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="1ac2f-120">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="1ac2f-121">certifcateValidationMode</span><span class="sxs-lookup"><span data-stu-id="1ac2f-121">certifcateValidationMode</span></span>|<span data-ttu-id="1ac2f-122">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="1ac2f-123">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|<span data-ttu-id="1ac2f-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="1ac2f-124">revocationMode</span></span>|<span data-ttu-id="1ac2f-125">用於檢查撤銷憑證清單 (CRL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|<span data-ttu-id="1ac2f-126">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="1ac2f-126">trustedStoreLocation</span></span>|<span data-ttu-id="1ac2f-127">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-127">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="1ac2f-128">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-128">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="1ac2f-129">針對執行驗證**受信任的人**將儲存在指定的存放區位置。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-129">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="1ac2f-130">customCertificateValidatorType 屬性</span><span class="sxs-lookup"><span data-stu-id="1ac2f-130">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="1ac2f-131">值</span><span class="sxs-lookup"><span data-stu-id="1ac2f-131">Value</span></span>|<span data-ttu-id="1ac2f-132">描述</span><span class="sxs-lookup"><span data-stu-id="1ac2f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ac2f-133">String</span><span class="sxs-lookup"><span data-stu-id="1ac2f-133">String</span></span>|<span data-ttu-id="1ac2f-134">選擇項。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-134">Optional.</span></span> <span data-ttu-id="1ac2f-135">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-135">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="1ac2f-136">至少需要命名空間和型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-136">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="1ac2f-137">選擇性的資訊包括：組件名稱、版本號碼、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-137">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="1ac2f-138">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="1ac2f-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="1ac2f-139">值</span><span class="sxs-lookup"><span data-stu-id="1ac2f-139">Value</span></span>|<span data-ttu-id="1ac2f-140">描述</span><span class="sxs-lookup"><span data-stu-id="1ac2f-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ac2f-141">列舉</span><span class="sxs-lookup"><span data-stu-id="1ac2f-141">Enumeration</span></span>|<span data-ttu-id="1ac2f-142">選擇項。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-142">Optional.</span></span> <span data-ttu-id="1ac2f-143">下列其中一個值：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-143">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="1ac2f-144">預設為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-144">The default is `ChainTrust`.</span></span> <span data-ttu-id="1ac2f-145">預設值為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="1ac2f-146">如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="1ac2f-147">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="1ac2f-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="1ac2f-148">值</span><span class="sxs-lookup"><span data-stu-id="1ac2f-148">Value</span></span>|<span data-ttu-id="1ac2f-149">描述</span><span class="sxs-lookup"><span data-stu-id="1ac2f-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ac2f-150">列舉</span><span class="sxs-lookup"><span data-stu-id="1ac2f-150">Enumeration</span></span>|<span data-ttu-id="1ac2f-151">下列其中一個值：`NoCheck`、`Online`、`Offline`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="1ac2f-152">預設值為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="1ac2f-153">如需詳細資訊，請參閱[使用憑證](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="1ac2f-154">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="1ac2f-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="1ac2f-155">值</span><span class="sxs-lookup"><span data-stu-id="1ac2f-155">Value</span></span>|<span data-ttu-id="1ac2f-156">描述</span><span class="sxs-lookup"><span data-stu-id="1ac2f-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ac2f-157">列舉</span><span class="sxs-lookup"><span data-stu-id="1ac2f-157">Enumeration</span></span>|<span data-ttu-id="1ac2f-158">下列其中一個值：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="1ac2f-159">預設為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="1ac2f-160">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="1ac2f-161">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="1ac2f-162">預設值為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-162">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ac2f-163">子元素</span><span class="sxs-lookup"><span data-stu-id="1ac2f-163">Child Elements</span></span>  
 <span data-ttu-id="1ac2f-164">無。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ac2f-165">父項目</span><span class="sxs-lookup"><span data-stu-id="1ac2f-165">Parent Elements</span></span>  
  
|<span data-ttu-id="1ac2f-166">項目</span><span class="sxs-lookup"><span data-stu-id="1ac2f-166">Element</span></span>|<span data-ttu-id="1ac2f-167">描述</span><span class="sxs-lookup"><span data-stu-id="1ac2f-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ac2f-168">\<peer></span><span class="sxs-lookup"><span data-stu-id="1ac2f-168">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="1ac2f-169">指定向對等服務驗證用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ac2f-170">備註</span><span class="sxs-lookup"><span data-stu-id="1ac2f-170">Remarks</span></span>  
 <span data-ttu-id="1ac2f-171">如果已選取訊息驗證，則必須設定這個項目。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-171">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="1ac2f-172">輸出通道的每個訊息會使用簽章所提供的憑證[\<憑證 >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-172">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="1ac2f-173">所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-173">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="1ac2f-174">驗證器可接受或拒絕認證。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-174">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ac2f-175">範例</span><span class="sxs-lookup"><span data-stu-id="1ac2f-175">Example</span></span>  
 <span data-ttu-id="1ac2f-176">下列程式碼會將訊息寄件者驗證模式設定為 `PeerOrChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="1ac2f-176">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ac2f-177">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ac2f-177">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="1ac2f-178">使用憑證</span><span class="sxs-lookup"><span data-stu-id="1ac2f-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="1ac2f-179">對等網路</span><span class="sxs-lookup"><span data-stu-id="1ac2f-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="1ac2f-180">對等通道訊息驗證</span><span class="sxs-lookup"><span data-stu-id="1ac2f-180">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="1ac2f-181">對等通道自訂驗證</span><span class="sxs-lookup"><span data-stu-id="1ac2f-181">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="1ac2f-182">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="1ac2f-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
