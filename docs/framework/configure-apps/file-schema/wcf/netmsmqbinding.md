---
title: '&lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: 05ab1b064f6dd7bb28d1d118ec8c4249da5a75e1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800387"
---
# <a name="ltnetmsmqbindinggt"></a><span data-ttu-id="76cdb-102">&lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="76cdb-102">&lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="76cdb-103">定義適合跨電腦通訊的佇列繫結。</span><span class="sxs-lookup"><span data-stu-id="76cdb-103">Defines a queued binding suitable for cross-machine communication.</span></span>  
  
 <span data-ttu-id="76cdb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="76cdb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="76cdb-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="76cdb-105">\<bindings></span></span>  
<span data-ttu-id="76cdb-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="76cdb-106">\<netMsmqBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76cdb-107">語法</span><span class="sxs-lookup"><span data-stu-id="76cdb-107">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding   
       closeTimeout="TimeSpan"   
       customDeadLetterQueue="Uri"  
       deadLetterQueue="Uri"  
       durable="Boolean"  
       exactlyOnce="Boolean"   
       maxBufferPoolSize="Integer"  
       maxReceivedMessageSize"Integer"  
       maxRetryCycles="Integer"   
       name="string"   
       openTimeout="TimeSpan"   
       poisonMessageHandling="Disabled/EnabledIfSupported"   
       queueTransferProtocol="Native/Srmp/SrmpSecure"  
       receiveErrorHandling="Drop/Fault/Move/Reject"  
       receiveTimeout="TimeSpan"   
       receiveRetryCount="Integer"  
       rejectAfterLastRetry="Boolean"   
       retryCycleDelay="TimeSpan"    
       sendTimeout="TimeSpan"   
       timeToLive="TimeSpan"    
       useActiveDirectory="Boolean"  
       useMsmqTracing="Boolean  
       useSourceJournal="Boolean"  
          <security>  
                  <message    
                        algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/InfoCard "/>  
                  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding></netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76cdb-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="76cdb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="76cdb-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="76cdb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76cdb-110">屬性</span><span class="sxs-lookup"><span data-stu-id="76cdb-110">Attributes</span></span>  
  
|<span data-ttu-id="76cdb-111">屬性</span><span class="sxs-lookup"><span data-stu-id="76cdb-111">Attribute</span></span>|<span data-ttu-id="76cdb-112">描述</span><span class="sxs-lookup"><span data-stu-id="76cdb-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="76cdb-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="76cdb-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="76cdb-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="76cdb-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="76cdb-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="76cdb-115">The default is 00:01:00.</span></span>|  
|`customDeadLetterQueue`|<span data-ttu-id="76cdb-116">URI，其中包含每個應用程式寄不出的信件佇列的位置，所有已過期、無法傳輸或傳遞的訊息都會放到該佇列中。</span><span class="sxs-lookup"><span data-stu-id="76cdb-116">A URI that contains the location of the per-application dead letter queue, where messages that have expired or that have failed transfer or delivery are placed.</span></span><br /><br /> <span data-ttu-id="76cdb-117">寄不出的信件佇列是傳送應用程式佇列管理員上的佇列，用於無法傳遞的過期訊息。</span><span class="sxs-lookup"><span data-stu-id="76cdb-117">The dead letter queue is a queue on the queue manager of the sending application for expired messages that have failed to be delivered.</span></span><br /><br /> <span data-ttu-id="76cdb-118">由 <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> 指定的 URI 必須使用 net.msmq 配置。</span><span class="sxs-lookup"><span data-stu-id="76cdb-118">The URI that is specified by <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> must use the net.msmq scheme.</span></span>|  
|`deadLetterQueue`|<span data-ttu-id="76cdb-119">指定要使用何種寄不出信件佇列類型的 <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> 值 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="76cdb-119">A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> value specifying which type of dead-letter queue to use, if any.</span></span><br /><br /> <span data-ttu-id="76cdb-120">無法傳遞至應用程式的訊息將會被傳輸至寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="76cdb-120">A dead-letter queue is the place where messages that have failed to be delivered to the application will be transferred.</span></span><br /><br /> <span data-ttu-id="76cdb-121">對於需要 `exactlyOnce` 保證的訊息 (也就是 `exactlyOnce` 屬性設定為 `true`)，這個屬性預設為 MSMQ 中的整個系統交易式寄不出信件佇列。</span><span class="sxs-lookup"><span data-stu-id="76cdb-121">For messages that require `exactlyOnce` assurance (that is, the `exactlyOnce` attribute is set to `true`), this attribute defaults to the system-wide transactional dead-letter queue in MSMQ.</span></span><br /><br /> <span data-ttu-id="76cdb-122">對於不需要保證的訊息，這個屬性預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="76cdb-122">For messages that require no assurances, this attribute defaults to `null`.</span></span>|  
|`durable`|<span data-ttu-id="76cdb-123">布林值，指出佇列中的訊息為永久性 (Durable) 或變動性 (Volatile)。</span><span class="sxs-lookup"><span data-stu-id="76cdb-123">A Boolean value that indicates whether the message is durable or volatile in the queue.</span></span> <span data-ttu-id="76cdb-124">永久性的訊息不受佇列管理員毀損的影響，但變動性訊息會受到影響。</span><span class="sxs-lookup"><span data-stu-id="76cdb-124">A durable message survives a queue manager crash, while a volatile message does not.</span></span> <span data-ttu-id="76cdb-125">如果應用程式需要較短的延遲時間，並可以容許訊息偶爾遺失，變動性訊息就很有用。</span><span class="sxs-lookup"><span data-stu-id="76cdb-125">Volatile messages are useful when applications require lower latency and can tolerate occasional lost messages.</span></span> <span data-ttu-id="76cdb-126">如果 `exactlyOnce` 屬性設定為 `true`，則訊息必須為永久性。</span><span class="sxs-lookup"><span data-stu-id="76cdb-126">If the `exactlyOnce` attribute is set to `true`, the messages must be durable.</span></span> <span data-ttu-id="76cdb-127">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="76cdb-127">The default is `true`.</span></span>|  
|`exactlyOnce`|<span data-ttu-id="76cdb-128">布林值，指出此繫結所處理的每個訊息是否只傳遞一次。</span><span class="sxs-lookup"><span data-stu-id="76cdb-128">A Boolean value that indicates whether each message processed by this binding is delivered only once.</span></span> <span data-ttu-id="76cdb-129">接著會通知傳送者傳遞失敗。</span><span class="sxs-lookup"><span data-stu-id="76cdb-129">The sender will then be notified of delivery failures.</span></span> <span data-ttu-id="76cdb-130">`durable` 為 `false` 時，會忽略這個屬性，並傳輸訊息，但不具傳遞保證。</span><span class="sxs-lookup"><span data-stu-id="76cdb-130">When `durable` is `false`, this attribute is ignored and messages are transferred without delivery assurance.</span></span> <span data-ttu-id="76cdb-131">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="76cdb-131">The default is `true`.</span></span> <span data-ttu-id="76cdb-132">如需詳細資訊，請參閱<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>。</span><span class="sxs-lookup"><span data-stu-id="76cdb-132">For more information, see <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="76cdb-133">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="76cdb-133">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="76cdb-134">預設值為 8。</span><span class="sxs-lookup"><span data-stu-id="76cdb-134">The default is 8.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="76cdb-135">正整數，定義此繫結可以處理的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="76cdb-135">A positive integer that defines the maximum message size, in bytes, including headers, that is processed by this binding.</span></span> <span data-ttu-id="76cdb-136">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="76cdb-136">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="76cdb-137">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="76cdb-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="76cdb-138">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="76cdb-138">The default is 65536.</span></span> <span data-ttu-id="76cdb-139">這項關於訊息大小的限制是為了避免受到阻絕服務 (DoS) 攻擊。</span><span class="sxs-lookup"><span data-stu-id="76cdb-139">This bound on message size is intended to limit exposure to Denial of Service (DoS) attacks.</span></span>|  
|`maxRetryCycles`|<span data-ttu-id="76cdb-140">整數，指出有害訊息偵測功能使用的重試循環次數。</span><span class="sxs-lookup"><span data-stu-id="76cdb-140">An integer that indicates the number of retry cycles used by the poison-message detection feature.</span></span> <span data-ttu-id="76cdb-141">當訊息無法在循環的傳遞嘗試中成功傳遞，便成為有害訊息。</span><span class="sxs-lookup"><span data-stu-id="76cdb-141">A message becomes a poison message when it fails all delivery attempts of all cycles.</span></span> <span data-ttu-id="76cdb-142">預設值為 3。</span><span class="sxs-lookup"><span data-stu-id="76cdb-142">The default is 3.</span></span> <span data-ttu-id="76cdb-143">如需詳細資訊，請參閱<xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>。</span><span class="sxs-lookup"><span data-stu-id="76cdb-143">For more information, see <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.</span></span>|  
|`name`|<span data-ttu-id="76cdb-144">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="76cdb-144">Required attribute.</span></span> <span data-ttu-id="76cdb-145">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="76cdb-145">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="76cdb-146">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="76cdb-146">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="76cdb-147">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="76cdb-147">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="76cdb-148">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="76cdb-148">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="76cdb-149"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="76cdb-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="76cdb-150">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="76cdb-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="76cdb-151">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="76cdb-151">The default is 00:01:00.</span></span>|  
|`QueueTransferProtocol`|<span data-ttu-id="76cdb-152">有效的 <xref:System.ServiceModel.QueueTransferProtocol> 值，指定此繫結所使用的佇列通訊通道傳輸。</span><span class="sxs-lookup"><span data-stu-id="76cdb-152">A valid <xref:System.ServiceModel.QueueTransferProtocol> value that specifies the queued communication channel transport that this binding uses.</span></span> <span data-ttu-id="76cdb-153">當使用 SOAP Reliable Messaging Protocol 時，MSMQ 不支援 Active Directory 定址。</span><span class="sxs-lookup"><span data-stu-id="76cdb-153">MSMQ does not support Active Directory addressing when using SOAP Reliable Messaging Protocol.</span></span> <span data-ttu-id="76cdb-154">因此，您應該設定這個屬性`Srmp`或是`Srmps`當`useActiveDirectory`屬性設為`true`。</span><span class="sxs-lookup"><span data-stu-id="76cdb-154">Therefore, you should not set this attribute to `Srmp` or `Srmps` when the `useActiveDirectory` attribute is set to `true`.</span></span>|  
|`receiveErrorHandling`|<span data-ttu-id="76cdb-155"><xref:System.ServiceModel.ReceiveErrorHandling> 值，指定如何處理有害和不可分派的訊息。</span><span class="sxs-lookup"><span data-stu-id="76cdb-155">A <xref:System.ServiceModel.ReceiveErrorHandling> value that specifies how poison and nondispatchable messages are handled.</span></span>|  
|`receiveRetryCount`|<span data-ttu-id="76cdb-156">整數，指定佇列管理員在傳送訊息至重試佇列之前，應嘗試傳送的次數上限。</span><span class="sxs-lookup"><span data-stu-id="76cdb-156">An integer that specifies the maximum number of times the queue manager should attempt to send a message before transferring it to the retry queue.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="76cdb-157"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="76cdb-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="76cdb-158">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="76cdb-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="76cdb-159">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="76cdb-159">The default is 00:10:00.</span></span>|  
|`retryCycleDelay`|<span data-ttu-id="76cdb-160">TimeSpan 值，指定嘗試傳遞無法立即傳遞之訊息時，重試循環之間的時間延遲。</span><span class="sxs-lookup"><span data-stu-id="76cdb-160">A TimeSpan value that specifies the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span> <span data-ttu-id="76cdb-161">該值只定義最小等待時間，因為實際的等待時間會更長。</span><span class="sxs-lookup"><span data-stu-id="76cdb-161">The value defines only the minimum wait time because actual wait time can be longer.</span></span> <span data-ttu-id="76cdb-162">預設值為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="76cdb-162">The default value is 00:10:00.</span></span> <span data-ttu-id="76cdb-163">如需詳細資訊，請參閱<xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>。</span><span class="sxs-lookup"><span data-stu-id="76cdb-163">For more information, see <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.</span></span>|  
|`sendTimeout`|<span data-ttu-id="76cdb-164"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="76cdb-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="76cdb-165">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="76cdb-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="76cdb-166">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="76cdb-166">The default is 00:01:00.</span></span>|  
|`timeToLive`|<span data-ttu-id="76cdb-167">TimeSpan 值，指定訊息在到期並置入寄不出的信件佇列之前，訊息仍保持有效的時間。</span><span class="sxs-lookup"><span data-stu-id="76cdb-167">A TimeSpan value that specifies how long the messages are valid before they are expired and put into the dead-letter queue.</span></span> <span data-ttu-id="76cdb-168">預設為 1.00:00:00。</span><span class="sxs-lookup"><span data-stu-id="76cdb-168">The default is 1.00:00:00.</span></span><br /><br /> <span data-ttu-id="76cdb-169">設定這個屬性可確保有時效的訊息在由接收應用程式處理之前不會變成過時。</span><span class="sxs-lookup"><span data-stu-id="76cdb-169">This attribute is set to ensure that time-sensitive messages do not become stale before they are processed by the receiving applications.</span></span> <span data-ttu-id="76cdb-170">佇列中未由接收應用程式於指定的時間間隔內使用的訊息，即稱為過期訊息。</span><span class="sxs-lookup"><span data-stu-id="76cdb-170">A message in a queue that is not consumed by the receiving application within the time interval specified is said to be expired.</span></span> <span data-ttu-id="76cdb-171">過期訊息會傳送至特別的佇列，稱為寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="76cdb-171">Expired messages are sent to special queue called the dead letter queue.</span></span> <span data-ttu-id="76cdb-172">寄不出的信件佇列的位置是使用 `DeadLetterQueue` 屬性設定，或根據保證設定為適當的預設值。</span><span class="sxs-lookup"><span data-stu-id="76cdb-172">The location of the dead letter queue is set with the `DeadLetterQueue` attribute or to the appropriate default, based on assurances.</span></span>|  
|`usingActiveDirectory`|<span data-ttu-id="76cdb-173">布林值，指定是否應該使用 Active Directory 來轉換佇列位址。</span><span class="sxs-lookup"><span data-stu-id="76cdb-173">A Boolean value that specifies if queue addresses should be converted using Active Directory.</span></span><br /><br /> <span data-ttu-id="76cdb-174">MSMQ 佇列位址可以由路徑名稱或直接格式名稱組成。</span><span class="sxs-lookup"><span data-stu-id="76cdb-174">MSMQ queue addresses can consist of path names or direct format names.</span></span> <span data-ttu-id="76cdb-175">如為直接格式名稱，MSMQ 會使用 DNS、NetBIOS 或 IP 解析電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="76cdb-175">With a direct format name, MSMQ resolves the computer name using DNS, NetBIOS or IP.</span></span> <span data-ttu-id="76cdb-176">如為路徑名稱，MSMQ 會使用 Active Directory 解析電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="76cdb-176">With a path name, MSMQ resolves the computer name using Active Directory.</span></span><br /><br /> <span data-ttu-id="76cdb-177">根據預設，Windows Communication Foundation (WCF) 佇列傳輸會將轉換成直接格式名稱的訊息佇列的 URI。</span><span class="sxs-lookup"><span data-stu-id="76cdb-177">By default, Windows Communication Foundation (WCF) queued transport converts the URI of a message queue to a direct format name.</span></span> <span data-ttu-id="76cdb-178">藉由將 `UseActiveDirectory` 屬性設定為 true，應用程式可以指定佇列傳輸應使用 Active Directory 來解析電腦名稱，而非使用 DNS、NetBIOS 或 IP 來解析。</span><span class="sxs-lookup"><span data-stu-id="76cdb-178">By setting the `UseActiveDirectory` property to true, an application can specify that the queued transport should resolve the computer name using Active Directory rather than DNS, NetBIOS, or IP.</span></span>|  
|`useMsmqTracing`|<span data-ttu-id="76cdb-179">布林值，指定是否應追蹤由此繫結處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="76cdb-179">A Boolean value that specifies whether messages processed by this binding should be traced.</span></span> <span data-ttu-id="76cdb-180">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="76cdb-180">The default is `false`.</span></span> <span data-ttu-id="76cdb-181">如果啟用追蹤，每當訊息離開或到達訊息佇列電腦時，都會建立報告訊息並傳送至報告佇列。</span><span class="sxs-lookup"><span data-stu-id="76cdb-181">When tracing is enabled, report messages are created and sent to the report queue each time the message leaves or arrives at a Message Queuing computer.</span></span>|  
|`useSourceJournal`|<span data-ttu-id="76cdb-182">布林值，指定是否要將此繫結處理之訊息的複本儲存在來源日誌。</span><span class="sxs-lookup"><span data-stu-id="76cdb-182">A Boolean value that specifies copies of messages processed by this binding should be stored in the source journal.</span></span> <span data-ttu-id="76cdb-183">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="76cdb-183">The default is `false`.</span></span><br /><br /> <span data-ttu-id="76cdb-184">有些佇列應用程式要記錄已離開電腦輸出佇列的訊息，這些程式可以將訊息複製到日誌佇列。</span><span class="sxs-lookup"><span data-stu-id="76cdb-184">Queued applications that want to keep a record of messages that have left the computer's outgoing queue can copy the messages to a journal queue.</span></span> <span data-ttu-id="76cdb-185">只要訊息一離開輸出佇列，而且收到目的端電腦已收到訊息的認可，訊息的複本就會保留在傳送端電腦的系統日誌佇列中。</span><span class="sxs-lookup"><span data-stu-id="76cdb-185">Once a message leaves the outgoing queue and an acknowledgment is received that the message was received on the destination computer, a copy of the message is kept in the sending computer's system journal queue.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76cdb-186">子元素</span><span class="sxs-lookup"><span data-stu-id="76cdb-186">Child Elements</span></span>  
  
|<span data-ttu-id="76cdb-187">項目</span><span class="sxs-lookup"><span data-stu-id="76cdb-187">Element</span></span>|<span data-ttu-id="76cdb-188">描述</span><span class="sxs-lookup"><span data-stu-id="76cdb-188">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76cdb-189">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="76cdb-189">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="76cdb-190">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="76cdb-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="76cdb-191">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="76cdb-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="76cdb-192">\<security></span><span class="sxs-lookup"><span data-stu-id="76cdb-192">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="76cdb-193">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="76cdb-193">Defines the security settings for the binding.</span></span> <span data-ttu-id="76cdb-194">此項目的型別為 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="76cdb-194">This element is of type <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76cdb-195">父項目</span><span class="sxs-lookup"><span data-stu-id="76cdb-195">Parent Elements</span></span>  
  
|<span data-ttu-id="76cdb-196">項目</span><span class="sxs-lookup"><span data-stu-id="76cdb-196">Element</span></span>|<span data-ttu-id="76cdb-197">描述</span><span class="sxs-lookup"><span data-stu-id="76cdb-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76cdb-198">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="76cdb-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="76cdb-199">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="76cdb-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76cdb-200">備註</span><span class="sxs-lookup"><span data-stu-id="76cdb-200">Remarks</span></span>  
 <span data-ttu-id="76cdb-201">`netMsmqBinding` 繫結利用 Microsoft Message Queuing (MSMQ) 做為傳輸來提供對於佇列的支援，並可支援結合鬆散的應用程式、失敗隔離、負載撫平和中斷連接作業。</span><span class="sxs-lookup"><span data-stu-id="76cdb-201">The `netMsmqBinding` binding provides support for queuing by leveraging Microsoft Message Queuing (MSMQ) as a transport and enables support for loosely coupled applications, failure isolation, load leveling and disconnected operations.</span></span> <span data-ttu-id="76cdb-202">如需這些功能的討論，請參閱 < [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="76cdb-202">For a discussion of these features, see [Queues in WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76cdb-203">範例</span><span class="sxs-lookup"><span data-stu-id="76cdb-203">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
    <bindings>  
           <netMsmqBinding>  
                <binding   
                         closeTimeout="00:00:10"   
                         openTimeout="00:00:20"   
                         receiveTimeout="00:00:30"  
                         sendTimeout="00:00:40"  
                         deadLetterQueue="net.msmq://localhost/blah"   
                         durable="true"   
                         exactlyOnce="true"   
                         maxReceivedMessageSize="1000"  
                         maxRetries="11"  
                         maxRetryCycles="12"   
                         poisonMessageHandling="Disabled"   
                         rejectAfterLastRetry="false"   
                         retryCycleDelay="00:05:55"   
                         timeToLive="00:11:11"   
                         sourceJournal="true"  
                         useMsmqTracing="true"  
                         useActiveDirectory="true">  
                         <security>  
                             <message clientCredentialType="Windows" />  
                         </security>  
            </netMsmqBinding>  
    </bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76cdb-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76cdb-204">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>  
 [<span data-ttu-id="76cdb-205">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="76cdb-205">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="76cdb-206">繫結</span><span class="sxs-lookup"><span data-stu-id="76cdb-206">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="76cdb-207">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="76cdb-207">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="76cdb-208">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="76cdb-208">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="76cdb-209">WCF 中的佇列</span><span class="sxs-lookup"><span data-stu-id="76cdb-209">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
