---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 4179d7ac1919610b0be131b079b28da0cd9cad75
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540291"
---
# \<binaryMessageEncoding>
<span data-ttu-id="79160-101">定義二進位訊息編碼器，以二進位編碼網路上的 Windows Communication Foundation (WCF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="79160-101">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="79160-102">語法</span><span class="sxs-lookup"><span data-stu-id="79160-102">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79160-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="79160-103">Attributes and Elements</span></span>  
 <span data-ttu-id="79160-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="79160-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79160-105">屬性</span><span class="sxs-lookup"><span data-stu-id="79160-105">Attributes</span></span>  
  
|<span data-ttu-id="79160-106">屬性</span><span class="sxs-lookup"><span data-stu-id="79160-106">Attribute</span></span>|<span data-ttu-id="79160-107">描述</span><span class="sxs-lookup"><span data-stu-id="79160-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79160-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="79160-108">maxReadPoolSize</span></span>|<span data-ttu-id="79160-109">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="79160-109">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="79160-110">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="79160-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="79160-111">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="79160-111">The default is 64.</span></span>|  
|<span data-ttu-id="79160-112">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="79160-112">maxSessionSize</span></span>|<span data-ttu-id="79160-113">正整數，設定用於編碼的緩衝區大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="79160-113">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="79160-114">較大的緩衝區會增加編碼速度，但是會犧牲工作集的大小。</span><span class="sxs-lookup"><span data-stu-id="79160-114">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="79160-115">預設值為 2048。</span><span class="sxs-lookup"><span data-stu-id="79160-115">The default is 2048.</span></span>|  
|<span data-ttu-id="79160-116">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="79160-116">maxWritePoolSize</span></span>|<span data-ttu-id="79160-117">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="79160-117">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="79160-118">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="79160-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="79160-119">預設值是 16。</span><span class="sxs-lookup"><span data-stu-id="79160-119">The default is 16.</span></span>|  
|<span data-ttu-id="79160-120">messageVersion</span><span class="sxs-lookup"><span data-stu-id="79160-120">messageVersion</span></span>|<span data-ttu-id="79160-121">指定已使用或必須使用的 SOAP 訊息和 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="79160-121">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79160-122">子元素</span><span class="sxs-lookup"><span data-stu-id="79160-122">Child Elements</span></span>  
  
|<span data-ttu-id="79160-123">項目</span><span class="sxs-lookup"><span data-stu-id="79160-123">Element</span></span>|<span data-ttu-id="79160-124">描述</span><span class="sxs-lookup"><span data-stu-id="79160-124">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="79160-125">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="79160-125">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="79160-126">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="79160-126">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79160-127">父項目</span><span class="sxs-lookup"><span data-stu-id="79160-127">Parent Elements</span></span>  
  
|<span data-ttu-id="79160-128">項目</span><span class="sxs-lookup"><span data-stu-id="79160-128">Element</span></span>|<span data-ttu-id="79160-129">描述</span><span class="sxs-lookup"><span data-stu-id="79160-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="79160-130">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="79160-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79160-131">備註</span><span class="sxs-lookup"><span data-stu-id="79160-131">Remarks</span></span>  
 <span data-ttu-id="79160-132">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="79160-132">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="79160-133">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="79160-133">Decoding is the reverse process.</span></span> <span data-ttu-id="79160-134">Windows Communication Foundation (WCF) 包含 SOAP 訊息的三種編碼類型：文字、二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="79160-134">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="79160-135">`binaryMessageEncoding` 項目會指定 XML 的 .NET 二進位格式，並且提供指定字元編碼以及要使用之 SOAP 和 WS-Addressing 版本的選項。</span><span class="sxs-lookup"><span data-stu-id="79160-135">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="79160-136">二進位訊息編碼器會以二進位編碼網路上的 Windows Communication Foundation (WCF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="79160-136">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="79160-137">雖然這個編碼會讓訊息傳輸速度非常快，但是會失去以 WS-\* 標準為基礎的互通性 (Interoperability)。</span><span class="sxs-lookup"><span data-stu-id="79160-137">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79160-138">範例</span><span class="sxs-lookup"><span data-stu-id="79160-138">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="79160-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79160-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="79160-140">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="79160-140">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="79160-141">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="79160-141">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="79160-142">繫結</span><span class="sxs-lookup"><span data-stu-id="79160-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="79160-143">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="79160-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="79160-144">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="79160-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
