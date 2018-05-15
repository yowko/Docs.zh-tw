---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5fb89ce5a942db40b07a65f59ddd05ab4cd624aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="cc309-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="cc309-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="cc309-103">代表組態區段，用於定義錯誤處理中使用的一組備份服務。</span><span class="sxs-lookup"><span data-stu-id="cc309-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="cc309-104">每個子項目是會列舉您希望路由服務在使用中無法連上主要端點的端點的一組備份清單。</span><span class="sxs-lookup"><span data-stu-id="cc309-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="cc309-105">如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="cc309-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="cc309-106">如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。</span><span class="sxs-lookup"><span data-stu-id="cc309-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="cc309-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cc309-107">\<system.serviceModel></span></span>  
<span data-ttu-id="cc309-108">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="cc309-108">\<routing></span></span>  
<span data-ttu-id="cc309-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="cc309-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc309-110">語法</span><span class="sxs-lookup"><span data-stu-id="cc309-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc309-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cc309-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cc309-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cc309-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc309-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cc309-113">Attributes</span></span>  
 <span data-ttu-id="cc309-114">無。</span><span class="sxs-lookup"><span data-stu-id="cc309-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cc309-115">子項目</span><span class="sxs-lookup"><span data-stu-id="cc309-115">Child Elements</span></span>  
  
|<span data-ttu-id="cc309-116">項目</span><span class="sxs-lookup"><span data-stu-id="cc309-116">Element</span></span>|<span data-ttu-id="cc309-117">描述</span><span class="sxs-lookup"><span data-stu-id="cc309-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc309-118">\<filter></span><span class="sxs-lookup"><span data-stu-id="cc309-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="cc309-119">包含您想要使用無法連上主要端點的路由服務的端點清單。</span><span class="sxs-lookup"><span data-stu-id="cc309-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="cc309-120">。</span><span class="sxs-lookup"><span data-stu-id="cc309-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc309-121">父項目</span><span class="sxs-lookup"><span data-stu-id="cc309-121">Parent Elements</span></span>  
  
|<span data-ttu-id="cc309-122">項目</span><span class="sxs-lookup"><span data-stu-id="cc309-122">Element</span></span>|<span data-ttu-id="cc309-123">描述</span><span class="sxs-lookup"><span data-stu-id="cc309-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc309-124">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="cc309-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="cc309-125">代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>傳入訊息及路由表定義目標端點時所要使用當篩選條件相符時傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="cc309-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc309-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc309-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
