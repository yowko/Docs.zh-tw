---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: a73085320eaf248887422316e1b7787b8654d71d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400494"
---
# <a name="compositeduplex"></a><span data-ttu-id="f465f-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="f465f-101">\<compositeDuplex></span></span>
<span data-ttu-id="f465f-102">定義繫結項目，這是當用戶端必須公開 (Expose) 服務的端點才能將訊息傳回用戶端時所使用的項目。</span><span class="sxs-lookup"><span data-stu-id="f465f-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
<span data-ttu-id="f465f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f465f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f465f-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f465f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f465f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f465f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f465f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="f465f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="f465f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="f465f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f465f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<compositeDuplex >**</span><span class="sxs-lookup"><span data-stu-id="f465f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f465f-109">語法</span><span class="sxs-lookup"><span data-stu-id="f465f-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f465f-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f465f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f465f-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f465f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f465f-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f465f-112">Attributes</span></span>  
  
|<span data-ttu-id="f465f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f465f-113">Attribute</span></span>|<span data-ttu-id="f465f-114">描述</span><span class="sxs-lookup"><span data-stu-id="f465f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f465f-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="f465f-115">clientBaseAddress</span></span>|<span data-ttu-id="f465f-116">URI，設定雙工模式中返回通道的位址。</span><span class="sxs-lookup"><span data-stu-id="f465f-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="f465f-117">服務會使用這個位址與用戶端接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="f465f-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="f465f-118">如果未設定此屬性，則會產生預設位址`full qualified name+default port\TemporaryIndigoAddress\guid`""。</span><span class="sxs-lookup"><span data-stu-id="f465f-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="f465f-119">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="f465f-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f465f-120">子元素</span><span class="sxs-lookup"><span data-stu-id="f465f-120">Child Elements</span></span>  
 <span data-ttu-id="f465f-121">None</span><span class="sxs-lookup"><span data-stu-id="f465f-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f465f-122">父項目</span><span class="sxs-lookup"><span data-stu-id="f465f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f465f-123">項目</span><span class="sxs-lookup"><span data-stu-id="f465f-123">Element</span></span>|<span data-ttu-id="f465f-124">說明</span><span class="sxs-lookup"><span data-stu-id="f465f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f465f-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="f465f-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="f465f-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="f465f-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f465f-127">備註</span><span class="sxs-lookup"><span data-stu-id="f465f-127">Remarks</span></span>  
 <span data-ttu-id="f465f-128">這個組態項目是和本身不允許雙工通訊的傳輸一起使用，例如 HTTP。</span><span class="sxs-lookup"><span data-stu-id="f465f-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="f465f-129">相反地，TCP 本身就允許雙工通訊，因此不需要使用這個繫結項目也可讓服務將訊息傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="f465f-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="f465f-130">用戶端必須公開位址，才能讓服務接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="f465f-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="f465f-131">這個用戶端位址是由 `clientBaseAddress` 屬性提供。</span><span class="sxs-lookup"><span data-stu-id="f465f-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="f465f-132">請注意，如果使用者未明確設定此屬性，則 Windows Communication Foundation (WCF) 會自動產生 ClientBaseAddress。</span><span class="sxs-lookup"><span data-stu-id="f465f-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f465f-133">範例</span><span class="sxs-lookup"><span data-stu-id="f465f-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f465f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f465f-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f465f-135">繫結</span><span class="sxs-lookup"><span data-stu-id="f465f-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f465f-136">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="f465f-136">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f465f-137">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="f465f-137">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f465f-138">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f465f-138">\<customBinding></span></span>](custombinding.md)
