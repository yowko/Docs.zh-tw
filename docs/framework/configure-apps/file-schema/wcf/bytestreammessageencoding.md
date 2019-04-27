---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: ce9f282ea1101befe3bf99762efa61e9b47b74cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673343"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="2e95d-101">\<byteStreamMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="2e95d-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="2e95d-102">將訊息編碼指定為位元組資料流，且含有指定字元編碼的選項。</span><span class="sxs-lookup"><span data-stu-id="2e95d-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="2e95d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2e95d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2e95d-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="2e95d-104">\<bindings></span></span>  
<span data-ttu-id="2e95d-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2e95d-105">\<customBinding></span></span>  
<span data-ttu-id="2e95d-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="2e95d-106">\<binding></span></span>  
<span data-ttu-id="2e95d-107">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="2e95d-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e95d-108">語法</span><span class="sxs-lookup"><span data-stu-id="2e95d-108">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e95d-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2e95d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2e95d-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2e95d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e95d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2e95d-111">Attributes</span></span>  
  
|<span data-ttu-id="2e95d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2e95d-112">Attribute</span></span>|<span data-ttu-id="2e95d-113">描述</span><span class="sxs-lookup"><span data-stu-id="2e95d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2e95d-114">messageVersion</span><span class="sxs-lookup"><span data-stu-id="2e95d-114">messageVersion</span></span>|<span data-ttu-id="2e95d-115">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="2e95d-115">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="2e95d-116">這個屬性只能設定為 <xref:System.ServiceModel.Channels.MessageVersion.None%2A> 的訊息版本值。</span><span class="sxs-lookup"><span data-stu-id="2e95d-116">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="2e95d-117">位元組資料流訊息編碼器不支援任何其他的訊息版本。</span><span class="sxs-lookup"><span data-stu-id="2e95d-117">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="2e95d-118">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="2e95d-118">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e95d-119">子元素</span><span class="sxs-lookup"><span data-stu-id="2e95d-119">Child Elements</span></span>  
  
|<span data-ttu-id="2e95d-120">項目</span><span class="sxs-lookup"><span data-stu-id="2e95d-120">Element</span></span>|<span data-ttu-id="2e95d-121">描述</span><span class="sxs-lookup"><span data-stu-id="2e95d-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e95d-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2e95d-122">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="2e95d-123">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="2e95d-123">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2e95d-124">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="2e95d-124">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e95d-125">父項目</span><span class="sxs-lookup"><span data-stu-id="2e95d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2e95d-126">項目</span><span class="sxs-lookup"><span data-stu-id="2e95d-126">Element</span></span>|<span data-ttu-id="2e95d-127">描述</span><span class="sxs-lookup"><span data-stu-id="2e95d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e95d-128">\<binding></span><span class="sxs-lookup"><span data-stu-id="2e95d-128">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2e95d-129">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="2e95d-129">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e95d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e95d-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="2e95d-131">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="2e95d-131">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [<span data-ttu-id="2e95d-132">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="2e95d-132">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="2e95d-133">繫結</span><span class="sxs-lookup"><span data-stu-id="2e95d-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="2e95d-134">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="2e95d-134">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2e95d-135">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="2e95d-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2e95d-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2e95d-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
