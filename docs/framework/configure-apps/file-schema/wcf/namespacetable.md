---
title: '&lt;a d d&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 470dd2dcc2e8554bb89eec159c6b96b24795c5d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="efce5-102">&lt;a d d&gt;</span><span class="sxs-lookup"><span data-stu-id="efce5-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="efce5-103">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="efce5-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="efce5-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="efce5-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="efce5-105">&nbsp;&nbsp;**\<路由 >** </span><span class="sxs-lookup"><span data-stu-id="efce5-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="efce5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<a d d >**</span><span class="sxs-lookup"><span data-stu-id="efce5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="efce5-107">語法</span><span class="sxs-lookup"><span data-stu-id="efce5-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="efce5-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="efce5-108">Attributes and elements</span></span>

<span data-ttu-id="efce5-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="efce5-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="efce5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="efce5-110">Attributes</span></span>

<span data-ttu-id="efce5-111">無</span><span class="sxs-lookup"><span data-stu-id="efce5-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="efce5-112">子元素</span><span class="sxs-lookup"><span data-stu-id="efce5-112">Child elements</span></span>

|     | <span data-ttu-id="efce5-113">說明</span><span class="sxs-lookup"><span data-stu-id="efce5-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="efce5-114">**\<篩選條件 >**</span><span class="sxs-lookup"><span data-stu-id="efce5-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="efce5-115">定義用於 XPath 運算式的命名空間前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="efce5-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="efce5-116">父元素</span><span class="sxs-lookup"><span data-stu-id="efce5-116">Parent elements</span></span>

|     | <span data-ttu-id="efce5-117">說明</span><span class="sxs-lookup"><span data-stu-id="efce5-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="efce5-118">**\<路由 >**</span><span class="sxs-lookup"><span data-stu-id="efce5-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="efce5-119">代表定義一組路由篩選條件的組態區段，這些篩選條件會判斷傳入訊息時所用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別及路由表 (定義當篩選條件相符時的訊息傳送目標端點)。</span><span class="sxs-lookup"><span data-stu-id="efce5-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="efce5-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="efce5-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
