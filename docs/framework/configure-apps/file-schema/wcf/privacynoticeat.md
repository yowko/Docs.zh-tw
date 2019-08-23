---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: f7349bf61082c5d8e5bd4249e01b8835a1861cb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934264"
---
# <a name="privacynoticeat"></a><span data-ttu-id="04229-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="04229-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="04229-102">表示組態項目，指定用於 `wsFederationHttp` 繫結中的隱私權注意事項。</span><span class="sxs-lookup"><span data-stu-id="04229-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="04229-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="04229-103">\<system.serviceModel></span></span>  
<span data-ttu-id="04229-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="04229-104">\<bindings></span></span>  
<span data-ttu-id="04229-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="04229-105">\<customBinding></span></span>  
<span data-ttu-id="04229-106">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="04229-106">\<binding></span></span>  
<span data-ttu-id="04229-107">\<privacyNotice></span><span class="sxs-lookup"><span data-stu-id="04229-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04229-108">語法</span><span class="sxs-lookup"><span data-stu-id="04229-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="04229-109">類型</span><span class="sxs-lookup"><span data-stu-id="04229-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04229-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="04229-110">Attributes and Elements</span></span>  
 <span data-ttu-id="04229-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="04229-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04229-112">屬性</span><span class="sxs-lookup"><span data-stu-id="04229-112">Attributes</span></span>  
  
|<span data-ttu-id="04229-113">屬性</span><span class="sxs-lookup"><span data-stu-id="04229-113">Attribute</span></span>|<span data-ttu-id="04229-114">說明</span><span class="sxs-lookup"><span data-stu-id="04229-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="04229-115">指定隱私權注意事項所在之 URI 的字串。</span><span class="sxs-lookup"><span data-stu-id="04229-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="04229-116">指定這個隱私權注意事項版本的整數。</span><span class="sxs-lookup"><span data-stu-id="04229-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04229-117">子元素</span><span class="sxs-lookup"><span data-stu-id="04229-117">Child Elements</span></span>  
 <span data-ttu-id="04229-118">無。</span><span class="sxs-lookup"><span data-stu-id="04229-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04229-119">父項目</span><span class="sxs-lookup"><span data-stu-id="04229-119">Parent Elements</span></span>  
  
|<span data-ttu-id="04229-120">項目</span><span class="sxs-lookup"><span data-stu-id="04229-120">Element</span></span>|<span data-ttu-id="04229-121">描述</span><span class="sxs-lookup"><span data-stu-id="04229-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04229-122">\<binding></span><span class="sxs-lookup"><span data-stu-id="04229-122">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="04229-123">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="04229-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04229-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04229-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="04229-125">繫結</span><span class="sxs-lookup"><span data-stu-id="04229-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="04229-126">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="04229-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="04229-127">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="04229-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="04229-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="04229-128">\<customBinding></span></span>](custombinding.md)
