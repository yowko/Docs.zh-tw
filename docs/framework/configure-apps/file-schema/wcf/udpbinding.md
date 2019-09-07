---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 9ee6d4b5e623248499adc43bb176d96bfc9cd1a8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399255"
---
# <a name="udpbinding"></a><span data-ttu-id="d7919-101">\<udpBinding></span><span class="sxs-lookup"><span data-stu-id="d7919-101">\<udpBinding></span></span>
<span data-ttu-id="d7919-102">用來設定 <xref:System.ServiceModel.UdpBinding> 繫結的組態元素。</span><span class="sxs-lookup"><span data-stu-id="d7919-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
<span data-ttu-id="d7919-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d7919-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d7919-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d7919-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d7919-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d7919-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d7919-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpBinding >**</span><span class="sxs-lookup"><span data-stu-id="d7919-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7919-107">語法</span><span class="sxs-lookup"><span data-stu-id="d7919-107">Syntax</span></span>  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7919-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d7919-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d7919-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d7919-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7919-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d7919-110">Attributes</span></span>  
  
|<span data-ttu-id="d7919-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d7919-111">Attribute</span></span>|<span data-ttu-id="d7919-112">描述</span><span class="sxs-lookup"><span data-stu-id="d7919-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="d7919-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="d7919-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d7919-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="d7919-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d7919-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="d7919-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="d7919-116">指定重複訊息記錄長度的整數值。</span><span class="sxs-lookup"><span data-stu-id="d7919-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="d7919-117">整數值，指定配置供從通道接收訊息之訊息緩衝區管理員使用的最大記憶體量。</span><span class="sxs-lookup"><span data-stu-id="d7919-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="d7919-118">預設值為 524288 (0x80000) 位元組。</span><span class="sxs-lookup"><span data-stu-id="d7919-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="d7919-119">整數值，指定儲存訊息之緩衝區的大小上限 (以位元組為單位)。在為此繫結設定的端點處理訊息時，可以將訊息儲存在緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="d7919-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="d7919-120">預設值為 65,536 位元組。</span><span class="sxs-lookup"><span data-stu-id="d7919-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="d7919-121">整數值，指定已接收但尚未從個別通道執行個體的輸入佇列移除的訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="d7919-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="d7919-122">正整數，定義在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="d7919-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="d7919-123">如果對收件者而言訊息太大，寄件者便會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d7919-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="d7919-124">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="d7919-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="d7919-125">預設為 65,536 個位元組。</span><span class="sxs-lookup"><span data-stu-id="d7919-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="d7919-126">指定重新傳輸訊息數目上限的整數值。</span><span class="sxs-lookup"><span data-stu-id="d7919-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="d7919-127">指定多點傳送介面 ID 的整數值。</span><span class="sxs-lookup"><span data-stu-id="d7919-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="d7919-128">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="d7919-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d7919-129">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="d7919-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d7919-130">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="d7919-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="d7919-131">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d7919-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="d7919-132">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="d7919-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d7919-133">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="d7919-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="d7919-134"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="d7919-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d7919-135">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="d7919-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d7919-136">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="d7919-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d7919-137"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="d7919-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d7919-138">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="d7919-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d7919-139">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="d7919-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="d7919-140"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="d7919-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d7919-141">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="d7919-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d7919-142">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="d7919-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="d7919-143">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="d7919-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="d7919-144">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="d7919-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d7919-145">BigEndianUnicodeUnicode BigEndian 編碼。</span><span class="sxs-lookup"><span data-stu-id="d7919-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="d7919-146">消除16位編碼。</span><span class="sxs-lookup"><span data-stu-id="d7919-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="d7919-147">UTF88位編碼</span><span class="sxs-lookup"><span data-stu-id="d7919-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="d7919-148">預設為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="d7919-148">The default is UTF8.</span></span> <span data-ttu-id="d7919-149">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="d7919-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="d7919-150">指定繫結存留時間的 timespan 值。</span><span class="sxs-lookup"><span data-stu-id="d7919-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7919-151">子元素</span><span class="sxs-lookup"><span data-stu-id="d7919-151">Child Elements</span></span>  
  
|<span data-ttu-id="d7919-152">項目</span><span class="sxs-lookup"><span data-stu-id="d7919-152">Element</span></span>|<span data-ttu-id="d7919-153">說明</span><span class="sxs-lookup"><span data-stu-id="d7919-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7919-154">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d7919-154">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="d7919-155">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="d7919-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d7919-156">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="d7919-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7919-157">父項目</span><span class="sxs-lookup"><span data-stu-id="d7919-157">Parent Elements</span></span>  
  
|<span data-ttu-id="d7919-158">項目</span><span class="sxs-lookup"><span data-stu-id="d7919-158">Element</span></span>|<span data-ttu-id="d7919-159">描述</span><span class="sxs-lookup"><span data-stu-id="d7919-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7919-160">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d7919-160">\<bindings></span></span>](bindings.md)|<span data-ttu-id="d7919-161">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="d7919-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7919-162">備註</span><span class="sxs-lookup"><span data-stu-id="d7919-162">Remarks</span></span>  
 <span data-ttu-id="d7919-163">UdpBinding 允許 WCF 服務透過 UDP 傳輸進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d7919-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="d7919-164">它允許「引發並忘記」訊息交換，其中用戶端會將訊息傳送至服務，並預期不會傳迴響應。</span><span class="sxs-lookup"><span data-stu-id="d7919-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7919-165">範例</span><span class="sxs-lookup"><span data-stu-id="d7919-165">Example</span></span>  
 <span data-ttu-id="d7919-166">下列範例示範如何<xref:System.ServiceModel.UdpBinding>使用 <`udpBinding`> 元素來設定。</span><span class="sxs-lookup"><span data-stu-id="d7919-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="d7919-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7919-167">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="d7919-168">繫結</span><span class="sxs-lookup"><span data-stu-id="d7919-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d7919-169">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d7919-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d7919-170">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="d7919-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d7919-171">\<binding></span><span class="sxs-lookup"><span data-stu-id="d7919-171">\<binding></span></span>](../../../misc/binding.md)
