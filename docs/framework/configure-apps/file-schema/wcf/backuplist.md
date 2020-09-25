---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 8f4dcf8f7d71cfa2ed9944822d7cce974e7f1979
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201560"
---
# \<backupList>

<span data-ttu-id="5f7e4-101">代表用於定義備份清單的組態區段，此清單會列舉您希望路由服務在無法連上主要端點時使用的一組端點。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-101">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="5f7e4-102">如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-102">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="5f7e4-103">如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-103">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
## <a name="syntax"></a><span data-ttu-id="5f7e4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5f7e4-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f7e4-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5f7e4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5f7e4-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f7e4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5f7e4-107">Attributes</span></span>  
  
|<span data-ttu-id="5f7e4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5f7e4-108">Attribute</span></span>|<span data-ttu-id="5f7e4-109">描述</span><span class="sxs-lookup"><span data-stu-id="5f7e4-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f7e4-110">NAME</span><span class="sxs-lookup"><span data-stu-id="5f7e4-110">name</span></span>|<span data-ttu-id="5f7e4-111">字串，指定用於識別這個端點清單的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-111">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f7e4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="5f7e4-112">Child Elements</span></span>  
  
|<span data-ttu-id="5f7e4-113">項目</span><span class="sxs-lookup"><span data-stu-id="5f7e4-113">Element</span></span>|<span data-ttu-id="5f7e4-114">描述</span><span class="sxs-lookup"><span data-stu-id="5f7e4-114">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="5f7e4-115">父項目</span><span class="sxs-lookup"><span data-stu-id="5f7e4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5f7e4-116">項目</span><span class="sxs-lookup"><span data-stu-id="5f7e4-116">Element</span></span>|<span data-ttu-id="5f7e4-117">描述</span><span class="sxs-lookup"><span data-stu-id="5f7e4-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="5f7e4-118">備份端點的清單。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-118">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f7e4-119">備註</span><span class="sxs-lookup"><span data-stu-id="5f7e4-119">Remarks</span></span>  

 <span data-ttu-id="5f7e4-120">這個區段包含依順序排列的端點集合，訊息會在傳送至主要端點期間發生通訊例外狀況事件時，傳輸至這些端點。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-120">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="5f7e4-121">如果傳送至屬性中所列的主要端點 `endpointName` [\<add>](add-of-entries.md) 因為發生通訊例外狀況而失敗，則路由服務會嘗試將訊息傳送至這個設定區段中的第一個端點。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-121">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="5f7e4-122">如果這項作業同樣因為通訊例外狀況而失敗，則路由服務將嘗試傳送訊息至這個區段中包含的下一個訊息，直到嘗試成功、傳回通訊例外狀況以外的失敗，或是集合中所有端點都傳回失敗為止。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-122">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="5f7e4-123">在下列範例中，如果傳送至名為 "Destination" 的主要端點傳回通訊例外狀況，服務會嘗試將訊息傳送至 "alternateServiceQueue"。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-123">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="5f7e4-124">如果這項嘗試同樣傳回通訊例外狀況，則路由服務將嘗試傳送訊息至集合中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="5f7e4-124">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f7e4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f7e4-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
