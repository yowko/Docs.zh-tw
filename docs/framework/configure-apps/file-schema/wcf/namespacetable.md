---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855103"
---
# \<namespaceTable>

<span data-ttu-id="7c0b0-101">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="7c0b0-101">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a><span data-ttu-id="7c0b0-102">語法</span><span class="sxs-lookup"><span data-stu-id="7c0b0-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c0b0-103">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="7c0b0-103">Attributes and elements</span></span>

<span data-ttu-id="7c0b0-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7c0b0-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c0b0-105">屬性</span><span class="sxs-lookup"><span data-stu-id="7c0b0-105">Attributes</span></span>

<span data-ttu-id="7c0b0-106">無</span><span class="sxs-lookup"><span data-stu-id="7c0b0-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c0b0-107">子元素</span><span class="sxs-lookup"><span data-stu-id="7c0b0-107">Child elements</span></span>

|     | <span data-ttu-id="7c0b0-108">描述</span><span class="sxs-lookup"><span data-stu-id="7c0b0-108">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="7c0b0-109">定義用於 XPath 運算式的命名空間前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="7c0b0-109">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="7c0b0-110">父元素</span><span class="sxs-lookup"><span data-stu-id="7c0b0-110">Parent elements</span></span>

|     | <span data-ttu-id="7c0b0-111">描述</span><span class="sxs-lookup"><span data-stu-id="7c0b0-111">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="7c0b0-112">表示定義一組路由篩選的設定區段，其會決定在評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型 <xref:System.ServiceModel.Dispatcher.MessageFilter> ，以及定義當篩選準則符合時，要傳送訊息的目標端點的路由表。</span><span class="sxs-lookup"><span data-stu-id="7c0b0-112">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="7c0b0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c0b0-113">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
