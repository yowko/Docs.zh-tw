---
title: <add> 的 <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 6d8fd26170059226583a300b1b48b849666db929
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181618"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="2bfac-102">\<add> 的 \<backupList></span><span class="sxs-lookup"><span data-stu-id="2bfac-102">\<add> of \<backupList></span></span>

<span data-ttu-id="2bfac-103">表示定義備份端點項目的組態項目。</span><span class="sxs-lookup"><span data-stu-id="2bfac-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="2bfac-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2bfac-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bfac-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2bfac-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2bfac-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2bfac-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bfac-107">屬性</span><span class="sxs-lookup"><span data-stu-id="2bfac-107">Attributes</span></span>  
  
|<span data-ttu-id="2bfac-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2bfac-108">Attribute</span></span>|<span data-ttu-id="2bfac-109">描述</span><span class="sxs-lookup"><span data-stu-id="2bfac-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2bfac-110">NAME</span><span class="sxs-lookup"><span data-stu-id="2bfac-110">name</span></span>|<span data-ttu-id="2bfac-111">指定備份端點名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="2bfac-111">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bfac-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2bfac-112">Child Elements</span></span>  

 <span data-ttu-id="2bfac-113">無。</span><span class="sxs-lookup"><span data-stu-id="2bfac-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2bfac-114">父項目</span><span class="sxs-lookup"><span data-stu-id="2bfac-114">Parent Elements</span></span>  
  
|<span data-ttu-id="2bfac-115">項目</span><span class="sxs-lookup"><span data-stu-id="2bfac-115">Element</span></span>|<span data-ttu-id="2bfac-116">描述</span><span class="sxs-lookup"><span data-stu-id="2bfac-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="2bfac-117">包含端點清單，這些端點是您希望路由服務在無法連上主要端點時使用的端點。</span><span class="sxs-lookup"><span data-stu-id="2bfac-117">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bfac-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bfac-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
