---
title: <transport> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ede4103f9c8f2f73ac34036fe7a58242e32350e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934685"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="fd6bd-102">\<netMsmqBinding > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="fd6bd-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="fd6bd-103">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="fd6bd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fd6bd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fd6bd-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="fd6bd-105">\<bindings></span></span>  
<span data-ttu-id="fd6bd-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="fd6bd-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="fd6bd-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="fd6bd-107">\<binding></span></span>  
<span data-ttu-id="fd6bd-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="fd6bd-108">\<security></span></span>  
<span data-ttu-id="fd6bd-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="fd6bd-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd6bd-110">語法</span><span class="sxs-lookup"><span data-stu-id="fd6bd-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd6bd-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fd6bd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fd6bd-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd6bd-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fd6bd-113">Attributes</span></span>  
  
|<span data-ttu-id="fd6bd-114">屬性</span><span class="sxs-lookup"><span data-stu-id="fd6bd-114">Attribute</span></span>|<span data-ttu-id="fd6bd-115">描述</span><span class="sxs-lookup"><span data-stu-id="fd6bd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd6bd-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="fd6bd-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="fd6bd-117">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="fd6bd-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="fd6bd-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd6bd-119">無無驗證。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-119">-   None: No authentication.</span></span><br /><span data-ttu-id="fd6bd-120">WindowsDomain驗證機制會使用 Active Directory 來取得與訊息相關聯之安全識別碼的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="fd6bd-121">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="fd6bd-122">證書通道會從憑證存放區抓取憑證。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="fd6bd-123">預設為 `WindowsDomain`。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="fd6bd-124">如果這個屬性設定為 `None`，則 `msmqProtectionLevel` 屬性也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="fd6bd-125">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="fd6bd-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="fd6bd-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="fd6bd-127">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="fd6bd-128">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="fd6bd-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd6bd-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="fd6bd-129">-   RC4Stream</span></span><br /><span data-ttu-id="fd6bd-130">-   AES</span><span class="sxs-lookup"><span data-stu-id="fd6bd-130">-   AES</span></span><br /><span data-ttu-id="fd6bd-131">-預設值是`RC4Stream`。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="fd6bd-132">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="fd6bd-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="fd6bd-133">msmqProtectionLevel</span></span>|<span data-ttu-id="fd6bd-134">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="fd6bd-135">加密可確保訊息的完整性，而簽署和加密可確保訊息的完整性和不可否認性。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="fd6bd-136">也就是，訊息確實來自寄件者，且寄件者就是他本人。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="fd6bd-137">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="fd6bd-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd6bd-138">無無保護。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-138">-   None: No protection.</span></span><br /><span data-ttu-id="fd6bd-139">簽訂訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="fd6bd-140">EncryptAndSign訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="fd6bd-141">-預設值為`Sign`。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="fd6bd-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="fd6bd-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="fd6bd-143">指定計算訊息摘要時使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="fd6bd-144">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="fd6bd-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fd6bd-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="fd6bd-145">-   MD5</span></span><br /><span data-ttu-id="fd6bd-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="fd6bd-146">-   SHA1</span></span><br /><span data-ttu-id="fd6bd-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="fd6bd-147">-   SHA256</span></span><br /><span data-ttu-id="fd6bd-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="fd6bd-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="fd6bd-149">預設為 `SHA1`。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-149">The default is `SHA1`.</span></span> <span data-ttu-id="fd6bd-150">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="fd6bd-151">由於 MD5 和 SHA1 的衝突問題, Microsoft 建議使用 SHA256 或更好的方式。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-151">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd6bd-152">子元素</span><span class="sxs-lookup"><span data-stu-id="fd6bd-152">Child Elements</span></span>  
 <span data-ttu-id="fd6bd-153">無</span><span class="sxs-lookup"><span data-stu-id="fd6bd-153">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd6bd-154">父項目</span><span class="sxs-lookup"><span data-stu-id="fd6bd-154">Parent Elements</span></span>  
  
|<span data-ttu-id="fd6bd-155">項目</span><span class="sxs-lookup"><span data-stu-id="fd6bd-155">Element</span></span>|<span data-ttu-id="fd6bd-156">描述</span><span class="sxs-lookup"><span data-stu-id="fd6bd-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd6bd-157">\<security></span><span class="sxs-lookup"><span data-stu-id="fd6bd-157">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="fd6bd-158">定義佇列傳輸的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-158">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd6bd-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd6bd-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="fd6bd-160">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="fd6bd-160">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="fd6bd-161">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="fd6bd-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fd6bd-162">繫結</span><span class="sxs-lookup"><span data-stu-id="fd6bd-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fd6bd-163">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="fd6bd-163">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fd6bd-164">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="fd6bd-164">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="fd6bd-165">\<binding></span><span class="sxs-lookup"><span data-stu-id="fd6bd-165">\<binding></span></span>](../../../misc/binding.md)
