---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 940bf28958251e7257b2cc19a9c5ff0059411bcd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201547"
---
# \<backupLists>

<span data-ttu-id="c017c-101">代表組態區段，用於定義錯誤處理中使用的一組備份服務。</span><span class="sxs-lookup"><span data-stu-id="c017c-101">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="c017c-102">每一個子項目都是一個備份清單，此清單會列舉您希望路由服務在無法連上主要端點時使用的一組端點。</span><span class="sxs-lookup"><span data-stu-id="c017c-102">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="c017c-103">如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="c017c-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="c017c-104">如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。</span><span class="sxs-lookup"><span data-stu-id="c017c-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a><span data-ttu-id="c017c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c017c-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c017c-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c017c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c017c-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c017c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c017c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c017c-108">Attributes</span></span>  

 <span data-ttu-id="c017c-109">無。</span><span class="sxs-lookup"><span data-stu-id="c017c-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c017c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c017c-110">Child Elements</span></span>  
  
|<span data-ttu-id="c017c-111">項目</span><span class="sxs-lookup"><span data-stu-id="c017c-111">Element</span></span>|<span data-ttu-id="c017c-112">描述</span><span class="sxs-lookup"><span data-stu-id="c017c-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)|<span data-ttu-id="c017c-113">包含端點清單，這些端點是您希望路由服務在無法連上主要端點時使用的端點。</span><span class="sxs-lookup"><span data-stu-id="c017c-113">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="c017c-114">.</span><span class="sxs-lookup"><span data-stu-id="c017c-114">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c017c-115">父項目</span><span class="sxs-lookup"><span data-stu-id="c017c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c017c-116">項目</span><span class="sxs-lookup"><span data-stu-id="c017c-116">Element</span></span>|<span data-ttu-id="c017c-117">描述</span><span class="sxs-lookup"><span data-stu-id="c017c-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="c017c-118">表示用於定義一組路由篩選的設定區段，這會決定要在評估內送訊息時使用的 Windows Communication Foundation (WCF) 的型別 <xref:System.ServiceModel.Dispatcher.MessageFilter> ，以及定義篩選準則符合時要傳送訊息的目標端點的路由表。</span><span class="sxs-lookup"><span data-stu-id="c017c-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c017c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c017c-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
