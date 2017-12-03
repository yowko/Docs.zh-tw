---
title: '&lt;textMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5e506d48c067871f5921d991c54ad8fb0d1593e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="lttextmessageencodinggt"></a><span data-ttu-id="4ebcb-102">&lt;textMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="4ebcb-102">&lt;textMessageEncoding&gt;</span></span>
<span data-ttu-id="4ebcb-103">指定字元編碼和訊息版本處理，用於文字 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-103">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
 <span data-ttu-id="4ebcb-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4ebcb-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4ebcb-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="4ebcb-105">\<bindings></span></span>  
<span data-ttu-id="4ebcb-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4ebcb-106">\<customBinding></span></span>  
<span data-ttu-id="4ebcb-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="4ebcb-107">\<binding></span></span>  
<span data-ttu-id="4ebcb-108">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="4ebcb-108">\<textMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ebcb-109">語法</span><span class="sxs-lookup"><span data-stu-id="4ebcb-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ebcb-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4ebcb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4ebcb-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ebcb-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4ebcb-112">Attributes</span></span>  
  
|<span data-ttu-id="4ebcb-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4ebcb-113">Attribute</span></span>|<span data-ttu-id="4ebcb-114">描述</span><span class="sxs-lookup"><span data-stu-id="4ebcb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ebcb-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4ebcb-115">maxReadPoolSize</span></span>|<span data-ttu-id="4ebcb-116">整數，指定可以同時讀取而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="4ebcb-117">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4ebcb-118">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-118">The default is 64.</span></span>|  
|<span data-ttu-id="4ebcb-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4ebcb-119">maxWritePoolSize</span></span>|<span data-ttu-id="4ebcb-120">整數，指定可以同時傳送而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="4ebcb-121">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4ebcb-122">預設值為 16。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-122">The default is 16.</span></span>|  
|<span data-ttu-id="4ebcb-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="4ebcb-123">messageVersion</span></span>|<span data-ttu-id="4ebcb-124">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="4ebcb-125">有效值為</span><span class="sxs-lookup"><span data-stu-id="4ebcb-125">Valid values are</span></span><br /><br /> <span data-ttu-id="4ebcb-126">-Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="4ebcb-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="4ebcb-127">-Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="4ebcb-127">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="4ebcb-128">預設為 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-128">The default is Soap12Addressing10.</span></span> <span data-ttu-id="4ebcb-129">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-129">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="4ebcb-130">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="4ebcb-130">writeEncoding</span></span>|<span data-ttu-id="4ebcb-131">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-131">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4ebcb-132">有效值為</span><span class="sxs-lookup"><span data-stu-id="4ebcb-132">Valid values are</span></span><br /><br /> <span data-ttu-id="4ebcb-133">-UnicodeFffeTextEncoding: Unicode BigEndian 編碼方式</span><span class="sxs-lookup"><span data-stu-id="4ebcb-133">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="4ebcb-134">-Utf16TextEncoding: Unicode 編碼方式</span><span class="sxs-lookup"><span data-stu-id="4ebcb-134">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="4ebcb-135">-Utf8TextEncoding: 8 位元編碼方式</span><span class="sxs-lookup"><span data-stu-id="4ebcb-135">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4ebcb-136">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-136">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="4ebcb-137">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-137">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ebcb-138">子元素</span><span class="sxs-lookup"><span data-stu-id="4ebcb-138">Child Elements</span></span>  
  
|<span data-ttu-id="4ebcb-139">項目</span><span class="sxs-lookup"><span data-stu-id="4ebcb-139">Element</span></span>|<span data-ttu-id="4ebcb-140">說明</span><span class="sxs-lookup"><span data-stu-id="4ebcb-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ebcb-141">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="4ebcb-141">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="4ebcb-142">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-142">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4ebcb-143">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-143">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ebcb-144">父項目</span><span class="sxs-lookup"><span data-stu-id="4ebcb-144">Parent Elements</span></span>  
  
|<span data-ttu-id="4ebcb-145">項目</span><span class="sxs-lookup"><span data-stu-id="4ebcb-145">Element</span></span>|<span data-ttu-id="4ebcb-146">說明</span><span class="sxs-lookup"><span data-stu-id="4ebcb-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ebcb-147">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="4ebcb-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4ebcb-148">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-148">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ebcb-149">備註</span><span class="sxs-lookup"><span data-stu-id="4ebcb-149">Remarks</span></span>  
 <span data-ttu-id="4ebcb-150">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="4ebcb-150">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="4ebcb-151">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-151">Decoding is the reverse process.</span></span> <span data-ttu-id="4ebcb-152">Windows Communication Foundation (WCF) 包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-152">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="4ebcb-153">`textMessageEncoding` 項目所代表的文字編碼為最具互通性，但針對 XML 訊息編碼器的效率最為不彰。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-153">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="4ebcb-154">文字編碼器會在網路上建立文字訊息。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-154">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="4ebcb-155">此編碼器產生的訊息適合 WS-* 型的互通性。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-155">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="4ebcb-156">Web 服務或 Web 服務用戶端通常可以了解文字 XML。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-156">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="4ebcb-157">不過，若要針對 XML 訊息進行編碼，將大型二進位資料區塊當做文字傳輸是效率最差的方法。</span><span class="sxs-lookup"><span data-stu-id="4ebcb-157">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ebcb-158">範例</span><span class="sxs-lookup"><span data-stu-id="4ebcb-158">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ebcb-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ebcb-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [<span data-ttu-id="4ebcb-160">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="4ebcb-160">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="4ebcb-161">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="4ebcb-161">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="4ebcb-162">繫結</span><span class="sxs-lookup"><span data-stu-id="4ebcb-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4ebcb-163">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="4ebcb-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="4ebcb-164">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="4ebcb-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="4ebcb-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4ebcb-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
