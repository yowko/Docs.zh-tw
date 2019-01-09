---
title: '&lt;backupList&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 4a8eb3df9be6b6b5bfe43aee330f3174ddca66ab
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151471"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="9fbd7-102">&lt;backupList&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="9fbd7-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="9fbd7-103">表示定義備份端點項目的組態項目。</span><span class="sxs-lookup"><span data-stu-id="9fbd7-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="9fbd7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9fbd7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9fbd7-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="9fbd7-105">\<routing></span></span>  
<span data-ttu-id="9fbd7-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="9fbd7-106">\<backupLists></span></span>  
<span data-ttu-id="9fbd7-107">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="9fbd7-107">\<backupList></span></span>  
<span data-ttu-id="9fbd7-108">\<add></span><span class="sxs-lookup"><span data-stu-id="9fbd7-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fbd7-109">語法</span><span class="sxs-lookup"><span data-stu-id="9fbd7-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9fbd7-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9fbd7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9fbd7-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9fbd7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9fbd7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9fbd7-112">Attributes</span></span>  
  
|<span data-ttu-id="9fbd7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9fbd7-113">Attribute</span></span>|<span data-ttu-id="9fbd7-114">描述</span><span class="sxs-lookup"><span data-stu-id="9fbd7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9fbd7-115">name</span><span class="sxs-lookup"><span data-stu-id="9fbd7-115">name</span></span>|<span data-ttu-id="9fbd7-116">指定備份端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="9fbd7-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9fbd7-117">子元素</span><span class="sxs-lookup"><span data-stu-id="9fbd7-117">Child Elements</span></span>  
 <span data-ttu-id="9fbd7-118">無。</span><span class="sxs-lookup"><span data-stu-id="9fbd7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9fbd7-119">父項目</span><span class="sxs-lookup"><span data-stu-id="9fbd7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9fbd7-120">項目</span><span class="sxs-lookup"><span data-stu-id="9fbd7-120">Element</span></span>|<span data-ttu-id="9fbd7-121">描述</span><span class="sxs-lookup"><span data-stu-id="9fbd7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9fbd7-122">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="9fbd7-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="9fbd7-123">包含一份您希望路由服務在無法找到主要端點時使用的端點。</span><span class="sxs-lookup"><span data-stu-id="9fbd7-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fbd7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fbd7-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
