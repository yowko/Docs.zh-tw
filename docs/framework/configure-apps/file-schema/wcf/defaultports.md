---
title: '&lt;a d d&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e127935977795181411dfa6b03d8b09fe88e0f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="adb8a-102">&lt;a d d&gt;</span><span class="sxs-lookup"><span data-stu-id="adb8a-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="adb8a-103">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="adb8a-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="adb8a-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="adb8a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="adb8a-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="adb8a-105">\<behaviors></span></span>  
<span data-ttu-id="adb8a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="adb8a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="adb8a-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="adb8a-107">\<behavior></span></span>  
<span data-ttu-id="adb8a-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="adb8a-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="adb8a-109">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="adb8a-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adb8a-110">語法</span><span class="sxs-lookup"><span data-stu-id="adb8a-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adb8a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="adb8a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="adb8a-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="adb8a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adb8a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="adb8a-113">Attributes</span></span>  
 <span data-ttu-id="adb8a-114">無。</span><span class="sxs-lookup"><span data-stu-id="adb8a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="adb8a-115">子項目</span><span class="sxs-lookup"><span data-stu-id="adb8a-115">Child Elements</span></span>  
  
|<span data-ttu-id="adb8a-116">項目</span><span class="sxs-lookup"><span data-stu-id="adb8a-116">Element</span></span>|<span data-ttu-id="adb8a-117">說明</span><span class="sxs-lookup"><span data-stu-id="adb8a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adb8a-118">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="adb8a-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="adb8a-119">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="adb8a-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adb8a-120">父項目</span><span class="sxs-lookup"><span data-stu-id="adb8a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="adb8a-121">項目</span><span class="sxs-lookup"><span data-stu-id="adb8a-121">Element</span></span>|<span data-ttu-id="adb8a-122">說明</span><span class="sxs-lookup"><span data-stu-id="adb8a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adb8a-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="adb8a-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="adb8a-124">預設連接埠清單。</span><span class="sxs-lookup"><span data-stu-id="adb8a-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="adb8a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adb8a-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
