---
title: '&lt;compositeDuplex&gt;'
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: ce04eb96868da9760412e37d2335d020cc768ac9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748343"
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="89040-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="89040-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="89040-103">定義繫結項目，這是當用戶端必須公開 (Expose) 服務的端點才能將訊息傳回用戶端時所使用的項目。</span><span class="sxs-lookup"><span data-stu-id="89040-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="89040-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="89040-104">\<system.serviceModel></span></span>  
<span data-ttu-id="89040-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="89040-105">\<bindings></span></span>  
<span data-ttu-id="89040-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="89040-106">\<customBinding></span></span>  
<span data-ttu-id="89040-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="89040-107">\<binding></span></span>  
<span data-ttu-id="89040-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="89040-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89040-109">語法</span><span class="sxs-lookup"><span data-stu-id="89040-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89040-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="89040-110">Attributes and Elements</span></span>  
 <span data-ttu-id="89040-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="89040-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89040-112">屬性</span><span class="sxs-lookup"><span data-stu-id="89040-112">Attributes</span></span>  
  
|<span data-ttu-id="89040-113">屬性</span><span class="sxs-lookup"><span data-stu-id="89040-113">Attribute</span></span>|<span data-ttu-id="89040-114">描述</span><span class="sxs-lookup"><span data-stu-id="89040-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89040-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="89040-115">clientBaseAddress</span></span>|<span data-ttu-id="89040-116">URI，設定雙工模式中返回通道的位址。</span><span class="sxs-lookup"><span data-stu-id="89040-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="89040-117">服務會使用這個位址與用戶端接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="89040-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="89040-118">如果這個屬性未設定，預設位址"`full qualified name+default port\TemporaryIndigoAddress\guid`」 產生。</span><span class="sxs-lookup"><span data-stu-id="89040-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="89040-119">預設值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="89040-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89040-120">子項目</span><span class="sxs-lookup"><span data-stu-id="89040-120">Child Elements</span></span>  
 <span data-ttu-id="89040-121">無</span><span class="sxs-lookup"><span data-stu-id="89040-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89040-122">父項目</span><span class="sxs-lookup"><span data-stu-id="89040-122">Parent Elements</span></span>  
  
|<span data-ttu-id="89040-123">項目</span><span class="sxs-lookup"><span data-stu-id="89040-123">Element</span></span>|<span data-ttu-id="89040-124">描述</span><span class="sxs-lookup"><span data-stu-id="89040-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89040-125">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="89040-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="89040-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="89040-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89040-127">備註</span><span class="sxs-lookup"><span data-stu-id="89040-127">Remarks</span></span>  
 <span data-ttu-id="89040-128">這個組態項目是和本身不允許雙工通訊的傳輸一起使用，例如 HTTP。</span><span class="sxs-lookup"><span data-stu-id="89040-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="89040-129">相反地，TCP 本身就允許雙工通訊，因此不需要使用這個繫結項目也可讓服務將訊息傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="89040-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="89040-130">用戶端必須公開位址，才能讓服務接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="89040-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="89040-131">這個用戶端位址是由 `clientBaseAddress` 屬性提供。</span><span class="sxs-lookup"><span data-stu-id="89040-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="89040-132">請注意，如果使用者未明確設定此屬性，則 Windows Communication Foundation (WCF) 會自動產生 ClientBaseAddress。</span><span class="sxs-lookup"><span data-stu-id="89040-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89040-133">範例</span><span class="sxs-lookup"><span data-stu-id="89040-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="89040-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89040-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="89040-135">繫結</span><span class="sxs-lookup"><span data-stu-id="89040-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="89040-136">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="89040-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="89040-137">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="89040-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="89040-138">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="89040-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
