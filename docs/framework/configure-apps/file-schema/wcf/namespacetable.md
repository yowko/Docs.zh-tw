---
title: '&lt;a d d&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 31d661f39f9e3de0f7012c7fa52d4964e7ee4a69
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748876"
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="04983-102">&lt;a d d&gt;</span><span class="sxs-lookup"><span data-stu-id="04983-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="04983-103">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="04983-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="04983-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="04983-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="04983-105">&nbsp;&nbsp;**\<路由 >** </span><span class="sxs-lookup"><span data-stu-id="04983-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="04983-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<a d d >**</span><span class="sxs-lookup"><span data-stu-id="04983-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="04983-107">語法</span><span class="sxs-lookup"><span data-stu-id="04983-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="04983-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="04983-108">Attributes and elements</span></span>

<span data-ttu-id="04983-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="04983-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="04983-110">屬性</span><span class="sxs-lookup"><span data-stu-id="04983-110">Attributes</span></span>

<span data-ttu-id="04983-111">無</span><span class="sxs-lookup"><span data-stu-id="04983-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="04983-112">子元素</span><span class="sxs-lookup"><span data-stu-id="04983-112">Child elements</span></span>

|     | <span data-ttu-id="04983-113">描述</span><span class="sxs-lookup"><span data-stu-id="04983-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="04983-114">**\<篩選條件 >**</span><span class="sxs-lookup"><span data-stu-id="04983-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="04983-115">定義用於 XPath 運算式的命名空間前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="04983-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="04983-116">父元素</span><span class="sxs-lookup"><span data-stu-id="04983-116">Parent elements</span></span>

|     | <span data-ttu-id="04983-117">描述</span><span class="sxs-lookup"><span data-stu-id="04983-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="04983-118">**\<路由 >**</span><span class="sxs-lookup"><span data-stu-id="04983-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="04983-119">代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>傳入訊息及路由表定義目標端點時所要使用當篩選條件相符時傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="04983-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="04983-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04983-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
