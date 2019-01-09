---
title: '&lt;BackupList&gt;'
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 1a6a7ac42b379dd8fb2ba80cf6a3a38998c26a59
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146546"
---
# <a name="ltbackuplistgt"></a><span data-ttu-id="96136-102">&lt;BackupList&gt;</span><span class="sxs-lookup"><span data-stu-id="96136-102">&lt;backupList&gt;</span></span>
<span data-ttu-id="96136-103">代表定義備份清單會列舉一組您希望路由服務在無法找到主要端點時使用的端點組態區段。</span><span class="sxs-lookup"><span data-stu-id="96136-103">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="96136-104">如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="96136-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="96136-105">如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。</span><span class="sxs-lookup"><span data-stu-id="96136-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="96136-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="96136-106">\<system.serviceModel></span></span>  
<span data-ttu-id="96136-107">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="96136-107">\<routing></span></span>  
<span data-ttu-id="96136-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="96136-108">\<backupLists></span></span>  
<span data-ttu-id="96136-109">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="96136-109">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96136-110">語法</span><span class="sxs-lookup"><span data-stu-id="96136-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96136-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="96136-111">Attributes and Elements</span></span>  
 <span data-ttu-id="96136-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="96136-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96136-113">屬性</span><span class="sxs-lookup"><span data-stu-id="96136-113">Attributes</span></span>  
  
|<span data-ttu-id="96136-114">屬性</span><span class="sxs-lookup"><span data-stu-id="96136-114">Attribute</span></span>|<span data-ttu-id="96136-115">描述</span><span class="sxs-lookup"><span data-stu-id="96136-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96136-116">name</span><span class="sxs-lookup"><span data-stu-id="96136-116">name</span></span>|<span data-ttu-id="96136-117">字串，指定用於識別這個端點清單的名稱。</span><span class="sxs-lookup"><span data-stu-id="96136-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96136-118">子元素</span><span class="sxs-lookup"><span data-stu-id="96136-118">Child Elements</span></span>  
  
|<span data-ttu-id="96136-119">項目</span><span class="sxs-lookup"><span data-stu-id="96136-119">Element</span></span>|<span data-ttu-id="96136-120">描述</span><span class="sxs-lookup"><span data-stu-id="96136-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96136-121">\<filter></span><span class="sxs-lookup"><span data-stu-id="96136-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="96136-122">父項目</span><span class="sxs-lookup"><span data-stu-id="96136-122">Parent Elements</span></span>  
  
|<span data-ttu-id="96136-123">項目</span><span class="sxs-lookup"><span data-stu-id="96136-123">Element</span></span>|<span data-ttu-id="96136-124">描述</span><span class="sxs-lookup"><span data-stu-id="96136-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96136-125">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="96136-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="96136-126">備份端點的清單。</span><span class="sxs-lookup"><span data-stu-id="96136-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96136-127">備註</span><span class="sxs-lookup"><span data-stu-id="96136-127">Remarks</span></span>  
 <span data-ttu-id="96136-128">這個區段包含依順序排列的端點集合，訊息會在傳送至主要端點期間發生通訊例外狀況事件時，傳輸至這些端點。</span><span class="sxs-lookup"><span data-stu-id="96136-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="96136-129">如果傳送至主要端點列於`endpointName`的屬性[\<新增 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md)因通訊例外狀況，路由服務會嘗試將訊息傳送至第一個端點，在此組態區段。</span><span class="sxs-lookup"><span data-stu-id="96136-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="96136-130">如果這項作業同樣因為通訊例外狀況而失敗，則路由服務將嘗試傳送訊息至這個區段中包含的下一個訊息，直到嘗試成功、傳回通訊例外狀況以外的失敗，或是集合中所有端點都傳回失敗為止。</span><span class="sxs-lookup"><span data-stu-id="96136-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="96136-131">在下列範例中，如果傳送至名為 「 目的地 」 的主要端點傳回通訊例外狀況，則服務將嘗試傳送訊息至"alternateServiceQueue"。</span><span class="sxs-lookup"><span data-stu-id="96136-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="96136-132">如果這項嘗試同樣傳回通訊例外狀況，則路由服務將嘗試傳送訊息至集合中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="96136-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a><span data-ttu-id="96136-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96136-133">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
