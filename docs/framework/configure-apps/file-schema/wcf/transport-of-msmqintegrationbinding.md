---
title: <transport> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: c266d751ff3e89f653763ed83c78041d89e22517
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290143"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="a4325-102">\<傳輸 > 的\<msmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="a4325-102">\<transport> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="a4325-103">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a4325-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
 <span data-ttu-id="a4325-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a4325-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a4325-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a4325-105">\<bindings></span></span>  
<span data-ttu-id="a4325-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="a4325-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="a4325-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="a4325-107">\<binding></span></span>  
<span data-ttu-id="a4325-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="a4325-108">\<security></span></span>  
<span data-ttu-id="a4325-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="a4325-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4325-110">語法</span><span class="sxs-lookup"><span data-stu-id="a4325-110">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4325-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a4325-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a4325-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="a4325-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4325-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a4325-113">Attributes</span></span>  
  
|<span data-ttu-id="a4325-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a4325-114">Attribute</span></span>|<span data-ttu-id="a4325-115">描述</span><span class="sxs-lookup"><span data-stu-id="a4325-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="a4325-116">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="a4325-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="a4325-117">如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="a4325-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="a4325-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a4325-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a4325-119">-None:沒有驗證。</span><span class="sxs-lookup"><span data-stu-id="a4325-119">-   None: No authentication.</span></span><br /><span data-ttu-id="a4325-120">-   WindowsDomain:驗證機制使用 Active Directory 與訊息相關聯的 SID 取得 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a4325-120">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="a4325-121">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="a4325-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="a4325-122">憑證：通道會從憑證存放區取得的憑證。</span><span class="sxs-lookup"><span data-stu-id="a4325-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="a4325-123">預設值為 WindowsDomain。</span><span class="sxs-lookup"><span data-stu-id="a4325-123">The default value is WindowsDomain.</span></span> <span data-ttu-id="a4325-124">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="a4325-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="a4325-125">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="a4325-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="a4325-126">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a4325-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a4325-127">-   RC4Stream</span><span class="sxs-lookup"><span data-stu-id="a4325-127">-   RC4Stream</span></span><br /><span data-ttu-id="a4325-128">-   AES</span><span class="sxs-lookup"><span data-stu-id="a4325-128">-   AES</span></span><br /><br /> <span data-ttu-id="a4325-129">預設值為 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="a4325-129">The default value is RC4Stream.</span></span> <span data-ttu-id="a4325-130">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="a4325-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="a4325-131">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="a4325-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="a4325-132">加密可確保訊息完整性，而 EncryptAndSign 可確保訊息完整性和不可否認性，也就是訊息確實來自寄件者，且寄件者就是他本人。</span><span class="sxs-lookup"><span data-stu-id="a4325-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span><br /><br /> <span data-ttu-id="a4325-133">無效的值包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="a4325-133">-   Valid values include the following:</span></span><br /><span data-ttu-id="a4325-134">-None:無保護。</span><span class="sxs-lookup"><span data-stu-id="a4325-134">-   None: No protection.</span></span><br /><span data-ttu-id="a4325-135">簽署：訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="a4325-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a4325-136">-EncryptAndSign:訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="a4325-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="a4325-137">預設值為 Sign。</span><span class="sxs-lookup"><span data-stu-id="a4325-137">The default value is Sign.</span></span> <span data-ttu-id="a4325-138">此屬性的型別為 ProtectionLevel。</span><span class="sxs-lookup"><span data-stu-id="a4325-138">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="a4325-139">-指定的演算法來計算摘要做為簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="a4325-139">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="a4325-140">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a4325-140">Valid values include the following:</span></span><br /><span data-ttu-id="a4325-141">-   MD5</span><span class="sxs-lookup"><span data-stu-id="a4325-141">-   MD5</span></span><br /><span data-ttu-id="a4325-142">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="a4325-142">-   SHA1</span></span><br /><span data-ttu-id="a4325-143">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="a4325-143">-   SHA256</span></span><br /><span data-ttu-id="a4325-144">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="a4325-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="a4325-145">預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="a4325-145">The default value is SHA1.</span></span> <span data-ttu-id="a4325-146">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="a4325-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4325-147">子元素</span><span class="sxs-lookup"><span data-stu-id="a4325-147">Child Elements</span></span>  
 <span data-ttu-id="a4325-148">無</span><span class="sxs-lookup"><span data-stu-id="a4325-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4325-149">父項目</span><span class="sxs-lookup"><span data-stu-id="a4325-149">Parent Elements</span></span>  
  
|<span data-ttu-id="a4325-150">項目</span><span class="sxs-lookup"><span data-stu-id="a4325-150">Element</span></span>|<span data-ttu-id="a4325-151">描述</span><span class="sxs-lookup"><span data-stu-id="a4325-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4325-152">\<security></span><span class="sxs-lookup"><span data-stu-id="a4325-152">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="a4325-153">定義 MSMQ 繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a4325-153">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4325-154">備註</span><span class="sxs-lookup"><span data-stu-id="a4325-154">Remarks</span></span>  
 <span data-ttu-id="a4325-155">這個項目會封裝訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a4325-155">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="a4325-156">這些設定同時適用於訊息佇列整合和已佇列之傳輸。</span><span class="sxs-lookup"><span data-stu-id="a4325-156">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="a4325-157">它還可讓您設定驗證模式、加密演算法、安全雜湊演算法和保護層級。</span><span class="sxs-lookup"><span data-stu-id="a4325-157">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4325-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4325-158">See also</span></span>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="a4325-159">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a4325-159">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a4325-160">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a4325-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a4325-161">繫結</span><span class="sxs-lookup"><span data-stu-id="a4325-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a4325-162">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a4325-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a4325-163">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="a4325-163">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a4325-164">\<binding></span><span class="sxs-lookup"><span data-stu-id="a4325-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
