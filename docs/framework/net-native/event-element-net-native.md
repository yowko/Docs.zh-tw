---
title: '<Event> 元素 ( .NET Native) '
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: b1cf2239e58839c5026bc375ba04568227881bdd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288095"
---
# <a name="event-element-net-native"></a><span data-ttu-id="1f60b-102">\<Event> 元素 ( .NET Native) </span><span class="sxs-lookup"><span data-stu-id="1f60b-102">\<Event> Element (.NET Native)</span></span>

<span data-ttu-id="1f60b-103">將執行階段反映原則套用至事件。</span><span class="sxs-lookup"><span data-stu-id="1f60b-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f60b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f60b-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f60b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1f60b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1f60b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1f60b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f60b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1f60b-107">Attributes</span></span>  
  
|<span data-ttu-id="1f60b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1f60b-108">Attribute</span></span>|<span data-ttu-id="1f60b-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="1f60b-109">Attribute type</span></span>|<span data-ttu-id="1f60b-110">描述</span><span class="sxs-lookup"><span data-stu-id="1f60b-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="1f60b-111">一般</span><span class="sxs-lookup"><span data-stu-id="1f60b-111">General</span></span>|<span data-ttu-id="1f60b-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1f60b-112">Required attribute.</span></span> <span data-ttu-id="1f60b-113">指定事件名稱。</span><span class="sxs-lookup"><span data-stu-id="1f60b-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="1f60b-114">反射</span><span class="sxs-lookup"><span data-stu-id="1f60b-114">Reflection</span></span>|<span data-ttu-id="1f60b-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f60b-115">Optional attribute.</span></span> <span data-ttu-id="1f60b-116">控制事件相關資訊的查詢或事件的列舉，但不會在執行階段啟用任何動態存取。</span><span class="sxs-lookup"><span data-stu-id="1f60b-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="1f60b-117">反射</span><span class="sxs-lookup"><span data-stu-id="1f60b-117">Reflection</span></span>|<span data-ttu-id="1f60b-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f60b-118">Optional attribute.</span></span> <span data-ttu-id="1f60b-119">控制事件的執行階段存取，以便啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="1f60b-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="1f60b-120">這個原則可確保在執行階段能夠以動態方式來處理事件。</span><span class="sxs-lookup"><span data-stu-id="1f60b-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="1f60b-121">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="1f60b-121">Name attribute</span></span>  
  
|<span data-ttu-id="1f60b-122">值</span><span class="sxs-lookup"><span data-stu-id="1f60b-122">Value</span></span>|<span data-ttu-id="1f60b-123">描述</span><span class="sxs-lookup"><span data-stu-id="1f60b-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1f60b-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="1f60b-124">*method_name*</span></span>|<span data-ttu-id="1f60b-125">事件名稱。</span><span class="sxs-lookup"><span data-stu-id="1f60b-125">The event name.</span></span> <span data-ttu-id="1f60b-126">事件的類型是由父系 [\<Type>](type-element-net-native.md) 或 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 元素定義。</span><span class="sxs-lookup"><span data-stu-id="1f60b-126">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="1f60b-127">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="1f60b-127">All other attributes</span></span>  
  
|<span data-ttu-id="1f60b-128">值</span><span class="sxs-lookup"><span data-stu-id="1f60b-128">Value</span></span>|<span data-ttu-id="1f60b-129">描述</span><span class="sxs-lookup"><span data-stu-id="1f60b-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1f60b-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="1f60b-130">*policy_setting*</span></span>|<span data-ttu-id="1f60b-131">要套用至事件之這個原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="1f60b-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="1f60b-132">可能的值為 `Auto`、`Excluded`、`Included` 和 `Required`。</span><span class="sxs-lookup"><span data-stu-id="1f60b-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="1f60b-133">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="1f60b-133">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f60b-134">子元素</span><span class="sxs-lookup"><span data-stu-id="1f60b-134">Child Elements</span></span>  

 <span data-ttu-id="1f60b-135">無。</span><span class="sxs-lookup"><span data-stu-id="1f60b-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f60b-136">父項目</span><span class="sxs-lookup"><span data-stu-id="1f60b-136">Parent Elements</span></span>  
  
|<span data-ttu-id="1f60b-137">元素</span><span class="sxs-lookup"><span data-stu-id="1f60b-137">Element</span></span>|<span data-ttu-id="1f60b-138">描述</span><span class="sxs-lookup"><span data-stu-id="1f60b-138">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="1f60b-139">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="1f60b-139">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="1f60b-140">將反映原則套用至建構泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="1f60b-140">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f60b-141">備註</span><span class="sxs-lookup"><span data-stu-id="1f60b-141">Remarks</span></span>  

 <span data-ttu-id="1f60b-142">如果未明確定義事件的原則，則會繼承其父項目的執行階段原則。</span><span class="sxs-lookup"><span data-stu-id="1f60b-142">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f60b-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f60b-143">See also</span></span>

- [<span data-ttu-id="1f60b-144">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="1f60b-144">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="1f60b-145">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="1f60b-145">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="1f60b-146">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="1f60b-146">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
