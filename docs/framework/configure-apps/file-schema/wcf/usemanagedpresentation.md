---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: eedf0ce6cf75b8fb56daf98f2005e66162ce10d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769846"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="fe34b-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="fe34b-101">\<useManagedPresentation></span></span>
<span data-ttu-id="fe34b-102">繫結項目，這個繫結項目可用來與 CardSpace 安全性權杖服務進行通訊，該服務支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="fe34b-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="fe34b-103">這個項目沒有屬性，並呈現為空白 switch。</span><span class="sxs-lookup"><span data-stu-id="fe34b-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="fe34b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fe34b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fe34b-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="fe34b-105">\<bindings></span></span>  
<span data-ttu-id="fe34b-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fe34b-106">\<customBinding></span></span>  
<span data-ttu-id="fe34b-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="fe34b-107">\<binding></span></span>  
<span data-ttu-id="fe34b-108">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="fe34b-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe34b-109">語法</span><span class="sxs-lookup"><span data-stu-id="fe34b-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe34b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fe34b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fe34b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fe34b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe34b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="fe34b-112">Attributes</span></span>  
 <span data-ttu-id="fe34b-113">無。</span><span class="sxs-lookup"><span data-stu-id="fe34b-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe34b-114">子元素</span><span class="sxs-lookup"><span data-stu-id="fe34b-114">Child Elements</span></span>  
 <span data-ttu-id="fe34b-115">None</span><span class="sxs-lookup"><span data-stu-id="fe34b-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe34b-116">父項目</span><span class="sxs-lookup"><span data-stu-id="fe34b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fe34b-117">項目</span><span class="sxs-lookup"><span data-stu-id="fe34b-117">Element</span></span>|<span data-ttu-id="fe34b-118">描述</span><span class="sxs-lookup"><span data-stu-id="fe34b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe34b-119">\<binding></span><span class="sxs-lookup"><span data-stu-id="fe34b-119">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="fe34b-120">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="fe34b-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe34b-121">備註</span><span class="sxs-lookup"><span data-stu-id="fe34b-121">Remarks</span></span>  
 <span data-ttu-id="fe34b-122">身分識別提供者會在其原則中使用這個項目，表示它支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="fe34b-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="fe34b-123">發行此類原則判斷提示的身分識別提供者，應該可以根據該 CardSpace 設定檔來發行權杖。</span><span class="sxs-lookup"><span data-stu-id="fe34b-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe34b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe34b-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fe34b-125">繫結</span><span class="sxs-lookup"><span data-stu-id="fe34b-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="fe34b-126">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="fe34b-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fe34b-127">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="fe34b-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="fe34b-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fe34b-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
