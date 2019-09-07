---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: dc7371d694925d3ac5aa49d7d1269df323358f90
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397804"
---
# <a name="msmqtransportsecurity"></a><span data-ttu-id="bc7f3-101">\<msmqTransportSecurity></span><span class="sxs-lookup"><span data-stu-id="bc7f3-101">\<msmqTransportSecurity></span></span>
<span data-ttu-id="bc7f3-102">指定自訂繫結的 MSMQ 傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-102">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
<span data-ttu-id="bc7f3-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc7f3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc7f3-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bc7f3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bc7f3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bc7f3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bc7f3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bc7f3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="bc7f3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="bc7f3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="bc7f3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Msmqintegration 繫結項目 >** ](msmqintegration.md)</span><span class="sxs-lookup"><span data-stu-id="bc7f3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)</span></span>\
<span data-ttu-id="bc7f3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Msmqtransportsecurity.msmqauthenticationmode >**</span><span class="sxs-lookup"><span data-stu-id="bc7f3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc7f3-110">語法</span><span class="sxs-lookup"><span data-stu-id="bc7f3-110">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc7f3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc7f3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bc7f3-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc7f3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="bc7f3-113">Attributes</span></span>  
  
|<span data-ttu-id="bc7f3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="bc7f3-114">Attribute</span></span>|<span data-ttu-id="bc7f3-115">描述</span><span class="sxs-lookup"><span data-stu-id="bc7f3-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="bc7f3-116">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="bc7f3-117">如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="bc7f3-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="bc7f3-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bc7f3-119">無無驗證。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-119">-   None: No authentication.</span></span><br /><span data-ttu-id="bc7f3-120">時段驗證機制會使用 Active Directory 來取得與訊息相關聯之 SID 的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-120">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="bc7f3-121">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="bc7f3-122">證書通道會從憑證存放區取得憑證。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="bc7f3-123">預設值為 Windows。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-123">The default value is Windows.</span></span> <span data-ttu-id="bc7f3-124">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="bc7f3-125">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="bc7f3-126">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="bc7f3-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bc7f3-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="bc7f3-127">-   RC4Stream</span></span><br /><span data-ttu-id="bc7f3-128">-   AES</span><span class="sxs-lookup"><span data-stu-id="bc7f3-128">-   AES</span></span><br /><br /> <span data-ttu-id="bc7f3-129">預設值為 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-129">The default value is RC4Stream.</span></span> <span data-ttu-id="bc7f3-130">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="bc7f3-131">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="bc7f3-132">加密可確保訊息完整性，而 EncryptAndSign 可確保訊息完整性和不可否認性，也就是訊息確實來自寄件者，且寄件者就是他本人。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="bc7f3-133">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="bc7f3-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bc7f3-134">無無保護。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-134">-   None: No protection.</span></span><br /><span data-ttu-id="bc7f3-135">簽訂訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="bc7f3-136">EncryptAndSign訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="bc7f3-137">預設值為 Sign。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-137">The default value is Sign.</span></span> <span data-ttu-id="bc7f3-138">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-138">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="bc7f3-139">指定計算摘要做為部分簽章時使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-139">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="bc7f3-140">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="bc7f3-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bc7f3-141">-   MD5</span><span class="sxs-lookup"><span data-stu-id="bc7f3-141">-   MD5</span></span><br /><span data-ttu-id="bc7f3-142">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="bc7f3-142">-   SHA1</span></span><br /><span data-ttu-id="bc7f3-143">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="bc7f3-143">-   SHA256</span></span><br /><span data-ttu-id="bc7f3-144">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="bc7f3-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="bc7f3-145">預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-145">The default value is SHA1.</span></span> <span data-ttu-id="bc7f3-146">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="bc7f3-147">由於 MD5 和 SHA1 的衝突問題，Microsoft 建議使用 SHA256 或更好的方式。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-147">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc7f3-148">子元素</span><span class="sxs-lookup"><span data-stu-id="bc7f3-148">Child Elements</span></span>  
 <span data-ttu-id="bc7f3-149">無。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc7f3-150">父項目</span><span class="sxs-lookup"><span data-stu-id="bc7f3-150">Parent Elements</span></span>  
  
|<span data-ttu-id="bc7f3-151">項目</span><span class="sxs-lookup"><span data-stu-id="bc7f3-151">Element</span></span>|<span data-ttu-id="bc7f3-152">描述</span><span class="sxs-lookup"><span data-stu-id="bc7f3-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc7f3-153">\<msmqIntegration></span><span class="sxs-lookup"><span data-stu-id="bc7f3-153">\<msmqIntegration></span></span>](msmqintegration.md)|<span data-ttu-id="bc7f3-154">指定與 Message Queuing (MSMQ) 寄件者或收件者互動所需的設定。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-154">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="bc7f3-155">\<msmqTransport></span><span class="sxs-lookup"><span data-stu-id="bc7f3-155">\<msmqTransport></span></span>](msmqtransport.md)|<span data-ttu-id="bc7f3-156">指定 Windows Communication Foundation (WCF) 服務的佇列通訊屬性 (該服務會使用原生 MSMQ 通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-156">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc7f3-157">備註</span><span class="sxs-lookup"><span data-stu-id="bc7f3-157">Remarks</span></span>  
 <span data-ttu-id="bc7f3-158">如需傳輸安全性的詳細資訊，請參閱[傳輸安全性](../../../wcf/feature-details/transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="bc7f3-158">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc7f3-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc7f3-159">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bc7f3-160">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="bc7f3-160">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="bc7f3-161">傳輸</span><span class="sxs-lookup"><span data-stu-id="bc7f3-161">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="bc7f3-162">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="bc7f3-162">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="bc7f3-163">繫結</span><span class="sxs-lookup"><span data-stu-id="bc7f3-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bc7f3-164">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="bc7f3-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bc7f3-165">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="bc7f3-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bc7f3-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bc7f3-166">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="bc7f3-167">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="bc7f3-167">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
