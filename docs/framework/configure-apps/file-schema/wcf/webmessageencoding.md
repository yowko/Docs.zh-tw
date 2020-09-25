---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: b250b64e1f073e00e4047ab6931a00d0b93b55b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177874"
---
# \<webMessageEncoding>

<span data-ttu-id="cdbab-101">啟用在用於 Windows Communication Foundation (WCF) 繫結時，要讀取與寫入的純文字 XML、JavaScript Object Notation (JSON) 訊息編碼和「未經處理」二進位內容。</span><span class="sxs-lookup"><span data-stu-id="cdbab-101">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="cdbab-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="cdbab-102">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdbab-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cdbab-103">Attributes and Elements</span></span>  

 <span data-ttu-id="cdbab-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cdbab-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdbab-105">屬性</span><span class="sxs-lookup"><span data-stu-id="cdbab-105">Attributes</span></span>  
  
|<span data-ttu-id="cdbab-106">屬性</span><span class="sxs-lookup"><span data-stu-id="cdbab-106">Attribute</span></span>|<span data-ttu-id="cdbab-107">描述</span><span class="sxs-lookup"><span data-stu-id="cdbab-107">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="cdbab-108">可以同時讀取，而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="cdbab-108">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="cdbab-109">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="cdbab-109">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="cdbab-110">每個內部編碼器 (text、JSON 與 "raw") 都預設有 64 個讀取器。</span><span class="sxs-lookup"><span data-stu-id="cdbab-110">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="cdbab-111">增加這個數字會增加記憶體消耗量，但是可讓編碼器做好處理傳入訊息量突然暴增的準備，因為編碼器可以使用集區中已經建立的讀取器，而不必建立新的讀取器。</span><span class="sxs-lookup"><span data-stu-id="cdbab-111">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="cdbab-112">可以同時傳送，而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="cdbab-112">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="cdbab-113">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="cdbab-113">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="cdbab-114">每個內部編碼器 (text、JSON 與 "raw") 都預設有 16 個寫入器。</span><span class="sxs-lookup"><span data-stu-id="cdbab-114">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="cdbab-115">增加這個數字會增加記憶體消耗量，但是可讓編碼器做好處理傳出訊息量突然暴增的準備，因為編碼器可以使用集區中已經建立的寫入器，而不必建立新的寫入器。</span><span class="sxs-lookup"><span data-stu-id="cdbab-115">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="cdbab-116">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="cdbab-116">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="cdbab-117">有效值為：</span><span class="sxs-lookup"><span data-stu-id="cdbab-117">Valid values are:</span></span><br /><br /> <span data-ttu-id="cdbab-118">-UnicodeFffeTextEncoding： Unicode Big Endian 編碼。</span><span class="sxs-lookup"><span data-stu-id="cdbab-118">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="cdbab-119">-Utf16TextEncoding： Unicode 編碼。</span><span class="sxs-lookup"><span data-stu-id="cdbab-119">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="cdbab-120">-Utf8TextEncoding：8位編碼。</span><span class="sxs-lookup"><span data-stu-id="cdbab-120">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="cdbab-121">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="cdbab-121">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="cdbab-122">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="cdbab-122">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdbab-123">子元素</span><span class="sxs-lookup"><span data-stu-id="cdbab-123">Child Elements</span></span>  
  
|<span data-ttu-id="cdbab-124">項目</span><span class="sxs-lookup"><span data-stu-id="cdbab-124">Element</span></span>|<span data-ttu-id="cdbab-125">描述</span><span class="sxs-lookup"><span data-stu-id="cdbab-125">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="cdbab-126">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="cdbab-126">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="cdbab-127">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="cdbab-127">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdbab-128">父項目</span><span class="sxs-lookup"><span data-stu-id="cdbab-128">Parent Elements</span></span>  
  
|<span data-ttu-id="cdbab-129">項目</span><span class="sxs-lookup"><span data-stu-id="cdbab-129">Element</span></span>|<span data-ttu-id="cdbab-130">描述</span><span class="sxs-lookup"><span data-stu-id="cdbab-130">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="cdbab-131">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="cdbab-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdbab-132">備註</span><span class="sxs-lookup"><span data-stu-id="cdbab-132">Remarks</span></span>  

 <span data-ttu-id="cdbab-133">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="cdbab-133">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="cdbab-134">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="cdbab-134">Decoding is the reverse process.</span></span> <span data-ttu-id="cdbab-135">這些處理序需要字元編碼的規格。</span><span class="sxs-lookup"><span data-stu-id="cdbab-135">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="cdbab-136">`webMessageEncoding` 項目的運作方式是委派給一系列的內部編碼器，以處理純文字 XML 和 JSON 編碼以及「原始」二進位資料。</span><span class="sxs-lookup"><span data-stu-id="cdbab-136">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="cdbab-137">這項委派是由複合訊息編碼器所完成。</span><span class="sxs-lookup"><span data-stu-id="cdbab-137">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="cdbab-138">在不使用 `webHttpBinding` 項目使用之 SOAP 傳訊的案例中，會使用這個繫結項目及其複合編碼器來控制其編碼方式。</span><span class="sxs-lookup"><span data-stu-id="cdbab-138">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="cdbab-139">這些案例包括 "Plain Old XML" (POX)、代表性狀態傳輸 (Representational State Transfer，REST)、Really Simple Syndication (RSS) 和 Atom 新聞訂閱，以及 Asynchronous JavaScript 與 XML (AJAX)。</span><span class="sxs-lookup"><span data-stu-id="cdbab-139">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="cdbab-140">複合訊息編碼器不支援 SOAP 或 WS-Addressing。</span><span class="sxs-lookup"><span data-stu-id="cdbab-140">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="cdbab-141">此繫結項目可藉由 `writeEncoding` 屬性，透過寫入字元編碼的方式進行設定。</span><span class="sxs-lookup"><span data-stu-id="cdbab-141">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="cdbab-142">提供的 <xref:System.Text.Encoding> 值會指定 JSON 和 Textual XML 案例在寫入時的行為。</span><span class="sxs-lookup"><span data-stu-id="cdbab-142">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="cdbab-143">在讀取時，任何有效的訊息編碼和文字編碼都是可解讀的。</span><span class="sxs-lookup"><span data-stu-id="cdbab-143">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="cdbab-144">`maxReadPoolSize` 和 `maxWritePoolSize` 也可以用來設定要分別配置之讀取器和寫入器的最大數目。</span><span class="sxs-lookup"><span data-stu-id="cdbab-144">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="cdbab-145">根據預設，將配置 64 個讀取器和 16 個寫入器。</span><span class="sxs-lookup"><span data-stu-id="cdbab-145">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="cdbab-146">預設複雜度條件約束也會使用專案 [\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) 來設定，以防止阻絕服務的類別 (DOS) 攻擊嘗試使用訊息複雜性來系結端點處理資源。</span><span class="sxs-lookup"><span data-stu-id="cdbab-146">Default complexity constraints are also set using the [\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdbab-147">範例</span><span class="sxs-lookup"><span data-stu-id="cdbab-147">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="cdbab-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdbab-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="cdbab-149">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="cdbab-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="cdbab-150">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="cdbab-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="cdbab-151">繫結</span><span class="sxs-lookup"><span data-stu-id="cdbab-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cdbab-152">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="cdbab-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cdbab-153">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="cdbab-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
