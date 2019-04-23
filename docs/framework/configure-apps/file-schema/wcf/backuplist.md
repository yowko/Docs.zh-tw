---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: b0a6c604b5741c1355c35fca510cd10544dab9f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135729"
---
# <a name="backuplist"></a><span data-ttu-id="32a8b-101">\<backupList></span><span class="sxs-lookup"><span data-stu-id="32a8b-101">\<backupList></span></span>
<span data-ttu-id="32a8b-102">代表定義備份清單會列舉一組您希望路由服務在無法找到主要端點時使用的端點組態區段。</span><span class="sxs-lookup"><span data-stu-id="32a8b-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="32a8b-103">如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="32a8b-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="32a8b-104">如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。</span><span class="sxs-lookup"><span data-stu-id="32a8b-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="32a8b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="32a8b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="32a8b-106">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="32a8b-106">\<routing></span></span>  
<span data-ttu-id="32a8b-107">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="32a8b-107">\<backupLists></span></span>  
<span data-ttu-id="32a8b-108">\<backupList></span><span class="sxs-lookup"><span data-stu-id="32a8b-108">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a8b-109">語法</span><span class="sxs-lookup"><span data-stu-id="32a8b-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32a8b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="32a8b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="32a8b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="32a8b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32a8b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="32a8b-112">Attributes</span></span>  
  
|<span data-ttu-id="32a8b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="32a8b-113">Attribute</span></span>|<span data-ttu-id="32a8b-114">描述</span><span class="sxs-lookup"><span data-stu-id="32a8b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32a8b-115">名稱</span><span class="sxs-lookup"><span data-stu-id="32a8b-115">name</span></span>|<span data-ttu-id="32a8b-116">字串，指定用於識別這個端點清單的名稱。</span><span class="sxs-lookup"><span data-stu-id="32a8b-116">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32a8b-117">子元素</span><span class="sxs-lookup"><span data-stu-id="32a8b-117">Child Elements</span></span>  
  
|<span data-ttu-id="32a8b-118">項目</span><span class="sxs-lookup"><span data-stu-id="32a8b-118">Element</span></span>|<span data-ttu-id="32a8b-119">描述</span><span class="sxs-lookup"><span data-stu-id="32a8b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32a8b-120">\<filter></span><span class="sxs-lookup"><span data-stu-id="32a8b-120">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="32a8b-121">父項目</span><span class="sxs-lookup"><span data-stu-id="32a8b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="32a8b-122">項目</span><span class="sxs-lookup"><span data-stu-id="32a8b-122">Element</span></span>|<span data-ttu-id="32a8b-123">描述</span><span class="sxs-lookup"><span data-stu-id="32a8b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32a8b-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="32a8b-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="32a8b-125">備份端點的清單。</span><span class="sxs-lookup"><span data-stu-id="32a8b-125">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32a8b-126">備註</span><span class="sxs-lookup"><span data-stu-id="32a8b-126">Remarks</span></span>  
 <span data-ttu-id="32a8b-127">這個區段包含依順序排列的端點集合，訊息會在傳送至主要端點期間發生通訊例外狀況事件時，傳輸至這些端點。</span><span class="sxs-lookup"><span data-stu-id="32a8b-127">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="32a8b-128">如果傳送至主要端點列於`endpointName`的屬性[\<新增 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md)因通訊例外狀況，路由服務會嘗試將訊息傳送至第一個端點，在此組態區段。</span><span class="sxs-lookup"><span data-stu-id="32a8b-128">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="32a8b-129">如果這項作業同樣因為通訊例外狀況而失敗，則路由服務將嘗試傳送訊息至這個區段中包含的下一個訊息，直到嘗試成功、傳回通訊例外狀況以外的失敗，或是集合中所有端點都傳回失敗為止。</span><span class="sxs-lookup"><span data-stu-id="32a8b-129">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="32a8b-130">在下列範例中，如果傳送至名為 「 目的地 」 的主要端點傳回通訊例外狀況，則服務將嘗試傳送訊息至"alternateServiceQueue"。</span><span class="sxs-lookup"><span data-stu-id="32a8b-130">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="32a8b-131">如果這項嘗試同樣傳回通訊例外狀況，則路由服務將嘗試傳送訊息至集合中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="32a8b-131">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32a8b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32a8b-132">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
