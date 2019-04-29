---
title: <add> 的 <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 03bf1bbb8156e4722d987e171d9034747ac6bb61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701199"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="ae629-102">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="ae629-102">\<add> of \<backupList></span></span>
<span data-ttu-id="ae629-103">表示定義備份端點項目的組態項目。</span><span class="sxs-lookup"><span data-stu-id="ae629-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="ae629-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae629-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ae629-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="ae629-105">\<routing></span></span>  
<span data-ttu-id="ae629-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="ae629-106">\<backupLists></span></span>  
<span data-ttu-id="ae629-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="ae629-107">\<backupList></span></span>  
<span data-ttu-id="ae629-108">\<add></span><span class="sxs-lookup"><span data-stu-id="ae629-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae629-109">語法</span><span class="sxs-lookup"><span data-stu-id="ae629-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae629-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ae629-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ae629-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ae629-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae629-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ae629-112">Attributes</span></span>  
  
|<span data-ttu-id="ae629-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ae629-113">Attribute</span></span>|<span data-ttu-id="ae629-114">描述</span><span class="sxs-lookup"><span data-stu-id="ae629-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae629-115">名稱</span><span class="sxs-lookup"><span data-stu-id="ae629-115">name</span></span>|<span data-ttu-id="ae629-116">指定備份端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="ae629-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae629-117">子元素</span><span class="sxs-lookup"><span data-stu-id="ae629-117">Child Elements</span></span>  
 <span data-ttu-id="ae629-118">無。</span><span class="sxs-lookup"><span data-stu-id="ae629-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae629-119">父項目</span><span class="sxs-lookup"><span data-stu-id="ae629-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ae629-120">項目</span><span class="sxs-lookup"><span data-stu-id="ae629-120">Element</span></span>|<span data-ttu-id="ae629-121">描述</span><span class="sxs-lookup"><span data-stu-id="ae629-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae629-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="ae629-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="ae629-123">包含一份您希望路由服務在無法找到主要端點時使用的端點。</span><span class="sxs-lookup"><span data-stu-id="ae629-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae629-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae629-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
