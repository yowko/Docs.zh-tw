---
title: <transport> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 84a5437de851ecdb96d0463ec574186ba5f91d9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203874"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="ac3fc-102">\<transport> 的 \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="ac3fc-102">\<transport> of \<netMsmqBinding></span></span>

<span data-ttu-id="ac3fc-103">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-103">Defines the transport security settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="ac3fc-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac3fc-104">Syntax</span></span>  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac3fc-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ac3fc-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ac3fc-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac3fc-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ac3fc-107">Attributes</span></span>  
  
|<span data-ttu-id="ac3fc-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ac3fc-108">Attribute</span></span>|<span data-ttu-id="ac3fc-109">描述</span><span class="sxs-lookup"><span data-stu-id="ac3fc-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac3fc-110">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="ac3fc-110">msmqAuthenticationMode</span></span>|<span data-ttu-id="ac3fc-111">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-111">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="ac3fc-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="ac3fc-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ac3fc-113">-None：無驗證。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-113">-   None: No authentication.</span></span><br /><span data-ttu-id="ac3fc-114">-WindowsDomain：驗證機制會使用 Active Directory 來取得與訊息相關聯之安全識別碼的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-114">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="ac3fc-115">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-115">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="ac3fc-116">-Certificate：通道會從憑證存放區捕獲憑證。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-116">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="ac3fc-117">預設值為 `WindowsDomain`。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-117">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="ac3fc-118">如果這個屬性設定為 `None`，則 `msmqProtectionLevel` 屬性也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-118">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="ac3fc-119">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-119">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="ac3fc-120">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="ac3fc-120">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="ac3fc-121">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-121">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="ac3fc-122">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="ac3fc-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ac3fc-123">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="ac3fc-123">-   RC4Stream</span></span><br /><span data-ttu-id="ac3fc-124">-AES</span><span class="sxs-lookup"><span data-stu-id="ac3fc-124">-   AES</span></span><br /><span data-ttu-id="ac3fc-125">-預設值為 `RC4Stream` 。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-125">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="ac3fc-126">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-126">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="ac3fc-127">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="ac3fc-127">msmqProtectionLevel</span></span>|<span data-ttu-id="ac3fc-128">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-128">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="ac3fc-129">加密可確保訊息的完整性，而簽署和加密可確保訊息的完整性和不可否認性。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-129">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="ac3fc-130">也就是說，訊息確實來自寄件者，且寄件者就是他們說的人。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-130">That is, the message indeed came from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="ac3fc-131">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="ac3fc-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ac3fc-132">-None：無保護。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-132">-   None: No protection.</span></span><br /><span data-ttu-id="ac3fc-133">-Sign：簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-133">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="ac3fc-134">-EncryptAndSign：訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-134">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="ac3fc-135">-預設值為 `Sign` 。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-135">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="ac3fc-136">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="ac3fc-136">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="ac3fc-137">指定計算訊息摘要時使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-137">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="ac3fc-138">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="ac3fc-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ac3fc-139">-MD5</span><span class="sxs-lookup"><span data-stu-id="ac3fc-139">-   MD5</span></span><br /><span data-ttu-id="ac3fc-140">-SHA1</span><span class="sxs-lookup"><span data-stu-id="ac3fc-140">-   SHA1</span></span><br /><span data-ttu-id="ac3fc-141">-SHA256</span><span class="sxs-lookup"><span data-stu-id="ac3fc-141">-   SHA256</span></span><br /><span data-ttu-id="ac3fc-142">-SHA512</span><span class="sxs-lookup"><span data-stu-id="ac3fc-142">-   SHA512</span></span><br /><br /> <span data-ttu-id="ac3fc-143">預設值為 `SHA1`。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-143">The default is `SHA1`.</span></span> <span data-ttu-id="ac3fc-144">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-144">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="ac3fc-145">由於 MD5 和 SHA1 的衝突問題，Microsoft 建議使用 SHA256 或更好的方式。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-145">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac3fc-146">子元素</span><span class="sxs-lookup"><span data-stu-id="ac3fc-146">Child Elements</span></span>  

 <span data-ttu-id="ac3fc-147">無</span><span class="sxs-lookup"><span data-stu-id="ac3fc-147">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac3fc-148">父項目</span><span class="sxs-lookup"><span data-stu-id="ac3fc-148">Parent Elements</span></span>  
  
|<span data-ttu-id="ac3fc-149">項目</span><span class="sxs-lookup"><span data-stu-id="ac3fc-149">Element</span></span>|<span data-ttu-id="ac3fc-150">描述</span><span class="sxs-lookup"><span data-stu-id="ac3fc-150">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="ac3fc-151">定義佇列傳輸的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ac3fc-151">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac3fc-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac3fc-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="ac3fc-153">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="ac3fc-153">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="ac3fc-154">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="ac3fc-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ac3fc-155">繫結</span><span class="sxs-lookup"><span data-stu-id="ac3fc-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ac3fc-156">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="ac3fc-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ac3fc-157">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="ac3fc-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
