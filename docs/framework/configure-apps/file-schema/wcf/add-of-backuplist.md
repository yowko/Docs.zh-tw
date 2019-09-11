---
title: <add> 的 <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850549"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="2b5e0-102">\<新增 backupList > \<的 ></span><span class="sxs-lookup"><span data-stu-id="2b5e0-102">\<add> of \<backupList></span></span>
<span data-ttu-id="2b5e0-103">表示定義備份端點項目的組態項目。</span><span class="sxs-lookup"><span data-stu-id="2b5e0-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
<span data-ttu-id="2b5e0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b5e0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2b5e0-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2b5e0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2b5e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<路由 >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="2b5e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="2b5e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="2b5e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="2b5e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupList >** ](backuplist.md)</span><span class="sxs-lookup"><span data-stu-id="2b5e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)</span></span>\
<span data-ttu-id="2b5e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="2b5e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b5e0-110">語法</span><span class="sxs-lookup"><span data-stu-id="2b5e0-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b5e0-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2b5e0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2b5e0-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2b5e0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b5e0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2b5e0-113">Attributes</span></span>  
  
|<span data-ttu-id="2b5e0-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2b5e0-114">Attribute</span></span>|<span data-ttu-id="2b5e0-115">描述</span><span class="sxs-lookup"><span data-stu-id="2b5e0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b5e0-116">NAME</span><span class="sxs-lookup"><span data-stu-id="2b5e0-116">name</span></span>|<span data-ttu-id="2b5e0-117">指定備份端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="2b5e0-117">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b5e0-118">子元素</span><span class="sxs-lookup"><span data-stu-id="2b5e0-118">Child Elements</span></span>  
 <span data-ttu-id="2b5e0-119">無。</span><span class="sxs-lookup"><span data-stu-id="2b5e0-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b5e0-120">父項目</span><span class="sxs-lookup"><span data-stu-id="2b5e0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2b5e0-121">項目</span><span class="sxs-lookup"><span data-stu-id="2b5e0-121">Element</span></span>|<span data-ttu-id="2b5e0-122">說明</span><span class="sxs-lookup"><span data-stu-id="2b5e0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b5e0-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="2b5e0-123">\<routing></span></span>](routing.md)|<span data-ttu-id="2b5e0-124">包含您希望路由服務在無法連上主要端點時使用的端點清單。</span><span class="sxs-lookup"><span data-stu-id="2b5e0-124">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b5e0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b5e0-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
