---
title: '&lt;backupList&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 7e7361b24c0444b5f3d51a6f5bf079d5eb2dee18
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="1837e-102">&lt;backupList&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="1837e-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="1837e-103">表示定義備份端點項目的組態項目。</span><span class="sxs-lookup"><span data-stu-id="1837e-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="1837e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1837e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1837e-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="1837e-105">\<routing></span></span>  
<span data-ttu-id="1837e-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="1837e-106">\<backupLists></span></span>  
<span data-ttu-id="1837e-107">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="1837e-107">\<backupList></span></span>  
<span data-ttu-id="1837e-108">\<add></span><span class="sxs-lookup"><span data-stu-id="1837e-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1837e-109">語法</span><span class="sxs-lookup"><span data-stu-id="1837e-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1837e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1837e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1837e-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1837e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1837e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1837e-112">Attributes</span></span>  
  
|<span data-ttu-id="1837e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1837e-113">Attribute</span></span>|<span data-ttu-id="1837e-114">描述</span><span class="sxs-lookup"><span data-stu-id="1837e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1837e-115">name</span><span class="sxs-lookup"><span data-stu-id="1837e-115">name</span></span>|<span data-ttu-id="1837e-116">指定備份端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="1837e-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1837e-117">子項目</span><span class="sxs-lookup"><span data-stu-id="1837e-117">Child Elements</span></span>  
 <span data-ttu-id="1837e-118">無。</span><span class="sxs-lookup"><span data-stu-id="1837e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1837e-119">父項目</span><span class="sxs-lookup"><span data-stu-id="1837e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1837e-120">項目</span><span class="sxs-lookup"><span data-stu-id="1837e-120">Element</span></span>|<span data-ttu-id="1837e-121">描述</span><span class="sxs-lookup"><span data-stu-id="1837e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1837e-122">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="1837e-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="1837e-123">包含您想要使用無法連上主要端點的路由服務的端點清單。</span><span class="sxs-lookup"><span data-stu-id="1837e-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1837e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1837e-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
