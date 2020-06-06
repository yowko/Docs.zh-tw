---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153005"
---
# \<msmqTransportSecurity>
<span data-ttu-id="25632-101">指定自訂繫結的 MSMQ 傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="25632-101">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="25632-102">語法</span><span class="sxs-lookup"><span data-stu-id="25632-102">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25632-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="25632-103">Attributes and Elements</span></span>  
 <span data-ttu-id="25632-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="25632-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25632-105">屬性</span><span class="sxs-lookup"><span data-stu-id="25632-105">Attributes</span></span>  
  
|<span data-ttu-id="25632-106">屬性</span><span class="sxs-lookup"><span data-stu-id="25632-106">Attribute</span></span>|<span data-ttu-id="25632-107">描述</span><span class="sxs-lookup"><span data-stu-id="25632-107">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="25632-108">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="25632-108">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="25632-109">如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="25632-109">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="25632-110">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="25632-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="25632-111">-None：不進行驗證。</span><span class="sxs-lookup"><span data-stu-id="25632-111">-   None: No authentication.</span></span><br /><span data-ttu-id="25632-112">-Windows：驗證機制會使用 Active Directory 來取得與訊息相關聯之 SID 的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="25632-112">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="25632-113">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="25632-113">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="25632-114">-Certificate：通道會從憑證存放區取得憑證。</span><span class="sxs-lookup"><span data-stu-id="25632-114">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="25632-115">預設值為 Windows。</span><span class="sxs-lookup"><span data-stu-id="25632-115">The default value is Windows.</span></span> <span data-ttu-id="25632-116">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="25632-116">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="25632-117">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="25632-117">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="25632-118">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="25632-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="25632-119">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="25632-119">-   RC4Stream</span></span><br /><span data-ttu-id="25632-120">-AES</span><span class="sxs-lookup"><span data-stu-id="25632-120">-   AES</span></span><br /><br /> <span data-ttu-id="25632-121">預設值為 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="25632-121">The default value is RC4Stream.</span></span> <span data-ttu-id="25632-122">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="25632-122">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="25632-123">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="25632-123">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="25632-124">加密可確保訊息完整性，而 EncryptAndSign 可確保訊息完整性和不可否認性;也就是說，訊息確實來自寄件者，而寄件者則是他們說的。</span><span class="sxs-lookup"><span data-stu-id="25632-124">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="25632-125">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="25632-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="25632-126">-None：沒有保護。</span><span class="sxs-lookup"><span data-stu-id="25632-126">-   None: No protection.</span></span><br /><span data-ttu-id="25632-127">-Sign：訊息已簽署。</span><span class="sxs-lookup"><span data-stu-id="25632-127">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="25632-128">-EncryptAndSign：訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="25632-128">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="25632-129">預設值為 Sign。</span><span class="sxs-lookup"><span data-stu-id="25632-129">The default value is Sign.</span></span> <span data-ttu-id="25632-130">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="25632-130">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="25632-131">指定計算摘要做為部分簽章時使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="25632-131">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="25632-132">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="25632-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="25632-133">-MD5</span><span class="sxs-lookup"><span data-stu-id="25632-133">-   MD5</span></span><br /><span data-ttu-id="25632-134">-SHA1</span><span class="sxs-lookup"><span data-stu-id="25632-134">-   SHA1</span></span><br /><span data-ttu-id="25632-135">-SHA256</span><span class="sxs-lookup"><span data-stu-id="25632-135">-   SHA256</span></span><br /><span data-ttu-id="25632-136">-SHA512</span><span class="sxs-lookup"><span data-stu-id="25632-136">-   SHA512</span></span><br /><br /> <span data-ttu-id="25632-137">預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="25632-137">The default value is SHA1.</span></span> <span data-ttu-id="25632-138">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="25632-138">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="25632-139">由於 MD5 和 SHA1 的衝突問題，Microsoft 建議使用 SHA256 或更好的方式。</span><span class="sxs-lookup"><span data-stu-id="25632-139">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25632-140">子元素</span><span class="sxs-lookup"><span data-stu-id="25632-140">Child Elements</span></span>  
 <span data-ttu-id="25632-141">無。</span><span class="sxs-lookup"><span data-stu-id="25632-141">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25632-142">父項目</span><span class="sxs-lookup"><span data-stu-id="25632-142">Parent Elements</span></span>  
  
|<span data-ttu-id="25632-143">元素</span><span class="sxs-lookup"><span data-stu-id="25632-143">Element</span></span>|<span data-ttu-id="25632-144">描述</span><span class="sxs-lookup"><span data-stu-id="25632-144">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="25632-145">指定與 Message Queuing (MSMQ) 寄件者或收件者互動所需的設定。</span><span class="sxs-lookup"><span data-stu-id="25632-145">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="25632-146">指定 Windows Communication Foundation (WCF) 服務的佇列通訊屬性 (該服務會使用原生 MSMQ 通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="25632-146">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25632-147">備註</span><span class="sxs-lookup"><span data-stu-id="25632-147">Remarks</span></span>  
 <span data-ttu-id="25632-148">如需傳輸安全性的詳細資訊，請參閱[傳輸安全性](../../../wcf/feature-details/transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="25632-148">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25632-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25632-149">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="25632-150">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="25632-150">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="25632-151">傳輸</span><span class="sxs-lookup"><span data-stu-id="25632-151">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="25632-152">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="25632-152">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="25632-153">繫結</span><span class="sxs-lookup"><span data-stu-id="25632-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="25632-154">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="25632-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="25632-155">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="25632-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="25632-156">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="25632-156">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
