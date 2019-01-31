---
title: <Field> 項目 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4a062e060e7b367f0d56b3633238de74ae8ed88
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281667"
---
# <a name="field-element-net-native"></a><span data-ttu-id="3bcda-102">\<欄位 > 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="3bcda-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="3bcda-103">將執行階段反映原則套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="3bcda-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bcda-104">語法</span><span class="sxs-lookup"><span data-stu-id="3bcda-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bcda-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3bcda-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3bcda-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3bcda-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bcda-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3bcda-107">Attributes</span></span>  
  
|<span data-ttu-id="3bcda-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3bcda-108">Attribute</span></span>|<span data-ttu-id="3bcda-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="3bcda-109">Attribute type</span></span>|<span data-ttu-id="3bcda-110">描述</span><span class="sxs-lookup"><span data-stu-id="3bcda-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="3bcda-111">一般</span><span class="sxs-lookup"><span data-stu-id="3bcda-111">General</span></span>|<span data-ttu-id="3bcda-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3bcda-112">Required attribute.</span></span> <span data-ttu-id="3bcda-113">指定欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="3bcda-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="3bcda-114">反射</span><span class="sxs-lookup"><span data-stu-id="3bcda-114">Reflection</span></span>|<span data-ttu-id="3bcda-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3bcda-115">Optional attribute.</span></span> <span data-ttu-id="3bcda-116">控制對欄位相關資訊的查詢，或控制欄位的列舉，但不會在執行階段啟用任何動態存取。</span><span class="sxs-lookup"><span data-stu-id="3bcda-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="3bcda-117">反射</span><span class="sxs-lookup"><span data-stu-id="3bcda-117">Reflection</span></span>|<span data-ttu-id="3bcda-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3bcda-118">Optional attribute.</span></span> <span data-ttu-id="3bcda-119">控制對欄位的執行階段存取權，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="3bcda-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="3bcda-120">此原則可確保能夠在執行階段動態設定或擷取欄位。</span><span class="sxs-lookup"><span data-stu-id="3bcda-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="3bcda-121">序列化</span><span class="sxs-lookup"><span data-stu-id="3bcda-121">Serialization</span></span>|<span data-ttu-id="3bcda-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3bcda-122">Optional attribute.</span></span> <span data-ttu-id="3bcda-123">控制對欄位的執行階段存取權，使類型執行個體能夠由 Newtonsoft JSON 序列化程式之類的程式庫來序列化，或是用於資料繫結。</span><span class="sxs-lookup"><span data-stu-id="3bcda-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="3bcda-124">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="3bcda-124">Name attribute</span></span>  
  
|<span data-ttu-id="3bcda-125">值</span><span class="sxs-lookup"><span data-stu-id="3bcda-125">Value</span></span>|<span data-ttu-id="3bcda-126">描述</span><span class="sxs-lookup"><span data-stu-id="3bcda-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3bcda-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="3bcda-127">*method_name*</span></span>|<span data-ttu-id="3bcda-128">欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="3bcda-128">The field name.</span></span> <span data-ttu-id="3bcda-129">欄位的類型是由父系 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 或 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目定義。</span><span class="sxs-lookup"><span data-stu-id="3bcda-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="3bcda-130">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="3bcda-130">All other attributes</span></span>  
  
|<span data-ttu-id="3bcda-131">值</span><span class="sxs-lookup"><span data-stu-id="3bcda-131">Value</span></span>|<span data-ttu-id="3bcda-132">描述</span><span class="sxs-lookup"><span data-stu-id="3bcda-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3bcda-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="3bcda-133">*policy_setting*</span></span>|<span data-ttu-id="3bcda-134">要為欄位套用此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="3bcda-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="3bcda-135">可能的值為 `Auto`、`Excluded`、`Included` 和 `Required`。</span><span class="sxs-lookup"><span data-stu-id="3bcda-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="3bcda-136">如需詳細資訊，請參閱[執行階段指示詞原則設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="3bcda-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bcda-137">子元素</span><span class="sxs-lookup"><span data-stu-id="3bcda-137">Child Elements</span></span>  
 <span data-ttu-id="3bcda-138">無。</span><span class="sxs-lookup"><span data-stu-id="3bcda-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bcda-139">父項目</span><span class="sxs-lookup"><span data-stu-id="3bcda-139">Parent Elements</span></span>  
  
|<span data-ttu-id="3bcda-140">項目</span><span class="sxs-lookup"><span data-stu-id="3bcda-140">Element</span></span>|<span data-ttu-id="3bcda-141">描述</span><span class="sxs-lookup"><span data-stu-id="3bcda-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bcda-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="3bcda-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="3bcda-143">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="3bcda-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="3bcda-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="3bcda-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="3bcda-145">將反映原則套用至已建構的泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="3bcda-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bcda-146">備註</span><span class="sxs-lookup"><span data-stu-id="3bcda-146">Remarks</span></span>  
 <span data-ttu-id="3bcda-147">如果未明確定義欄位的原則，則會繼承其父元素的執行階段原則。</span><span class="sxs-lookup"><span data-stu-id="3bcda-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bcda-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bcda-148">See also</span></span>
- [<span data-ttu-id="3bcda-149">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="3bcda-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
- [<span data-ttu-id="3bcda-150">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="3bcda-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="3bcda-151">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="3bcda-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
