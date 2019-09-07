---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 538591c85d91960eb4d4fa04caa945954ee5a997
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397708"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="70604-101">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="70604-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="70604-102">指定編碼和訊息版本處理，用於 SOAP 訊息傳輸最佳化機制 (Message Transmission Optimization Mechanism，MTOM) 的訊息。</span><span class="sxs-lookup"><span data-stu-id="70604-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
<span data-ttu-id="70604-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="70604-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="70604-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="70604-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="70604-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="70604-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="70604-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="70604-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="70604-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="70604-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="70604-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mtomMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="70604-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70604-109">語法</span><span class="sxs-lookup"><span data-stu-id="70604-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70604-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="70604-110">Attributes and Elements</span></span>  
 <span data-ttu-id="70604-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="70604-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70604-112">屬性</span><span class="sxs-lookup"><span data-stu-id="70604-112">Attributes</span></span>  
  
|<span data-ttu-id="70604-113">屬性</span><span class="sxs-lookup"><span data-stu-id="70604-113">Attribute</span></span>|<span data-ttu-id="70604-114">說明</span><span class="sxs-lookup"><span data-stu-id="70604-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70604-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="70604-115">maxBufferSize</span></span>|<span data-ttu-id="70604-116">整數，指定可使用的緩衝區大小上限。</span><span class="sxs-lookup"><span data-stu-id="70604-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="70604-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="70604-117">maxReadPoolSize</span></span>|<span data-ttu-id="70604-118">整數，指定可以同時讀取而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="70604-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="70604-119">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="70604-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="70604-120">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="70604-120">The default is 64.</span></span>|  
|<span data-ttu-id="70604-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="70604-121">maxWritePoolSize</span></span>|<span data-ttu-id="70604-122">整數，指定可以同時傳送而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="70604-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="70604-123">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="70604-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="70604-124">預設值為 16。</span><span class="sxs-lookup"><span data-stu-id="70604-124">The default is 16.</span></span>|  
|<span data-ttu-id="70604-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="70604-125">messageVersion</span></span>|<span data-ttu-id="70604-126">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="70604-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="70604-127">有效值為</span><span class="sxs-lookup"><span data-stu-id="70604-127">Valid values are</span></span><br /><br /> <span data-ttu-id="70604-128">-   Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="70604-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="70604-129">-   Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="70604-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="70604-130">預設為 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="70604-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="70604-131">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="70604-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="70604-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="70604-132">writeEncoding</span></span>|<span data-ttu-id="70604-133">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="70604-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="70604-134">有效值為</span><span class="sxs-lookup"><span data-stu-id="70604-134">Valid values are</span></span><br /><br /> <span data-ttu-id="70604-135">UnicodeFffeTextEncodingUnicode BigEndian 編碼</span><span class="sxs-lookup"><span data-stu-id="70604-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="70604-136">Utf16TextEncodingUnicode 編碼</span><span class="sxs-lookup"><span data-stu-id="70604-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="70604-137">Utf8TextEncoding8位編碼</span><span class="sxs-lookup"><span data-stu-id="70604-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="70604-138">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="70604-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="70604-139">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="70604-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70604-140">子元素</span><span class="sxs-lookup"><span data-stu-id="70604-140">Child Elements</span></span>  
  
|<span data-ttu-id="70604-141">項目</span><span class="sxs-lookup"><span data-stu-id="70604-141">Element</span></span>|<span data-ttu-id="70604-142">說明</span><span class="sxs-lookup"><span data-stu-id="70604-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70604-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="70604-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="70604-144">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="70604-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="70604-145">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="70604-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70604-146">父項目</span><span class="sxs-lookup"><span data-stu-id="70604-146">Parent Elements</span></span>  
  
|<span data-ttu-id="70604-147">項目</span><span class="sxs-lookup"><span data-stu-id="70604-147">Element</span></span>|<span data-ttu-id="70604-148">描述</span><span class="sxs-lookup"><span data-stu-id="70604-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70604-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="70604-149">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="70604-150">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="70604-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70604-151">備註</span><span class="sxs-lookup"><span data-stu-id="70604-151">Remarks</span></span>  
 <span data-ttu-id="70604-152">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="70604-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="70604-153">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="70604-153">Decoding is the reverse process.</span></span> <span data-ttu-id="70604-154">Windows Communication Foundation （WCF）包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸優化機制（MTOM）。</span><span class="sxs-lookup"><span data-stu-id="70604-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="70604-155">`MtomMessageEncoding` 項目會為使用訊息傳輸最佳化機制 (MTOM) 編碼的訊息，指定使用的字元編碼、訊息版本控制以及其他設定。</span><span class="sxs-lookup"><span data-stu-id="70604-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="70604-156">MTOM 是在 WCF 訊息中傳輸二進位資料的有效技術。</span><span class="sxs-lookup"><span data-stu-id="70604-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="70604-157">MTOM 編碼器會嘗試在效率和互通性之間建立平衡。</span><span class="sxs-lookup"><span data-stu-id="70604-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="70604-158">MTOM 編碼會以文字格式傳輸大部分的 XML，但是在傳輸大型區塊的二進位資料時，會依照原狀來傳送 (不轉換成其 base64 編碼格式)，好讓這些資料最佳化。</span><span class="sxs-lookup"><span data-stu-id="70604-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70604-159">範例</span><span class="sxs-lookup"><span data-stu-id="70604-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="70604-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70604-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="70604-161">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="70604-161">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="70604-162">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="70604-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="70604-163">繫結</span><span class="sxs-lookup"><span data-stu-id="70604-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="70604-164">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="70604-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="70604-165">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="70604-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="70604-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="70604-166">\<customBinding></span></span>](custombinding.md)
