---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: be0a11c71083c713042ab572cb78fbae27d52912
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277689"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="a55de-101">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="a55de-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="a55de-102">指定編碼和訊息版本處理，用於 SOAP 訊息傳輸最佳化機制 (Message Transmission Optimization Mechanism，MTOM) 的訊息。</span><span class="sxs-lookup"><span data-stu-id="a55de-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
 <span data-ttu-id="a55de-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a55de-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a55de-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a55de-104">\<bindings></span></span>  
<span data-ttu-id="a55de-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a55de-105">\<customBinding></span></span>  
<span data-ttu-id="a55de-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="a55de-106">\<binding></span></span>  
<span data-ttu-id="a55de-107">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="a55de-107">\<mtomMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a55de-108">語法</span><span class="sxs-lookup"><span data-stu-id="a55de-108">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a55de-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a55de-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a55de-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a55de-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a55de-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a55de-111">Attributes</span></span>  
  
|<span data-ttu-id="a55de-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a55de-112">Attribute</span></span>|<span data-ttu-id="a55de-113">描述</span><span class="sxs-lookup"><span data-stu-id="a55de-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a55de-114">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="a55de-114">maxBufferSize</span></span>|<span data-ttu-id="a55de-115">整數，指定可使用的緩衝區大小上限。</span><span class="sxs-lookup"><span data-stu-id="a55de-115">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="a55de-116">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="a55de-116">maxReadPoolSize</span></span>|<span data-ttu-id="a55de-117">整數，指定可以同時讀取而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="a55de-117">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="a55de-118">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="a55de-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a55de-119">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="a55de-119">The default is 64.</span></span>|  
|<span data-ttu-id="a55de-120">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="a55de-120">maxWritePoolSize</span></span>|<span data-ttu-id="a55de-121">整數，指定可以同時傳送而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="a55de-121">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="a55de-122">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="a55de-122">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a55de-123">預設值為 16。</span><span class="sxs-lookup"><span data-stu-id="a55de-123">The default is 16.</span></span>|  
|<span data-ttu-id="a55de-124">messageVersion</span><span class="sxs-lookup"><span data-stu-id="a55de-124">messageVersion</span></span>|<span data-ttu-id="a55de-125">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="a55de-125">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="a55de-126">有效值為</span><span class="sxs-lookup"><span data-stu-id="a55de-126">Valid values are</span></span><br /><br /> <span data-ttu-id="a55de-127">-   Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="a55de-127">-   Soap11Addressing1</span></span><br /><span data-ttu-id="a55de-128">-   Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="a55de-128">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="a55de-129">預設為 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="a55de-129">The default is Soap12Addressing10.</span></span> <span data-ttu-id="a55de-130">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="a55de-130">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="a55de-131">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="a55de-131">writeEncoding</span></span>|<span data-ttu-id="a55de-132">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="a55de-132">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a55de-133">有效值為</span><span class="sxs-lookup"><span data-stu-id="a55de-133">Valid values are</span></span><br /><br /> <span data-ttu-id="a55de-134">-UnicodeFffeTextEncoding:Unicode BigEndian 編碼方式</span><span class="sxs-lookup"><span data-stu-id="a55de-134">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="a55de-135">-Utf16textencoding:unicodeUnicode 編碼</span><span class="sxs-lookup"><span data-stu-id="a55de-135">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="a55de-136">-Utf8TextEncoding:8 位元編碼</span><span class="sxs-lookup"><span data-stu-id="a55de-136">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="a55de-137">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="a55de-137">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="a55de-138">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="a55de-138">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a55de-139">子元素</span><span class="sxs-lookup"><span data-stu-id="a55de-139">Child Elements</span></span>  
  
|<span data-ttu-id="a55de-140">項目</span><span class="sxs-lookup"><span data-stu-id="a55de-140">Element</span></span>|<span data-ttu-id="a55de-141">描述</span><span class="sxs-lookup"><span data-stu-id="a55de-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a55de-142">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="a55de-142">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="a55de-143">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="a55de-143">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a55de-144">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="a55de-144">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a55de-145">父項目</span><span class="sxs-lookup"><span data-stu-id="a55de-145">Parent Elements</span></span>  
  
|<span data-ttu-id="a55de-146">項目</span><span class="sxs-lookup"><span data-stu-id="a55de-146">Element</span></span>|<span data-ttu-id="a55de-147">描述</span><span class="sxs-lookup"><span data-stu-id="a55de-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a55de-148">\<binding></span><span class="sxs-lookup"><span data-stu-id="a55de-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a55de-149">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="a55de-149">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a55de-150">備註</span><span class="sxs-lookup"><span data-stu-id="a55de-150">Remarks</span></span>  
 <span data-ttu-id="a55de-151">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="a55de-151">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="a55de-152">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="a55de-152">Decoding is the reverse process.</span></span> <span data-ttu-id="a55de-153">Windows Communication Foundation (WCF) 包含三種類型的 SOAP 訊息的編碼方式：文字、 二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="a55de-153">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="a55de-154">`MtomMessageEncoding` 項目會為使用訊息傳輸最佳化機制 (MTOM) 編碼的訊息，指定使用的字元編碼、訊息版本控制以及其他設定。</span><span class="sxs-lookup"><span data-stu-id="a55de-154">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="a55de-155">MTOM 是在 WCF 訊息中傳輸二進位資料的有效技術。</span><span class="sxs-lookup"><span data-stu-id="a55de-155">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="a55de-156">MTOM 編碼器會嘗試在效率和互通性之間建立平衡。</span><span class="sxs-lookup"><span data-stu-id="a55de-156">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="a55de-157">MTOM 編碼會以文字格式傳輸大部分的 XML，但是在傳輸大型區塊的二進位資料時，會依照原狀來傳送 (不轉換成其 base64 編碼格式)，好讓這些資料最佳化。</span><span class="sxs-lookup"><span data-stu-id="a55de-157">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a55de-158">範例</span><span class="sxs-lookup"><span data-stu-id="a55de-158">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="a55de-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a55de-159">See also</span></span>
- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="a55de-160">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="a55de-160">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="a55de-161">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="a55de-161">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="a55de-162">繫結</span><span class="sxs-lookup"><span data-stu-id="a55de-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a55de-163">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="a55de-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a55de-164">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="a55de-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a55de-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a55de-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
