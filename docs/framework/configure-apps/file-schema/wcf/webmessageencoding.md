---
title: '&lt;webMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: e8b45075c7c07efc49f84526382352a5b1a556b1
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148665"
---
# <a name="ltwebmessageencodinggt"></a><span data-ttu-id="f6e16-102">&lt;webMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="f6e16-102">&lt;webMessageEncoding&gt;</span></span>
<span data-ttu-id="f6e16-103">啟用在用於 Windows Communication Foundation (WCF) 繫結時，要讀取與寫入的純文字 XML、JavaScript Object Notation (JSON) 訊息編碼和「未經處理」二進位內容。</span><span class="sxs-lookup"><span data-stu-id="f6e16-103">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
 <span data-ttu-id="f6e16-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f6e16-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f6e16-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="f6e16-105">\<bindings></span></span>  
<span data-ttu-id="f6e16-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f6e16-106">\<customBinding></span></span>  
<span data-ttu-id="f6e16-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="f6e16-107">\<binding></span></span>  
<span data-ttu-id="f6e16-108">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="f6e16-108">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6e16-109">語法</span><span class="sxs-lookup"><span data-stu-id="f6e16-109">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6e16-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f6e16-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f6e16-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f6e16-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6e16-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f6e16-112">Attributes</span></span>  
  
|<span data-ttu-id="f6e16-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f6e16-113">Attribute</span></span>|<span data-ttu-id="f6e16-114">描述</span><span class="sxs-lookup"><span data-stu-id="f6e16-114">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="f6e16-115">可以同時讀取，而不需配置新讀取器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="f6e16-115">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="f6e16-116">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="f6e16-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f6e16-117">每個內部編碼器 (text、JSON 與 "raw") 都預設有 64 個讀取器。</span><span class="sxs-lookup"><span data-stu-id="f6e16-117">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="f6e16-118">增加這個數字會增加記憶體消耗量，但是可讓編碼器做好處理傳入訊息量突然暴增的準備，因為編碼器可以使用集區中已經建立的讀取器，而不必建立新的讀取器。</span><span class="sxs-lookup"><span data-stu-id="f6e16-118">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="f6e16-119">可以同時傳送，而不需配置新寫入器的訊息數。</span><span class="sxs-lookup"><span data-stu-id="f6e16-119">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="f6e16-120">較大的集區大小可讓系統容許更多活動失效的情況，但是會產生較大的工作集。</span><span class="sxs-lookup"><span data-stu-id="f6e16-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f6e16-121">每個內部編碼器 (text、JSON 與 "raw") 都預設有 16 個寫入器。</span><span class="sxs-lookup"><span data-stu-id="f6e16-121">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="f6e16-122">增加這個數字會增加記憶體消耗量，但是可讓編碼器做好處理傳出訊息量突然暴增的準備，因為編碼器可以使用集區中已經建立的寫入器，而不必建立新的寫入器。</span><span class="sxs-lookup"><span data-stu-id="f6e16-122">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="f6e16-123">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f6e16-123">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f6e16-124">有效值為：</span><span class="sxs-lookup"><span data-stu-id="f6e16-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="f6e16-125">-UnicodeFffeTextEncoding:Unicode Bigendian 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f6e16-125">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="f6e16-126">-Utf16textencoding:unicodeUnicode 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f6e16-126">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="f6e16-127">-Utf8TextEncoding:8 位元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f6e16-127">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="f6e16-128">預設為 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="f6e16-128">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="f6e16-129">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="f6e16-129">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6e16-130">子元素</span><span class="sxs-lookup"><span data-stu-id="f6e16-130">Child Elements</span></span>  
  
|<span data-ttu-id="f6e16-131">項目</span><span class="sxs-lookup"><span data-stu-id="f6e16-131">Element</span></span>|<span data-ttu-id="f6e16-132">描述</span><span class="sxs-lookup"><span data-stu-id="f6e16-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6e16-133">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="f6e16-133">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="f6e16-134">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="f6e16-134">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f6e16-135">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="f6e16-135">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f6e16-136">父項目</span><span class="sxs-lookup"><span data-stu-id="f6e16-136">Parent Elements</span></span>  
  
|<span data-ttu-id="f6e16-137">項目</span><span class="sxs-lookup"><span data-stu-id="f6e16-137">Element</span></span>|<span data-ttu-id="f6e16-138">描述</span><span class="sxs-lookup"><span data-stu-id="f6e16-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6e16-139">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="f6e16-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f6e16-140">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="f6e16-140">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6e16-141">備註</span><span class="sxs-lookup"><span data-stu-id="f6e16-141">Remarks</span></span>  
 <span data-ttu-id="f6e16-142">編碼是將訊息轉換成位元組序列的處理序，</span><span class="sxs-lookup"><span data-stu-id="f6e16-142">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="f6e16-143">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="f6e16-143">Decoding is the reverse process.</span></span> <span data-ttu-id="f6e16-144">這些處理序需要字元編碼的規格。</span><span class="sxs-lookup"><span data-stu-id="f6e16-144">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="f6e16-145">`webMessageEncoding` 項目的運作方式是委派給一系列的內部編碼器，以處理純文字 XML 和 JSON 編碼以及「原始」二進位資料。</span><span class="sxs-lookup"><span data-stu-id="f6e16-145">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="f6e16-146">這項委派是由複合訊息編碼器所完成。</span><span class="sxs-lookup"><span data-stu-id="f6e16-146">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="f6e16-147">在不使用 `webHttpBinding` 項目使用之 SOAP 傳訊的案例中，會使用這個繫結項目及其複合編碼器來控制其編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f6e16-147">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="f6e16-148">這些案例包括 "Plain Old XML" (POX)、代表性狀態傳輸 (Representational State Transfer，REST)、Really Simple Syndication (RSS) 和 Atom 新聞訂閱，以及 Asynchronous JavaScript 與 XML (AJAX)。</span><span class="sxs-lookup"><span data-stu-id="f6e16-148">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="f6e16-149">複合訊息編碼器不支援 SOAP 或 WS-Addressing。</span><span class="sxs-lookup"><span data-stu-id="f6e16-149">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="f6e16-150">此繫結項目可藉由 `writeEncoding` 屬性，透過寫入字元編碼的方式進行設定。</span><span class="sxs-lookup"><span data-stu-id="f6e16-150">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="f6e16-151">提供的 <xref:System.Text.Encoding> 值會指定 JSON 和 Textual XML 案例在寫入時的行為。</span><span class="sxs-lookup"><span data-stu-id="f6e16-151">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="f6e16-152">在讀取時，任何有效的訊息編碼和文字編碼都是可解讀的。</span><span class="sxs-lookup"><span data-stu-id="f6e16-152">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="f6e16-153">`maxReadPoolSize` 和 `maxWritePoolSize` 也可以用來設定要分別配置之讀取器和寫入器的最大數目。</span><span class="sxs-lookup"><span data-stu-id="f6e16-153">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="f6e16-154">根據預設，將配置 64 個讀取器和 16 個寫入器。</span><span class="sxs-lookup"><span data-stu-id="f6e16-154">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="f6e16-155">預設複雜度條件約束也會設定使用[ \<readerQuotas >](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)項目，以防止阻絕服務 (DOS) 類別攻擊試圖使用訊息複雜性困住端點處理資源。</span><span class="sxs-lookup"><span data-stu-id="f6e16-155">Default complexity constraints are also set using the [\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6e16-156">範例</span><span class="sxs-lookup"><span data-stu-id="f6e16-156">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f6e16-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6e16-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [<span data-ttu-id="f6e16-158">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="f6e16-158">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="f6e16-159">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="f6e16-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="f6e16-160">繫結</span><span class="sxs-lookup"><span data-stu-id="f6e16-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f6e16-161">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="f6e16-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f6e16-162">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="f6e16-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f6e16-163">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f6e16-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
