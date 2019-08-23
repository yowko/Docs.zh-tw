---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5a7dcac4edce75029bb2e0293461557f56e3c3be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933214"
---
# <a name="msmqtransportsecurity"></a><span data-ttu-id="ee79b-101">\<msmqTransportSecurity></span><span class="sxs-lookup"><span data-stu-id="ee79b-101">\<msmqTransportSecurity></span></span>
<span data-ttu-id="ee79b-102">指定自訂繫結的 MSMQ 傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ee79b-102">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
 <span data-ttu-id="ee79b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ee79b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ee79b-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ee79b-104">\<bindings></span></span>  
<span data-ttu-id="ee79b-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ee79b-105">\<customBinding></span></span>  
<span data-ttu-id="ee79b-106">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="ee79b-106">\<binding></span></span>  
<span data-ttu-id="ee79b-107">\<msmqIntegration></span><span class="sxs-lookup"><span data-stu-id="ee79b-107">\<msmqIntegration></span></span>  
<span data-ttu-id="ee79b-108">\<msmqTransportSecurity></span><span class="sxs-lookup"><span data-stu-id="ee79b-108">\<msmqTransportSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee79b-109">語法</span><span class="sxs-lookup"><span data-stu-id="ee79b-109">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee79b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ee79b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ee79b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ee79b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee79b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ee79b-112">Attributes</span></span>  
  
|<span data-ttu-id="ee79b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ee79b-113">Attribute</span></span>|<span data-ttu-id="ee79b-114">描述</span><span class="sxs-lookup"><span data-stu-id="ee79b-114">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="ee79b-115">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="ee79b-115">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="ee79b-116">如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="ee79b-116">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="ee79b-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="ee79b-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ee79b-118">無無驗證。</span><span class="sxs-lookup"><span data-stu-id="ee79b-118">-   None: No authentication.</span></span><br /><span data-ttu-id="ee79b-119">時段驗證機制會使用 Active Directory 來取得與訊息相關聯之 SID 的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="ee79b-119">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="ee79b-120">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="ee79b-120">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="ee79b-121">證書通道會從憑證存放區取得憑證。</span><span class="sxs-lookup"><span data-stu-id="ee79b-121">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="ee79b-122">預設值為 Windows。</span><span class="sxs-lookup"><span data-stu-id="ee79b-122">The default value is Windows.</span></span> <span data-ttu-id="ee79b-123">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="ee79b-123">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="ee79b-124">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="ee79b-124">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="ee79b-125">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="ee79b-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ee79b-126">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="ee79b-126">-   RC4Stream</span></span><br /><span data-ttu-id="ee79b-127">-   AES</span><span class="sxs-lookup"><span data-stu-id="ee79b-127">-   AES</span></span><br /><br /> <span data-ttu-id="ee79b-128">預設值為 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="ee79b-128">The default value is RC4Stream.</span></span> <span data-ttu-id="ee79b-129">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="ee79b-129">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="ee79b-130">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="ee79b-130">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="ee79b-131">加密可確保訊息完整性，而 EncryptAndSign 可確保訊息完整性和不可否認性，也就是訊息確實來自寄件者，且寄件者就是他本人。</span><span class="sxs-lookup"><span data-stu-id="ee79b-131">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="ee79b-132">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="ee79b-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ee79b-133">無無保護。</span><span class="sxs-lookup"><span data-stu-id="ee79b-133">-   None: No protection.</span></span><br /><span data-ttu-id="ee79b-134">簽訂訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="ee79b-134">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="ee79b-135">EncryptAndSign訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="ee79b-135">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="ee79b-136">預設值為 Sign。</span><span class="sxs-lookup"><span data-stu-id="ee79b-136">The default value is Sign.</span></span> <span data-ttu-id="ee79b-137">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="ee79b-137">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="ee79b-138">指定計算摘要做為部分簽章時使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="ee79b-138">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="ee79b-139">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="ee79b-139">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ee79b-140">-   MD5</span><span class="sxs-lookup"><span data-stu-id="ee79b-140">-   MD5</span></span><br /><span data-ttu-id="ee79b-141">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="ee79b-141">-   SHA1</span></span><br /><span data-ttu-id="ee79b-142">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="ee79b-142">-   SHA256</span></span><br /><span data-ttu-id="ee79b-143">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="ee79b-143">-   SHA512</span></span><br /><br /> <span data-ttu-id="ee79b-144">預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="ee79b-144">The default value is SHA1.</span></span> <span data-ttu-id="ee79b-145">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="ee79b-145">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="ee79b-146">由於 MD5 和 SHA1 的衝突問題, Microsoft 建議使用 SHA256 或更好的方式。</span><span class="sxs-lookup"><span data-stu-id="ee79b-146">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee79b-147">子元素</span><span class="sxs-lookup"><span data-stu-id="ee79b-147">Child Elements</span></span>  
 <span data-ttu-id="ee79b-148">無。</span><span class="sxs-lookup"><span data-stu-id="ee79b-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee79b-149">父項目</span><span class="sxs-lookup"><span data-stu-id="ee79b-149">Parent Elements</span></span>  
  
|<span data-ttu-id="ee79b-150">項目</span><span class="sxs-lookup"><span data-stu-id="ee79b-150">Element</span></span>|<span data-ttu-id="ee79b-151">說明</span><span class="sxs-lookup"><span data-stu-id="ee79b-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee79b-152">\<msmqIntegration></span><span class="sxs-lookup"><span data-stu-id="ee79b-152">\<msmqIntegration></span></span>](msmqintegration.md)|<span data-ttu-id="ee79b-153">指定與 Message Queuing (MSMQ) 寄件者或收件者互動所需的設定。</span><span class="sxs-lookup"><span data-stu-id="ee79b-153">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="ee79b-154">\<msmqTransport></span><span class="sxs-lookup"><span data-stu-id="ee79b-154">\<msmqTransport></span></span>](msmqtransport.md)|<span data-ttu-id="ee79b-155">指定 Windows Communication Foundation (WCF) 服務的佇列通訊屬性 (該服務會使用原生 MSMQ 通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="ee79b-155">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee79b-156">備註</span><span class="sxs-lookup"><span data-stu-id="ee79b-156">Remarks</span></span>  
 <span data-ttu-id="ee79b-157">如需傳輸安全性的詳細資訊, 請參閱[傳輸安全性](../../../wcf/feature-details/transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="ee79b-157">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee79b-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee79b-158">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ee79b-159">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="ee79b-159">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="ee79b-160">傳輸</span><span class="sxs-lookup"><span data-stu-id="ee79b-160">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="ee79b-161">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="ee79b-161">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="ee79b-162">繫結</span><span class="sxs-lookup"><span data-stu-id="ee79b-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ee79b-163">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="ee79b-163">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ee79b-164">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="ee79b-164">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ee79b-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ee79b-165">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="ee79b-166">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="ee79b-166">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
