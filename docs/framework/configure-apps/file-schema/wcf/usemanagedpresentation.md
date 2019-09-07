---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: c410967e84c9318d21ce0b3072d08b026a37b190
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399217"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="4e942-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="4e942-101">\<useManagedPresentation></span></span>
<span data-ttu-id="4e942-102">繫結項目，這個繫結項目可用來與 CardSpace 安全性權杖服務進行通訊，該服務支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="4e942-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="4e942-103">這個項目沒有屬性，並呈現為空白 switch。</span><span class="sxs-lookup"><span data-stu-id="4e942-103">This element has no attribute and is present as an empty switch.</span></span>  
  
<span data-ttu-id="4e942-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4e942-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4e942-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4e942-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4e942-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4e942-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4e942-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4e942-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="4e942-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="4e942-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4e942-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useManagedPresentation >**</span><span class="sxs-lookup"><span data-stu-id="4e942-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e942-110">語法</span><span class="sxs-lookup"><span data-stu-id="4e942-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e942-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4e942-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4e942-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4e942-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e942-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4e942-113">Attributes</span></span>  
 <span data-ttu-id="4e942-114">無。</span><span class="sxs-lookup"><span data-stu-id="4e942-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4e942-115">子元素</span><span class="sxs-lookup"><span data-stu-id="4e942-115">Child Elements</span></span>  
 <span data-ttu-id="4e942-116">無</span><span class="sxs-lookup"><span data-stu-id="4e942-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e942-117">父項目</span><span class="sxs-lookup"><span data-stu-id="4e942-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4e942-118">項目</span><span class="sxs-lookup"><span data-stu-id="4e942-118">Element</span></span>|<span data-ttu-id="4e942-119">描述</span><span class="sxs-lookup"><span data-stu-id="4e942-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e942-120">\<binding></span><span class="sxs-lookup"><span data-stu-id="4e942-120">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="4e942-121">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="4e942-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e942-122">備註</span><span class="sxs-lookup"><span data-stu-id="4e942-122">Remarks</span></span>  
 <span data-ttu-id="4e942-123">身分識別提供者會在其原則中使用這個項目，表示它支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="4e942-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="4e942-124">發行此類原則判斷提示的身分識別提供者，應該可以根據該 CardSpace 設定檔來發行權杖。</span><span class="sxs-lookup"><span data-stu-id="4e942-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e942-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e942-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4e942-126">繫結</span><span class="sxs-lookup"><span data-stu-id="4e942-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4e942-127">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="4e942-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4e942-128">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="4e942-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4e942-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4e942-129">\<customBinding></span></span>](custombinding.md)
