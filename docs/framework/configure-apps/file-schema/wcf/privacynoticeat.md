---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: e2ce2111e4bb26cc6a51b4a772b1d8a4d3238c70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200762"
---
# <a name="privacynoticeat"></a><span data-ttu-id="19c02-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="19c02-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="19c02-102">表示組態項目，指定用於 `wsFederationHttp` 繫結中的隱私權注意事項。</span><span class="sxs-lookup"><span data-stu-id="19c02-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="19c02-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="19c02-103">\<system.serviceModel></span></span>  
<span data-ttu-id="19c02-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="19c02-104">\<bindings></span></span>  
<span data-ttu-id="19c02-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="19c02-105">\<customBinding></span></span>  
<span data-ttu-id="19c02-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="19c02-106">\<binding></span></span>  
<span data-ttu-id="19c02-107">\<privacyNotice></span><span class="sxs-lookup"><span data-stu-id="19c02-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19c02-108">語法</span><span class="sxs-lookup"><span data-stu-id="19c02-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="19c02-109">類型</span><span class="sxs-lookup"><span data-stu-id="19c02-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19c02-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="19c02-110">Attributes and Elements</span></span>  
 <span data-ttu-id="19c02-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="19c02-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19c02-112">屬性</span><span class="sxs-lookup"><span data-stu-id="19c02-112">Attributes</span></span>  
  
|<span data-ttu-id="19c02-113">屬性</span><span class="sxs-lookup"><span data-stu-id="19c02-113">Attribute</span></span>|<span data-ttu-id="19c02-114">描述</span><span class="sxs-lookup"><span data-stu-id="19c02-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="19c02-115">指定隱私權注意事項所在之 URI 的字串。</span><span class="sxs-lookup"><span data-stu-id="19c02-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="19c02-116">指定這個隱私權注意事項版本的整數。</span><span class="sxs-lookup"><span data-stu-id="19c02-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19c02-117">子元素</span><span class="sxs-lookup"><span data-stu-id="19c02-117">Child Elements</span></span>  
 <span data-ttu-id="19c02-118">無。</span><span class="sxs-lookup"><span data-stu-id="19c02-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19c02-119">父項目</span><span class="sxs-lookup"><span data-stu-id="19c02-119">Parent Elements</span></span>  
  
|<span data-ttu-id="19c02-120">項目</span><span class="sxs-lookup"><span data-stu-id="19c02-120">Element</span></span>|<span data-ttu-id="19c02-121">描述</span><span class="sxs-lookup"><span data-stu-id="19c02-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19c02-122">\<binding></span><span class="sxs-lookup"><span data-stu-id="19c02-122">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="19c02-123">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="19c02-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19c02-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19c02-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="19c02-125">繫結</span><span class="sxs-lookup"><span data-stu-id="19c02-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="19c02-126">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="19c02-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="19c02-127">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="19c02-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="19c02-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="19c02-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
