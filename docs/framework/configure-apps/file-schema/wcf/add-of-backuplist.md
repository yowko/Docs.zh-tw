---
title: <add> 的 <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 53af01a519c244376b262db1f6515a438dcc554f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663375"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="a997e-102">\<新增 backupList > \<的 ></span><span class="sxs-lookup"><span data-stu-id="a997e-102">\<add> of \<backupList></span></span>
<span data-ttu-id="a997e-103">表示定義備份端點項目的組態項目。</span><span class="sxs-lookup"><span data-stu-id="a997e-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="a997e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a997e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a997e-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="a997e-105">\<routing></span></span>  
<span data-ttu-id="a997e-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="a997e-106">\<backupLists></span></span>  
<span data-ttu-id="a997e-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="a997e-107">\<backupList></span></span>  
<span data-ttu-id="a997e-108">\<add></span><span class="sxs-lookup"><span data-stu-id="a997e-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a997e-109">語法</span><span class="sxs-lookup"><span data-stu-id="a997e-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a997e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a997e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a997e-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a997e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a997e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a997e-112">Attributes</span></span>  
  
|<span data-ttu-id="a997e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a997e-113">Attribute</span></span>|<span data-ttu-id="a997e-114">描述</span><span class="sxs-lookup"><span data-stu-id="a997e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a997e-115">NAME</span><span class="sxs-lookup"><span data-stu-id="a997e-115">name</span></span>|<span data-ttu-id="a997e-116">指定備份端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="a997e-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a997e-117">子元素</span><span class="sxs-lookup"><span data-stu-id="a997e-117">Child Elements</span></span>  
 <span data-ttu-id="a997e-118">無。</span><span class="sxs-lookup"><span data-stu-id="a997e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a997e-119">父項目</span><span class="sxs-lookup"><span data-stu-id="a997e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a997e-120">項目</span><span class="sxs-lookup"><span data-stu-id="a997e-120">Element</span></span>|<span data-ttu-id="a997e-121">說明</span><span class="sxs-lookup"><span data-stu-id="a997e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a997e-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="a997e-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="a997e-123">包含您希望路由服務在無法連上主要端點時使用的端點清單。</span><span class="sxs-lookup"><span data-stu-id="a997e-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a997e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a997e-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
