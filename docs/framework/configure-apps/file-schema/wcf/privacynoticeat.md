---
title: '&lt;privacyNoticeAt&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30b3f0bdd1aa02473470c354a730bcfa450f0264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="d177e-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="d177e-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="d177e-103">表示組態項目，指定用於 `wsFederationHttp` 繫結中的隱私權注意事項。</span><span class="sxs-lookup"><span data-stu-id="d177e-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="d177e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d177e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d177e-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="d177e-105">\<bindings></span></span>  
<span data-ttu-id="d177e-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d177e-106">\<customBinding></span></span>  
<span data-ttu-id="d177e-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="d177e-107">\<binding></span></span>  
<span data-ttu-id="d177e-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="d177e-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d177e-109">語法</span><span class="sxs-lookup"><span data-stu-id="d177e-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="d177e-110">類型</span><span class="sxs-lookup"><span data-stu-id="d177e-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d177e-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d177e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d177e-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d177e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d177e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d177e-113">Attributes</span></span>  
  
|<span data-ttu-id="d177e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d177e-114">Attribute</span></span>|<span data-ttu-id="d177e-115">描述</span><span class="sxs-lookup"><span data-stu-id="d177e-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="d177e-116">指定隱私權注意事項所在之 URI 的字串。</span><span class="sxs-lookup"><span data-stu-id="d177e-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="d177e-117">指定這個隱私權注意事項版本的整數。</span><span class="sxs-lookup"><span data-stu-id="d177e-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d177e-118">子元素</span><span class="sxs-lookup"><span data-stu-id="d177e-118">Child Elements</span></span>  
 <span data-ttu-id="d177e-119">無。</span><span class="sxs-lookup"><span data-stu-id="d177e-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d177e-120">父項目</span><span class="sxs-lookup"><span data-stu-id="d177e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d177e-121">項目</span><span class="sxs-lookup"><span data-stu-id="d177e-121">Element</span></span>|<span data-ttu-id="d177e-122">描述</span><span class="sxs-lookup"><span data-stu-id="d177e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d177e-123">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="d177e-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d177e-124">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="d177e-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d177e-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="d177e-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="d177e-126">繫結</span><span class="sxs-lookup"><span data-stu-id="d177e-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d177e-127">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="d177e-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="d177e-128">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="d177e-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="d177e-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d177e-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
