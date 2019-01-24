---
title: '&lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 045d5649ae7f59087eacd035d7be09d0024b6fd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725658"
---
# <a name="ltnetpeertcpbindinggt"></a><span data-ttu-id="e169a-102">&lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e169a-102">&lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="e169a-103">為對等通道特定的 TCP 訊息定義繫結。</span><span class="sxs-lookup"><span data-stu-id="e169a-103">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="e169a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e169a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e169a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e169a-105">\<bindings></span></span>  
<span data-ttu-id="e169a-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="e169a-106">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e169a-107">語法</span><span class="sxs-lookup"><span data-stu-id="e169a-107">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding name="string"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           listenIPAddress="String"
           maxBufferPoolSize="integer"
           maxReceiveMessageSize="Integer"
           port="Integer">
    <security mode="None/Transport/Message/TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e169a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e169a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e169a-109">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="e169a-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e169a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e169a-110">Attributes</span></span>  
  
|<span data-ttu-id="e169a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e169a-111">Attribute</span></span>|<span data-ttu-id="e169a-112">描述</span><span class="sxs-lookup"><span data-stu-id="e169a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e169a-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="e169a-113">closeTimeout</span></span>|<span data-ttu-id="e169a-114"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="e169a-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e169a-115">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e169a-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e169a-116">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="e169a-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e169a-117">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="e169a-117">listenIPAddress</span></span>|<span data-ttu-id="e169a-118">字串，指定對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e169a-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="e169a-119">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="e169a-119">The default is `null`.</span></span>|  
|<span data-ttu-id="e169a-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="e169a-120">maxBufferPoolSize</span></span>|<span data-ttu-id="e169a-121">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="e169a-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="e169a-122">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="e169a-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="e169a-123">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e169a-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="e169a-124">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="e169a-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="e169a-125">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="e169a-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="e169a-126">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="e169a-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="e169a-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="e169a-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="e169a-128">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="e169a-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="e169a-129">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="e169a-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="e169a-130">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="e169a-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e169a-131">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="e169a-131">The default is 65536.</span></span>|  
|<span data-ttu-id="e169a-132">name</span><span class="sxs-lookup"><span data-stu-id="e169a-132">name</span></span>|<span data-ttu-id="e169a-133">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="e169a-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e169a-134">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="e169a-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e169a-135">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="e169a-135">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e169a-136">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e169a-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="e169a-137">openTimeout</span><span class="sxs-lookup"><span data-stu-id="e169a-137">openTimeout</span></span>|<span data-ttu-id="e169a-138"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="e169a-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e169a-139">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e169a-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e169a-140">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="e169a-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="e169a-141">連接埠</span><span class="sxs-lookup"><span data-stu-id="e169a-141">port</span></span>|<span data-ttu-id="e169a-142">整數，指定這個繫結處理對等通道 TCP 訊息的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="e169a-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="e169a-143">這個值必須介於 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之間。</span><span class="sxs-lookup"><span data-stu-id="e169a-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="e169a-144">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="e169a-144">The default is 0.</span></span>|  
|<span data-ttu-id="e169a-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="e169a-145">receiveTimeout</span></span>|<span data-ttu-id="e169a-146"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="e169a-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e169a-147">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e169a-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e169a-148">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="e169a-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="e169a-149">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="e169a-149">sendTimeout</span></span>|<span data-ttu-id="e169a-150"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="e169a-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e169a-151">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e169a-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e169a-152">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="e169a-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e169a-153">子元素</span><span class="sxs-lookup"><span data-stu-id="e169a-153">Child Elements</span></span>  
  
|<span data-ttu-id="e169a-154">項目</span><span class="sxs-lookup"><span data-stu-id="e169a-154">Element</span></span>|<span data-ttu-id="e169a-155">描述</span><span class="sxs-lookup"><span data-stu-id="e169a-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e169a-156">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="e169a-156">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="e169a-157">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="e169a-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="e169a-158">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="e169a-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="e169a-159">\<resolver></span><span class="sxs-lookup"><span data-stu-id="e169a-159">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="e169a-160">指定這個繫結使用的對等解析程式，將對等網狀結構 ID 解析為對等網狀結構內節點的端點 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e169a-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="e169a-161">\<security></span><span class="sxs-lookup"><span data-stu-id="e169a-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="e169a-162">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="e169a-162">Defines the security settings for the message.</span></span> <span data-ttu-id="e169a-163">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="e169a-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e169a-164">父項目</span><span class="sxs-lookup"><span data-stu-id="e169a-164">Parent Elements</span></span>  
  
|<span data-ttu-id="e169a-165">項目</span><span class="sxs-lookup"><span data-stu-id="e169a-165">Element</span></span>|<span data-ttu-id="e169a-166">描述</span><span class="sxs-lookup"><span data-stu-id="e169a-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e169a-167">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e169a-167">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="e169a-168">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="e169a-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e169a-169">備註</span><span class="sxs-lookup"><span data-stu-id="e169a-169">Remarks</span></span>  
 <span data-ttu-id="e169a-170">這個繫結使用透過 TCP 的對等傳輸，藉此支援對等或多方應用程式的建立。</span><span class="sxs-lookup"><span data-stu-id="e169a-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="e169a-171">每個對等節點都可以裝載多個以這個繫結類型所定義的對等通道。</span><span class="sxs-lookup"><span data-stu-id="e169a-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e169a-172">範例</span><span class="sxs-lookup"><span data-stu-id="e169a-172">Example</span></span>  
 <span data-ttu-id="e169a-173">下列範例示範使用 NetPeerTcpBinding 繫結，此繫結會使用對等通道提供多方通訊。</span><span class="sxs-lookup"><span data-stu-id="e169a-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="e169a-174">使用這個繫結的詳細案例，請參閱[Net 的對等 TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)。</span><span class="sxs-lookup"><span data-stu-id="e169a-174">For a detailed scenario of using this binding, see [Net Peer TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netPeerBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 maxBufferSize="1001"
                 maxConnections="123"
                 maxReceiveMessageSize="1000">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="TransportWithMessageCredential">
            <message clientCredentialType="CardSpace" />
          </security>
        </binding>
      </netPeerBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="e169a-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e169a-175">See also</span></span>
- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="e169a-176">繫結</span><span class="sxs-lookup"><span data-stu-id="e169a-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e169a-177">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e169a-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e169a-178">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="e169a-178">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e169a-179">\<binding></span><span class="sxs-lookup"><span data-stu-id="e169a-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="e169a-180">網路對等 TCP</span><span class="sxs-lookup"><span data-stu-id="e169a-180">Net Peer TCP</span></span>](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)
- [<span data-ttu-id="e169a-181">對等網路</span><span class="sxs-lookup"><span data-stu-id="e169a-181">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
