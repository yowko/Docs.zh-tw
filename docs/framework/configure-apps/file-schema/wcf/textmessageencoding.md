---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 1494cee0e412bebc6637ad73354f7c91dc636e15
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399437"
---
# <a name="textmessageencoding"></a><span data-ttu-id="95282-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="95282-101">\<textMessageEncoding></span></span>
<span data-ttu-id="95282-102">指定字元編碼和訊息版本處理，用於文字 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="95282-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
<span data-ttu-id="95282-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="95282-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="95282-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="95282-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="95282-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="95282-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="95282-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="95282-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="95282-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="95282-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="95282-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<textMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="95282-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95282-109">語法</span><span class="sxs-lookup"><span data-stu-id="95282-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95282-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="95282-110">Attributes and Elements</span></span>  
 <span data-ttu-id="95282-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="95282-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95282-112">屬性</span><span class="sxs-lookup"><span data-stu-id="95282-112">Attributes</span></span>  
  
|<span data-ttu-id="95282-113">屬性</span><span class="sxs-lookup"><span data-stu-id="95282-113">Attribute</span></span>|<span data-ttu-id="95282-114">說明</span><span class="sxs-lookup"><span data-stu-id="95282-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95282-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="95282-115">maxReadPoolSize</span></span>|<span data-ttu-id="95282-116">整數，指定可以同時讀取而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="95282-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="95282-117">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="95282-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="95282-118">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="95282-118">The default is 64.</span></span>|  
|<span data-ttu-id="95282-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="95282-119">maxWritePoolSize</span></span>|<span data-ttu-id="95282-120">整數，指定可以同時傳送而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="95282-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="95282-121">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="95282-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="95282-122">預設值為 16。</span><span class="sxs-lookup"><span data-stu-id="95282-122">The default is 16.</span></span>|  
|<span data-ttu-id="95282-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="95282-123">messageVersion</span></span>|<span data-ttu-id="95282-124">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="95282-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="95282-125">有效值為</span><span class="sxs-lookup"><span data-stu-id="95282-125">Valid values are</span></span><br /><br /> <span data-ttu-id="95282-126">-   Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="95282-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="95282-127">-   Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="95282-127">-   Soap12Addressing10</span></span><br /><span data-ttu-id="95282-128">-   Soap11</span><span class="sxs-lookup"><span data-stu-id="95282-128">-   Soap11</span></span><br /><span data-ttu-id="95282-129">-  Soap12</span><span class="sxs-lookup"><span data-stu-id="95282-129">-  Soap12</span></span><br /><br /><span data-ttu-id="95282-130">預設為 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="95282-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="95282-131">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="95282-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="95282-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="95282-132">writeEncoding</span></span>|<span data-ttu-id="95282-133">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="95282-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="95282-134">有效值為</span><span class="sxs-lookup"><span data-stu-id="95282-134">Valid values are</span></span><br /><br /> <span data-ttu-id="95282-135">UnicodeFffeTextEncodingUnicode BigEndian 編碼</span><span class="sxs-lookup"><span data-stu-id="95282-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="95282-136">Utf16TextEncodingUnicode 編碼</span><span class="sxs-lookup"><span data-stu-id="95282-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="95282-137">Utf8TextEncoding8位編碼</span><span class="sxs-lookup"><span data-stu-id="95282-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="95282-138">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="95282-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="95282-139">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="95282-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95282-140">子元素</span><span class="sxs-lookup"><span data-stu-id="95282-140">Child Elements</span></span>  
  
|<span data-ttu-id="95282-141">項目</span><span class="sxs-lookup"><span data-stu-id="95282-141">Element</span></span>|<span data-ttu-id="95282-142">說明</span><span class="sxs-lookup"><span data-stu-id="95282-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95282-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="95282-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="95282-144">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="95282-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="95282-145">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="95282-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95282-146">父項目</span><span class="sxs-lookup"><span data-stu-id="95282-146">Parent Elements</span></span>  
  
|<span data-ttu-id="95282-147">項目</span><span class="sxs-lookup"><span data-stu-id="95282-147">Element</span></span>|<span data-ttu-id="95282-148">描述</span><span class="sxs-lookup"><span data-stu-id="95282-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95282-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="95282-149">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="95282-150">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="95282-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95282-151">備註</span><span class="sxs-lookup"><span data-stu-id="95282-151">Remarks</span></span>  
 <span data-ttu-id="95282-152">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="95282-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="95282-153">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="95282-153">Decoding is the reverse process.</span></span> <span data-ttu-id="95282-154">Windows Communication Foundation （WCF）包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸優化機制（MTOM）。</span><span class="sxs-lookup"><span data-stu-id="95282-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="95282-155">`textMessageEncoding` 項目所代表的文字編碼為最具互通性，但針對 XML 訊息編碼器的效率最為不彰。</span><span class="sxs-lookup"><span data-stu-id="95282-155">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="95282-156">文字編碼器會在網路上建立文字訊息。</span><span class="sxs-lookup"><span data-stu-id="95282-156">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="95282-157">此編碼器產生的訊息適合 WS-\* 型的互通性。</span><span class="sxs-lookup"><span data-stu-id="95282-157">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="95282-158">Web 服務或 Web 服務用戶端通常可以了解文字 XML。</span><span class="sxs-lookup"><span data-stu-id="95282-158">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="95282-159">不過，若要針對 XML 訊息進行編碼，將大型二進位資料區塊當做文字傳輸是效率最差的方法。</span><span class="sxs-lookup"><span data-stu-id="95282-159">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95282-160">範例</span><span class="sxs-lookup"><span data-stu-id="95282-160">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="95282-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95282-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="95282-162">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="95282-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="95282-163">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="95282-163">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="95282-164">繫結</span><span class="sxs-lookup"><span data-stu-id="95282-164">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="95282-165">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="95282-165">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="95282-166">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="95282-166">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="95282-167">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="95282-167">\<customBinding></span></span>](custombinding.md)
