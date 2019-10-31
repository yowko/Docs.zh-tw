---
title: <Field> 元素（.NET Native）
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: 2a63b88c399a999cd00750dee1614352cea10e80
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128412"
---
# <a name="field-element-net-native"></a><span data-ttu-id="99432-102">\<欄位 > 元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="99432-102">\<Field> Element (.NET Native)</span></span>
<span data-ttu-id="99432-103">將執行階段反映原則套用至欄位。</span><span class="sxs-lookup"><span data-stu-id="99432-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99432-104">語法</span><span class="sxs-lookup"><span data-stu-id="99432-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99432-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="99432-105">Attributes and Elements</span></span>  
 <span data-ttu-id="99432-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="99432-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99432-107">屬性</span><span class="sxs-lookup"><span data-stu-id="99432-107">Attributes</span></span>  
  
|<span data-ttu-id="99432-108">屬性</span><span class="sxs-lookup"><span data-stu-id="99432-108">Attribute</span></span>|<span data-ttu-id="99432-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="99432-109">Attribute type</span></span>|<span data-ttu-id="99432-110">描述</span><span class="sxs-lookup"><span data-stu-id="99432-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="99432-111">一般</span><span class="sxs-lookup"><span data-stu-id="99432-111">General</span></span>|<span data-ttu-id="99432-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="99432-112">Required attribute.</span></span> <span data-ttu-id="99432-113">指定欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="99432-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="99432-114">反射</span><span class="sxs-lookup"><span data-stu-id="99432-114">Reflection</span></span>|<span data-ttu-id="99432-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="99432-115">Optional attribute.</span></span> <span data-ttu-id="99432-116">控制對欄位相關資訊的查詢，或控制欄位的列舉，但不會在執行階段啟用任何動態存取。</span><span class="sxs-lookup"><span data-stu-id="99432-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="99432-117">反射</span><span class="sxs-lookup"><span data-stu-id="99432-117">Reflection</span></span>|<span data-ttu-id="99432-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="99432-118">Optional attribute.</span></span> <span data-ttu-id="99432-119">控制對欄位的執行階段存取權，以啟用動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="99432-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="99432-120">此原則可確保能夠在執行階段動態設定或擷取欄位。</span><span class="sxs-lookup"><span data-stu-id="99432-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="99432-121">序列化</span><span class="sxs-lookup"><span data-stu-id="99432-121">Serialization</span></span>|<span data-ttu-id="99432-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="99432-122">Optional attribute.</span></span> <span data-ttu-id="99432-123">控制對欄位的執行階段存取權，使類型執行個體能夠由 Newtonsoft JSON 序列化程式之類的程式庫來序列化，或是用於資料繫結。</span><span class="sxs-lookup"><span data-stu-id="99432-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="99432-124">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="99432-124">Name attribute</span></span>  
  
|<span data-ttu-id="99432-125">值</span><span class="sxs-lookup"><span data-stu-id="99432-125">Value</span></span>|<span data-ttu-id="99432-126">描述</span><span class="sxs-lookup"><span data-stu-id="99432-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="99432-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="99432-127">*method_name*</span></span>|<span data-ttu-id="99432-128">欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="99432-128">The field name.</span></span> <span data-ttu-id="99432-129">欄位的類型是由父系 [\<Type>](type-element-net-native.md) 或 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 項目定義。</span><span class="sxs-lookup"><span data-stu-id="99432-129">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="99432-130">所有其他屬性</span><span class="sxs-lookup"><span data-stu-id="99432-130">All other attributes</span></span>  
  
|<span data-ttu-id="99432-131">值</span><span class="sxs-lookup"><span data-stu-id="99432-131">Value</span></span>|<span data-ttu-id="99432-132">描述</span><span class="sxs-lookup"><span data-stu-id="99432-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="99432-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="99432-133">*policy_setting*</span></span>|<span data-ttu-id="99432-134">要為欄位套用此原則類型的設定。</span><span class="sxs-lookup"><span data-stu-id="99432-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="99432-135">可能的值為 `Auto`、`Excluded`、`Included` 和 `Required`。</span><span class="sxs-lookup"><span data-stu-id="99432-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="99432-136">如需詳細資訊，請參閱[執行階段指示詞原則設定](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="99432-136">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99432-137">子項目</span><span class="sxs-lookup"><span data-stu-id="99432-137">Child Elements</span></span>  
 <span data-ttu-id="99432-138">無。</span><span class="sxs-lookup"><span data-stu-id="99432-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99432-139">父項目</span><span class="sxs-lookup"><span data-stu-id="99432-139">Parent Elements</span></span>  
  
|<span data-ttu-id="99432-140">項目</span><span class="sxs-lookup"><span data-stu-id="99432-140">Element</span></span>|<span data-ttu-id="99432-141">描述</span><span class="sxs-lookup"><span data-stu-id="99432-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99432-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="99432-142">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="99432-143">將反映原則套用至類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="99432-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="99432-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="99432-144">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="99432-145">將反映原則套用至建構泛型類型及其所有成員。</span><span class="sxs-lookup"><span data-stu-id="99432-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99432-146">備註</span><span class="sxs-lookup"><span data-stu-id="99432-146">Remarks</span></span>  
 <span data-ttu-id="99432-147">如果未明確定義欄位的原則，則會繼承其父元素的執行階段原則。</span><span class="sxs-lookup"><span data-stu-id="99432-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99432-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="99432-148">See also</span></span>

- [<span data-ttu-id="99432-149">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="99432-149">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="99432-150">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="99432-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="99432-151">執行階段指示詞原則設定</span><span class="sxs-lookup"><span data-stu-id="99432-151">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
