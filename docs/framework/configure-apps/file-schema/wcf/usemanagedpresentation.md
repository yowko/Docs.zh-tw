---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: bb2989ed52a88d805510d65e1dc1740df7bb55eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735948"
---
# \<useManagedPresentation>
<span data-ttu-id="9a10b-101">繫結項目，這個繫結項目可用來與 CardSpace 安全性權杖服務進行通訊，該服務支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="9a10b-101">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="9a10b-102">這個項目沒有屬性，並呈現為空白 switch。</span><span class="sxs-lookup"><span data-stu-id="9a10b-102">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="9a10b-103">語法</span><span class="sxs-lookup"><span data-stu-id="9a10b-103">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a10b-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9a10b-104">Attributes and Elements</span></span>  
 <span data-ttu-id="9a10b-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9a10b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a10b-106">屬性</span><span class="sxs-lookup"><span data-stu-id="9a10b-106">Attributes</span></span>  
 <span data-ttu-id="9a10b-107">無。</span><span class="sxs-lookup"><span data-stu-id="9a10b-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9a10b-108">子元素</span><span class="sxs-lookup"><span data-stu-id="9a10b-108">Child Elements</span></span>  
 <span data-ttu-id="9a10b-109">無</span><span class="sxs-lookup"><span data-stu-id="9a10b-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a10b-110">父項目</span><span class="sxs-lookup"><span data-stu-id="9a10b-110">Parent Elements</span></span>  
  
|<span data-ttu-id="9a10b-111">元素</span><span class="sxs-lookup"><span data-stu-id="9a10b-111">Element</span></span>|<span data-ttu-id="9a10b-112">描述</span><span class="sxs-lookup"><span data-stu-id="9a10b-112">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="9a10b-113">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="9a10b-113">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a10b-114">備註</span><span class="sxs-lookup"><span data-stu-id="9a10b-114">Remarks</span></span>  
 <span data-ttu-id="9a10b-115">身分識別提供者會在其原則中使用這個項目，表示它支援 WS-Trust 的 CardSpace 設定檔。</span><span class="sxs-lookup"><span data-stu-id="9a10b-115">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="9a10b-116">發行此類原則判斷提示的身分識別提供者，應該可以根據該 CardSpace 設定檔來發行權杖。</span><span class="sxs-lookup"><span data-stu-id="9a10b-116">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a10b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a10b-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9a10b-118">繫結</span><span class="sxs-lookup"><span data-stu-id="9a10b-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9a10b-119">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="9a10b-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9a10b-120">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="9a10b-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
