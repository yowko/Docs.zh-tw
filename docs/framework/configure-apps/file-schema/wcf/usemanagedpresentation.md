---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: e67cc316b8747ee785055ceb4f954988fa82a44c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940618"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="b6951-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="b6951-101">\<useManagedPresentation></span></span>
<span data-ttu-id="b6951-102">繫結項目，這個繫結項目可用來與 CardSpace 安全性權杖服務進行通訊，該服務支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b6951-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="b6951-103">這個項目沒有屬性，並呈現為空白 switch。</span><span class="sxs-lookup"><span data-stu-id="b6951-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="b6951-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b6951-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b6951-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b6951-105">\<bindings></span></span>  
<span data-ttu-id="b6951-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b6951-106">\<customBinding></span></span>  
<span data-ttu-id="b6951-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="b6951-107">\<binding></span></span>  
<span data-ttu-id="b6951-108">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="b6951-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6951-109">語法</span><span class="sxs-lookup"><span data-stu-id="b6951-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6951-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b6951-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b6951-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b6951-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6951-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b6951-112">Attributes</span></span>  
 <span data-ttu-id="b6951-113">無。</span><span class="sxs-lookup"><span data-stu-id="b6951-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b6951-114">子元素</span><span class="sxs-lookup"><span data-stu-id="b6951-114">Child Elements</span></span>  
 <span data-ttu-id="b6951-115">None</span><span class="sxs-lookup"><span data-stu-id="b6951-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6951-116">父項目</span><span class="sxs-lookup"><span data-stu-id="b6951-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b6951-117">項目</span><span class="sxs-lookup"><span data-stu-id="b6951-117">Element</span></span>|<span data-ttu-id="b6951-118">說明</span><span class="sxs-lookup"><span data-stu-id="b6951-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6951-119">\<binding></span><span class="sxs-lookup"><span data-stu-id="b6951-119">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b6951-120">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="b6951-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6951-121">備註</span><span class="sxs-lookup"><span data-stu-id="b6951-121">Remarks</span></span>  
 <span data-ttu-id="b6951-122">身分識別提供者會在其原則中使用這個項目，表示它支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b6951-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="b6951-123">發行此類原則判斷提示的身分識別提供者，應該可以根據該 CardSpace 設定檔來發行權杖。</span><span class="sxs-lookup"><span data-stu-id="b6951-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6951-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6951-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b6951-125">繫結</span><span class="sxs-lookup"><span data-stu-id="b6951-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b6951-126">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="b6951-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b6951-127">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="b6951-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b6951-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b6951-128">\<customBinding></span></span>](custombinding.md)
