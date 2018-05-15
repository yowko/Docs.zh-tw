---
title: '&lt;路由&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 1771d8a2603a8f61af6ba6e2acf6243d2fd073f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltroutinggt"></a><span data-ttu-id="6f7cc-102">&lt;路由&gt;</span><span class="sxs-lookup"><span data-stu-id="6f7cc-102">&lt;routing&gt;</span></span>

<span data-ttu-id="6f7cc-103">代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>傳入訊息及路由表定義目標端點時所要使用當篩選條件相符時傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="6f7cc-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="6f7cc-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6f7cc-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="6f7cc-105">&nbsp;&nbsp;**\<路由 >**</span><span class="sxs-lookup"><span data-stu-id="6f7cc-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6f7cc-106">語法</span><span class="sxs-lookup"><span data-stu-id="6f7cc-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="6f7cc-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="6f7cc-107">Attributes and elements</span></span>

<span data-ttu-id="6f7cc-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6f7cc-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6f7cc-109">屬性</span><span class="sxs-lookup"><span data-stu-id="6f7cc-109">Attributes</span></span>

<span data-ttu-id="6f7cc-110">無</span><span class="sxs-lookup"><span data-stu-id="6f7cc-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="6f7cc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6f7cc-111">Child elements</span></span>

|     | <span data-ttu-id="6f7cc-112">描述</span><span class="sxs-lookup"><span data-stu-id="6f7cc-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6f7cc-113">**\<篩選條件 >**</span><span class="sxs-lookup"><span data-stu-id="6f7cc-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="6f7cc-114">包含一組路由篩選條件，以決定評估內送訊息時，就會使用 Windows Communication Foundation (WCF) MessageFilter 的型別。</span><span class="sxs-lookup"><span data-stu-id="6f7cc-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="6f7cc-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="6f7cc-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="6f7cc-116">包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。</span><span class="sxs-lookup"><span data-stu-id="6f7cc-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="6f7cc-117">父元素</span><span class="sxs-lookup"><span data-stu-id="6f7cc-117">Parent elements</span></span>

|     | <span data-ttu-id="6f7cc-118">描述</span><span class="sxs-lookup"><span data-stu-id="6f7cc-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="6f7cc-119">**\<系統。ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="6f7cc-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="6f7cc-120">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="6f7cc-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="6f7cc-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f7cc-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
