---
title: '&lt;binaryMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 11d819d5d6302da309dd3e4ce674110c8419978f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltbinarymessageencodinggt"></a><span data-ttu-id="311c3-102">&lt;binaryMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="311c3-102">&lt;binaryMessageEncoding&gt;</span></span>
<span data-ttu-id="311c3-103">定義二進位訊息編碼器，以二進位編碼網路上的 Windows Communication Foundation (WCF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="311c3-103">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="311c3-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="311c3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="311c3-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="311c3-105">\<bindings></span></span>  
<span data-ttu-id="311c3-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="311c3-106">\<customBinding></span></span>  
<span data-ttu-id="311c3-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="311c3-107">\<binding></span></span>  
<span data-ttu-id="311c3-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="311c3-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="311c3-109">語法</span><span class="sxs-lookup"><span data-stu-id="311c3-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding   
      maxReadPoolSize="Integer"  
   maxSessionSize="Integer"   
   maxWritePoolSize="Integer"   messageVersion="Soap11Addressing10/Soap12Addressing10" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="311c3-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="311c3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="311c3-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="311c3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="311c3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="311c3-112">Attributes</span></span>  
  
|<span data-ttu-id="311c3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="311c3-113">Attribute</span></span>|<span data-ttu-id="311c3-114">描述</span><span class="sxs-lookup"><span data-stu-id="311c3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="311c3-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="311c3-115">maxReadPoolSize</span></span>|<span data-ttu-id="311c3-116">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="311c3-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="311c3-117">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="311c3-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="311c3-118">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="311c3-118">The default is 64.</span></span>|  
|<span data-ttu-id="311c3-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="311c3-119">maxSessionSize</span></span>|<span data-ttu-id="311c3-120">正整數，設定用於編碼的緩衝區大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="311c3-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="311c3-121">較大的緩衝區會增加編碼速度，但是會犧牲工作集的大小。</span><span class="sxs-lookup"><span data-stu-id="311c3-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="311c3-122">預設值為 2048。</span><span class="sxs-lookup"><span data-stu-id="311c3-122">The default is 2048.</span></span>|  
|<span data-ttu-id="311c3-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="311c3-123">maxWritePoolSize</span></span>|<span data-ttu-id="311c3-124">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="311c3-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="311c3-125">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="311c3-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="311c3-126">預設值為 16。</span><span class="sxs-lookup"><span data-stu-id="311c3-126">The default is 16.</span></span>|  
|<span data-ttu-id="311c3-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="311c3-127">messageVersion</span></span>|<span data-ttu-id="311c3-128">指定已使用或必須使用的 SOAP 訊息和 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="311c3-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="311c3-129">子元素</span><span class="sxs-lookup"><span data-stu-id="311c3-129">Child Elements</span></span>  
  
|<span data-ttu-id="311c3-130">項目</span><span class="sxs-lookup"><span data-stu-id="311c3-130">Element</span></span>|<span data-ttu-id="311c3-131">說明</span><span class="sxs-lookup"><span data-stu-id="311c3-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="311c3-132">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="311c3-132">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="311c3-133">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="311c3-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="311c3-134">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="311c3-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="311c3-135">父項目</span><span class="sxs-lookup"><span data-stu-id="311c3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="311c3-136">項目</span><span class="sxs-lookup"><span data-stu-id="311c3-136">Element</span></span>|<span data-ttu-id="311c3-137">說明</span><span class="sxs-lookup"><span data-stu-id="311c3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="311c3-138">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="311c3-138">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="311c3-139">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="311c3-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="311c3-140">備註</span><span class="sxs-lookup"><span data-stu-id="311c3-140">Remarks</span></span>  
 <span data-ttu-id="311c3-141">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="311c3-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="311c3-142">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="311c3-142">Decoding is the reverse process.</span></span> <span data-ttu-id="311c3-143">Windows Communication Foundation (WCF) 包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="311c3-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="311c3-144">`binaryMessageEncoding` 項目會指定 XML 的 .NET 二進位格式，並且提供指定字元編碼以及要使用之 SOAP 和 WS-Addressing 版本的選項。</span><span class="sxs-lookup"><span data-stu-id="311c3-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="311c3-145">二進位訊息編碼器會以二進位編碼網路上的 Windows Communication Foundation (WCF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="311c3-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="311c3-146">雖然這個編碼會讓訊息傳輸速度非常快，但是會失去以 WS-* 標準為基礎的互通性 (Interoperability)。</span><span class="sxs-lookup"><span data-stu-id="311c3-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="311c3-147">範例</span><span class="sxs-lookup"><span data-stu-id="311c3-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"  
   maxWritePoolSize="2132"  
   maxSessionSize="3141" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="311c3-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="311c3-148">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
 [<span data-ttu-id="311c3-149">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="311c3-149">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="311c3-150">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="311c3-150">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="311c3-151">繫結</span><span class="sxs-lookup"><span data-stu-id="311c3-151">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="311c3-152">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="311c3-152">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="311c3-153">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="311c3-153">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="311c3-154">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="311c3-154">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
