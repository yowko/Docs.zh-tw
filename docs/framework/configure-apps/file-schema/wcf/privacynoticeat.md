---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 624b52c0618362f48063c8f7e7c53c5a68d7de8f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400033"
---
# <a name="privacynoticeat"></a><span data-ttu-id="bd7db-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="bd7db-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="bd7db-102">表示組態項目，指定用於 `wsFederationHttp` 繫結中的隱私權注意事項。</span><span class="sxs-lookup"><span data-stu-id="bd7db-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
<span data-ttu-id="bd7db-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd7db-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd7db-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bd7db-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bd7db-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bd7db-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bd7db-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bd7db-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="bd7db-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="bd7db-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="bd7db-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<privacyNotice >**</span><span class="sxs-lookup"><span data-stu-id="bd7db-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd7db-109">語法</span><span class="sxs-lookup"><span data-stu-id="bd7db-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="bd7db-110">類型</span><span class="sxs-lookup"><span data-stu-id="bd7db-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd7db-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bd7db-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bd7db-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bd7db-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd7db-113">屬性</span><span class="sxs-lookup"><span data-stu-id="bd7db-113">Attributes</span></span>  
  
|<span data-ttu-id="bd7db-114">屬性</span><span class="sxs-lookup"><span data-stu-id="bd7db-114">Attribute</span></span>|<span data-ttu-id="bd7db-115">描述</span><span class="sxs-lookup"><span data-stu-id="bd7db-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="bd7db-116">指定隱私權注意事項所在之 URI 的字串。</span><span class="sxs-lookup"><span data-stu-id="bd7db-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="bd7db-117">指定這個隱私權注意事項版本的整數。</span><span class="sxs-lookup"><span data-stu-id="bd7db-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd7db-118">子元素</span><span class="sxs-lookup"><span data-stu-id="bd7db-118">Child Elements</span></span>  
 <span data-ttu-id="bd7db-119">無。</span><span class="sxs-lookup"><span data-stu-id="bd7db-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd7db-120">父項目</span><span class="sxs-lookup"><span data-stu-id="bd7db-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bd7db-121">項目</span><span class="sxs-lookup"><span data-stu-id="bd7db-121">Element</span></span>|<span data-ttu-id="bd7db-122">說明</span><span class="sxs-lookup"><span data-stu-id="bd7db-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd7db-123">\<binding></span><span class="sxs-lookup"><span data-stu-id="bd7db-123">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="bd7db-124">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="bd7db-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd7db-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd7db-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bd7db-126">繫結</span><span class="sxs-lookup"><span data-stu-id="bd7db-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bd7db-127">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="bd7db-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bd7db-128">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="bd7db-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bd7db-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bd7db-129">\<customBinding></span></span>](custombinding.md)
