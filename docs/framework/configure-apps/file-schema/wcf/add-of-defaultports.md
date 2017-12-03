---
title: "&lt;defaultPorts&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2aa63c7a5e730b2fb45f614cb2fe5f88444cee4a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="070ff-102">&lt;defaultPorts&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="070ff-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="070ff-103">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="070ff-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="070ff-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="070ff-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="070ff-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="070ff-105">\<behaviors></span></span>  
<span data-ttu-id="070ff-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="070ff-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="070ff-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="070ff-107">\<behavior></span></span>  
<span data-ttu-id="070ff-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="070ff-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="070ff-109">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="070ff-109">\<defaultPorts></span></span>  
<span data-ttu-id="070ff-110">\<add></span><span class="sxs-lookup"><span data-stu-id="070ff-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="070ff-111">語法</span><span class="sxs-lookup"><span data-stu-id="070ff-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="070ff-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="070ff-112">Attributes and Elements</span></span>  
 <span data-ttu-id="070ff-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="070ff-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="070ff-114">屬性</span><span class="sxs-lookup"><span data-stu-id="070ff-114">Attributes</span></span>  
  
|<span data-ttu-id="070ff-115">屬性</span><span class="sxs-lookup"><span data-stu-id="070ff-115">Attribute</span></span>|<span data-ttu-id="070ff-116">描述</span><span class="sxs-lookup"><span data-stu-id="070ff-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="070ff-117">連接埠</span><span class="sxs-lookup"><span data-stu-id="070ff-117">port</span></span>|<span data-ttu-id="070ff-118">指定預設通訊埠編號的整數。</span><span class="sxs-lookup"><span data-stu-id="070ff-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="070ff-119">scheme</span><span class="sxs-lookup"><span data-stu-id="070ff-119">scheme</span></span>|<span data-ttu-id="070ff-120">指定與通訊連接埠相關之通訊協定設定群組的字串。</span><span class="sxs-lookup"><span data-stu-id="070ff-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="070ff-121">子元素</span><span class="sxs-lookup"><span data-stu-id="070ff-121">Child Elements</span></span>  
 <span data-ttu-id="070ff-122">無。</span><span class="sxs-lookup"><span data-stu-id="070ff-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="070ff-123">父項目</span><span class="sxs-lookup"><span data-stu-id="070ff-123">Parent Elements</span></span>  
  
|<span data-ttu-id="070ff-124">項目</span><span class="sxs-lookup"><span data-stu-id="070ff-124">Element</span></span>|<span data-ttu-id="070ff-125">說明</span><span class="sxs-lookup"><span data-stu-id="070ff-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="070ff-126">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="070ff-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="070ff-127">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="070ff-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="070ff-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="070ff-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
