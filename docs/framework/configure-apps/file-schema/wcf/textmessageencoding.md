---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: c9f8347b4ee5f8fdbcf5c65c9a38b171ea6309de
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289597"
---
# <a name="textmessageencoding"></a><span data-ttu-id="63990-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="63990-101">\<textMessageEncoding></span></span>
<span data-ttu-id="63990-102">指定字元編碼和訊息版本處理，用於文字 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="63990-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="63990-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="63990-103">\<system.serviceModel></span></span>  
<span data-ttu-id="63990-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="63990-104">\<bindings></span></span>  
<span data-ttu-id="63990-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="63990-105">\<customBinding></span></span>  
<span data-ttu-id="63990-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="63990-106">\<binding></span></span>  
<span data-ttu-id="63990-107">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="63990-107">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63990-108">語法</span><span class="sxs-lookup"><span data-stu-id="63990-108">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63990-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="63990-109">Attributes and Elements</span></span>  
 <span data-ttu-id="63990-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="63990-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63990-111">屬性</span><span class="sxs-lookup"><span data-stu-id="63990-111">Attributes</span></span>  
  
|<span data-ttu-id="63990-112">屬性</span><span class="sxs-lookup"><span data-stu-id="63990-112">Attribute</span></span>|<span data-ttu-id="63990-113">描述</span><span class="sxs-lookup"><span data-stu-id="63990-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63990-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="63990-114">maxReadPoolSize</span></span>|<span data-ttu-id="63990-115">整數，指定可以同時讀取而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="63990-115">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="63990-116">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="63990-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="63990-117">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="63990-117">The default is 64.</span></span>|  
|<span data-ttu-id="63990-118">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="63990-118">maxWritePoolSize</span></span>|<span data-ttu-id="63990-119">整數，指定可以同時傳送而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="63990-119">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="63990-120">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="63990-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="63990-121">預設值為 16。</span><span class="sxs-lookup"><span data-stu-id="63990-121">The default is 16.</span></span>|  
|<span data-ttu-id="63990-122">messageVersion</span><span class="sxs-lookup"><span data-stu-id="63990-122">messageVersion</span></span>|<span data-ttu-id="63990-123">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="63990-123">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="63990-124">有效值為</span><span class="sxs-lookup"><span data-stu-id="63990-124">Valid values are</span></span><br /><br /> <span data-ttu-id="63990-125">-   Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="63990-125">-   Soap11Addressing10</span></span><br /><span data-ttu-id="63990-126">-   Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="63990-126">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="63990-127">預設為 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="63990-127">The default is Soap12Addressing10.</span></span> <span data-ttu-id="63990-128">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="63990-128">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="63990-129">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="63990-129">writeEncoding</span></span>|<span data-ttu-id="63990-130">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="63990-130">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="63990-131">有效值為</span><span class="sxs-lookup"><span data-stu-id="63990-131">Valid values are</span></span><br /><br /> <span data-ttu-id="63990-132">-UnicodeFffeTextEncoding:Unicode BigEndian 編碼方式</span><span class="sxs-lookup"><span data-stu-id="63990-132">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="63990-133">-Utf16textencoding:unicodeUnicode 編碼</span><span class="sxs-lookup"><span data-stu-id="63990-133">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="63990-134">-Utf8TextEncoding:8 位元編碼</span><span class="sxs-lookup"><span data-stu-id="63990-134">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="63990-135">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="63990-135">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="63990-136">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="63990-136">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63990-137">子元素</span><span class="sxs-lookup"><span data-stu-id="63990-137">Child Elements</span></span>  
  
|<span data-ttu-id="63990-138">項目</span><span class="sxs-lookup"><span data-stu-id="63990-138">Element</span></span>|<span data-ttu-id="63990-139">描述</span><span class="sxs-lookup"><span data-stu-id="63990-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63990-140">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="63990-140">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="63990-141">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="63990-141">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="63990-142">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="63990-142">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63990-143">父項目</span><span class="sxs-lookup"><span data-stu-id="63990-143">Parent Elements</span></span>  
  
|<span data-ttu-id="63990-144">項目</span><span class="sxs-lookup"><span data-stu-id="63990-144">Element</span></span>|<span data-ttu-id="63990-145">描述</span><span class="sxs-lookup"><span data-stu-id="63990-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63990-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="63990-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="63990-147">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="63990-147">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63990-148">備註</span><span class="sxs-lookup"><span data-stu-id="63990-148">Remarks</span></span>  
 <span data-ttu-id="63990-149">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="63990-149">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="63990-150">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="63990-150">Decoding is the reverse process.</span></span> <span data-ttu-id="63990-151">Windows Communication Foundation (WCF) 包含三種類型的 SOAP 訊息的編碼方式：文字、 二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="63990-151">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="63990-152">`textMessageEncoding` 項目所代表的文字編碼為最具互通性，但針對 XML 訊息編碼器的效率最為不彰。</span><span class="sxs-lookup"><span data-stu-id="63990-152">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="63990-153">文字編碼器會在網路上建立文字訊息。</span><span class="sxs-lookup"><span data-stu-id="63990-153">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="63990-154">此編碼器產生的訊息適合 WS-\* 型的互通性。</span><span class="sxs-lookup"><span data-stu-id="63990-154">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="63990-155">Web 服務或 Web 服務用戶端通常可以了解文字 XML。</span><span class="sxs-lookup"><span data-stu-id="63990-155">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="63990-156">不過，若要針對 XML 訊息進行編碼，將大型二進位資料區塊當做文字傳輸是效率最差的方法。</span><span class="sxs-lookup"><span data-stu-id="63990-156">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63990-157">範例</span><span class="sxs-lookup"><span data-stu-id="63990-157">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="63990-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63990-158">See also</span></span>
- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="63990-159">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="63990-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="63990-160">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="63990-160">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="63990-161">繫結</span><span class="sxs-lookup"><span data-stu-id="63990-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="63990-162">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="63990-162">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="63990-163">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="63990-163">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="63990-164">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="63990-164">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
