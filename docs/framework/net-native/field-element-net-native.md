---
title: "&lt;Field&gt; 項目 (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9a3a928185146ac90ec4c3a905bf4f0e69e0e8d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltfieldgt-element-net-native"></a><span data-ttu-id="e6af0-102">&lt;Field&gt; 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e6af0-102">&lt;Field&gt; Element (.NET Native)</span></span>
<span data-ttu-id="e6af0-103">將執行階段反映原則套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="e6af0-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6af0-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6af0-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6af0-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6af0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e6af0-106">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e6af0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6af0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e6af0-107">Attributes</span></span>  
  
|<span data-ttu-id="e6af0-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e6af0-108">Attribute</span></span>|<span data-ttu-id="e6af0-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="e6af0-109">Attribute type</span></span>|<span data-ttu-id="e6af0-110">說明</span><span class="sxs-lookup"><span data-stu-id="e6af0-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e6af0-111">一般</span><span class="sxs-lookup"><span data-stu-id="e6af0-111">General</span></span>|<span data-ttu-id="e6af0-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e6af0-112">Required attribute.</span></span> <span data-ttu-id="e6af0-113">指定欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="e6af0-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="e6af0-114">反射</span><span class="sxs-lookup"><span data-stu-id="e6af0-114">Reflection</span></span>|<span data-ttu-id="e6af0-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e6af0-115">Optional attribute.</span></span> <span data-ttu-id="e6af0-116">控制對欄位相關資訊的查詢，或控制欄位的列舉，但不會在執行階段啟用任何動態存取。</span><span class="sxs-lookup"><span data-stu-id="e6af0-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="e6af0-117">反射</span><span class="sxs-lookup"><span data-stu-id="e6af0-117">Reflection</span></span>|<span data-ttu-id="e6af0-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e6af0-118">Optional attribute.</span></span> <span data-ttu-id="e6af0-119">控制對欄位的執行階段存取權，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="e6af0-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="e6af0-120">此原則可確保能夠在執行階段動態設定或擷取欄位。</span><span class="sxs-lookup"><span data-stu-id="e6af0-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="e6af0-121">序列化</span><span class="sxs-lookup"><span data-stu-id="e6af0-121">Serialization</span></span>|<span data-ttu-id="e6af0-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e6af0-122">Optional attribute.</span></span> <span data-ttu-id="e6af0-123">控制對欄位的執行階段存取權，使類型執行個體能夠由 Newtonsoft JSON 序列化程式之類的程式庫來序列化，或是用於資料繫結。</span><span class="sxs-lookup"><span data-stu-id="e6af0-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e6af0-124">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="e6af0-124">Name attribute</span></span>  
  
|<span data-ttu-id="e6af0-125">值</span><span class="sxs-lookup"><span data-stu-id="e6af0-125">Value</span></span>|<span data-ttu-id="e6af0-126">說明</span><span class="sxs-lookup"><span data-stu-id="e6af0-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6af0-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="e6af0-127">*method_name*</span></span>|<span data-ttu-id="e6af0-128">欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="e6af0-128">The field name.</span></span> <span data-ttu-id="e6af0-129">欄位的類型是由父系 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 或 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目定義。</span><span class="sxs-lookup"><span data-stu-id="e6af0-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e6af0-130">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="e6af0-130">All other attributes</span></span>  
  
|<span data-ttu-id="e6af0-131">值</span><span class="sxs-lookup"><span data-stu-id="e6af0-131">Value</span></span>|<span data-ttu-id="e6af0-132">說明</span><span class="sxs-lookup"><span data-stu-id="e6af0-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6af0-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="e6af0-133">*policy_setting*</span></span>|<span data-ttu-id="e6af0-134">要為欄位套用此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="e6af0-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="e6af0-135">可能的值為 `Auto`、`Excluded`、`Included` 和 `Required`。</span><span class="sxs-lookup"><span data-stu-id="e6af0-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="e6af0-136">如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="e6af0-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6af0-137">子元素</span><span class="sxs-lookup"><span data-stu-id="e6af0-137">Child Elements</span></span>  
 <span data-ttu-id="e6af0-138">無。</span><span class="sxs-lookup"><span data-stu-id="e6af0-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6af0-139">父項目</span><span class="sxs-lookup"><span data-stu-id="e6af0-139">Parent Elements</span></span>  
  
|<span data-ttu-id="e6af0-140">項目</span><span class="sxs-lookup"><span data-stu-id="e6af0-140">Element</span></span>|<span data-ttu-id="e6af0-141">說明</span><span class="sxs-lookup"><span data-stu-id="e6af0-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6af0-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="e6af0-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="e6af0-143">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="e6af0-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="e6af0-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="e6af0-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="e6af0-145">將反映原則套用至建構的泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="e6af0-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6af0-146">備註</span><span class="sxs-lookup"><span data-stu-id="e6af0-146">Remarks</span></span>  
 <span data-ttu-id="e6af0-147">如果未明確定義欄位的原則，則會繼承其父元素的執行階段原則。</span><span class="sxs-lookup"><span data-stu-id="e6af0-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6af0-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6af0-148">See Also</span></span>  
 [<span data-ttu-id="e6af0-149">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="e6af0-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="e6af0-150">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="e6af0-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="e6af0-151">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="e6af0-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
