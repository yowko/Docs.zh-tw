---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 4b031bfb0d0979dc99df13c104a712d6dd771e8a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422970"
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="2a2df-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="2a2df-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="2a2df-103">將訊息編碼指定為位元組資料流，且含有指定字元編碼的選項。</span><span class="sxs-lookup"><span data-stu-id="2a2df-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="2a2df-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2a2df-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2a2df-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2a2df-105">\<bindings></span></span>  
<span data-ttu-id="2a2df-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2a2df-106">\<customBinding></span></span>  
<span data-ttu-id="2a2df-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2a2df-107">\<binding></span></span>  
<span data-ttu-id="2a2df-108">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="2a2df-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a2df-109">語法</span><span class="sxs-lookup"><span data-stu-id="2a2df-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a2df-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2a2df-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a2df-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2a2df-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a2df-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2a2df-112">Attributes</span></span>  
  
|<span data-ttu-id="2a2df-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2a2df-113">Attribute</span></span>|<span data-ttu-id="2a2df-114">描述</span><span class="sxs-lookup"><span data-stu-id="2a2df-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a2df-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="2a2df-115">messageVersion</span></span>|<span data-ttu-id="2a2df-116">指定使用這個繫結所傳送訊息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="2a2df-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="2a2df-117">這個屬性只能設定為 <xref:System.ServiceModel.Channels.MessageVersion.None%2A> 的訊息版本值。</span><span class="sxs-lookup"><span data-stu-id="2a2df-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="2a2df-118">位元組資料流訊息編碼器不支援任何其他的訊息版本。</span><span class="sxs-lookup"><span data-stu-id="2a2df-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="2a2df-119">此屬性的型別為 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="2a2df-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a2df-120">子元素</span><span class="sxs-lookup"><span data-stu-id="2a2df-120">Child Elements</span></span>  
  
|<span data-ttu-id="2a2df-121">項目</span><span class="sxs-lookup"><span data-stu-id="2a2df-121">Element</span></span>|<span data-ttu-id="2a2df-122">描述</span><span class="sxs-lookup"><span data-stu-id="2a2df-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a2df-123">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="2a2df-123">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="2a2df-124">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="2a2df-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2a2df-125">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="2a2df-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a2df-126">父項目</span><span class="sxs-lookup"><span data-stu-id="2a2df-126">Parent Elements</span></span>  
  
|<span data-ttu-id="2a2df-127">項目</span><span class="sxs-lookup"><span data-stu-id="2a2df-127">Element</span></span>|<span data-ttu-id="2a2df-128">描述</span><span class="sxs-lookup"><span data-stu-id="2a2df-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a2df-129">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2a2df-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2a2df-130">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="2a2df-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a2df-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a2df-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="2a2df-132">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="2a2df-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="2a2df-133">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="2a2df-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="2a2df-134">繫結</span><span class="sxs-lookup"><span data-stu-id="2a2df-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2a2df-135">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="2a2df-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2a2df-136">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="2a2df-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2a2df-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2a2df-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
