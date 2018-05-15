---
title: '&lt;netTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: f6cbdbb7c5569851055102cfe5d413e0b94376f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltnettcpbindinggt"></a><span data-ttu-id="2e27b-102">&lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="2e27b-102">&lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="2e27b-103">指定一個適用於跨電腦通訊的安全、可靠且最佳化的繫結。</span><span class="sxs-lookup"><span data-stu-id="2e27b-103">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="2e27b-104">根據預設，會產生具備 Windows 安全性 (提供訊息安全性和驗證)、TCP (進行訊息傳遞) 和二進位訊息編碼的執行階段通訊堆疊。</span><span class="sxs-lookup"><span data-stu-id="2e27b-104">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="2e27b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2e27b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2e27b-106">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2e27b-106">\<bindings></span></span>  
<span data-ttu-id="2e27b-107">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="2e27b-107">\<netTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e27b-108">語法</span><span class="sxs-lookup"><span data-stu-id="2e27b-108">Syntax</span></span>  
  
```xml  
<netTcpBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      maxBufferPoolSize="integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
      name="string"  
      openTimeout="TimeSpan"  
      portSharingEnabled="Boolean"  
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"   
      transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"   
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
  
      <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan"  
            enabled="Boolean" />  
      <security mode="None/Transport/Message/Both">  
            <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                defaultProtectionLevel="None/Sign/EncryptAndSign"   
algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
            <transport clientCredentialType="None/Windows/Certificate"  
                protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e27b-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2e27b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2e27b-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2e27b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e27b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2e27b-111">Attributes</span></span>  
  
|<span data-ttu-id="2e27b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2e27b-112">Attribute</span></span>|<span data-ttu-id="2e27b-113">描述</span><span class="sxs-lookup"><span data-stu-id="2e27b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2e27b-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="2e27b-114">closeTimeout</span></span>|<span data-ttu-id="2e27b-115"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="2e27b-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="2e27b-116">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="2e27b-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2e27b-117">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="2e27b-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="2e27b-118">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="2e27b-118">hostnameComparisonMode</span></span>|<span data-ttu-id="2e27b-119">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="2e27b-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="2e27b-120">這個屬性的型別為 `System.ServiceModel.HostnameComparisonMode`，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="2e27b-120">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="2e27b-121">預設值為 `StrongWildcard`，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="2e27b-121">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="2e27b-122">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="2e27b-122">listenBacklog</span></span>|<span data-ttu-id="2e27b-123">正整數，指定在接聽程式上等待接受的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="2e27b-123">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="2e27b-124">超過這個限制的連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="2e27b-124">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="2e27b-125">`connectionTimeout` 屬性會限制用戶端在擲回連線例外狀況之前，等待連線的時間。</span><span class="sxs-lookup"><span data-stu-id="2e27b-125">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="2e27b-126">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="2e27b-126">The default is 10.</span></span>|  
|<span data-ttu-id="2e27b-127">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="2e27b-127">maxBufferPoolSize</span></span>|<span data-ttu-id="2e27b-128">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="2e27b-128">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="2e27b-129">預設為 512 \* 1024 個位元組。</span><span class="sxs-lookup"><span data-stu-id="2e27b-129">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="2e27b-130">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2e27b-130">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="2e27b-131">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="2e27b-131">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="2e27b-132">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="2e27b-132">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="2e27b-133">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="2e27b-133">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="2e27b-134">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="2e27b-134">maxBufferSize</span></span>|<span data-ttu-id="2e27b-135">正整數，指定記憶體中用來儲存訊息的緩衝區大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="2e27b-135">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="2e27b-136">如果 `transferMode` 屬性等於 `Buffered`，則此屬性應該等於 `maxReceivedMessageSize` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="2e27b-136">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="2e27b-137">如果 `transferMode` 屬性等於 `Streamed`，則此屬性不能超過 `maxReceivedMessageSize` 屬性值，並且應該至少為標頭的大小。</span><span class="sxs-lookup"><span data-stu-id="2e27b-137">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="2e27b-138">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="2e27b-138">The default is 65536.</span></span> <span data-ttu-id="2e27b-139">如需詳細資訊，請參閱<xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>。</span><span class="sxs-lookup"><span data-stu-id="2e27b-139">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="2e27b-140">maxConnections</span><span class="sxs-lookup"><span data-stu-id="2e27b-140">maxConnections</span></span>|<span data-ttu-id="2e27b-141">整數，指定服務建立/接受的傳出和傳入連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="2e27b-141">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="2e27b-142">傳入和傳出連線是依據此屬性指定的個別限制來計算的。</span><span class="sxs-lookup"><span data-stu-id="2e27b-142">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="2e27b-143">超過限制的傳入連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="2e27b-143">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="2e27b-144">超過限制的傳出連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="2e27b-144">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="2e27b-145">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="2e27b-145">The default is 10.</span></span>|  
|<span data-ttu-id="2e27b-146">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="2e27b-146">maxReceivedMessageSize</span></span>|<span data-ttu-id="2e27b-147">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="2e27b-147">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="2e27b-148">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e27b-148">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="2e27b-149">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="2e27b-149">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="2e27b-150">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="2e27b-150">The default is 65536.</span></span>|  
|<span data-ttu-id="2e27b-151">name</span><span class="sxs-lookup"><span data-stu-id="2e27b-151">name</span></span>|<span data-ttu-id="2e27b-152">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="2e27b-152">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="2e27b-153">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="2e27b-153">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="2e27b-154">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="2e27b-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2e27b-155">如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2e27b-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="2e27b-156">openTimeout</span><span class="sxs-lookup"><span data-stu-id="2e27b-156">openTimeout</span></span>|<span data-ttu-id="2e27b-157"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="2e27b-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="2e27b-158">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="2e27b-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2e27b-159">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="2e27b-159">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="2e27b-160">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="2e27b-160">portSharingEnabled</span></span>|<span data-ttu-id="2e27b-161">布林值，這個值指定是否為此連線啟用 TCP 連接埠共用。</span><span class="sxs-lookup"><span data-stu-id="2e27b-161">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="2e27b-162">如果這是 `false`，則每個繫結使用它自己的獨佔連接埠。</span><span class="sxs-lookup"><span data-stu-id="2e27b-162">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="2e27b-163">這個設定只與服務有關，因為用戶端未受影響。</span><span class="sxs-lookup"><span data-stu-id="2e27b-163">This setting is relevant only to services, because clients are not affected.</span></span>|  
|<span data-ttu-id="2e27b-164">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="2e27b-164">receiveTimeout</span></span>|<span data-ttu-id="2e27b-165"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="2e27b-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="2e27b-166">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="2e27b-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2e27b-167">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="2e27b-167">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="2e27b-168">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="2e27b-168">sendTimeout</span></span>|<span data-ttu-id="2e27b-169"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="2e27b-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="2e27b-170">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="2e27b-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2e27b-171">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="2e27b-171">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="2e27b-172">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="2e27b-172">transactionFlow</span></span>|<span data-ttu-id="2e27b-173">指定繫結是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="2e27b-173">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="2e27b-174">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="2e27b-174">The default is `false`.</span></span>|  
|<span data-ttu-id="2e27b-175">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="2e27b-175">transactionProtocol</span></span>|<span data-ttu-id="2e27b-176">指定要搭配此繫結使用的交易通訊協定。</span><span class="sxs-lookup"><span data-stu-id="2e27b-176">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="2e27b-177">有效值為</span><span class="sxs-lookup"><span data-stu-id="2e27b-177">Valid values are</span></span><br /><br /> <span data-ttu-id="2e27b-178">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="2e27b-178">-   OleTransactions</span></span><br /><span data-ttu-id="2e27b-179">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="2e27b-179">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="2e27b-180">預設值為 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="2e27b-180">The default is OleTransactions.</span></span> <span data-ttu-id="2e27b-181">此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="2e27b-181">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="2e27b-182">transferMode</span><span class="sxs-lookup"><span data-stu-id="2e27b-182">transferMode</span></span>|<span data-ttu-id="2e27b-183"><xref:System.ServiceModel.TransferMode> 值，指定訊息要經過緩衝處理或資料流處理，或為要求或回應。</span><span class="sxs-lookup"><span data-stu-id="2e27b-183">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e27b-184">子項目</span><span class="sxs-lookup"><span data-stu-id="2e27b-184">Child Elements</span></span>  
  
|<span data-ttu-id="2e27b-185">項目</span><span class="sxs-lookup"><span data-stu-id="2e27b-185">Element</span></span>|<span data-ttu-id="2e27b-186">描述</span><span class="sxs-lookup"><span data-stu-id="2e27b-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e27b-187">\<security></span><span class="sxs-lookup"><span data-stu-id="2e27b-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="2e27b-188">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="2e27b-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="2e27b-189">此項目的型別為 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="2e27b-189">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[<span data-ttu-id="2e27b-190">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="2e27b-190">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="2e27b-191">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="2e27b-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2e27b-192">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="2e27b-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="2e27b-193">reliableSession</span><span class="sxs-lookup"><span data-stu-id="2e27b-193">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="2e27b-194">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="2e27b-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e27b-195">父項目</span><span class="sxs-lookup"><span data-stu-id="2e27b-195">Parent Elements</span></span>  
  
|<span data-ttu-id="2e27b-196">項目</span><span class="sxs-lookup"><span data-stu-id="2e27b-196">Element</span></span>|<span data-ttu-id="2e27b-197">描述</span><span class="sxs-lookup"><span data-stu-id="2e27b-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e27b-198">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2e27b-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="2e27b-199">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="2e27b-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e27b-200">備註</span><span class="sxs-lookup"><span data-stu-id="2e27b-200">Remarks</span></span>  
 <span data-ttu-id="2e27b-201">根據預設，這個繫結會產生執行階段通訊堆疊，它會使用傳輸安全、TCP 進行訊息傳遞，以及二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="2e27b-201">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="2e27b-202">這個繫結是適當 Windows Communication Foundation (WCF) 系統提供的現成選擇在內部網路進行通訊。</span><span class="sxs-lookup"><span data-stu-id="2e27b-202">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="2e27b-203">`netTcpBinding` 的預設組態較 `wsHttpBinding` 所提供的組態還快，不過它只是用來進行 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 對 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 通訊。</span><span class="sxs-lookup"><span data-stu-id="2e27b-203">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]-to-[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] communication.</span></span> <span data-ttu-id="2e27b-204">安全性行為可以使用選擇性的 `securityMode` 屬性進行設定。</span><span class="sxs-lookup"><span data-stu-id="2e27b-204">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="2e27b-205">您可以使用選擇性的 `reliableSessionEnabled` 屬性，設定是否要使用 WS-ReliableMessaging。</span><span class="sxs-lookup"><span data-stu-id="2e27b-205">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="2e27b-206">不過可信賴傳訊預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="2e27b-206">But reliable messaging is off by default.</span></span> <span data-ttu-id="2e27b-207">較常見地，HTTP 系統提供繫結，例如 `wsHttpBinding` 及 `basicHttpBinding` 設定好可預設啟動，而 `netTcpBinding` 繫結則預設關閉，因此必須 Opt-In 以尋求支援，例如 WS-\* 規格其中一個。</span><span class="sxs-lookup"><span data-stu-id="2e27b-207">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="2e27b-208">這意味著預設的 TCP 組態在端點間交換訊息的速度，比預設針對 HTTP 繫結所設定的速度還快。</span><span class="sxs-lookup"><span data-stu-id="2e27b-208">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e27b-209">範例</span><span class="sxs-lookup"><span data-stu-id="2e27b-209">Example</span></span>  
 <span data-ttu-id="2e27b-210">用戶端和服務的組態檔中會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="2e27b-210">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="2e27b-211">繫結型別是在 `binding` 項目的 `<endpoint>` 屬性中指定。</span><span class="sxs-lookup"><span data-stu-id="2e27b-211">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="2e27b-212">如果您要設定 netTcpBinding 繫結，並變更其部分設定，則必須定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="2e27b-212">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="2e27b-213">端點必須參考含有 `bindingConfiguration` 屬性的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="2e27b-213">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="2e27b-214">下列範例會定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="2e27b-214">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
    <endpoint address=""  
              binding="netTcpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
  
<bindings>  
  <netTcpBinding>  
    <binding   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             listenBacklog="10"  
             maxBufferPoolSize="524288"   
             maxBufferSize="65536"   
             maxConnections="10"  
             maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32"   
                    maxStringContentLength="8192"   
                    maxArrayLength="16384"  
                    maxBytesPerRead="4096"   
                    maxNameTableCharCount="16384" />  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e27b-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e27b-215">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement>  
 [<span data-ttu-id="2e27b-216">繫結</span><span class="sxs-lookup"><span data-stu-id="2e27b-216">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2e27b-217">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="2e27b-217">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2e27b-218">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="2e27b-218">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2e27b-219">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2e27b-219">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
