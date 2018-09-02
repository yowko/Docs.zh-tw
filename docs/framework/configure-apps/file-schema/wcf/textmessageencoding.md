---
title: '&lt;textMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e684c21c0b1360a9b270214ebe7b3ad00b42657f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417791"
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="3cabb-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="3cabb-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="3cabb-103">指定字元編碼和訊息版本處理，用於文字 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="3cabb-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="3cabb-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3cabb-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3cabb-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="3cabb-105">\<bindings></span></span>  
<span data-ttu-id="3cabb-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3cabb-106">\<customBinding></span></span>  
<span data-ttu-id="3cabb-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="3cabb-107">\<binding></span></span>  
<span data-ttu-id="3cabb-108">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="3cabb-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cabb-109">語法</span><span class="sxs-lookup"><span data-stu-id="3cabb-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cabb-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3cabb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3cabb-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3cabb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cabb-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3cabb-112">Attributes</span></span>  
  
|<span data-ttu-id="3cabb-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3cabb-113">Attribute</span></span>|<span data-ttu-id="3cabb-114">描述</span><span class="sxs-lookup"><span data-stu-id="3cabb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3cabb-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="3cabb-115">maxReadPoolSize</span></span>|<span data-ttu-id="3cabb-116">整數，指定可以同時讀取而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="3cabb-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="3cabb-117">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="3cabb-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="3cabb-118">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="3cabb-118">The default is 64.</span></span>|  
|<span data-ttu-id="3cabb-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="3cabb-119">maxWritePoolSize</span></span>|<span data-ttu-id="3cabb-120">整數，指定可以同時傳送而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="3cabb-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="3cabb-121">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="3cabb-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="3cabb-122">預設值為 16。</span><span class="sxs-lookup"><span data-stu-id="3cabb-122">The default is 16.</span></span>|  
|<span data-ttu-id="3cabb-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="3cabb-123">messageVersion</span></span>|<span data-ttu-id="3cabb-124">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="3cabb-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="3cabb-125">有效值為</span><span class="sxs-lookup"><span data-stu-id="3cabb-125">Valid values are</span></span><br /><br /> <span data-ttu-id="3cabb-126">-   Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="3cabb-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="3cabb-127">-   Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="3cabb-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="3cabb-128">預設為 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="3cabb-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="3cabb-129">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="3cabb-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="3cabb-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="3cabb-130">writeEncoding</span></span>|<span data-ttu-id="3cabb-131">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="3cabb-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="3cabb-132">有效值為</span><span class="sxs-lookup"><span data-stu-id="3cabb-132">Valid values are</span></span><br /><br /> <span data-ttu-id="3cabb-133">-UnicodeFffeTextEncoding: Unicode BigEndian 編碼方式</span><span class="sxs-lookup"><span data-stu-id="3cabb-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="3cabb-134">-Utf16textencoding:unicode 編碼方式</span><span class="sxs-lookup"><span data-stu-id="3cabb-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="3cabb-135">-Utf8TextEncoding: 8 位元編碼</span><span class="sxs-lookup"><span data-stu-id="3cabb-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="3cabb-136">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="3cabb-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="3cabb-137">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="3cabb-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cabb-138">子元素</span><span class="sxs-lookup"><span data-stu-id="3cabb-138">Child Elements</span></span>  
  
|<span data-ttu-id="3cabb-139">項目</span><span class="sxs-lookup"><span data-stu-id="3cabb-139">Element</span></span>|<span data-ttu-id="3cabb-140">描述</span><span class="sxs-lookup"><span data-stu-id="3cabb-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cabb-141">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="3cabb-141">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="3cabb-142">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="3cabb-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3cabb-143">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="3cabb-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3cabb-144">父項目</span><span class="sxs-lookup"><span data-stu-id="3cabb-144">Parent Elements</span></span>  
  
|<span data-ttu-id="3cabb-145">項目</span><span class="sxs-lookup"><span data-stu-id="3cabb-145">Element</span></span>|<span data-ttu-id="3cabb-146">描述</span><span class="sxs-lookup"><span data-stu-id="3cabb-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cabb-147">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="3cabb-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3cabb-148">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="3cabb-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cabb-149">備註</span><span class="sxs-lookup"><span data-stu-id="3cabb-149">Remarks</span></span>  
 <span data-ttu-id="3cabb-150">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="3cabb-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="3cabb-151">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="3cabb-151">Decoding is the reverse process.</span></span> <span data-ttu-id="3cabb-152">Windows Communication Foundation (WCF) 包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="3cabb-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="3cabb-153">`textMessageEncoding` 項目所代表的文字編碼為最具互通性，但針對 XML 訊息編碼器的效率最為不彰。</span><span class="sxs-lookup"><span data-stu-id="3cabb-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="3cabb-154">文字編碼器會在網路上建立文字訊息。</span><span class="sxs-lookup"><span data-stu-id="3cabb-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="3cabb-155">此編碼器產生的訊息適合 WS-\* 型的互通性。</span><span class="sxs-lookup"><span data-stu-id="3cabb-155">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="3cabb-156">Web 服務或 Web 服務用戶端通常可以了解文字 XML。</span><span class="sxs-lookup"><span data-stu-id="3cabb-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="3cabb-157">不過，若要針對 XML 訊息進行編碼，將大型二進位資料區塊當做文字傳輸是效率最差的方法。</span><span class="sxs-lookup"><span data-stu-id="3cabb-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cabb-158">範例</span><span class="sxs-lookup"><span data-stu-id="3cabb-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cabb-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cabb-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="3cabb-160">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="3cabb-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="3cabb-161">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="3cabb-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="3cabb-162">繫結</span><span class="sxs-lookup"><span data-stu-id="3cabb-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3cabb-163">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="3cabb-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="3cabb-164">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3cabb-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="3cabb-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3cabb-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
