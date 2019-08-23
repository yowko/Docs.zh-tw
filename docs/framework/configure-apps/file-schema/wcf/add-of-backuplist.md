---
title: <add> 的 <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: c590dbd671807b32e08ad5d871d376a0dc51e611
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926881"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="a16d5-102">\<新增 backupList > \<的 ></span><span class="sxs-lookup"><span data-stu-id="a16d5-102">\<add> of \<backupList></span></span>
<span data-ttu-id="a16d5-103">表示定義備份端點項目的組態項目。</span><span class="sxs-lookup"><span data-stu-id="a16d5-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="a16d5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a16d5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a16d5-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="a16d5-105">\<routing></span></span>  
<span data-ttu-id="a16d5-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="a16d5-106">\<backupLists></span></span>  
<span data-ttu-id="a16d5-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="a16d5-107">\<backupList></span></span>  
<span data-ttu-id="a16d5-108">\<add></span><span class="sxs-lookup"><span data-stu-id="a16d5-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a16d5-109">語法</span><span class="sxs-lookup"><span data-stu-id="a16d5-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a16d5-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a16d5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a16d5-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a16d5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a16d5-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a16d5-112">Attributes</span></span>  
  
|<span data-ttu-id="a16d5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a16d5-113">Attribute</span></span>|<span data-ttu-id="a16d5-114">描述</span><span class="sxs-lookup"><span data-stu-id="a16d5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a16d5-115">NAME</span><span class="sxs-lookup"><span data-stu-id="a16d5-115">name</span></span>|<span data-ttu-id="a16d5-116">指定備份端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="a16d5-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a16d5-117">子元素</span><span class="sxs-lookup"><span data-stu-id="a16d5-117">Child Elements</span></span>  
 <span data-ttu-id="a16d5-118">無。</span><span class="sxs-lookup"><span data-stu-id="a16d5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a16d5-119">父項目</span><span class="sxs-lookup"><span data-stu-id="a16d5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a16d5-120">項目</span><span class="sxs-lookup"><span data-stu-id="a16d5-120">Element</span></span>|<span data-ttu-id="a16d5-121">描述</span><span class="sxs-lookup"><span data-stu-id="a16d5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a16d5-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="a16d5-122">\<routing></span></span>](routing.md)|<span data-ttu-id="a16d5-123">包含您希望路由服務在無法連上主要端點時使用的端點清單。</span><span class="sxs-lookup"><span data-stu-id="a16d5-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a16d5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a16d5-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
