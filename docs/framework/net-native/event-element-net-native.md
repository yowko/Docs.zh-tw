---
title: '&lt;Event&gt; 項目 (.NET Native)'
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7ccf013398420dbeb7918f99baa922aa1bc89db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395550"
---
# <a name="lteventgt-element-net-native"></a><span data-ttu-id="5820f-102">&lt;Event&gt; 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="5820f-102">&lt;Event&gt; Element (.NET Native)</span></span>
<span data-ttu-id="5820f-103">將執行階段反映原則套用至事件。</span><span class="sxs-lookup"><span data-stu-id="5820f-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5820f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5820f-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5820f-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5820f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5820f-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5820f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5820f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5820f-107">Attributes</span></span>  
  
|<span data-ttu-id="5820f-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5820f-108">Attribute</span></span>|<span data-ttu-id="5820f-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="5820f-109">Attribute type</span></span>|<span data-ttu-id="5820f-110">描述</span><span class="sxs-lookup"><span data-stu-id="5820f-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="5820f-111">一般</span><span class="sxs-lookup"><span data-stu-id="5820f-111">General</span></span>|<span data-ttu-id="5820f-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5820f-112">Required attribute.</span></span> <span data-ttu-id="5820f-113">指定事件名稱。</span><span class="sxs-lookup"><span data-stu-id="5820f-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="5820f-114">反射</span><span class="sxs-lookup"><span data-stu-id="5820f-114">Reflection</span></span>|<span data-ttu-id="5820f-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="5820f-115">Optional attribute.</span></span> <span data-ttu-id="5820f-116">控制事件相關資訊的查詢或事件的列舉，但不會在執行階段啟用任何動態存取。</span><span class="sxs-lookup"><span data-stu-id="5820f-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="5820f-117">反射</span><span class="sxs-lookup"><span data-stu-id="5820f-117">Reflection</span></span>|<span data-ttu-id="5820f-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="5820f-118">Optional attribute.</span></span> <span data-ttu-id="5820f-119">控制事件的執行階段存取，以便啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="5820f-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="5820f-120">這個原則可確保在執行階段能夠以動態方式來處理事件。</span><span class="sxs-lookup"><span data-stu-id="5820f-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="5820f-121">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="5820f-121">Name attribute</span></span>  
  
|<span data-ttu-id="5820f-122">值</span><span class="sxs-lookup"><span data-stu-id="5820f-122">Value</span></span>|<span data-ttu-id="5820f-123">描述</span><span class="sxs-lookup"><span data-stu-id="5820f-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5820f-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="5820f-124">*method_name*</span></span>|<span data-ttu-id="5820f-125">事件名稱。</span><span class="sxs-lookup"><span data-stu-id="5820f-125">The event name.</span></span> <span data-ttu-id="5820f-126">事件的類型是由父 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 或 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目所定義。</span><span class="sxs-lookup"><span data-stu-id="5820f-126">The type of the event is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="5820f-127">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="5820f-127">All other attributes</span></span>  
  
|<span data-ttu-id="5820f-128">值</span><span class="sxs-lookup"><span data-stu-id="5820f-128">Value</span></span>|<span data-ttu-id="5820f-129">描述</span><span class="sxs-lookup"><span data-stu-id="5820f-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5820f-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="5820f-130">*policy_setting*</span></span>|<span data-ttu-id="5820f-131">要套用至事件之這個原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="5820f-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="5820f-132">可能的值為 `Auto`、`Excluded`、`Included` 和 `Required`。</span><span class="sxs-lookup"><span data-stu-id="5820f-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="5820f-133">如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="5820f-133">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5820f-134">子項目</span><span class="sxs-lookup"><span data-stu-id="5820f-134">Child Elements</span></span>  
 <span data-ttu-id="5820f-135">無。</span><span class="sxs-lookup"><span data-stu-id="5820f-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5820f-136">父項目</span><span class="sxs-lookup"><span data-stu-id="5820f-136">Parent Elements</span></span>  
  
|<span data-ttu-id="5820f-137">項目</span><span class="sxs-lookup"><span data-stu-id="5820f-137">Element</span></span>|<span data-ttu-id="5820f-138">描述</span><span class="sxs-lookup"><span data-stu-id="5820f-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5820f-139">\<Type></span><span class="sxs-lookup"><span data-stu-id="5820f-139">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="5820f-140">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="5820f-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="5820f-141">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="5820f-141">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="5820f-142">將反映原則套用至已建構的泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="5820f-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5820f-143">備註</span><span class="sxs-lookup"><span data-stu-id="5820f-143">Remarks</span></span>  
 <span data-ttu-id="5820f-144">如果未明確定義事件的原則，則會繼承其父項目的執行階段原則。</span><span class="sxs-lookup"><span data-stu-id="5820f-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5820f-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5820f-145">See Also</span></span>  
 [<span data-ttu-id="5820f-146">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="5820f-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="5820f-147">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="5820f-147">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="5820f-148">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="5820f-148">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
