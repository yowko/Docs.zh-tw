---
title: '&lt;backupList&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 2cc7cce62082317bb86218d68bd2881b74649771
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670182"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="04592-102">&lt;backupList&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="04592-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="04592-103">表示定義備份端點項目的組態項目。</span><span class="sxs-lookup"><span data-stu-id="04592-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="04592-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="04592-104">\<system.serviceModel></span></span>  
<span data-ttu-id="04592-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="04592-105">\<routing></span></span>  
<span data-ttu-id="04592-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="04592-106">\<backupLists></span></span>  
<span data-ttu-id="04592-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="04592-107">\<backupList></span></span>  
<span data-ttu-id="04592-108">\<add></span><span class="sxs-lookup"><span data-stu-id="04592-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04592-109">語法</span><span class="sxs-lookup"><span data-stu-id="04592-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04592-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="04592-110">Attributes and Elements</span></span>  
 <span data-ttu-id="04592-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="04592-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04592-112">屬性</span><span class="sxs-lookup"><span data-stu-id="04592-112">Attributes</span></span>  
  
|<span data-ttu-id="04592-113">屬性</span><span class="sxs-lookup"><span data-stu-id="04592-113">Attribute</span></span>|<span data-ttu-id="04592-114">描述</span><span class="sxs-lookup"><span data-stu-id="04592-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04592-115">name</span><span class="sxs-lookup"><span data-stu-id="04592-115">name</span></span>|<span data-ttu-id="04592-116">指定備份端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="04592-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04592-117">子元素</span><span class="sxs-lookup"><span data-stu-id="04592-117">Child Elements</span></span>  
 <span data-ttu-id="04592-118">無。</span><span class="sxs-lookup"><span data-stu-id="04592-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04592-119">父項目</span><span class="sxs-lookup"><span data-stu-id="04592-119">Parent Elements</span></span>  
  
|<span data-ttu-id="04592-120">項目</span><span class="sxs-lookup"><span data-stu-id="04592-120">Element</span></span>|<span data-ttu-id="04592-121">描述</span><span class="sxs-lookup"><span data-stu-id="04592-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04592-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="04592-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="04592-123">包含一份您希望路由服務在無法找到主要端點時使用的端點。</span><span class="sxs-lookup"><span data-stu-id="04592-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04592-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04592-124">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
