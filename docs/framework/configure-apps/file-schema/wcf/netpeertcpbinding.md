---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: a039e805bc4378582d7a7bcf6ef84591ec3d2b6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261434"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="592a1-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="592a1-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="592a1-102">為對等通道特定的 TCP 訊息定義繫結。</span><span class="sxs-lookup"><span data-stu-id="592a1-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="592a1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="592a1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="592a1-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="592a1-104">\<bindings></span></span>  
<span data-ttu-id="592a1-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="592a1-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="592a1-106">語法</span><span class="sxs-lookup"><span data-stu-id="592a1-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="592a1-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="592a1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="592a1-108">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="592a1-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="592a1-109">屬性</span><span class="sxs-lookup"><span data-stu-id="592a1-109">Attributes</span></span>  
  
|<span data-ttu-id="592a1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="592a1-110">Attribute</span></span>|<span data-ttu-id="592a1-111">描述</span><span class="sxs-lookup"><span data-stu-id="592a1-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="592a1-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="592a1-112">closeTimeout</span></span>|<span data-ttu-id="592a1-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="592a1-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="592a1-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="592a1-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="592a1-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="592a1-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="592a1-116">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="592a1-116">listenIPAddress</span></span>|<span data-ttu-id="592a1-117">字串，指定對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="592a1-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="592a1-118">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="592a1-118">The default is `null`.</span></span>|  
|<span data-ttu-id="592a1-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="592a1-119">maxBufferPoolSize</span></span>|<span data-ttu-id="592a1-120">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="592a1-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="592a1-121">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="592a1-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="592a1-122">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="592a1-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="592a1-123">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="592a1-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="592a1-124">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="592a1-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="592a1-125">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="592a1-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="592a1-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="592a1-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="592a1-127">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="592a1-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="592a1-128">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="592a1-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="592a1-129">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="592a1-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="592a1-130">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="592a1-130">The default is 65536.</span></span>|  
|<span data-ttu-id="592a1-131">name</span><span class="sxs-lookup"><span data-stu-id="592a1-131">name</span></span>|<span data-ttu-id="592a1-132">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="592a1-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="592a1-133">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="592a1-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="592a1-134">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="592a1-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="592a1-135">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="592a1-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="592a1-136">openTimeout</span><span class="sxs-lookup"><span data-stu-id="592a1-136">openTimeout</span></span>|<span data-ttu-id="592a1-137"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="592a1-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="592a1-138">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="592a1-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="592a1-139">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="592a1-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="592a1-140">連接埠</span><span class="sxs-lookup"><span data-stu-id="592a1-140">port</span></span>|<span data-ttu-id="592a1-141">整數，指定這個繫結處理對等通道 TCP 訊息的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="592a1-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="592a1-142">這個值必須介於 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之間。</span><span class="sxs-lookup"><span data-stu-id="592a1-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="592a1-143">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="592a1-143">The default is 0.</span></span>|  
|<span data-ttu-id="592a1-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="592a1-144">receiveTimeout</span></span>|<span data-ttu-id="592a1-145"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="592a1-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="592a1-146">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="592a1-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="592a1-147">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="592a1-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="592a1-148">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="592a1-148">sendTimeout</span></span>|<span data-ttu-id="592a1-149"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="592a1-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="592a1-150">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="592a1-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="592a1-151">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="592a1-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="592a1-152">子元素</span><span class="sxs-lookup"><span data-stu-id="592a1-152">Child Elements</span></span>  
  
|<span data-ttu-id="592a1-153">項目</span><span class="sxs-lookup"><span data-stu-id="592a1-153">Element</span></span>|<span data-ttu-id="592a1-154">描述</span><span class="sxs-lookup"><span data-stu-id="592a1-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="592a1-155">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="592a1-155">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="592a1-156">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="592a1-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="592a1-157">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="592a1-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="592a1-158">\<resolver></span><span class="sxs-lookup"><span data-stu-id="592a1-158">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="592a1-159">指定這個繫結使用的對等解析程式，將對等網狀結構 ID 解析為對等網狀結構內節點的端點 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="592a1-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="592a1-160">\<security></span><span class="sxs-lookup"><span data-stu-id="592a1-160">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="592a1-161">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="592a1-161">Defines the security settings for the message.</span></span> <span data-ttu-id="592a1-162">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="592a1-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="592a1-163">父項目</span><span class="sxs-lookup"><span data-stu-id="592a1-163">Parent Elements</span></span>  
  
|<span data-ttu-id="592a1-164">項目</span><span class="sxs-lookup"><span data-stu-id="592a1-164">Element</span></span>|<span data-ttu-id="592a1-165">描述</span><span class="sxs-lookup"><span data-stu-id="592a1-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="592a1-166">\<bindings></span><span class="sxs-lookup"><span data-stu-id="592a1-166">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="592a1-167">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="592a1-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="592a1-168">備註</span><span class="sxs-lookup"><span data-stu-id="592a1-168">Remarks</span></span>  
 <span data-ttu-id="592a1-169">這個繫結使用透過 TCP 的對等傳輸，藉此支援對等或多方應用程式的建立。</span><span class="sxs-lookup"><span data-stu-id="592a1-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="592a1-170">每個對等節點都可以裝載多個以這個繫結類型所定義的對等通道。</span><span class="sxs-lookup"><span data-stu-id="592a1-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="592a1-171">範例</span><span class="sxs-lookup"><span data-stu-id="592a1-171">Example</span></span>  
 <span data-ttu-id="592a1-172">下列範例示範使用 NetPeerTcpBinding 繫結，此繫結會使用對等通道提供多方通訊。</span><span class="sxs-lookup"><span data-stu-id="592a1-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="592a1-173">使用這個繫結的詳細案例，請參閱[Net 的對等 TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)。</span><span class="sxs-lookup"><span data-stu-id="592a1-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="592a1-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="592a1-174">See also</span></span>
- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="592a1-175">繫結</span><span class="sxs-lookup"><span data-stu-id="592a1-175">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="592a1-176">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="592a1-176">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="592a1-177">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="592a1-177">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="592a1-178">\<binding></span><span class="sxs-lookup"><span data-stu-id="592a1-178">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="592a1-179">網路對等 TCP</span><span class="sxs-lookup"><span data-stu-id="592a1-179">Net Peer TCP</span></span>](https://msdn.microsoft.com/library/31f4db66-edb2-40a6-b92a-14098e92acae)
- [<span data-ttu-id="592a1-180">對等網路</span><span class="sxs-lookup"><span data-stu-id="592a1-180">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
