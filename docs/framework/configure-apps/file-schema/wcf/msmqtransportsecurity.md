---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: fece74e76f879eff51f154eab8c8edea2c27119e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180124"
---
# <a name="msmqtransportsecurity"></a><span data-ttu-id="df29c-101">\<msmqTransportSecurity></span><span class="sxs-lookup"><span data-stu-id="df29c-101">\<msmqTransportSecurity></span></span>
<span data-ttu-id="df29c-102">指定自訂繫結的 MSMQ 傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="df29c-102">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
 <span data-ttu-id="df29c-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="df29c-103">\<system.serviceModel></span></span>  
<span data-ttu-id="df29c-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="df29c-104">\<bindings></span></span>  
<span data-ttu-id="df29c-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="df29c-105">\<customBinding></span></span>  
<span data-ttu-id="df29c-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="df29c-106">\<binding></span></span>  
<span data-ttu-id="df29c-107">\<msmqIntegration></span><span class="sxs-lookup"><span data-stu-id="df29c-107">\<msmqIntegration></span></span>  
<span data-ttu-id="df29c-108">\<msmqTransportSecurity></span><span class="sxs-lookup"><span data-stu-id="df29c-108">\<msmqTransportSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df29c-109">語法</span><span class="sxs-lookup"><span data-stu-id="df29c-109">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df29c-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="df29c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="df29c-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="df29c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df29c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="df29c-112">Attributes</span></span>  
  
|<span data-ttu-id="df29c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="df29c-113">Attribute</span></span>|<span data-ttu-id="df29c-114">描述</span><span class="sxs-lookup"><span data-stu-id="df29c-114">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="df29c-115">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="df29c-115">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="df29c-116">如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="df29c-116">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="df29c-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="df29c-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="df29c-118">-None:沒有驗證。</span><span class="sxs-lookup"><span data-stu-id="df29c-118">-   None: No authentication.</span></span><br /><span data-ttu-id="df29c-119">-Windows:驗證機制使用 Active Directory 與訊息相關聯的 SID 取得 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="df29c-119">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="df29c-120">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="df29c-120">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="df29c-121">憑證：通道會從憑證存放區取得的憑證。</span><span class="sxs-lookup"><span data-stu-id="df29c-121">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="df29c-122">預設值為 Windows。</span><span class="sxs-lookup"><span data-stu-id="df29c-122">The default value is Windows.</span></span> <span data-ttu-id="df29c-123">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="df29c-123">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="df29c-124">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="df29c-124">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="df29c-125">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="df29c-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="df29c-126">-   RC4Stream</span><span class="sxs-lookup"><span data-stu-id="df29c-126">-   RC4Stream</span></span><br /><span data-ttu-id="df29c-127">-   AES</span><span class="sxs-lookup"><span data-stu-id="df29c-127">-   AES</span></span><br /><br /> <span data-ttu-id="df29c-128">預設值為 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="df29c-128">The default value is RC4Stream.</span></span> <span data-ttu-id="df29c-129">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="df29c-129">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="df29c-130">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="df29c-130">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="df29c-131">加密可確保訊息完整性，而 EncryptAndSign 可確保訊息完整性和不可否認性，也就是訊息確實來自寄件者，且寄件者就是他本人。</span><span class="sxs-lookup"><span data-stu-id="df29c-131">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="df29c-132">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="df29c-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="df29c-133">-None:無保護。</span><span class="sxs-lookup"><span data-stu-id="df29c-133">-   None: No protection.</span></span><br /><span data-ttu-id="df29c-134">簽署：訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="df29c-134">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="df29c-135">-EncryptAndSign:訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="df29c-135">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="df29c-136">預設值為 Sign。</span><span class="sxs-lookup"><span data-stu-id="df29c-136">The default value is Sign.</span></span> <span data-ttu-id="df29c-137">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="df29c-137">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="df29c-138">指定計算摘要做為部分簽章時使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="df29c-138">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="df29c-139">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="df29c-139">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="df29c-140">-   MD5</span><span class="sxs-lookup"><span data-stu-id="df29c-140">-   MD5</span></span><br /><span data-ttu-id="df29c-141">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="df29c-141">-   SHA1</span></span><br /><span data-ttu-id="df29c-142">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="df29c-142">-   SHA256</span></span><br /><span data-ttu-id="df29c-143">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="df29c-143">-   SHA512</span></span><br /><br /> <span data-ttu-id="df29c-144">預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="df29c-144">The default value is SHA1.</span></span> <span data-ttu-id="df29c-145">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="df29c-145">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="df29c-146">因為使用 MD5 和 SHA1 的衝突問題，Microsoft 建議 SHA256 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="df29c-146">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df29c-147">子元素</span><span class="sxs-lookup"><span data-stu-id="df29c-147">Child Elements</span></span>  
 <span data-ttu-id="df29c-148">無。</span><span class="sxs-lookup"><span data-stu-id="df29c-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df29c-149">父項目</span><span class="sxs-lookup"><span data-stu-id="df29c-149">Parent Elements</span></span>  
  
|<span data-ttu-id="df29c-150">項目</span><span class="sxs-lookup"><span data-stu-id="df29c-150">Element</span></span>|<span data-ttu-id="df29c-151">描述</span><span class="sxs-lookup"><span data-stu-id="df29c-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df29c-152">\<msmqIntegration></span><span class="sxs-lookup"><span data-stu-id="df29c-152">\<msmqIntegration></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|<span data-ttu-id="df29c-153">指定與 Message Queuing (MSMQ) 寄件者或收件者互動所需的設定。</span><span class="sxs-lookup"><span data-stu-id="df29c-153">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="df29c-154">\<msmqTransport></span><span class="sxs-lookup"><span data-stu-id="df29c-154">\<msmqTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|<span data-ttu-id="df29c-155">指定 Windows Communication Foundation (WCF) 服務的佇列通訊屬性 (該服務會使用原生 MSMQ 通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="df29c-155">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df29c-156">備註</span><span class="sxs-lookup"><span data-stu-id="df29c-156">Remarks</span></span>  
 <span data-ttu-id="df29c-157">如需有關傳輸安全性的詳細資訊，請參閱[傳輸安全性](../../../../../docs/framework/wcf/feature-details/transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="df29c-157">For more information on transport security, see [Transport Security](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df29c-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df29c-158">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="df29c-159">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="df29c-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="df29c-160">傳輸</span><span class="sxs-lookup"><span data-stu-id="df29c-160">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="df29c-161">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="df29c-161">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="df29c-162">繫結</span><span class="sxs-lookup"><span data-stu-id="df29c-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="df29c-163">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="df29c-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="df29c-164">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="df29c-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="df29c-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="df29c-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="df29c-166">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="df29c-166">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
