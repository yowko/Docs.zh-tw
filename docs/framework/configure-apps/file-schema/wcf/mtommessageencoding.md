---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: cffde19c8fd06836eaaedb5c4fc8687b97ae0afe
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556176"
---
# \<mtomMessageEncoding>
<span data-ttu-id="4989c-101">指定編碼和訊息版本處理，用於 SOAP 訊息傳輸最佳化機制 (Message Transmission Optimization Mechanism，MTOM) 的訊息。</span><span class="sxs-lookup"><span data-stu-id="4989c-101">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="4989c-102">語法</span><span class="sxs-lookup"><span data-stu-id="4989c-102">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4989c-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4989c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="4989c-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4989c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4989c-105">屬性</span><span class="sxs-lookup"><span data-stu-id="4989c-105">Attributes</span></span>  
  
|<span data-ttu-id="4989c-106">屬性</span><span class="sxs-lookup"><span data-stu-id="4989c-106">Attribute</span></span>|<span data-ttu-id="4989c-107">描述</span><span class="sxs-lookup"><span data-stu-id="4989c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4989c-108">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="4989c-108">maxBufferSize</span></span>|<span data-ttu-id="4989c-109">整數，指定可使用的緩衝區大小上限。</span><span class="sxs-lookup"><span data-stu-id="4989c-109">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="4989c-110">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4989c-110">maxReadPoolSize</span></span>|<span data-ttu-id="4989c-111">整數，指定可以同時讀取而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="4989c-111">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="4989c-112">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="4989c-112">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4989c-113">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="4989c-113">The default is 64.</span></span>|  
|<span data-ttu-id="4989c-114">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4989c-114">maxWritePoolSize</span></span>|<span data-ttu-id="4989c-115">整數，指定可以同時傳送而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="4989c-115">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="4989c-116">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="4989c-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4989c-117">預設值是 16。</span><span class="sxs-lookup"><span data-stu-id="4989c-117">The default is 16.</span></span>|  
|<span data-ttu-id="4989c-118">messageVersion</span><span class="sxs-lookup"><span data-stu-id="4989c-118">messageVersion</span></span>|<span data-ttu-id="4989c-119">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="4989c-119">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="4989c-120">有效值為</span><span class="sxs-lookup"><span data-stu-id="4989c-120">Valid values are</span></span><br /><br /> <span data-ttu-id="4989c-121">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="4989c-121">-   Soap11Addressing1</span></span><br /><span data-ttu-id="4989c-122">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="4989c-122">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="4989c-123">預設為 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="4989c-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="4989c-124">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="4989c-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="4989c-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="4989c-125">writeEncoding</span></span>|<span data-ttu-id="4989c-126">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4989c-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4989c-127">有效值為</span><span class="sxs-lookup"><span data-stu-id="4989c-127">Valid values are</span></span><br /><br /> <span data-ttu-id="4989c-128">-UnicodeFffeTextEncoding： Unicode BigEndian 編碼</span><span class="sxs-lookup"><span data-stu-id="4989c-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="4989c-129">-Utf16TextEncoding： Unicode 編碼</span><span class="sxs-lookup"><span data-stu-id="4989c-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="4989c-130">-Utf8TextEncoding：8位編碼</span><span class="sxs-lookup"><span data-stu-id="4989c-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4989c-131">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="4989c-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="4989c-132">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="4989c-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4989c-133">子元素</span><span class="sxs-lookup"><span data-stu-id="4989c-133">Child Elements</span></span>  
  
|<span data-ttu-id="4989c-134">項目</span><span class="sxs-lookup"><span data-stu-id="4989c-134">Element</span></span>|<span data-ttu-id="4989c-135">描述</span><span class="sxs-lookup"><span data-stu-id="4989c-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="4989c-136">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="4989c-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4989c-137">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="4989c-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4989c-138">父項目</span><span class="sxs-lookup"><span data-stu-id="4989c-138">Parent Elements</span></span>  
  
|<span data-ttu-id="4989c-139">項目</span><span class="sxs-lookup"><span data-stu-id="4989c-139">Element</span></span>|<span data-ttu-id="4989c-140">描述</span><span class="sxs-lookup"><span data-stu-id="4989c-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="4989c-141">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="4989c-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4989c-142">備註</span><span class="sxs-lookup"><span data-stu-id="4989c-142">Remarks</span></span>  
 <span data-ttu-id="4989c-143">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="4989c-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="4989c-144">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="4989c-144">Decoding is the reverse process.</span></span> <span data-ttu-id="4989c-145">Windows Communication Foundation (WCF) 包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="4989c-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="4989c-146">`MtomMessageEncoding` 項目會為使用訊息傳輸最佳化機制 (MTOM) 編碼的訊息，指定使用的字元編碼、訊息版本控制以及其他設定。</span><span class="sxs-lookup"><span data-stu-id="4989c-146">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="4989c-147">MTOM 是在 WCF 訊息中傳輸二進位資料的有效技術。</span><span class="sxs-lookup"><span data-stu-id="4989c-147">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="4989c-148">MTOM 編碼器會嘗試在效率和互通性之間建立平衡。</span><span class="sxs-lookup"><span data-stu-id="4989c-148">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="4989c-149">MTOM 編碼會以文字格式傳輸大部分的 XML，但是在傳輸大型區塊的二進位資料時，會依照原狀來傳送 (不轉換成其 base64 編碼格式)，好讓這些資料最佳化。</span><span class="sxs-lookup"><span data-stu-id="4989c-149">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4989c-150">範例</span><span class="sxs-lookup"><span data-stu-id="4989c-150">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="4989c-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4989c-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="4989c-152">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="4989c-152">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="4989c-153">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="4989c-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="4989c-154">繫結</span><span class="sxs-lookup"><span data-stu-id="4989c-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4989c-155">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="4989c-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4989c-156">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="4989c-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
