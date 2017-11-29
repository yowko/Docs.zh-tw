---
title: "&lt;netMsmqBinding&gt; 的 &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2df5bf18605fcf20b253212cb0f9a62b4719b0ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="dd986-102">&lt;netMsmqBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="dd986-102">&lt;transport&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="dd986-103">定義傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="dd986-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="dd986-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="dd986-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd986-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dd986-105">\<bindings></span></span>  
<span data-ttu-id="dd986-106">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="dd986-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="dd986-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dd986-107">\<binding></span></span>  
<span data-ttu-id="dd986-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="dd986-108">\<security></span></span>  
<span data-ttu-id="dd986-109">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="dd986-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd986-110">語法</span><span class="sxs-lookup"><span data-stu-id="dd986-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd986-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dd986-111">Attributes and Elements</span></span>  
 <span data-ttu-id="dd986-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dd986-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd986-113">屬性</span><span class="sxs-lookup"><span data-stu-id="dd986-113">Attributes</span></span>  
  
|<span data-ttu-id="dd986-114">屬性</span><span class="sxs-lookup"><span data-stu-id="dd986-114">Attribute</span></span>|<span data-ttu-id="dd986-115">描述</span><span class="sxs-lookup"><span data-stu-id="dd986-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd986-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="dd986-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="dd986-117">指定 MSMQ 傳輸必須如何驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="dd986-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="dd986-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="dd986-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dd986-119">-None： 無驗證。</span><span class="sxs-lookup"><span data-stu-id="dd986-119">-   None: No authentication.</span></span><br /><span data-ttu-id="dd986-120">-WindowsDomain： 驗證機制使用 Active Directory 來擷取與訊息相關聯的安全性識別碼的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="dd986-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="dd986-121">接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="dd986-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="dd986-122">憑證： 通道會從憑證存放區擷取憑證。</span><span class="sxs-lookup"><span data-stu-id="dd986-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="dd986-123">預設為 `WindowsDomain`。</span><span class="sxs-lookup"><span data-stu-id="dd986-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="dd986-124">如果這個屬性設定為 `None`，則 `msmqProtectionLevel` 屬性也必須設定為 `None`。</span><span class="sxs-lookup"><span data-stu-id="dd986-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="dd986-125">此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="dd986-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="dd986-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="dd986-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="dd986-127">指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。</span><span class="sxs-lookup"><span data-stu-id="dd986-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="dd986-128">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="dd986-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dd986-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="dd986-129">-   RC4Stream</span></span><br /><span data-ttu-id="dd986-130">-AES</span><span class="sxs-lookup"><span data-stu-id="dd986-130">-   AES</span></span><br /><span data-ttu-id="dd986-131">-預設值是`RC4Stream`。</span><span class="sxs-lookup"><span data-stu-id="dd986-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="dd986-132">此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="dd986-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="dd986-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="dd986-133">msmqProtectionLevel</span></span>|<span data-ttu-id="dd986-134">指定在 MSMQ 傳輸層級上保護訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="dd986-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="dd986-135">加密可確保訊息的完整性，而簽署和加密可確保訊息的完整性和不可否認性。</span><span class="sxs-lookup"><span data-stu-id="dd986-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="dd986-136">也就是，訊息確實來自寄件者，且寄件者就是他本人。</span><span class="sxs-lookup"><span data-stu-id="dd986-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="dd986-137">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="dd986-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dd986-138">-None： 無保護。</span><span class="sxs-lookup"><span data-stu-id="dd986-138">-   None: No protection.</span></span><br /><span data-ttu-id="dd986-139">-Sign： 簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="dd986-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="dd986-140">-EncryptAndSign： 加密和訊息簽署。</span><span class="sxs-lookup"><span data-stu-id="dd986-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="dd986-141">-預設值是`Sign`。</span><span class="sxs-lookup"><span data-stu-id="dd986-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="dd986-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="dd986-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="dd986-143">指定計算訊息摘要時使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="dd986-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="dd986-144">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="dd986-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dd986-145">MD5</span><span class="sxs-lookup"><span data-stu-id="dd986-145">-   MD5</span></span><br /><span data-ttu-id="dd986-146">-SHA1</span><span class="sxs-lookup"><span data-stu-id="dd986-146">-   SHA1</span></span><br /><span data-ttu-id="dd986-147">RSA-SHA256</span><span class="sxs-lookup"><span data-stu-id="dd986-147">-   SHA256</span></span><br /><span data-ttu-id="dd986-148">-SHA512</span><span class="sxs-lookup"><span data-stu-id="dd986-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="dd986-149">預設為 `SHA1`。</span><span class="sxs-lookup"><span data-stu-id="dd986-149">The default is `SHA1`.</span></span> <span data-ttu-id="dd986-150">此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="dd986-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd986-151">子元素</span><span class="sxs-lookup"><span data-stu-id="dd986-151">Child Elements</span></span>  
 <span data-ttu-id="dd986-152">無</span><span class="sxs-lookup"><span data-stu-id="dd986-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd986-153">父項目</span><span class="sxs-lookup"><span data-stu-id="dd986-153">Parent Elements</span></span>  
  
|<span data-ttu-id="dd986-154">項目</span><span class="sxs-lookup"><span data-stu-id="dd986-154">Element</span></span>|<span data-ttu-id="dd986-155">說明</span><span class="sxs-lookup"><span data-stu-id="dd986-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd986-156">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="dd986-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="dd986-157">定義佇列傳輸的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="dd986-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd986-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd986-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="dd986-159">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="dd986-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="dd986-160">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="dd986-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="dd986-161">繫結</span><span class="sxs-lookup"><span data-stu-id="dd986-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="dd986-162">設定系統提供繫結</span><span class="sxs-lookup"><span data-stu-id="dd986-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="dd986-163">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="dd986-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="dd986-164">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dd986-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
