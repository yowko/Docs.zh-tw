---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399966"
---
# <a name="routing"></a><span data-ttu-id="d2399-101">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="d2399-101">\<routing></span></span>

<span data-ttu-id="d2399-102">表示定義一組路由篩選的設定區段，其決定在評估傳入訊息時所使用的 Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> （WCF）類型，以及將目標端點定義為的路由表。當篩選準則相符時，將訊息傳送至。</span><span class="sxs-lookup"><span data-stu-id="d2399-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="d2399-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2399-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d2399-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d2399-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d2399-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<路由 >**</span><span class="sxs-lookup"><span data-stu-id="d2399-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="d2399-106">語法</span><span class="sxs-lookup"><span data-stu-id="d2399-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2399-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="d2399-107">Attributes and elements</span></span>

<span data-ttu-id="d2399-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d2399-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d2399-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d2399-109">Attributes</span></span>

<span data-ttu-id="d2399-110">無</span><span class="sxs-lookup"><span data-stu-id="d2399-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d2399-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d2399-111">Child elements</span></span>

|     | <span data-ttu-id="d2399-112">說明</span><span class="sxs-lookup"><span data-stu-id="d2399-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d2399-113"> **\<filters>** </span><span class="sxs-lookup"><span data-stu-id="d2399-113">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="d2399-114">包含一組路由篩選準則，決定在評估傳入訊息時，會使用 Windows Communication Foundation （WCF） MessageFilter 的類型。</span><span class="sxs-lookup"><span data-stu-id="d2399-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="d2399-115"> **\<filterTables>** </span><span class="sxs-lookup"><span data-stu-id="d2399-115">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="d2399-116">包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。</span><span class="sxs-lookup"><span data-stu-id="d2399-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="d2399-117">父元素</span><span class="sxs-lookup"><span data-stu-id="d2399-117">Parent elements</span></span>

|     | <span data-ttu-id="d2399-118">描述</span><span class="sxs-lookup"><span data-stu-id="d2399-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="d2399-119">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="d2399-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="d2399-120">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="d2399-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="d2399-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2399-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
