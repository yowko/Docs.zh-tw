---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 921da4d0b010672585a045d58d03182e480a255a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140725"
---
# \<netPeerTcpBinding>
<span data-ttu-id="1dfa7-101">為對等通道特定的 TCP 訊息定義繫結。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-101">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="1dfa7-102">語法</span><span class="sxs-lookup"><span data-stu-id="1dfa7-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dfa7-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1dfa7-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1dfa7-104">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="1dfa7-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dfa7-105">屬性</span><span class="sxs-lookup"><span data-stu-id="1dfa7-105">Attributes</span></span>  
  
|<span data-ttu-id="1dfa7-106">屬性</span><span class="sxs-lookup"><span data-stu-id="1dfa7-106">Attribute</span></span>|<span data-ttu-id="1dfa7-107">描述</span><span class="sxs-lookup"><span data-stu-id="1dfa7-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1dfa7-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="1dfa7-108">closeTimeout</span></span>|<span data-ttu-id="1dfa7-109"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1dfa7-110">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1dfa7-111">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-111">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="1dfa7-112">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="1dfa7-112">listenIPAddress</span></span>|<span data-ttu-id="1dfa7-113">字串，指定對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-113">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="1dfa7-114">預設值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-114">The default is `null`.</span></span>|  
|<span data-ttu-id="1dfa7-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="1dfa7-115">maxBufferPoolSize</span></span>|<span data-ttu-id="1dfa7-116">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-116">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="1dfa7-117">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="1dfa7-118">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="1dfa7-119">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="1dfa7-120">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="1dfa7-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="1dfa7-121">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="1dfa7-122">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="1dfa7-122">maxReceivedMessageSize</span></span>|<span data-ttu-id="1dfa7-123">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-123">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="1dfa7-124">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-124">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="1dfa7-125">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1dfa7-126">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-126">The default is 65536.</span></span>|  
|<span data-ttu-id="1dfa7-127">NAME</span><span class="sxs-lookup"><span data-stu-id="1dfa7-127">name</span></span>|<span data-ttu-id="1dfa7-128">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1dfa7-129">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1dfa7-130">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1dfa7-131">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="1dfa7-132">openTimeout</span><span class="sxs-lookup"><span data-stu-id="1dfa7-132">openTimeout</span></span>|<span data-ttu-id="1dfa7-133"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1dfa7-134">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1dfa7-135">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-135">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="1dfa7-136">連接埠</span><span class="sxs-lookup"><span data-stu-id="1dfa7-136">port</span></span>|<span data-ttu-id="1dfa7-137">整數，指定這個繫結處理對等通道 TCP 訊息的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-137">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="1dfa7-138">這個值必須介於 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之間。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-138">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="1dfa7-139">預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-139">The default is 0.</span></span>|  
|<span data-ttu-id="1dfa7-140">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="1dfa7-140">receiveTimeout</span></span>|<span data-ttu-id="1dfa7-141"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1dfa7-142">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1dfa7-143">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-143">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="1dfa7-144">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="1dfa7-144">sendTimeout</span></span>|<span data-ttu-id="1dfa7-145"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1dfa7-146">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1dfa7-147">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-147">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1dfa7-148">子元素</span><span class="sxs-lookup"><span data-stu-id="1dfa7-148">Child Elements</span></span>  
  
|<span data-ttu-id="1dfa7-149">元素</span><span class="sxs-lookup"><span data-stu-id="1dfa7-149">Element</span></span>|<span data-ttu-id="1dfa7-150">描述</span><span class="sxs-lookup"><span data-stu-id="1dfa7-150">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="1dfa7-151">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-151">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1dfa7-152">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-152">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="1dfa7-153">指定這個繫結使用的對等解析程式，將對等網狀結構 ID 解析為對等網狀結構內節點的端點 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-153">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="1dfa7-154">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-154">Defines the security settings for the message.</span></span> <span data-ttu-id="1dfa7-155">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-155">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1dfa7-156">父項目</span><span class="sxs-lookup"><span data-stu-id="1dfa7-156">Parent Elements</span></span>  
  
|<span data-ttu-id="1dfa7-157">元素</span><span class="sxs-lookup"><span data-stu-id="1dfa7-157">Element</span></span>|<span data-ttu-id="1dfa7-158">描述</span><span class="sxs-lookup"><span data-stu-id="1dfa7-158">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="1dfa7-159">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dfa7-160">備註</span><span class="sxs-lookup"><span data-stu-id="1dfa7-160">Remarks</span></span>  
 <span data-ttu-id="1dfa7-161">這個繫結使用透過 TCP 的對等傳輸，藉此支援對等或多方應用程式的建立。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-161">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="1dfa7-162">每個對等節點都可以裝載多個以這個繫結類型所定義的對等通道。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-162">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dfa7-163">範例</span><span class="sxs-lookup"><span data-stu-id="1dfa7-163">Example</span></span>  
 <span data-ttu-id="1dfa7-164">下列範例示範使用 NetPeerTcpBinding 繫結，此繫結會使用對等通道提供多方通訊。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-164">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="1dfa7-165">如需使用此系結的詳細案例，請參閱[Net 對等 TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="1dfa7-165">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1dfa7-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dfa7-166">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="1dfa7-167">繫結</span><span class="sxs-lookup"><span data-stu-id="1dfa7-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1dfa7-168">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="1dfa7-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1dfa7-169">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="1dfa7-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="1dfa7-170">[網路對等 TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1dfa7-170">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="1dfa7-171">對等網路</span><span class="sxs-lookup"><span data-stu-id="1dfa7-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
