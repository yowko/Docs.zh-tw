---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855103"
---
# <a name="namespacetable"></a><span data-ttu-id="be1a6-101">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="be1a6-101">\<namespaceTable></span></span>

<span data-ttu-id="be1a6-102">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="be1a6-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="be1a6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="be1a6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="be1a6-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="be1a6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="be1a6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<路由 >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="be1a6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="be1a6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="be1a6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be1a6-107">語法</span><span class="sxs-lookup"><span data-stu-id="be1a6-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be1a6-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="be1a6-108">Attributes and elements</span></span>

<span data-ttu-id="be1a6-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="be1a6-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="be1a6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="be1a6-110">Attributes</span></span>

<span data-ttu-id="be1a6-111">None</span><span class="sxs-lookup"><span data-stu-id="be1a6-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="be1a6-112">子元素</span><span class="sxs-lookup"><span data-stu-id="be1a6-112">Child elements</span></span>

|     | <span data-ttu-id="be1a6-113">描述</span><span class="sxs-lookup"><span data-stu-id="be1a6-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="be1a6-114"> **\<filter>** </span><span class="sxs-lookup"><span data-stu-id="be1a6-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="be1a6-115">定義用於 XPath 運算式的命名空間前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="be1a6-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="be1a6-116">父元素</span><span class="sxs-lookup"><span data-stu-id="be1a6-116">Parent elements</span></span>

|     | <span data-ttu-id="be1a6-117">描述</span><span class="sxs-lookup"><span data-stu-id="be1a6-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="be1a6-118"> **\<routing>** </span><span class="sxs-lookup"><span data-stu-id="be1a6-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="be1a6-119">表示定義一組路由篩選的設定區段，其決定在評估傳入訊息時所使用的 Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> （WCF）類型，以及將目標端點定義為的路由表。當篩選準則相符時，將訊息傳送至。</span><span class="sxs-lookup"><span data-stu-id="be1a6-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="be1a6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be1a6-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
