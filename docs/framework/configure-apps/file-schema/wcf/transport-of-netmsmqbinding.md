---
title: <transport> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152927"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="b00e4-102">\<\<網路mq綁定>的傳輸></span><span class="sxs-lookup"><span data-stu-id="b00e4-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="b00e4-103">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="b00e4-103">Defines the transport security settings.</span></span>  
  
<span data-ttu-id="b00e4-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b00e4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b00e4-105">&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b00e4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b00e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<綁定>**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b00e4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b00e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<淨Mmq綁定>**](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b00e4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="b00e4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<綁定>**</span><span class="sxs-lookup"><span data-stu-id="b00e4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b00e4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全>**](security-of-netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b00e4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="b00e4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<運輸>**</span><span class="sxs-lookup"><span data-stu-id="b00e4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b00e4-111">語法</span><span class="sxs-lookup"><span data-stu-id="b00e4-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b00e4-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b00e4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b00e4-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b00e4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b00e4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b00e4-114">Attributes</span></span>  
  
|<span data-ttu-id="b00e4-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b00e4-115">Attribute</span></span>|<span data-ttu-id="b00e4-116">描述</span><span class="sxs-lookup"><span data-stu-id="b00e4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b00e4-117">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="b00e4-117">msmqAuthenticationMode</span></span>|<span data-ttu-id="b00e4-118">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="b00e4-118">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="b00e4-119">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="b00e4-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b00e4-120">- 無：無身份驗證。</span><span class="sxs-lookup"><span data-stu-id="b00e4-120">-   None: No authentication.</span></span><br /><span data-ttu-id="b00e4-121">- WindowsDomain：身份驗證機制使用 Active Directory 檢索與消息關聯的安全識別碼的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="b00e4-121">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="b00e4-122">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="b00e4-122">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="b00e4-123">- 證書：通道從憑證存放區中檢索證書。</span><span class="sxs-lookup"><span data-stu-id="b00e4-123">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="b00e4-124">預設值為 `WindowsDomain`。</span><span class="sxs-lookup"><span data-stu-id="b00e4-124">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="b00e4-125">如果這個屬性設定為 `None`，則 `msmqProtectionLevel` 屬性也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="b00e4-125">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="b00e4-126">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="b00e4-126">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="b00e4-127">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="b00e4-127">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="b00e4-128">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="b00e4-128">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="b00e4-129">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="b00e4-129">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b00e4-130">- RC4流</span><span class="sxs-lookup"><span data-stu-id="b00e4-130">-   RC4Stream</span></span><br /><span data-ttu-id="b00e4-131">- AES</span><span class="sxs-lookup"><span data-stu-id="b00e4-131">-   AES</span></span><br /><span data-ttu-id="b00e4-132">- 預設值為`RC4Stream`。</span><span class="sxs-lookup"><span data-stu-id="b00e4-132">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="b00e4-133">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="b00e4-133">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="b00e4-134">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="b00e4-134">msmqProtectionLevel</span></span>|<span data-ttu-id="b00e4-135">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="b00e4-135">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="b00e4-136">加密可確保訊息的完整性，而簽署和加密可確保訊息的完整性和不可否認性。</span><span class="sxs-lookup"><span data-stu-id="b00e4-136">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="b00e4-137">也就是說，郵件確實來自寄件者，寄件者就是他們所說的寄件者。</span><span class="sxs-lookup"><span data-stu-id="b00e4-137">That is, the message indeed came from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="b00e4-138">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="b00e4-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b00e4-139">-無：沒有保護</span><span class="sxs-lookup"><span data-stu-id="b00e4-139">-   None: No protection.</span></span><br /><span data-ttu-id="b00e4-140">- 簽名：消息已簽名。</span><span class="sxs-lookup"><span data-stu-id="b00e4-140">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="b00e4-141">- 加密和簽名：郵件經過加密並簽名。</span><span class="sxs-lookup"><span data-stu-id="b00e4-141">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="b00e4-142">- 預設值為`Sign`。</span><span class="sxs-lookup"><span data-stu-id="b00e4-142">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="b00e4-143">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="b00e4-143">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="b00e4-144">指定計算訊息摘要時使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="b00e4-144">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="b00e4-145">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="b00e4-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b00e4-146">- MD5</span><span class="sxs-lookup"><span data-stu-id="b00e4-146">-   MD5</span></span><br /><span data-ttu-id="b00e4-147">- SHA1</span><span class="sxs-lookup"><span data-stu-id="b00e4-147">-   SHA1</span></span><br /><span data-ttu-id="b00e4-148">- SHA256</span><span class="sxs-lookup"><span data-stu-id="b00e4-148">-   SHA256</span></span><br /><span data-ttu-id="b00e4-149">- SHA512</span><span class="sxs-lookup"><span data-stu-id="b00e4-149">-   SHA512</span></span><br /><br /> <span data-ttu-id="b00e4-150">預設值為 `SHA1`。</span><span class="sxs-lookup"><span data-stu-id="b00e4-150">The default is `SHA1`.</span></span> <span data-ttu-id="b00e4-151">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="b00e4-151">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="b00e4-152">由於與 MD5 和 SHA1 的碰撞問題，Microsoft 推薦 SHA256 或更高。</span><span class="sxs-lookup"><span data-stu-id="b00e4-152">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b00e4-153">子元素</span><span class="sxs-lookup"><span data-stu-id="b00e4-153">Child Elements</span></span>  
 <span data-ttu-id="b00e4-154">None</span><span class="sxs-lookup"><span data-stu-id="b00e4-154">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b00e4-155">父項目</span><span class="sxs-lookup"><span data-stu-id="b00e4-155">Parent Elements</span></span>  
  
|<span data-ttu-id="b00e4-156">元素</span><span class="sxs-lookup"><span data-stu-id="b00e4-156">Element</span></span>|<span data-ttu-id="b00e4-157">描述</span><span class="sxs-lookup"><span data-stu-id="b00e4-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b00e4-158">\<安全></span><span class="sxs-lookup"><span data-stu-id="b00e4-158">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="b00e4-159">定義佇列傳輸的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="b00e4-159">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b00e4-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b00e4-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="b00e4-161">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="b00e4-161">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="b00e4-162">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="b00e4-162">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b00e4-163">綁定</span><span class="sxs-lookup"><span data-stu-id="b00e4-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b00e4-164">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="b00e4-164">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b00e4-165">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="b00e4-165">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b00e4-166">\<綁定></span><span class="sxs-lookup"><span data-stu-id="b00e4-166">\<binding></span></span>](bindings.md)
