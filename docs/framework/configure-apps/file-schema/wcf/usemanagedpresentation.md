---
title: '&lt;useManagedPresentation&gt;'
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 35af7f5e10594617807384c20ab706ad675d11ef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="01693-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="01693-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="01693-103">繫結項目，這個繫結項目可用來與 CardSpace 安全性權杖服務進行通訊，該服務支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="01693-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="01693-104">這個項目沒有屬性，並呈現為空白 switch。</span><span class="sxs-lookup"><span data-stu-id="01693-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="01693-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="01693-105">\<system.serviceModel></span></span>  
<span data-ttu-id="01693-106">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="01693-106">\<bindings></span></span>  
<span data-ttu-id="01693-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="01693-107">\<customBinding></span></span>  
<span data-ttu-id="01693-108">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="01693-108">\<binding></span></span>  
<span data-ttu-id="01693-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="01693-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01693-110">語法</span><span class="sxs-lookup"><span data-stu-id="01693-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01693-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="01693-111">Attributes and Elements</span></span>  
 <span data-ttu-id="01693-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="01693-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01693-113">屬性</span><span class="sxs-lookup"><span data-stu-id="01693-113">Attributes</span></span>  
 <span data-ttu-id="01693-114">無。</span><span class="sxs-lookup"><span data-stu-id="01693-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01693-115">子項目</span><span class="sxs-lookup"><span data-stu-id="01693-115">Child Elements</span></span>  
 <span data-ttu-id="01693-116">無</span><span class="sxs-lookup"><span data-stu-id="01693-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01693-117">父項目</span><span class="sxs-lookup"><span data-stu-id="01693-117">Parent Elements</span></span>  
  
|<span data-ttu-id="01693-118">項目</span><span class="sxs-lookup"><span data-stu-id="01693-118">Element</span></span>|<span data-ttu-id="01693-119">描述</span><span class="sxs-lookup"><span data-stu-id="01693-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01693-120">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="01693-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="01693-121">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="01693-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01693-122">備註</span><span class="sxs-lookup"><span data-stu-id="01693-122">Remarks</span></span>  
 <span data-ttu-id="01693-123">身分識別提供者會在其原則中使用這個項目，表示它支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="01693-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="01693-124">發行此類原則判斷提示的身分識別提供者，應該可以根據該 CardSpace 設定檔來發行權杖。</span><span class="sxs-lookup"><span data-stu-id="01693-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01693-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01693-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="01693-126">繫結</span><span class="sxs-lookup"><span data-stu-id="01693-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="01693-127">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="01693-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="01693-128">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="01693-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="01693-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="01693-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
