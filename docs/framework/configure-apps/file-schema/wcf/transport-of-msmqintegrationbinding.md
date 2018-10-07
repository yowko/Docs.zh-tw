---
title: '&lt;msmqIntegrationBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 8f6fcb19f67caba34334b649cc2e452c9e10bf93
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845602"
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="a7065-102">&lt;msmqIntegrationBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="a7065-102">&lt;transport&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="a7065-103">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a7065-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
 <span data-ttu-id="a7065-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7065-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7065-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a7065-105">\<bindings></span></span>  
<span data-ttu-id="a7065-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="a7065-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="a7065-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a7065-107">\<binding></span></span>  
<span data-ttu-id="a7065-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="a7065-108">\<security></span></span>  
<span data-ttu-id="a7065-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="a7065-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7065-110">語法</span><span class="sxs-lookup"><span data-stu-id="a7065-110">Syntax</span></span>  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7065-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a7065-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a7065-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="a7065-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7065-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a7065-113">Attributes</span></span>  
  
|<span data-ttu-id="a7065-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a7065-114">Attribute</span></span>|<span data-ttu-id="a7065-115">描述</span><span class="sxs-lookup"><span data-stu-id="a7065-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="a7065-116">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="a7065-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="a7065-117">如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="a7065-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="a7065-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a7065-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a7065-119">-None： 沒有驗證。</span><span class="sxs-lookup"><span data-stu-id="a7065-119">-   None: No authentication.</span></span><br /><span data-ttu-id="a7065-120">-WindowsDomain： 驗證機制使用 Active Directory 為與訊息相關聯的 SID 取得 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a7065-120">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="a7065-121">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="a7065-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="a7065-122">-Certificate： 通道在從憑證存放區取得的憑證。</span><span class="sxs-lookup"><span data-stu-id="a7065-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="a7065-123">預設值為 WindowsDomain。</span><span class="sxs-lookup"><span data-stu-id="a7065-123">The default value is WindowsDomain.</span></span> <span data-ttu-id="a7065-124">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="a7065-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="a7065-125">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="a7065-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="a7065-126">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a7065-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a7065-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="a7065-127">-   RC4Stream</span></span><br /><span data-ttu-id="a7065-128">AES</span><span class="sxs-lookup"><span data-stu-id="a7065-128">-   AES</span></span><br /><br /> <span data-ttu-id="a7065-129">預設值為 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="a7065-129">The default value is RC4Stream.</span></span> <span data-ttu-id="a7065-130">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="a7065-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="a7065-131">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="a7065-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="a7065-132">加密可確保訊息完整性，而 EncryptAndSign 可確保訊息完整性和不可否認性，也就是訊息確實來自寄件者，且寄件者就是他本人。</span><span class="sxs-lookup"><span data-stu-id="a7065-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span><br /><br /> <span data-ttu-id="a7065-133">無效的值包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="a7065-133">-   Valid values include the following:</span></span><br /><span data-ttu-id="a7065-134">-None： 無保護。</span><span class="sxs-lookup"><span data-stu-id="a7065-134">-   None: No protection.</span></span><br /><span data-ttu-id="a7065-135">簽署： 簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="a7065-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a7065-136">-EncryptAndSign： 訊息會經過加密及簽署。</span><span class="sxs-lookup"><span data-stu-id="a7065-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="a7065-137">預設值為 Sign。</span><span class="sxs-lookup"><span data-stu-id="a7065-137">The default value is Sign.</span></span> <span data-ttu-id="a7065-138">此屬性的型別為 ProtectionLevel。</span><span class="sxs-lookup"><span data-stu-id="a7065-138">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="a7065-139">-指定的演算法來計算摘要做為簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="a7065-139">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="a7065-140">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a7065-140">Valid values include the following:</span></span><br /><span data-ttu-id="a7065-141">-   MD5</span><span class="sxs-lookup"><span data-stu-id="a7065-141">-   MD5</span></span><br /><span data-ttu-id="a7065-142">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="a7065-142">-   SHA1</span></span><br /><span data-ttu-id="a7065-143">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="a7065-143">-   SHA256</span></span><br /><span data-ttu-id="a7065-144">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="a7065-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="a7065-145">預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="a7065-145">The default value is SHA1.</span></span> <span data-ttu-id="a7065-146">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="a7065-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7065-147">子元素</span><span class="sxs-lookup"><span data-stu-id="a7065-147">Child Elements</span></span>  
 <span data-ttu-id="a7065-148">無</span><span class="sxs-lookup"><span data-stu-id="a7065-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7065-149">父項目</span><span class="sxs-lookup"><span data-stu-id="a7065-149">Parent Elements</span></span>  
  
|<span data-ttu-id="a7065-150">項目</span><span class="sxs-lookup"><span data-stu-id="a7065-150">Element</span></span>|<span data-ttu-id="a7065-151">描述</span><span class="sxs-lookup"><span data-stu-id="a7065-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7065-152">\<security></span><span class="sxs-lookup"><span data-stu-id="a7065-152">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="a7065-153">定義 MSMQ 繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a7065-153">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7065-154">備註</span><span class="sxs-lookup"><span data-stu-id="a7065-154">Remarks</span></span>  
 <span data-ttu-id="a7065-155">這個項目會封裝訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a7065-155">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="a7065-156">這些設定同時適用於訊息佇列整合和已佇列之傳輸。</span><span class="sxs-lookup"><span data-stu-id="a7065-156">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="a7065-157">它還可讓您設定驗證模式、加密演算法、安全雜湊演算法和保護層級。</span><span class="sxs-lookup"><span data-stu-id="a7065-157">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7065-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7065-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="a7065-159">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a7065-159">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a7065-160">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a7065-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a7065-161">繫結</span><span class="sxs-lookup"><span data-stu-id="a7065-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a7065-162">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a7065-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a7065-163">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="a7065-163">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="a7065-164">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a7065-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
