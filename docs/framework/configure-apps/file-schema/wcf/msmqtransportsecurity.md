---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153005"
---
# <a name="msmqtransportsecurity"></a><span data-ttu-id="489b5-101">\<msmq運輸安全></span><span class="sxs-lookup"><span data-stu-id="489b5-101">\<msmqTransportSecurity></span></span>
<span data-ttu-id="489b5-102">指定自訂繫結的 MSMQ 傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="489b5-102">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
<span data-ttu-id="489b5-103">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="489b5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="489b5-104">&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="489b5-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="489b5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<綁定>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="489b5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="489b5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<自訂綁定>**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="489b5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="489b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<綁定>**</span><span class="sxs-lookup"><span data-stu-id="489b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="489b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmq集成>**](msmqintegration.md)</span><span class="sxs-lookup"><span data-stu-id="489b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)</span></span>\
<span data-ttu-id="489b5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmq傳輸安全>**</span><span class="sxs-lookup"><span data-stu-id="489b5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="489b5-110">語法</span><span class="sxs-lookup"><span data-stu-id="489b5-110">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="489b5-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="489b5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="489b5-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="489b5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="489b5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="489b5-113">Attributes</span></span>  
  
|<span data-ttu-id="489b5-114">屬性</span><span class="sxs-lookup"><span data-stu-id="489b5-114">Attribute</span></span>|<span data-ttu-id="489b5-115">描述</span><span class="sxs-lookup"><span data-stu-id="489b5-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="489b5-116">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="489b5-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="489b5-117">如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="489b5-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="489b5-118">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="489b5-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="489b5-119">- 無：無身份驗證。</span><span class="sxs-lookup"><span data-stu-id="489b5-119">-   None: No authentication.</span></span><br /><span data-ttu-id="489b5-120">- Windows：身份驗證機制使用 Active Directory 獲取與消息關聯的 SID 的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="489b5-120">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="489b5-121">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="489b5-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="489b5-122">- 證書：通道從憑證存放區獲取證書。</span><span class="sxs-lookup"><span data-stu-id="489b5-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="489b5-123">預設值為 Windows。</span><span class="sxs-lookup"><span data-stu-id="489b5-123">The default value is Windows.</span></span> <span data-ttu-id="489b5-124">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="489b5-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="489b5-125">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="489b5-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="489b5-126">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="489b5-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="489b5-127">- RC4流</span><span class="sxs-lookup"><span data-stu-id="489b5-127">-   RC4Stream</span></span><br /><span data-ttu-id="489b5-128">- AES</span><span class="sxs-lookup"><span data-stu-id="489b5-128">-   AES</span></span><br /><br /> <span data-ttu-id="489b5-129">預設值為 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="489b5-129">The default value is RC4Stream.</span></span> <span data-ttu-id="489b5-130">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="489b5-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="489b5-131">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="489b5-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="489b5-132">加密可確保郵件完整性，而加密和簽名可確保郵件的完整性和非否認性;也就是說，郵件確實來自寄件者，寄件者是他們說的。</span><span class="sxs-lookup"><span data-stu-id="489b5-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="489b5-133">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="489b5-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="489b5-134">-無：沒有保護</span><span class="sxs-lookup"><span data-stu-id="489b5-134">-   None: No protection.</span></span><br /><span data-ttu-id="489b5-135">- 簽名：消息已簽名。</span><span class="sxs-lookup"><span data-stu-id="489b5-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="489b5-136">- 加密和簽名：郵件經過加密並簽名。</span><span class="sxs-lookup"><span data-stu-id="489b5-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="489b5-137">預設值為 Sign。</span><span class="sxs-lookup"><span data-stu-id="489b5-137">The default value is Sign.</span></span> <span data-ttu-id="489b5-138">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="489b5-138">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="489b5-139">指定計算摘要做為部分簽章時使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="489b5-139">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="489b5-140">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="489b5-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="489b5-141">- MD5</span><span class="sxs-lookup"><span data-stu-id="489b5-141">-   MD5</span></span><br /><span data-ttu-id="489b5-142">- SHA1</span><span class="sxs-lookup"><span data-stu-id="489b5-142">-   SHA1</span></span><br /><span data-ttu-id="489b5-143">- SHA256</span><span class="sxs-lookup"><span data-stu-id="489b5-143">-   SHA256</span></span><br /><span data-ttu-id="489b5-144">- SHA512</span><span class="sxs-lookup"><span data-stu-id="489b5-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="489b5-145">預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="489b5-145">The default value is SHA1.</span></span> <span data-ttu-id="489b5-146">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="489b5-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="489b5-147">由於與 MD5 和 SHA1 的碰撞問題，Microsoft 推薦 SHA256 或更高。</span><span class="sxs-lookup"><span data-stu-id="489b5-147">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="489b5-148">子元素</span><span class="sxs-lookup"><span data-stu-id="489b5-148">Child Elements</span></span>  
 <span data-ttu-id="489b5-149">無。</span><span class="sxs-lookup"><span data-stu-id="489b5-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="489b5-150">父項目</span><span class="sxs-lookup"><span data-stu-id="489b5-150">Parent Elements</span></span>  
  
|<span data-ttu-id="489b5-151">元素</span><span class="sxs-lookup"><span data-stu-id="489b5-151">Element</span></span>|<span data-ttu-id="489b5-152">描述</span><span class="sxs-lookup"><span data-stu-id="489b5-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="489b5-153">\<msmq集成></span><span class="sxs-lookup"><span data-stu-id="489b5-153">\<msmqIntegration></span></span>](msmqintegration.md)|<span data-ttu-id="489b5-154">指定與 Message Queuing (MSMQ) 寄件者或收件者互動所需的設定。</span><span class="sxs-lookup"><span data-stu-id="489b5-154">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="489b5-155">\<msmq 傳輸></span><span class="sxs-lookup"><span data-stu-id="489b5-155">\<msmqTransport></span></span>](msmqtransport.md)|<span data-ttu-id="489b5-156">指定 Windows Communication Foundation (WCF) 服務的佇列通訊屬性 (該服務會使用原生 MSMQ 通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="489b5-156">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="489b5-157">備註</span><span class="sxs-lookup"><span data-stu-id="489b5-157">Remarks</span></span>  
 <span data-ttu-id="489b5-158">有關運輸安全的詳細資訊，請參閱[運輸安全](../../../wcf/feature-details/transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="489b5-158">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="489b5-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="489b5-159">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="489b5-160">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="489b5-160">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="489b5-161">傳輸</span><span class="sxs-lookup"><span data-stu-id="489b5-161">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="489b5-162">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="489b5-162">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="489b5-163">綁定</span><span class="sxs-lookup"><span data-stu-id="489b5-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="489b5-164">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="489b5-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="489b5-165">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="489b5-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="489b5-166">\<自訂綁定></span><span class="sxs-lookup"><span data-stu-id="489b5-166">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="489b5-167">運輸安全</span><span class="sxs-lookup"><span data-stu-id="489b5-167">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
