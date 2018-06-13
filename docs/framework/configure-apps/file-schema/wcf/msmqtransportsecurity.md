---
title: '&lt;msmqTransportSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ff60772e96d2709e018a2201459a1a0c65659464
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750202"
---
# <a name="ltmsmqtransportsecuritygt"></a><span data-ttu-id="a328c-102">&lt;msmqTransportSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="a328c-102">&lt;msmqTransportSecurity&gt;</span></span>
<span data-ttu-id="a328c-103">指定自訂繫結的 MSMQ 傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a328c-103">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
 <span data-ttu-id="a328c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a328c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a328c-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a328c-105">\<bindings></span></span>  
<span data-ttu-id="a328c-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a328c-106">\<customBinding></span></span>  
<span data-ttu-id="a328c-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a328c-107">\<binding></span></span>  
<span data-ttu-id="a328c-108">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="a328c-108">\<msmqIntegration></span></span>  
<span data-ttu-id="a328c-109">\<msmqTransportSecurity ></span><span class="sxs-lookup"><span data-stu-id="a328c-109">\<msmqTransportSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a328c-110">語法</span><span class="sxs-lookup"><span data-stu-id="a328c-110">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity>  
   msmqAuthenticationMode="None/Windows/Certificate"  
   msmqEncryptionAlgorithm="RC4Stream/AES"  
   msmqProtectionLevel="None/Sign/EncryptAndSign"  
   msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</msmqTransportSecurity>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a328c-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a328c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a328c-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a328c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a328c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a328c-113">Attributes</span></span>  
  
|<span data-ttu-id="a328c-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a328c-114">Attribute</span></span>|<span data-ttu-id="a328c-115">描述</span><span class="sxs-lookup"><span data-stu-id="a328c-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="a328c-116">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="a328c-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="a328c-117">如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="a328c-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="a328c-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a328c-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a328c-119">-None： 無驗證。</span><span class="sxs-lookup"><span data-stu-id="a328c-119">-   None: No authentication.</span></span><br /><span data-ttu-id="a328c-120">Windows： 驗證機制使用 Active Directory 為與訊息相關聯的 SID 取得 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a328c-120">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="a328c-121">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="a328c-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="a328c-122">-Certificate： 通道會從憑證存放區取得憑證。</span><span class="sxs-lookup"><span data-stu-id="a328c-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="a328c-123">預設值為 Windows。</span><span class="sxs-lookup"><span data-stu-id="a328c-123">The default value is Windows.</span></span> <span data-ttu-id="a328c-124">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="a328c-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="a328c-125">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="a328c-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="a328c-126">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a328c-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a328c-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="a328c-127">-   RC4Stream</span></span><br /><span data-ttu-id="a328c-128">-AES</span><span class="sxs-lookup"><span data-stu-id="a328c-128">-   AES</span></span><br /><br /> <span data-ttu-id="a328c-129">預設值為 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="a328c-129">The default value is RC4Stream.</span></span> <span data-ttu-id="a328c-130">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="a328c-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="a328c-131">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="a328c-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="a328c-132">加密可確保訊息完整性，而 EncryptAndSign 可確保訊息完整性和不可否認性，也就是訊息確實來自寄件者，且寄件者就是他本人。</span><span class="sxs-lookup"><span data-stu-id="a328c-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="a328c-133">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a328c-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a328c-134">-None： 無保護。</span><span class="sxs-lookup"><span data-stu-id="a328c-134">-   None: No protection.</span></span><br /><span data-ttu-id="a328c-135">-Sign： 簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="a328c-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a328c-136">-EncryptAndSign： 加密和訊息簽署。</span><span class="sxs-lookup"><span data-stu-id="a328c-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="a328c-137">預設值為 Sign。</span><span class="sxs-lookup"><span data-stu-id="a328c-137">The default value is Sign.</span></span> <span data-ttu-id="a328c-138">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="a328c-138">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="a328c-139">指定計算摘要做為部分簽章時使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="a328c-139">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="a328c-140">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="a328c-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a328c-141">-   MD5</span><span class="sxs-lookup"><span data-stu-id="a328c-141">-   MD5</span></span><br /><span data-ttu-id="a328c-142">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="a328c-142">-   SHA1</span></span><br /><span data-ttu-id="a328c-143">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="a328c-143">-   SHA256</span></span><br /><span data-ttu-id="a328c-144">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="a328c-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="a328c-145">預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="a328c-145">The default value is SHA1.</span></span> <span data-ttu-id="a328c-146">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="a328c-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a328c-147">子項目</span><span class="sxs-lookup"><span data-stu-id="a328c-147">Child Elements</span></span>  
 <span data-ttu-id="a328c-148">無。</span><span class="sxs-lookup"><span data-stu-id="a328c-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a328c-149">父項目</span><span class="sxs-lookup"><span data-stu-id="a328c-149">Parent Elements</span></span>  
  
|<span data-ttu-id="a328c-150">項目</span><span class="sxs-lookup"><span data-stu-id="a328c-150">Element</span></span>|<span data-ttu-id="a328c-151">描述</span><span class="sxs-lookup"><span data-stu-id="a328c-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a328c-152">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="a328c-152">\<msmqIntegration></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|<span data-ttu-id="a328c-153">指定與 Message Queuing (MSMQ) 寄件者或收件者互動所需的設定。</span><span class="sxs-lookup"><span data-stu-id="a328c-153">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="a328c-154">\<msmqTransport ></span><span class="sxs-lookup"><span data-stu-id="a328c-154">\<msmqTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|<span data-ttu-id="a328c-155">指定 Windows Communication Foundation (WCF) 服務的佇列通訊屬性 (該服務會使用原生 MSMQ 通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="a328c-155">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a328c-156">備註</span><span class="sxs-lookup"><span data-stu-id="a328c-156">Remarks</span></span>  
 <span data-ttu-id="a328c-157">如需有關傳輸安全性的詳細資訊，請參閱[傳輸安全性](../../../../../docs/framework/wcf/feature-details/transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="a328c-157">For more information on transport security, see [Transport Security](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a328c-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a328c-158">See Also</span></span>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a328c-159">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="a328c-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="a328c-160">傳輸</span><span class="sxs-lookup"><span data-stu-id="a328c-160">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="a328c-161">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="a328c-161">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="a328c-162">繫結</span><span class="sxs-lookup"><span data-stu-id="a328c-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a328c-163">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="a328c-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a328c-164">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="a328c-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a328c-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a328c-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="a328c-166">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="a328c-166">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
