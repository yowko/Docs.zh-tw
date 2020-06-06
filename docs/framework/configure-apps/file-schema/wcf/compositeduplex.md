---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736786"
---
# \<compositeDuplex>
<span data-ttu-id="1902b-101">定義繫結項目，這是當用戶端必須公開 (Expose) 服務的端點才能將訊息傳回用戶端時所使用的項目。</span><span class="sxs-lookup"><span data-stu-id="1902b-101">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="1902b-102">語法</span><span class="sxs-lookup"><span data-stu-id="1902b-102">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1902b-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1902b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1902b-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1902b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1902b-105">屬性</span><span class="sxs-lookup"><span data-stu-id="1902b-105">Attributes</span></span>  
  
|<span data-ttu-id="1902b-106">屬性</span><span class="sxs-lookup"><span data-stu-id="1902b-106">Attribute</span></span>|<span data-ttu-id="1902b-107">描述</span><span class="sxs-lookup"><span data-stu-id="1902b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1902b-108">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="1902b-108">clientBaseAddress</span></span>|<span data-ttu-id="1902b-109">URI，設定雙工模式中返回通道的位址。</span><span class="sxs-lookup"><span data-stu-id="1902b-109">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="1902b-110">服務會使用這個位址與用戶端接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="1902b-110">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="1902b-111">如果未設定此屬性， `full qualified name+default port\TemporaryIndigoAddress\guid` 則會產生預設位址 ""。</span><span class="sxs-lookup"><span data-stu-id="1902b-111">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="1902b-112">預設值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="1902b-112">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1902b-113">子元素</span><span class="sxs-lookup"><span data-stu-id="1902b-113">Child Elements</span></span>  
 <span data-ttu-id="1902b-114">無</span><span class="sxs-lookup"><span data-stu-id="1902b-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1902b-115">父項目</span><span class="sxs-lookup"><span data-stu-id="1902b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="1902b-116">元素</span><span class="sxs-lookup"><span data-stu-id="1902b-116">Element</span></span>|<span data-ttu-id="1902b-117">描述</span><span class="sxs-lookup"><span data-stu-id="1902b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="1902b-118">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="1902b-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1902b-119">備註</span><span class="sxs-lookup"><span data-stu-id="1902b-119">Remarks</span></span>  
 <span data-ttu-id="1902b-120">這個組態項目是和本身不允許雙工通訊的傳輸一起使用，例如 HTTP。</span><span class="sxs-lookup"><span data-stu-id="1902b-120">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="1902b-121">相反地，TCP 本身就允許雙工通訊，因此不需要使用這個繫結項目也可讓服務將訊息傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="1902b-121">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="1902b-122">用戶端必須公開位址，才能讓服務接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="1902b-122">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="1902b-123">這個用戶端位址是由 `clientBaseAddress` 屬性提供。</span><span class="sxs-lookup"><span data-stu-id="1902b-123">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="1902b-124">請注意，如果使用者未明確設定此屬性，則 Windows Communication Foundation (WCF) 會自動產生 ClientBaseAddress。</span><span class="sxs-lookup"><span data-stu-id="1902b-124">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1902b-125">範例</span><span class="sxs-lookup"><span data-stu-id="1902b-125">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="1902b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1902b-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1902b-127">繫結</span><span class="sxs-lookup"><span data-stu-id="1902b-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1902b-128">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="1902b-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1902b-129">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="1902b-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
