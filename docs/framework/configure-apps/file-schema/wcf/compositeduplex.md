---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: f8615637a0fa6d0fff594ef1970711ac408f02f3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264501"
---
# <a name="compositeduplex"></a><span data-ttu-id="abb6a-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="abb6a-101">\<compositeDuplex></span></span>
<span data-ttu-id="abb6a-102">定義繫結項目，這是當用戶端必須公開 (Expose) 服務的端點才能將訊息傳回用戶端時所使用的項目。</span><span class="sxs-lookup"><span data-stu-id="abb6a-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="abb6a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="abb6a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="abb6a-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="abb6a-104">\<bindings></span></span>  
<span data-ttu-id="abb6a-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="abb6a-105">\<customBinding></span></span>  
<span data-ttu-id="abb6a-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="abb6a-106">\<binding></span></span>  
<span data-ttu-id="abb6a-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="abb6a-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb6a-108">語法</span><span class="sxs-lookup"><span data-stu-id="abb6a-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abb6a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="abb6a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="abb6a-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="abb6a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abb6a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="abb6a-111">Attributes</span></span>  
  
|<span data-ttu-id="abb6a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="abb6a-112">Attribute</span></span>|<span data-ttu-id="abb6a-113">描述</span><span class="sxs-lookup"><span data-stu-id="abb6a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="abb6a-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="abb6a-114">clientBaseAddress</span></span>|<span data-ttu-id="abb6a-115">URI，設定雙工模式中返回通道的位址。</span><span class="sxs-lookup"><span data-stu-id="abb6a-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="abb6a-116">服務會使用這個位址與用戶端接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="abb6a-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="abb6a-117">如果這個屬性未設定，預設位址"`full qualified name+default port\TemporaryIndigoAddress\guid`」 產生。</span><span class="sxs-lookup"><span data-stu-id="abb6a-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="abb6a-118">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="abb6a-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abb6a-119">子元素</span><span class="sxs-lookup"><span data-stu-id="abb6a-119">Child Elements</span></span>  
 <span data-ttu-id="abb6a-120">無</span><span class="sxs-lookup"><span data-stu-id="abb6a-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="abb6a-121">父項目</span><span class="sxs-lookup"><span data-stu-id="abb6a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="abb6a-122">項目</span><span class="sxs-lookup"><span data-stu-id="abb6a-122">Element</span></span>|<span data-ttu-id="abb6a-123">描述</span><span class="sxs-lookup"><span data-stu-id="abb6a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abb6a-124">\<binding></span><span class="sxs-lookup"><span data-stu-id="abb6a-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="abb6a-125">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="abb6a-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abb6a-126">備註</span><span class="sxs-lookup"><span data-stu-id="abb6a-126">Remarks</span></span>  
 <span data-ttu-id="abb6a-127">這個組態項目是和本身不允許雙工通訊的傳輸一起使用，例如 HTTP。</span><span class="sxs-lookup"><span data-stu-id="abb6a-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="abb6a-128">相反地，TCP 本身就允許雙工通訊，因此不需要使用這個繫結項目也可讓服務將訊息傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="abb6a-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="abb6a-129">用戶端必須公開位址，才能讓服務接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="abb6a-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="abb6a-130">這個用戶端位址是由 `clientBaseAddress` 屬性提供。</span><span class="sxs-lookup"><span data-stu-id="abb6a-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="abb6a-131">請注意，如果使用者未明確設定此屬性，則 Windows Communication Foundation (WCF) 會自動產生 ClientBaseAddress。</span><span class="sxs-lookup"><span data-stu-id="abb6a-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abb6a-132">範例</span><span class="sxs-lookup"><span data-stu-id="abb6a-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="abb6a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abb6a-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="abb6a-134">繫結</span><span class="sxs-lookup"><span data-stu-id="abb6a-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="abb6a-135">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="abb6a-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="abb6a-136">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="abb6a-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="abb6a-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="abb6a-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
