---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739058"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="3f5ff-101">\<byteStreamMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="3f5ff-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="3f5ff-102">將訊息編碼指定為位元組資料流，且含有指定字元編碼的選項。</span><span class="sxs-lookup"><span data-stu-id="3f5ff-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
<span data-ttu-id="3f5ff-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3f5ff-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3f5ff-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="3f5ff-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3f5ff-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="3f5ff-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3f5ff-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="3f5ff-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="3f5ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="3f5ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="3f5ff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<byteStreamMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="3f5ff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f5ff-109">語法</span><span class="sxs-lookup"><span data-stu-id="3f5ff-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f5ff-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3f5ff-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3f5ff-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3f5ff-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f5ff-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3f5ff-112">Attributes</span></span>  
  
|<span data-ttu-id="3f5ff-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3f5ff-113">Attribute</span></span>|<span data-ttu-id="3f5ff-114">描述</span><span class="sxs-lookup"><span data-stu-id="3f5ff-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f5ff-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="3f5ff-115">messageVersion</span></span>|<span data-ttu-id="3f5ff-116">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="3f5ff-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="3f5ff-117">這個屬性只能設定為 <xref:System.ServiceModel.Channels.MessageVersion.None%2A> 的訊息版本值。</span><span class="sxs-lookup"><span data-stu-id="3f5ff-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="3f5ff-118">位元組資料流訊息編碼器不支援任何其他的訊息版本。</span><span class="sxs-lookup"><span data-stu-id="3f5ff-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="3f5ff-119">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="3f5ff-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f5ff-120">子項目</span><span class="sxs-lookup"><span data-stu-id="3f5ff-120">Child Elements</span></span>  
  
|<span data-ttu-id="3f5ff-121">項目</span><span class="sxs-lookup"><span data-stu-id="3f5ff-121">Element</span></span>|<span data-ttu-id="3f5ff-122">描述</span><span class="sxs-lookup"><span data-stu-id="3f5ff-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f5ff-123">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f5ff-123">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="3f5ff-124">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="3f5ff-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3f5ff-125">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="3f5ff-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f5ff-126">父項目</span><span class="sxs-lookup"><span data-stu-id="3f5ff-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3f5ff-127">項目</span><span class="sxs-lookup"><span data-stu-id="3f5ff-127">Element</span></span>|<span data-ttu-id="3f5ff-128">描述</span><span class="sxs-lookup"><span data-stu-id="3f5ff-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f5ff-129">\<binding ></span><span class="sxs-lookup"><span data-stu-id="3f5ff-129">\<binding></span></span>](bindings.md)|<span data-ttu-id="3f5ff-130">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="3f5ff-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f5ff-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="3f5ff-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="3f5ff-132">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="3f5ff-132">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="3f5ff-133">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="3f5ff-133">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="3f5ff-134">繫結</span><span class="sxs-lookup"><span data-stu-id="3f5ff-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3f5ff-135">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="3f5ff-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3f5ff-136">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3f5ff-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3f5ff-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3f5ff-137">\<customBinding></span></span>](custombinding.md)
