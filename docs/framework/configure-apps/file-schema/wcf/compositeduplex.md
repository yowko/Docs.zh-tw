---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736786"
---
# <a name="compositeduplex"></a><span data-ttu-id="66a6b-101">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="66a6b-101">\<compositeDuplex></span></span>
<span data-ttu-id="66a6b-102">定義繫結項目，這是當用戶端必須公開 (Expose) 服務的端點才能將訊息傳回用戶端時所使用的項目。</span><span class="sxs-lookup"><span data-stu-id="66a6b-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
<span data-ttu-id="66a6b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="66a6b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="66a6b-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="66a6b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="66a6b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="66a6b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="66a6b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="66a6b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="66a6b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="66a6b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="66a6b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<compositeDuplex >**</span><span class="sxs-lookup"><span data-stu-id="66a6b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a6b-109">語法</span><span class="sxs-lookup"><span data-stu-id="66a6b-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66a6b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="66a6b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="66a6b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="66a6b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66a6b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="66a6b-112">Attributes</span></span>  
  
|<span data-ttu-id="66a6b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="66a6b-113">Attribute</span></span>|<span data-ttu-id="66a6b-114">描述</span><span class="sxs-lookup"><span data-stu-id="66a6b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66a6b-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="66a6b-115">clientBaseAddress</span></span>|<span data-ttu-id="66a6b-116">URI，設定雙工模式中返回通道的位址。</span><span class="sxs-lookup"><span data-stu-id="66a6b-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="66a6b-117">服務會使用這個位址與用戶端接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="66a6b-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="66a6b-118">如果未設定此屬性，則會產生預設位址 "`full qualified name+default port\TemporaryIndigoAddress\guid`"。</span><span class="sxs-lookup"><span data-stu-id="66a6b-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="66a6b-119">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="66a6b-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66a6b-120">子項目</span><span class="sxs-lookup"><span data-stu-id="66a6b-120">Child Elements</span></span>  
 <span data-ttu-id="66a6b-121">None</span><span class="sxs-lookup"><span data-stu-id="66a6b-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66a6b-122">父項目</span><span class="sxs-lookup"><span data-stu-id="66a6b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="66a6b-123">項目</span><span class="sxs-lookup"><span data-stu-id="66a6b-123">Element</span></span>|<span data-ttu-id="66a6b-124">描述</span><span class="sxs-lookup"><span data-stu-id="66a6b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66a6b-125">\<binding ></span><span class="sxs-lookup"><span data-stu-id="66a6b-125">\<binding></span></span>](bindings.md)|<span data-ttu-id="66a6b-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="66a6b-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66a6b-127">備註</span><span class="sxs-lookup"><span data-stu-id="66a6b-127">Remarks</span></span>  
 <span data-ttu-id="66a6b-128">這個組態項目是和本身不允許雙工通訊的傳輸一起使用，例如 HTTP。</span><span class="sxs-lookup"><span data-stu-id="66a6b-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="66a6b-129">相反地，TCP 本身就允許雙工通訊，因此不需要使用這個繫結項目也可讓服務將訊息傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="66a6b-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="66a6b-130">用戶端必須公開位址，才能讓服務接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="66a6b-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="66a6b-131">這個用戶端位址是由 `clientBaseAddress` 屬性提供。</span><span class="sxs-lookup"><span data-stu-id="66a6b-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="66a6b-132">請注意，如果使用者未明確設定此屬性，則 Windows Communication Foundation (WCF) 會自動產生 ClientBaseAddress。</span><span class="sxs-lookup"><span data-stu-id="66a6b-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66a6b-133">範例</span><span class="sxs-lookup"><span data-stu-id="66a6b-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="66a6b-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="66a6b-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="66a6b-135">繫結</span><span class="sxs-lookup"><span data-stu-id="66a6b-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="66a6b-136">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="66a6b-136">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="66a6b-137">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="66a6b-137">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="66a6b-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="66a6b-138">\<customBinding></span></span>](custombinding.md)
