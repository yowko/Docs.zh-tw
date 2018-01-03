---
title: '&lt;useManagedPresentation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae9851794d77972066fb897aa76528fec86fd6f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="7874b-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="7874b-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="7874b-103">繫結項目，這個繫結項目可用來與 CardSpace 安全性權杖服務進行通訊，該服務支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="7874b-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="7874b-104">這個項目沒有屬性，並呈現為空白 switch。</span><span class="sxs-lookup"><span data-stu-id="7874b-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="7874b-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7874b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="7874b-106">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7874b-106">\<bindings></span></span>  
<span data-ttu-id="7874b-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7874b-107">\<customBinding></span></span>  
<span data-ttu-id="7874b-108">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7874b-108">\<binding></span></span>  
<span data-ttu-id="7874b-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="7874b-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7874b-110">語法</span><span class="sxs-lookup"><span data-stu-id="7874b-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7874b-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7874b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7874b-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7874b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7874b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7874b-113">Attributes</span></span>  
 <span data-ttu-id="7874b-114">無。</span><span class="sxs-lookup"><span data-stu-id="7874b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7874b-115">子元素</span><span class="sxs-lookup"><span data-stu-id="7874b-115">Child Elements</span></span>  
 <span data-ttu-id="7874b-116">無</span><span class="sxs-lookup"><span data-stu-id="7874b-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7874b-117">父項目</span><span class="sxs-lookup"><span data-stu-id="7874b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7874b-118">項目</span><span class="sxs-lookup"><span data-stu-id="7874b-118">Element</span></span>|<span data-ttu-id="7874b-119">描述</span><span class="sxs-lookup"><span data-stu-id="7874b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7874b-120">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="7874b-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="7874b-121">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="7874b-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7874b-122">備註</span><span class="sxs-lookup"><span data-stu-id="7874b-122">Remarks</span></span>  
 <span data-ttu-id="7874b-123">身分識別提供者會在其原則中使用這個項目，表示它支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="7874b-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="7874b-124">發行此類原則判斷提示的身分識別提供者，應該可以根據該 CardSpace 設定檔來發行權杖。</span><span class="sxs-lookup"><span data-stu-id="7874b-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7874b-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="7874b-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="7874b-126">繫結</span><span class="sxs-lookup"><span data-stu-id="7874b-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7874b-127">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="7874b-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="7874b-128">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="7874b-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="7874b-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7874b-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
