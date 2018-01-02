---
title: "&lt;backupList&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 786620b0daf1cd22a95f9d0c94b7fc3d17c1a2c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="22df7-102">&lt;backupList&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="22df7-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="22df7-103">表示定義備份端點項目的組態項目。</span><span class="sxs-lookup"><span data-stu-id="22df7-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="22df7-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="22df7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="22df7-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="22df7-105">\<routing></span></span>  
<span data-ttu-id="22df7-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="22df7-106">\<backupLists></span></span>  
<span data-ttu-id="22df7-107">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="22df7-107">\<backupList></span></span>  
<span data-ttu-id="22df7-108">\<add></span><span class="sxs-lookup"><span data-stu-id="22df7-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22df7-109">語法</span><span class="sxs-lookup"><span data-stu-id="22df7-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22df7-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="22df7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="22df7-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="22df7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22df7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="22df7-112">Attributes</span></span>  
  
|<span data-ttu-id="22df7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="22df7-113">Attribute</span></span>|<span data-ttu-id="22df7-114">描述</span><span class="sxs-lookup"><span data-stu-id="22df7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22df7-115">name</span><span class="sxs-lookup"><span data-stu-id="22df7-115">name</span></span>|<span data-ttu-id="22df7-116">指定備份端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="22df7-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22df7-117">子元素</span><span class="sxs-lookup"><span data-stu-id="22df7-117">Child Elements</span></span>  
 <span data-ttu-id="22df7-118">無。</span><span class="sxs-lookup"><span data-stu-id="22df7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22df7-119">父項目</span><span class="sxs-lookup"><span data-stu-id="22df7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="22df7-120">項目</span><span class="sxs-lookup"><span data-stu-id="22df7-120">Element</span></span>|<span data-ttu-id="22df7-121">描述</span><span class="sxs-lookup"><span data-stu-id="22df7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22df7-122">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="22df7-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="22df7-123">包含您想要使用無法連上主要端點的路由服務的端點清單。</span><span class="sxs-lookup"><span data-stu-id="22df7-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22df7-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="22df7-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
