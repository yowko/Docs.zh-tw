---
title: <transport> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152953"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="5548b-102">\<transport> 的 \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="5548b-102">\<transport> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="5548b-103">定義訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="5548b-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="5548b-104">語法</span><span class="sxs-lookup"><span data-stu-id="5548b-104">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5548b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5548b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5548b-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="5548b-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5548b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5548b-107">Attributes</span></span>  
  
|<span data-ttu-id="5548b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5548b-108">Attribute</span></span>|<span data-ttu-id="5548b-109">描述</span><span class="sxs-lookup"><span data-stu-id="5548b-109">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="5548b-110">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="5548b-110">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="5548b-111">如果這設定為 `None`，則 `msmqProtectionLevel` 屬性的值也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="5548b-111">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="5548b-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="5548b-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5548b-113">-None：不進行驗證。</span><span class="sxs-lookup"><span data-stu-id="5548b-113">-   None: No authentication.</span></span><br /><span data-ttu-id="5548b-114">-WindowsDomain：驗證機制會使用 Active Directory 來取得與訊息相關聯之 SID 的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="5548b-114">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="5548b-115">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="5548b-115">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="5548b-116">-Certificate：通道會從憑證存放區取得憑證。</span><span class="sxs-lookup"><span data-stu-id="5548b-116">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="5548b-117">預設值為 WindowsDomain。</span><span class="sxs-lookup"><span data-stu-id="5548b-117">The default value is WindowsDomain.</span></span> <span data-ttu-id="5548b-118">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="5548b-118">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="5548b-119">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="5548b-119">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="5548b-120">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="5548b-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5548b-121">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="5548b-121">-   RC4Stream</span></span><br /><span data-ttu-id="5548b-122">-AES</span><span class="sxs-lookup"><span data-stu-id="5548b-122">-   AES</span></span><br /><br /> <span data-ttu-id="5548b-123">預設值為 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="5548b-123">The default value is RC4Stream.</span></span> <span data-ttu-id="5548b-124">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="5548b-124">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="5548b-125">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="5548b-125">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="5548b-126">加密可確保訊息完整性，而 EncryptAndSign 可確保訊息完整性和不可否認性;也就是說，訊息確實來自寄件者，而寄件者則是他們說的。</span><span class="sxs-lookup"><span data-stu-id="5548b-126">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span><br /><br /> <span data-ttu-id="5548b-127">-有效的值包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="5548b-127">-   Valid values include the following:</span></span><br /><span data-ttu-id="5548b-128">-None：沒有保護。</span><span class="sxs-lookup"><span data-stu-id="5548b-128">-   None: No protection.</span></span><br /><span data-ttu-id="5548b-129">-Sign：訊息已簽署。</span><span class="sxs-lookup"><span data-stu-id="5548b-129">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="5548b-130">-EncryptAndSign：訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="5548b-130">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="5548b-131">預設值為 Sign。</span><span class="sxs-lookup"><span data-stu-id="5548b-131">The default value is Sign.</span></span> <span data-ttu-id="5548b-132">此屬性的型別為 ProtectionLevel。</span><span class="sxs-lookup"><span data-stu-id="5548b-132">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="5548b-133">-指定要用來將摘要計算為簽章一部分的演算法。</span><span class="sxs-lookup"><span data-stu-id="5548b-133">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="5548b-134">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="5548b-134">Valid values include the following:</span></span><br /><span data-ttu-id="5548b-135">-MD5</span><span class="sxs-lookup"><span data-stu-id="5548b-135">-   MD5</span></span><br /><span data-ttu-id="5548b-136">-SHA1</span><span class="sxs-lookup"><span data-stu-id="5548b-136">-   SHA1</span></span><br /><span data-ttu-id="5548b-137">-SHA256</span><span class="sxs-lookup"><span data-stu-id="5548b-137">-   SHA256</span></span><br /><span data-ttu-id="5548b-138">-SHA512</span><span class="sxs-lookup"><span data-stu-id="5548b-138">-   SHA512</span></span><br /><br /> <span data-ttu-id="5548b-139">預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="5548b-139">The default value is SHA1.</span></span> <span data-ttu-id="5548b-140">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="5548b-140">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="5548b-141">由於 MD5 和 SHA1 的衝突問題，Microsoft 建議使用 SHA256 或更好的方式。</span><span class="sxs-lookup"><span data-stu-id="5548b-141">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5548b-142">子元素</span><span class="sxs-lookup"><span data-stu-id="5548b-142">Child Elements</span></span>  
 <span data-ttu-id="5548b-143">無</span><span class="sxs-lookup"><span data-stu-id="5548b-143">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5548b-144">父項目</span><span class="sxs-lookup"><span data-stu-id="5548b-144">Parent Elements</span></span>  
  
|<span data-ttu-id="5548b-145">元素</span><span class="sxs-lookup"><span data-stu-id="5548b-145">Element</span></span>|<span data-ttu-id="5548b-146">描述</span><span class="sxs-lookup"><span data-stu-id="5548b-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="5548b-147">定義 MSMQ 繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="5548b-147">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5548b-148">備註</span><span class="sxs-lookup"><span data-stu-id="5548b-148">Remarks</span></span>  
 <span data-ttu-id="5548b-149">這個項目會封裝訊息佇列整合傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="5548b-149">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="5548b-150">這些設定同時適用於訊息佇列整合和已佇列之傳輸。</span><span class="sxs-lookup"><span data-stu-id="5548b-150">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="5548b-151">它還可讓您設定驗證模式、加密演算法、安全雜湊演算法和保護層級。</span><span class="sxs-lookup"><span data-stu-id="5548b-151">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5548b-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5548b-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="5548b-153">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="5548b-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5548b-154">繫結</span><span class="sxs-lookup"><span data-stu-id="5548b-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5548b-155">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="5548b-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5548b-156">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="5548b-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
