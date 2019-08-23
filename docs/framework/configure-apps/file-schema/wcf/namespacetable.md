---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 0316e983446644671ead2f8f843dc91b493b29c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933162"
---
# <a name="namespacetable"></a><span data-ttu-id="340be-101">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="340be-101">\<namespaceTable></span></span>

<span data-ttu-id="340be-102">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="340be-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="340be-103">**\<system.serviceModel>**  </span><span class="sxs-lookup"><span data-stu-id="340be-103">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="340be-104">&nbsp;&nbsp; **\<routing>**  </span><span class="sxs-lookup"><span data-stu-id="340be-104">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="340be-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<namespaceTable>**</span><span class="sxs-lookup"><span data-stu-id="340be-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="340be-106">語法</span><span class="sxs-lookup"><span data-stu-id="340be-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="340be-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="340be-107">Attributes and elements</span></span>

<span data-ttu-id="340be-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="340be-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="340be-109">屬性</span><span class="sxs-lookup"><span data-stu-id="340be-109">Attributes</span></span>

<span data-ttu-id="340be-110">None</span><span class="sxs-lookup"><span data-stu-id="340be-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="340be-111">子元素</span><span class="sxs-lookup"><span data-stu-id="340be-111">Child elements</span></span>

|     | <span data-ttu-id="340be-112">描述</span><span class="sxs-lookup"><span data-stu-id="340be-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="340be-113"> **\<filter>** </span><span class="sxs-lookup"><span data-stu-id="340be-113">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="340be-114">定義用於 XPath 運算式的命名空間前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="340be-114">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="340be-115">父元素</span><span class="sxs-lookup"><span data-stu-id="340be-115">Parent elements</span></span>

|     | <span data-ttu-id="340be-116">描述</span><span class="sxs-lookup"><span data-stu-id="340be-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="340be-117"> **\<routing>** </span><span class="sxs-lookup"><span data-stu-id="340be-117">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="340be-118">表示定義一組路由篩選的設定區段, 其決定在評估傳入訊息時所使用的 Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) 類型, 以及將目標端點定義為的路由表。當篩選準則相符時, 將訊息傳送至。</span><span class="sxs-lookup"><span data-stu-id="340be-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="340be-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="340be-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
