---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e9942ce3ccbec949160ee70dd103d3c1799bd44d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186299"
---
# <a name="textmessageencoding"></a><span data-ttu-id="23202-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="23202-101">\<textMessageEncoding></span></span>
<span data-ttu-id="23202-102">指定字元編碼和訊息版本處理，用於文字 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="23202-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="23202-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="23202-103">\<system.serviceModel></span></span>  
<span data-ttu-id="23202-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="23202-104">\<bindings></span></span>  
<span data-ttu-id="23202-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="23202-105">\<customBinding></span></span>  
<span data-ttu-id="23202-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="23202-106">\<binding></span></span>  
<span data-ttu-id="23202-107">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="23202-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23202-108">語法</span><span class="sxs-lookup"><span data-stu-id="23202-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23202-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="23202-109">Attributes and Elements</span></span>  
 <span data-ttu-id="23202-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="23202-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23202-111">屬性</span><span class="sxs-lookup"><span data-stu-id="23202-111">Attributes</span></span>  
  
|<span data-ttu-id="23202-112">屬性</span><span class="sxs-lookup"><span data-stu-id="23202-112">Attribute</span></span>|<span data-ttu-id="23202-113">描述</span><span class="sxs-lookup"><span data-stu-id="23202-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23202-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="23202-114">maxReadPoolSize</span></span>|<span data-ttu-id="23202-115">整數，指定可以同時讀取而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="23202-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="23202-116">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="23202-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="23202-117">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="23202-117">The default is 64.</span></span>|  
|<span data-ttu-id="23202-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="23202-118">maxWritePoolSize</span></span>|<span data-ttu-id="23202-119">整數，指定可以同時傳送而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="23202-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="23202-120">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="23202-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="23202-121">預設值為 16。</span><span class="sxs-lookup"><span data-stu-id="23202-121">The default is 16.</span></span>|  
|<span data-ttu-id="23202-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="23202-122">messageVersion</span></span>|<span data-ttu-id="23202-123">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="23202-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="23202-124">有效值為</span><span class="sxs-lookup"><span data-stu-id="23202-124">Valid values are</span></span><br /><br /> <span data-ttu-id="23202-125">-   Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="23202-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="23202-126">-   Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="23202-126">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="23202-127">預設為 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="23202-127">The default is Soap12Addressing10.</span></span> <span data-ttu-id="23202-128">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="23202-128">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="23202-129">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="23202-129">writeEncoding</span></span>|<span data-ttu-id="23202-130">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="23202-130">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="23202-131">有效值為</span><span class="sxs-lookup"><span data-stu-id="23202-131">Valid values are</span></span><br /><br /> <span data-ttu-id="23202-132">-UnicodeFffeTextEncoding:Unicode BigEndian 編碼方式</span><span class="sxs-lookup"><span data-stu-id="23202-132">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="23202-133">-Utf16textencoding:unicodeUnicode 編碼</span><span class="sxs-lookup"><span data-stu-id="23202-133">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="23202-134">-Utf8TextEncoding:8 位元編碼</span><span class="sxs-lookup"><span data-stu-id="23202-134">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="23202-135">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="23202-135">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="23202-136">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="23202-136">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23202-137">子元素</span><span class="sxs-lookup"><span data-stu-id="23202-137">Child Elements</span></span>  
  
|<span data-ttu-id="23202-138">項目</span><span class="sxs-lookup"><span data-stu-id="23202-138">Element</span></span>|<span data-ttu-id="23202-139">描述</span><span class="sxs-lookup"><span data-stu-id="23202-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23202-140">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="23202-140">\<readerQuotas></span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="23202-141">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="23202-141">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="23202-142">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="23202-142">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23202-143">父項目</span><span class="sxs-lookup"><span data-stu-id="23202-143">Parent Elements</span></span>  
  
|<span data-ttu-id="23202-144">項目</span><span class="sxs-lookup"><span data-stu-id="23202-144">Element</span></span>|<span data-ttu-id="23202-145">描述</span><span class="sxs-lookup"><span data-stu-id="23202-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23202-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="23202-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="23202-147">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="23202-147">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23202-148">備註</span><span class="sxs-lookup"><span data-stu-id="23202-148">Remarks</span></span>  
 <span data-ttu-id="23202-149">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="23202-149">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="23202-150">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="23202-150">Decoding is the reverse process.</span></span> <span data-ttu-id="23202-151">Windows Communication Foundation (WCF) 包含三種類型的 SOAP 訊息的編碼方式：文字、 二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="23202-151">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="23202-152">`textMessageEncoding` 項目所代表的文字編碼為最具互通性，但針對 XML 訊息編碼器的效率最為不彰。</span><span class="sxs-lookup"><span data-stu-id="23202-152">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="23202-153">文字編碼器會在網路上建立文字訊息。</span><span class="sxs-lookup"><span data-stu-id="23202-153">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="23202-154">此編碼器產生的訊息適合 WS-\* 型的互通性。</span><span class="sxs-lookup"><span data-stu-id="23202-154">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="23202-155">Web 服務或 Web 服務用戶端通常可以了解文字 XML。</span><span class="sxs-lookup"><span data-stu-id="23202-155">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="23202-156">不過，若要針對 XML 訊息進行編碼，將大型二進位資料區塊當做文字傳輸是效率最差的方法。</span><span class="sxs-lookup"><span data-stu-id="23202-156">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23202-157">範例</span><span class="sxs-lookup"><span data-stu-id="23202-157">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="23202-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23202-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="23202-159">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="23202-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="23202-160">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="23202-160">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="23202-161">繫結</span><span class="sxs-lookup"><span data-stu-id="23202-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="23202-162">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="23202-162">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="23202-163">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="23202-163">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="23202-164">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="23202-164">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
