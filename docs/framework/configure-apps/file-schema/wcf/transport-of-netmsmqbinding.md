---
title: <transport> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: d6588e36a8a9420aa37837305aa904763c90781d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399352"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="92a32-102">\<netMsmqBinding > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="92a32-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="92a32-103">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="92a32-103">Defines the transport security settings.</span></span>  
  
<span data-ttu-id="92a32-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="92a32-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="92a32-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="92a32-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="92a32-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="92a32-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="92a32-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="92a32-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="92a32-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="92a32-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="92a32-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="92a32-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="92a32-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="92a32-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92a32-111">語法</span><span class="sxs-lookup"><span data-stu-id="92a32-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92a32-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="92a32-112">Attributes and Elements</span></span>  
 <span data-ttu-id="92a32-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="92a32-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92a32-114">屬性</span><span class="sxs-lookup"><span data-stu-id="92a32-114">Attributes</span></span>  
  
|<span data-ttu-id="92a32-115">屬性</span><span class="sxs-lookup"><span data-stu-id="92a32-115">Attribute</span></span>|<span data-ttu-id="92a32-116">說明</span><span class="sxs-lookup"><span data-stu-id="92a32-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92a32-117">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="92a32-117">msmqAuthenticationMode</span></span>|<span data-ttu-id="92a32-118">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="92a32-118">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="92a32-119">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="92a32-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="92a32-120">無無驗證。</span><span class="sxs-lookup"><span data-stu-id="92a32-120">-   None: No authentication.</span></span><br /><span data-ttu-id="92a32-121">WindowsDomain驗證機制會使用 Active Directory 來取得與訊息相關聯之安全識別碼的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="92a32-121">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="92a32-122">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="92a32-122">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="92a32-123">證書通道會從憑證存放區抓取憑證。</span><span class="sxs-lookup"><span data-stu-id="92a32-123">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="92a32-124">預設為 `WindowsDomain`。</span><span class="sxs-lookup"><span data-stu-id="92a32-124">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="92a32-125">如果這個屬性設定為 `None`，則 `msmqProtectionLevel` 屬性也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="92a32-125">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="92a32-126">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="92a32-126">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="92a32-127">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="92a32-127">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="92a32-128">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="92a32-128">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="92a32-129">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="92a32-129">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="92a32-130">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="92a32-130">-   RC4Stream</span></span><br /><span data-ttu-id="92a32-131">-   AES</span><span class="sxs-lookup"><span data-stu-id="92a32-131">-   AES</span></span><br /><span data-ttu-id="92a32-132">-預設值是`RC4Stream`。</span><span class="sxs-lookup"><span data-stu-id="92a32-132">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="92a32-133">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="92a32-133">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="92a32-134">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="92a32-134">msmqProtectionLevel</span></span>|<span data-ttu-id="92a32-135">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="92a32-135">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="92a32-136">加密可確保訊息的完整性，而簽署和加密可確保訊息的完整性和不可否認性。</span><span class="sxs-lookup"><span data-stu-id="92a32-136">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="92a32-137">也就是，訊息確實來自寄件者，且寄件者就是他本人。</span><span class="sxs-lookup"><span data-stu-id="92a32-137">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="92a32-138">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="92a32-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="92a32-139">無無保護。</span><span class="sxs-lookup"><span data-stu-id="92a32-139">-   None: No protection.</span></span><br /><span data-ttu-id="92a32-140">簽訂訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="92a32-140">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="92a32-141">EncryptAndSign訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="92a32-141">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="92a32-142">-預設值為`Sign`。</span><span class="sxs-lookup"><span data-stu-id="92a32-142">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="92a32-143">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="92a32-143">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="92a32-144">指定計算訊息摘要時使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="92a32-144">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="92a32-145">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="92a32-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="92a32-146">-   MD5</span><span class="sxs-lookup"><span data-stu-id="92a32-146">-   MD5</span></span><br /><span data-ttu-id="92a32-147">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="92a32-147">-   SHA1</span></span><br /><span data-ttu-id="92a32-148">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="92a32-148">-   SHA256</span></span><br /><span data-ttu-id="92a32-149">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="92a32-149">-   SHA512</span></span><br /><br /> <span data-ttu-id="92a32-150">預設為 `SHA1`。</span><span class="sxs-lookup"><span data-stu-id="92a32-150">The default is `SHA1`.</span></span> <span data-ttu-id="92a32-151">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="92a32-151">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="92a32-152">由於 MD5 和 SHA1 的衝突問題，Microsoft 建議使用 SHA256 或更好的方式。</span><span class="sxs-lookup"><span data-stu-id="92a32-152">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92a32-153">子元素</span><span class="sxs-lookup"><span data-stu-id="92a32-153">Child Elements</span></span>  
 <span data-ttu-id="92a32-154">無</span><span class="sxs-lookup"><span data-stu-id="92a32-154">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92a32-155">父項目</span><span class="sxs-lookup"><span data-stu-id="92a32-155">Parent Elements</span></span>  
  
|<span data-ttu-id="92a32-156">項目</span><span class="sxs-lookup"><span data-stu-id="92a32-156">Element</span></span>|<span data-ttu-id="92a32-157">描述</span><span class="sxs-lookup"><span data-stu-id="92a32-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92a32-158">\<security></span><span class="sxs-lookup"><span data-stu-id="92a32-158">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="92a32-159">定義佇列傳輸的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="92a32-159">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92a32-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92a32-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="92a32-161">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="92a32-161">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="92a32-162">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="92a32-162">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="92a32-163">繫結</span><span class="sxs-lookup"><span data-stu-id="92a32-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="92a32-164">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="92a32-164">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="92a32-165">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="92a32-165">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="92a32-166">\<binding></span><span class="sxs-lookup"><span data-stu-id="92a32-166">\<binding></span></span>](../../../misc/binding.md)
