---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: d67d623736f3cbf50568356132a74d2b234fdfd9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736213"
---
# \<textMessageEncoding>
<span data-ttu-id="59686-101">指定字元編碼和訊息版本處理，用於文字 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="59686-101">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="59686-102">語法</span><span class="sxs-lookup"><span data-stu-id="59686-102">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59686-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="59686-103">Attributes and Elements</span></span>  
 <span data-ttu-id="59686-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="59686-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59686-105">屬性</span><span class="sxs-lookup"><span data-stu-id="59686-105">Attributes</span></span>  
  
|<span data-ttu-id="59686-106">屬性</span><span class="sxs-lookup"><span data-stu-id="59686-106">Attribute</span></span>|<span data-ttu-id="59686-107">描述</span><span class="sxs-lookup"><span data-stu-id="59686-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59686-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="59686-108">maxReadPoolSize</span></span>|<span data-ttu-id="59686-109">整數，指定可以同時讀取而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="59686-109">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="59686-110">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="59686-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="59686-111">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="59686-111">The default is 64.</span></span>|  
|<span data-ttu-id="59686-112">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="59686-112">maxWritePoolSize</span></span>|<span data-ttu-id="59686-113">整數，指定可以同時傳送而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="59686-113">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="59686-114">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="59686-114">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="59686-115">預設值是 16。</span><span class="sxs-lookup"><span data-stu-id="59686-115">The default is 16.</span></span>|  
|<span data-ttu-id="59686-116">messageVersion</span><span class="sxs-lookup"><span data-stu-id="59686-116">messageVersion</span></span>|<span data-ttu-id="59686-117">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="59686-117">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="59686-118">有效值為</span><span class="sxs-lookup"><span data-stu-id="59686-118">Valid values are</span></span><br /><br /> <span data-ttu-id="59686-119">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="59686-119">-   Soap11Addressing10</span></span><br /><span data-ttu-id="59686-120">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="59686-120">-   Soap12Addressing10</span></span><br /><span data-ttu-id="59686-121">-Soap11</span><span class="sxs-lookup"><span data-stu-id="59686-121">-   Soap11</span></span><br /><span data-ttu-id="59686-122">-Soap12</span><span class="sxs-lookup"><span data-stu-id="59686-122">-  Soap12</span></span><br /><br /><span data-ttu-id="59686-123">預設為 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="59686-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="59686-124">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="59686-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="59686-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="59686-125">writeEncoding</span></span>|<span data-ttu-id="59686-126">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="59686-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="59686-127">有效值為</span><span class="sxs-lookup"><span data-stu-id="59686-127">Valid values are</span></span><br /><br /> <span data-ttu-id="59686-128">-UnicodeFffeTextEncoding： Unicode BigEndian 編碼</span><span class="sxs-lookup"><span data-stu-id="59686-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="59686-129">-Utf16TextEncoding： Unicode 編碼</span><span class="sxs-lookup"><span data-stu-id="59686-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="59686-130">-Utf8TextEncoding：8位編碼</span><span class="sxs-lookup"><span data-stu-id="59686-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="59686-131">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="59686-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="59686-132">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="59686-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59686-133">子元素</span><span class="sxs-lookup"><span data-stu-id="59686-133">Child Elements</span></span>  
  
|<span data-ttu-id="59686-134">元素</span><span class="sxs-lookup"><span data-stu-id="59686-134">Element</span></span>|<span data-ttu-id="59686-135">描述</span><span class="sxs-lookup"><span data-stu-id="59686-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="59686-136">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="59686-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="59686-137">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="59686-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59686-138">父項目</span><span class="sxs-lookup"><span data-stu-id="59686-138">Parent Elements</span></span>  
  
|<span data-ttu-id="59686-139">元素</span><span class="sxs-lookup"><span data-stu-id="59686-139">Element</span></span>|<span data-ttu-id="59686-140">描述</span><span class="sxs-lookup"><span data-stu-id="59686-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="59686-141">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="59686-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59686-142">備註</span><span class="sxs-lookup"><span data-stu-id="59686-142">Remarks</span></span>  
 <span data-ttu-id="59686-143">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="59686-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="59686-144">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="59686-144">Decoding is the reverse process.</span></span> <span data-ttu-id="59686-145">Windows Communication Foundation (WCF) 包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="59686-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="59686-146">`textMessageEncoding` 項目所代表的文字編碼為最具互通性，但針對 XML 訊息編碼器的效率最為不彰。</span><span class="sxs-lookup"><span data-stu-id="59686-146">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="59686-147">文字編碼器會在網路上建立文字訊息。</span><span class="sxs-lookup"><span data-stu-id="59686-147">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="59686-148">此編碼器產生的訊息適合 WS-\* 型的互通性。</span><span class="sxs-lookup"><span data-stu-id="59686-148">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="59686-149">Web 服務或 Web 服務用戶端通常可以了解文字 XML。</span><span class="sxs-lookup"><span data-stu-id="59686-149">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="59686-150">不過，若要針對 XML 訊息進行編碼，將大型二進位資料區塊當做文字傳輸是效率最差的方法。</span><span class="sxs-lookup"><span data-stu-id="59686-150">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59686-151">範例</span><span class="sxs-lookup"><span data-stu-id="59686-151">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="59686-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59686-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="59686-153">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="59686-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="59686-154">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="59686-154">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="59686-155">繫結</span><span class="sxs-lookup"><span data-stu-id="59686-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="59686-156">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="59686-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="59686-157">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="59686-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
