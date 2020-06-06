---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: c43c141093c8287adb6d5a841a43ac893deefccd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139338"
---
# \<netTcpBinding>

<span data-ttu-id="8c0bc-101">指定一個適用於跨電腦通訊的安全、可靠且最佳化的繫結。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-101">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="8c0bc-102">根據預設，會產生具備 Windows 安全性 (提供訊息安全性和驗證)、TCP (進行訊息傳遞) 和二進位訊息編碼的執行階段通訊堆疊。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-102">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="8c0bc-103">語法</span><span class="sxs-lookup"><span data-stu-id="8c0bc-103">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
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
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c0bc-104">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="8c0bc-104">Attributes and elements</span></span>

<span data-ttu-id="8c0bc-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c0bc-106">屬性</span><span class="sxs-lookup"><span data-stu-id="8c0bc-106">Attributes</span></span>  
  
|<span data-ttu-id="8c0bc-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8c0bc-107">Attribute</span></span>|<span data-ttu-id="8c0bc-108">描述</span><span class="sxs-lookup"><span data-stu-id="8c0bc-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="8c0bc-109"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="8c0bc-110">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8c0bc-111">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-111">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="8c0bc-112">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-112">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="8c0bc-113">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-113">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="8c0bc-114">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-114">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="8c0bc-115">正整數，指定在接聽程式上等待接受的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-115">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="8c0bc-116">超過這個限制的連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-116">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="8c0bc-117">`connectionTimeout` 屬性會限制用戶端在擲回連線例外狀況之前，等待連線的時間。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-117">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="8c0bc-118">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-118">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="8c0bc-119">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-119">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="8c0bc-120">預設為 512 \* 1024 個位元組。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-120">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="8c0bc-121">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-121">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="8c0bc-122">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="8c0bc-123">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="8c0bc-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="8c0bc-124">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="8c0bc-125">正整數，指定記憶體中用來儲存訊息的緩衝區大小上限 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-125">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="8c0bc-126">如果 `transferMode` 屬性等於 `Buffered`，則此屬性應該等於 `maxReceivedMessageSize` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-126">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="8c0bc-127">如果 `transferMode` 屬性等於 `Streamed`，則此屬性不能超過 `maxReceivedMessageSize` 屬性值，並且應該至少為標頭的大小。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-127">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="8c0bc-128">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-128">The default is 65536.</span></span> <span data-ttu-id="8c0bc-129">如需詳細資訊，請參閱 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A> 。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-129">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="8c0bc-130">整數，指定服務建立/接受的傳出和傳入連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-130">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="8c0bc-131">傳入和傳出連線是依據此屬性指定的個別限制來計算的。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-131">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="8c0bc-132">超過限制的傳入連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-132">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="8c0bc-133">超過限制的傳出連線都會排入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-133">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="8c0bc-134">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-134">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="8c0bc-135">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-135">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="8c0bc-136">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-136">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="8c0bc-137">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="8c0bc-138">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-138">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="8c0bc-139">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-139">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="8c0bc-140">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-140">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="8c0bc-141">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-141">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="8c0bc-142">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-142">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="8c0bc-143"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-143">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="8c0bc-144">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-144">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8c0bc-145">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-145">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="8c0bc-146">布林值，這個值指定是否為此連線啟用 TCP 連接埠共用。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-146">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="8c0bc-147">如果這是 `false`，則每個繫結使用它自己的獨佔連接埠。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-147">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="8c0bc-148">這個設定只與服務有關，因為用戶端未受影響。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-148">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="8c0bc-149"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="8c0bc-150">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8c0bc-151">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="8c0bc-152"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="8c0bc-153">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8c0bc-154">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-154">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="8c0bc-155">指定繫結程序是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-155">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="8c0bc-156">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-156">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="8c0bc-157">指定要搭配此繫結程序使用的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-157">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="8c0bc-158">有效值為</span><span class="sxs-lookup"><span data-stu-id="8c0bc-158">Valid values are</span></span><br /><br /> <span data-ttu-id="8c0bc-159">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="8c0bc-159">-   OleTransactions</span></span><br /><span data-ttu-id="8c0bc-160">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="8c0bc-160">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="8c0bc-161">預設值為 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-161">The default is OleTransactions.</span></span> <span data-ttu-id="8c0bc-162">此屬性的型別為 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-162">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="8c0bc-163"><xref:System.ServiceModel.TransferMode> 值，指定訊息要經過緩衝處理或資料流處理，或為要求或回應。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-163">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c0bc-164">子元素</span><span class="sxs-lookup"><span data-stu-id="8c0bc-164">Child elements</span></span>  
  
|<span data-ttu-id="8c0bc-165">元素</span><span class="sxs-lookup"><span data-stu-id="8c0bc-165">Element</span></span>|<span data-ttu-id="8c0bc-166">描述</span><span class="sxs-lookup"><span data-stu-id="8c0bc-166">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="8c0bc-167">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-167">Defines the security settings for the binding.</span></span> <span data-ttu-id="8c0bc-168">此項目的型別為 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-168">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="8c0bc-169">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-169">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8c0bc-170">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-170">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="8c0bc-171">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-171">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c0bc-172">父元素</span><span class="sxs-lookup"><span data-stu-id="8c0bc-172">Parent elements</span></span>  
  
|<span data-ttu-id="8c0bc-173">元素</span><span class="sxs-lookup"><span data-stu-id="8c0bc-173">Element</span></span>|<span data-ttu-id="8c0bc-174">描述</span><span class="sxs-lookup"><span data-stu-id="8c0bc-174">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="8c0bc-175">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-175">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c0bc-176">備註</span><span class="sxs-lookup"><span data-stu-id="8c0bc-176">Remarks</span></span>

<span data-ttu-id="8c0bc-177">根據預設，這個繫結會產生執行階段通訊堆疊，它會使用傳輸安全、TCP 進行訊息傳遞，以及二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-177">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="8c0bc-178">這個系結是適當的 Windows Communication Foundation （WCF）系統提供的選項，可透過內部網路進行通訊。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-178">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="8c0bc-179">的預設設定比所 `netTcpBinding` 提供的設定快 `wsHttpBinding` ，但僅供 WCF 通訊使用。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-179">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="8c0bc-180">安全性行為可以使用選擇性的 `securityMode` 屬性進行設定。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-180">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="8c0bc-181">您可以使用選擇性的 `reliableSessionEnabled` 屬性，設定是否要使用 WS-ReliableMessaging。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-181">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="8c0bc-182">不過可信賴傳訊預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-182">But reliable messaging is off by default.</span></span> <span data-ttu-id="8c0bc-183">較常見地，HTTP 系統提供繫結，例如 `wsHttpBinding` 及 `basicHttpBinding` 設定好可預設啟動，而 `netTcpBinding` 繫結則預設關閉，因此必須 Opt-In 以尋求支援，例如 WS-\* 規格其中一個。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-183">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="8c0bc-184">這意味著預設的 TCP 組態在端點間交換訊息的速度，比預設針對 HTTP 繫結所設定的速度還快。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-184">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c0bc-185">範例</span><span class="sxs-lookup"><span data-stu-id="8c0bc-185">Example</span></span>

<span data-ttu-id="8c0bc-186">用戶端和服務的組態檔中會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-186">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="8c0bc-187">繫結型別是在 `binding` 項目的 `<endpoint>` 屬性中指定。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-187">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="8c0bc-188">如果您要設定 netTcpBinding 繫結，並變更其部分設定，則必須定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-188">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="8c0bc-189">端點必須參考含有 `bindingConfiguration` 屬性的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-189">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="8c0bc-190">下列範例會定義繫結組態。</span><span class="sxs-lookup"><span data-stu-id="8c0bc-190">In the following example, a binding configuration is defined.</span></span>  
  
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
    <binding closeTimeout="00:01:00"
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
  
## <a name="see-also"></a><span data-ttu-id="8c0bc-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c0bc-191">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="8c0bc-192">繫結</span><span class="sxs-lookup"><span data-stu-id="8c0bc-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8c0bc-193">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="8c0bc-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8c0bc-194">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="8c0bc-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
