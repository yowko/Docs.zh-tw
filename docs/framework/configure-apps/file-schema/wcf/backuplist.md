---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 1e2b3eacbc845ad40030f3a48be2ef93c4ddbd8c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262422"
---
# <a name="backuplist"></a><span data-ttu-id="0eb9c-101">\<backupList></span><span class="sxs-lookup"><span data-stu-id="0eb9c-101">\<backupList></span></span>
<span data-ttu-id="0eb9c-102">代表定義備份清單會列舉一組您希望路由服務在無法找到主要端點時使用的端點組態區段。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="0eb9c-103">如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="0eb9c-104">如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="0eb9c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0eb9c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="0eb9c-106">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="0eb9c-106">\<routing></span></span>  
<span data-ttu-id="0eb9c-107">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="0eb9c-107">\<backupLists></span></span>  
<span data-ttu-id="0eb9c-108">\<backupList></span><span class="sxs-lookup"><span data-stu-id="0eb9c-108">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb9c-109">語法</span><span class="sxs-lookup"><span data-stu-id="0eb9c-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eb9c-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0eb9c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0eb9c-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eb9c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0eb9c-112">Attributes</span></span>  
  
|<span data-ttu-id="0eb9c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0eb9c-113">Attribute</span></span>|<span data-ttu-id="0eb9c-114">描述</span><span class="sxs-lookup"><span data-stu-id="0eb9c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0eb9c-115">name</span><span class="sxs-lookup"><span data-stu-id="0eb9c-115">name</span></span>|<span data-ttu-id="0eb9c-116">字串，指定用於識別這個端點清單的名稱。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-116">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0eb9c-117">子元素</span><span class="sxs-lookup"><span data-stu-id="0eb9c-117">Child Elements</span></span>  
  
|<span data-ttu-id="0eb9c-118">項目</span><span class="sxs-lookup"><span data-stu-id="0eb9c-118">Element</span></span>|<span data-ttu-id="0eb9c-119">描述</span><span class="sxs-lookup"><span data-stu-id="0eb9c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eb9c-120">\<filter></span><span class="sxs-lookup"><span data-stu-id="0eb9c-120">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="0eb9c-121">父項目</span><span class="sxs-lookup"><span data-stu-id="0eb9c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0eb9c-122">項目</span><span class="sxs-lookup"><span data-stu-id="0eb9c-122">Element</span></span>|<span data-ttu-id="0eb9c-123">描述</span><span class="sxs-lookup"><span data-stu-id="0eb9c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eb9c-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="0eb9c-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="0eb9c-125">備份端點的清單。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-125">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eb9c-126">備註</span><span class="sxs-lookup"><span data-stu-id="0eb9c-126">Remarks</span></span>  
 <span data-ttu-id="0eb9c-127">這個區段包含依順序排列的端點集合，訊息會在傳送至主要端點期間發生通訊例外狀況事件時，傳輸至這些端點。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-127">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="0eb9c-128">如果傳送至主要端點列於`endpointName`的屬性[\<新增 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md)因通訊例外狀況，路由服務會嘗試將訊息傳送至第一個端點，在此組態區段。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-128">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="0eb9c-129">如果這項作業同樣因為通訊例外狀況而失敗，則路由服務將嘗試傳送訊息至這個區段中包含的下一個訊息，直到嘗試成功、傳回通訊例外狀況以外的失敗，或是集合中所有端點都傳回失敗為止。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-129">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="0eb9c-130">在下列範例中，如果傳送至名為 「 目的地 」 的主要端點傳回通訊例外狀況，則服務將嘗試傳送訊息至"alternateServiceQueue"。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-130">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="0eb9c-131">如果這項嘗試同樣傳回通訊例外狀況，則路由服務將嘗試傳送訊息至集合中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="0eb9c-131">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0eb9c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eb9c-132">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
