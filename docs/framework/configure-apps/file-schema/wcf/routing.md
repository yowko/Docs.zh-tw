---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 3c7e9cb1284ab55c8dd199d9fb47a223698814f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934131"
---
# <a name="routing"></a><span data-ttu-id="41fa7-101">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="41fa7-101">\<routing></span></span>

<span data-ttu-id="41fa7-102">表示定義一組路由篩選的設定區段, 其決定在評估傳入訊息時所使用的 Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) 類型, 以及將目標端點定義為的路由表。當篩選準則相符時, 將訊息傳送至。</span><span class="sxs-lookup"><span data-stu-id="41fa7-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="41fa7-103">[ **\<system.serviceModel>** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="41fa7-103">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="41fa7-104">&nbsp;&nbsp; **\<routing>**</span><span class="sxs-lookup"><span data-stu-id="41fa7-104">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="41fa7-105">語法</span><span class="sxs-lookup"><span data-stu-id="41fa7-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41fa7-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="41fa7-106">Attributes and elements</span></span>

<span data-ttu-id="41fa7-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="41fa7-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="41fa7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="41fa7-108">Attributes</span></span>

<span data-ttu-id="41fa7-109">無</span><span class="sxs-lookup"><span data-stu-id="41fa7-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="41fa7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="41fa7-110">Child elements</span></span>

|     | <span data-ttu-id="41fa7-111">描述</span><span class="sxs-lookup"><span data-stu-id="41fa7-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="41fa7-112"> **\<filters>** </span><span class="sxs-lookup"><span data-stu-id="41fa7-112">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="41fa7-113">包含一組路由篩選準則, 決定在評估傳入訊息時, 會使用 Windows Communication Foundation (WCF) MessageFilter 的類型。</span><span class="sxs-lookup"><span data-stu-id="41fa7-113">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="41fa7-114"> **\<filterTables>** </span><span class="sxs-lookup"><span data-stu-id="41fa7-114">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="41fa7-115">包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。</span><span class="sxs-lookup"><span data-stu-id="41fa7-115">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="41fa7-116">父元素</span><span class="sxs-lookup"><span data-stu-id="41fa7-116">Parent elements</span></span>

|     | <span data-ttu-id="41fa7-117">描述</span><span class="sxs-lookup"><span data-stu-id="41fa7-117">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="41fa7-118">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="41fa7-118">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="41fa7-119">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="41fa7-119">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="41fa7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41fa7-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
