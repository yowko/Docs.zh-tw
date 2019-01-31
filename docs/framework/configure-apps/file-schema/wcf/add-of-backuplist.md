---
title: <add> 的 <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: e61ee275a7e98f13370504f5f15fdbe62a8221bd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285788"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="79ef7-102">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="79ef7-102">\<add> of \<backupList></span></span>
<span data-ttu-id="79ef7-103">表示定義備份端點項目的組態項目。</span><span class="sxs-lookup"><span data-stu-id="79ef7-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="79ef7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="79ef7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="79ef7-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="79ef7-105">\<routing></span></span>  
<span data-ttu-id="79ef7-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="79ef7-106">\<backupLists></span></span>  
<span data-ttu-id="79ef7-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="79ef7-107">\<backupList></span></span>  
<span data-ttu-id="79ef7-108">\<add></span><span class="sxs-lookup"><span data-stu-id="79ef7-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79ef7-109">語法</span><span class="sxs-lookup"><span data-stu-id="79ef7-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79ef7-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="79ef7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="79ef7-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="79ef7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79ef7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="79ef7-112">Attributes</span></span>  
  
|<span data-ttu-id="79ef7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="79ef7-113">Attribute</span></span>|<span data-ttu-id="79ef7-114">描述</span><span class="sxs-lookup"><span data-stu-id="79ef7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79ef7-115">name</span><span class="sxs-lookup"><span data-stu-id="79ef7-115">name</span></span>|<span data-ttu-id="79ef7-116">指定備份端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="79ef7-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79ef7-117">子元素</span><span class="sxs-lookup"><span data-stu-id="79ef7-117">Child Elements</span></span>  
 <span data-ttu-id="79ef7-118">無。</span><span class="sxs-lookup"><span data-stu-id="79ef7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79ef7-119">父項目</span><span class="sxs-lookup"><span data-stu-id="79ef7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="79ef7-120">項目</span><span class="sxs-lookup"><span data-stu-id="79ef7-120">Element</span></span>|<span data-ttu-id="79ef7-121">描述</span><span class="sxs-lookup"><span data-stu-id="79ef7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79ef7-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="79ef7-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="79ef7-123">包含一份您希望路由服務在無法找到主要端點時使用的端點。</span><span class="sxs-lookup"><span data-stu-id="79ef7-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79ef7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79ef7-124">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
