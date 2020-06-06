---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739058"
---
# \<byteStreamMessageEncoding>
<span data-ttu-id="46f5c-101">將訊息編碼指定為位元組資料流，且含有指定字元編碼的選項。</span><span class="sxs-lookup"><span data-stu-id="46f5c-101">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="46f5c-102">語法</span><span class="sxs-lookup"><span data-stu-id="46f5c-102">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46f5c-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="46f5c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="46f5c-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="46f5c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46f5c-105">屬性</span><span class="sxs-lookup"><span data-stu-id="46f5c-105">Attributes</span></span>  
  
|<span data-ttu-id="46f5c-106">屬性</span><span class="sxs-lookup"><span data-stu-id="46f5c-106">Attribute</span></span>|<span data-ttu-id="46f5c-107">描述</span><span class="sxs-lookup"><span data-stu-id="46f5c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46f5c-108">messageVersion</span><span class="sxs-lookup"><span data-stu-id="46f5c-108">messageVersion</span></span>|<span data-ttu-id="46f5c-109">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="46f5c-109">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="46f5c-110">這個屬性只能設定為 <xref:System.ServiceModel.Channels.MessageVersion.None%2A> 的訊息版本值。</span><span class="sxs-lookup"><span data-stu-id="46f5c-110">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="46f5c-111">位元組資料流訊息編碼器不支援任何其他的訊息版本。</span><span class="sxs-lookup"><span data-stu-id="46f5c-111">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="46f5c-112">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="46f5c-112">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46f5c-113">子元素</span><span class="sxs-lookup"><span data-stu-id="46f5c-113">Child Elements</span></span>  
  
|<span data-ttu-id="46f5c-114">元素</span><span class="sxs-lookup"><span data-stu-id="46f5c-114">Element</span></span>|<span data-ttu-id="46f5c-115">描述</span><span class="sxs-lookup"><span data-stu-id="46f5c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="46f5c-116">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="46f5c-116">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="46f5c-117">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="46f5c-117">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46f5c-118">父項目</span><span class="sxs-lookup"><span data-stu-id="46f5c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="46f5c-119">元素</span><span class="sxs-lookup"><span data-stu-id="46f5c-119">Element</span></span>|<span data-ttu-id="46f5c-120">描述</span><span class="sxs-lookup"><span data-stu-id="46f5c-120">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="46f5c-121">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="46f5c-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46f5c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46f5c-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="46f5c-123">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="46f5c-123">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="46f5c-124">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="46f5c-124">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="46f5c-125">繫結</span><span class="sxs-lookup"><span data-stu-id="46f5c-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="46f5c-126">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="46f5c-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="46f5c-127">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="46f5c-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
