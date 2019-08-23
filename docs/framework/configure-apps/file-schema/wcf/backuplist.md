---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: d5feab6cb374f98e683cf15f797de4f478e23131
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919915"
---
# <a name="backuplist"></a><span data-ttu-id="3cef7-101">\<backupList></span><span class="sxs-lookup"><span data-stu-id="3cef7-101">\<backupList></span></span>
<span data-ttu-id="3cef7-102">表示用來定義備份清單的設定區段, 其會列舉您希望路由服務在無法連上主要端點時使用的一組端點。</span><span class="sxs-lookup"><span data-stu-id="3cef7-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="3cef7-103">如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="3cef7-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="3cef7-104">如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。</span><span class="sxs-lookup"><span data-stu-id="3cef7-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="3cef7-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3cef7-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3cef7-106">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="3cef7-106">\<routing></span></span>  
<span data-ttu-id="3cef7-107">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="3cef7-107">\<backupLists></span></span>  
<span data-ttu-id="3cef7-108">\<backupList></span><span class="sxs-lookup"><span data-stu-id="3cef7-108">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cef7-109">語法</span><span class="sxs-lookup"><span data-stu-id="3cef7-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cef7-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3cef7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3cef7-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3cef7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cef7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3cef7-112">Attributes</span></span>  
  
|<span data-ttu-id="3cef7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3cef7-113">Attribute</span></span>|<span data-ttu-id="3cef7-114">描述</span><span class="sxs-lookup"><span data-stu-id="3cef7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3cef7-115">NAME</span><span class="sxs-lookup"><span data-stu-id="3cef7-115">name</span></span>|<span data-ttu-id="3cef7-116">字串，指定用於識別這個端點清單的名稱。</span><span class="sxs-lookup"><span data-stu-id="3cef7-116">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cef7-117">子元素</span><span class="sxs-lookup"><span data-stu-id="3cef7-117">Child Elements</span></span>  
  
|<span data-ttu-id="3cef7-118">項目</span><span class="sxs-lookup"><span data-stu-id="3cef7-118">Element</span></span>|<span data-ttu-id="3cef7-119">描述</span><span class="sxs-lookup"><span data-stu-id="3cef7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cef7-120">\<filter></span><span class="sxs-lookup"><span data-stu-id="3cef7-120">\<filter></span></span>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="3cef7-121">父項目</span><span class="sxs-lookup"><span data-stu-id="3cef7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3cef7-122">項目</span><span class="sxs-lookup"><span data-stu-id="3cef7-122">Element</span></span>|<span data-ttu-id="3cef7-123">描述</span><span class="sxs-lookup"><span data-stu-id="3cef7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cef7-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="3cef7-124">\<routing></span></span>](routing.md)|<span data-ttu-id="3cef7-125">備份端點的清單。</span><span class="sxs-lookup"><span data-stu-id="3cef7-125">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cef7-126">備註</span><span class="sxs-lookup"><span data-stu-id="3cef7-126">Remarks</span></span>  
 <span data-ttu-id="3cef7-127">這個區段包含依順序排列的端點集合，訊息會在傳送至主要端點期間發生通訊例外狀況事件時，傳輸至這些端點。</span><span class="sxs-lookup"><span data-stu-id="3cef7-127">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="3cef7-128">如果在 [ `endpointName` [ \<新增 >](add-of-entries.md) ] 的屬性中所列出的主要端點傳送因通訊例外狀況而失敗, 則路由服務會嘗試將訊息傳送到此設定區段中的第一個端點。</span><span class="sxs-lookup"><span data-stu-id="3cef7-128">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="3cef7-129">如果這項作業同樣因為通訊例外狀況而失敗，則路由服務將嘗試傳送訊息至這個區段中包含的下一個訊息，直到嘗試成功、傳回通訊例外狀況以外的失敗，或是集合中所有端點都傳回失敗為止。</span><span class="sxs-lookup"><span data-stu-id="3cef7-129">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="3cef7-130">在下列範例中, 如果傳送至名為「目的地」的主要端點傳回通訊例外狀況, 服務就會嘗試將訊息傳送至 "alternateServiceQueue"。</span><span class="sxs-lookup"><span data-stu-id="3cef7-130">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="3cef7-131">如果這項嘗試同樣傳回通訊例外狀況，則路由服務將嘗試傳送訊息至集合中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="3cef7-131">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3cef7-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cef7-132">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
