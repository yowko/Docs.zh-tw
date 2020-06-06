---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399966"
---
# \<routing>

<span data-ttu-id="b1c2f-101">表示定義一組路由篩選的設定區段，其會決定在評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型 <xref:System.ServiceModel.Dispatcher.MessageFilter> ，以及定義當篩選準則符合時，要傳送訊息的目標端點的路由表。</span><span class="sxs-lookup"><span data-stu-id="b1c2f-101">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a><span data-ttu-id="b1c2f-102">語法</span><span class="sxs-lookup"><span data-stu-id="b1c2f-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1c2f-103">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="b1c2f-103">Attributes and elements</span></span>

<span data-ttu-id="b1c2f-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b1c2f-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1c2f-105">屬性</span><span class="sxs-lookup"><span data-stu-id="b1c2f-105">Attributes</span></span>

<span data-ttu-id="b1c2f-106">無</span><span class="sxs-lookup"><span data-stu-id="b1c2f-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1c2f-107">子元素</span><span class="sxs-lookup"><span data-stu-id="b1c2f-107">Child elements</span></span>

|     | <span data-ttu-id="b1c2f-108">描述</span><span class="sxs-lookup"><span data-stu-id="b1c2f-108">Description</span></span> |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | <span data-ttu-id="b1c2f-109">包含一組路由篩選準則，決定在評估傳入訊息時，會使用 Windows Communication Foundation （WCF） MessageFilter 的類型。</span><span class="sxs-lookup"><span data-stu-id="b1c2f-109">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [**\<filterTables>**](filtertables.md) | <span data-ttu-id="b1c2f-110">包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。</span><span class="sxs-lookup"><span data-stu-id="b1c2f-110">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="b1c2f-111">父元素</span><span class="sxs-lookup"><span data-stu-id="b1c2f-111">Parent elements</span></span>

|     | <span data-ttu-id="b1c2f-112">描述</span><span class="sxs-lookup"><span data-stu-id="b1c2f-112">Description</span></span> |
| --- | ----------- |
| **\<system.ServiceModel>** | <span data-ttu-id="b1c2f-113">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="b1c2f-113">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="b1c2f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1c2f-114">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
