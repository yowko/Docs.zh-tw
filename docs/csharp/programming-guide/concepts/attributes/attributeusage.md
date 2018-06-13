---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 869e6509e55268767915a783a8652f7f950d7137
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "33955924"
---
# <a name="attributeusage-c"></a><span data-ttu-id="156ea-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="156ea-102">AttributeUsage (C#)</span></span>

<span data-ttu-id="156ea-103">決定如何使用自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="156ea-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="156ea-104"><xref:System.AttributeUsageAttribute> 是您套用至自訂屬性定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="156ea-104"><xref:System.AttributeUsageAttribute> is an attribute you apply to custom attribute definitions.</span></span> <span data-ttu-id="156ea-105">`AttributeUsage` 屬性可讓您控制：</span><span class="sxs-lookup"><span data-stu-id="156ea-105">The `AttributeUsage` attribute enables you to control:</span></span>

- <span data-ttu-id="156ea-106">屬性可能套用至哪些程式元素。</span><span class="sxs-lookup"><span data-stu-id="156ea-106">Which program elements attribute may be applied to.</span></span> <span data-ttu-id="156ea-107">除非您限制使用方式，否則屬性可能會套用至下列任一程式元素：</span><span class="sxs-lookup"><span data-stu-id="156ea-107">Unless you restrict is usage, an attribute may be applied to any of the following program elements:</span></span>
  - <span data-ttu-id="156ea-108">組件</span><span class="sxs-lookup"><span data-stu-id="156ea-108">assembly</span></span>
  - <span data-ttu-id="156ea-109">name</span><span class="sxs-lookup"><span data-stu-id="156ea-109">module</span></span>
  - <span data-ttu-id="156ea-110">Field - 欄位</span><span class="sxs-lookup"><span data-stu-id="156ea-110">field</span></span>
  - <span data-ttu-id="156ea-111">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="156ea-111">event</span></span>
  - <span data-ttu-id="156ea-112">方法</span><span class="sxs-lookup"><span data-stu-id="156ea-112">method</span></span>
  - <span data-ttu-id="156ea-113">param</span><span class="sxs-lookup"><span data-stu-id="156ea-113">param</span></span>
  - <span data-ttu-id="156ea-114">屬性</span><span class="sxs-lookup"><span data-stu-id="156ea-114">property</span></span>
  - <span data-ttu-id="156ea-115">return</span><span class="sxs-lookup"><span data-stu-id="156ea-115">return</span></span>
  - <span data-ttu-id="156ea-116">類型</span><span class="sxs-lookup"><span data-stu-id="156ea-116">type</span></span>
- <span data-ttu-id="156ea-117">屬性是否可以套用至單一程式元素多次。</span><span class="sxs-lookup"><span data-stu-id="156ea-117">Whether an attribute can be applied to a single program element multiple times.</span></span>
- <span data-ttu-id="156ea-118">衍生類別是否會繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="156ea-118">Whether attributes are inherited by derived classes.</span></span>

<span data-ttu-id="156ea-119">明確套用時，預設設定看起來像下列範例：</span><span class="sxs-lookup"><span data-stu-id="156ea-119">The default settings look like the following example when applied explicitly:</span></span>

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

<span data-ttu-id="156ea-120">在此範例中，`NewAttribute`　類別可套用至任何支援的程式元素。</span><span class="sxs-lookup"><span data-stu-id="156ea-120">In this example, the `NewAttribute` class can be applied to any supported program element.</span></span> <span data-ttu-id="156ea-121">但是，它只能套用至每個實體一次。</span><span class="sxs-lookup"><span data-stu-id="156ea-121">But it can be applied only once to each entity.</span></span> <span data-ttu-id="156ea-122">屬性在套用至基底類別時，會由衍生類別所繼承。</span><span class="sxs-lookup"><span data-stu-id="156ea-122">The attribute is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="156ea-123"><xref:System.AttributeUsageAttribute.AllowMultiple> 和 <xref:System.AttributeUsageAttribute.Inherited> 是選擇性引數，因此下列程式碼具有相同的效果：</span><span class="sxs-lookup"><span data-stu-id="156ea-123">The <xref:System.AttributeUsageAttribute.AllowMultiple> and <xref:System.AttributeUsageAttribute.Inherited> arguments are optional, so the following code has the same effect:</span></span>

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

<span data-ttu-id="156ea-124">第一個 <xref:System.AttributeUsageAttribute> 引數必須是 <xref:System.AttributeTargets> 列舉的一或多個元素。</span><span class="sxs-lookup"><span data-stu-id="156ea-124">The first <xref:System.AttributeUsageAttribute> argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="156ea-125">您可以使用 OR 運算子來連結多個目標類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="156ea-125">Multiple target types can be linked together with the OR operator, like the following example shows:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

<span data-ttu-id="156ea-126">從 C# 7.3 開始，屬性 (attribute) 可以套用至屬性 (property) 或自動實作屬性 (property) 的支援欄位。</span><span class="sxs-lookup"><span data-stu-id="156ea-126">Beginning in C# 7.3, attributes can be applied to either the property or the backing field for an auto-implemented property.</span></span> <span data-ttu-id="156ea-127">除非您在屬性 (attribute) 上指定 `field` 指定名稱，否則屬性 (attribute) 會套用至屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="156ea-127">The attribute applies to the property, unless you specify the `field` specifier on the attribute.</span></span> <span data-ttu-id="156ea-128">下列範例會顯示這兩者：</span><span class="sxs-lookup"><span data-stu-id="156ea-128">Both are shown in the following example:</span></span>

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<span data-ttu-id="156ea-129">如果 <xref:System.AttributeUsageAttribute.AllowMultiple> 引數為 `true`，則可以將產生的屬性多次套用至單一實體，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="156ea-129">If the <xref:System.AttributeUsageAttribute.AllowMultiple> argument is `true`, then the resulting attribute can be applied more than once to a single entity, as shown in the following example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

<span data-ttu-id="156ea-130">在此情況下，因為 `AllowMultiple` 設為 `true`，所以可以重複套用 `MultiUseAttribute`。</span><span class="sxs-lookup"><span data-stu-id="156ea-130">In this case, `MultiUseAttribute` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="156ea-131">套用多個屬性所顯示的兩種格式都有效。</span><span class="sxs-lookup"><span data-stu-id="156ea-131">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="156ea-132">如果 <xref:System.AttributeUsageAttribute.Inherited> 為 `false`，則衍生自屬性化類別的類別不會繼承此屬性。</span><span class="sxs-lookup"><span data-stu-id="156ea-132">If <xref:System.AttributeUsageAttribute.Inherited> is `false`, then the attribute isn't inherited by classes derived from an attributed class.</span></span> <span data-ttu-id="156ea-133">例如: </span><span class="sxs-lookup"><span data-stu-id="156ea-133">For example:</span></span>

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

<span data-ttu-id="156ea-134">在此情況下，不會透過繼承將 `NonInheritedAttribute` 套用至 `DClass`。</span><span class="sxs-lookup"><span data-stu-id="156ea-134">In this case `NonInheritedAttribute` isn't applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="156ea-135">備註</span><span class="sxs-lookup"><span data-stu-id="156ea-135">Remarks</span></span>

<span data-ttu-id="156ea-136">`AttributeUsage` 屬性是單次使用的屬性--它無法多次套用至相同的類別。</span><span class="sxs-lookup"><span data-stu-id="156ea-136">The `AttributeUsage` attribute is a single-use attribute--it can't be applied more than once to the same class.</span></span> <span data-ttu-id="156ea-137">`AttributeUsage` 是 <xref:System.AttributeUsageAttribute> 的別名。</span><span class="sxs-lookup"><span data-stu-id="156ea-137">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="156ea-138">如需詳細資訊，請參閱[使用反映存取屬性 (C#)](accessing-attributes-by-using-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="156ea-138">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="156ea-139">範例</span><span class="sxs-lookup"><span data-stu-id="156ea-139">Example</span></span>

<span data-ttu-id="156ea-140">下列範例示範 <xref:System.AttributeUsageAttribute> 屬性的 <xref:System.AttributeUsageAttribute.Inherited> 和 <xref:System.AttributeUsageAttribute.AllowMultiple> 引數的效果，以及如何列舉套用至類別的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="156ea-140">The following example demonstrates the effect of the <xref:System.AttributeUsageAttribute.Inherited> and <xref:System.AttributeUsageAttribute.AllowMultiple> arguments to the <xref:System.AttributeUsageAttribute> attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a><span data-ttu-id="156ea-141">範例輸出</span><span class="sxs-lookup"><span data-stu-id="156ea-141">Sample Output</span></span>

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a><span data-ttu-id="156ea-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="156ea-142">See Also</span></span>
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="156ea-143">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="156ea-143">C# Programming Guide</span></span>](../..//index.md)  
 [<span data-ttu-id="156ea-144">屬性</span><span class="sxs-lookup"><span data-stu-id="156ea-144">Attributes</span></span>](../../../..//standard/attributes/index.md)  
 [<span data-ttu-id="156ea-145">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="156ea-145">Reflection (C#)</span></span>](../reflection.md)  
 [<span data-ttu-id="156ea-146">屬性</span><span class="sxs-lookup"><span data-stu-id="156ea-146">Attributes</span></span>](index.md)  
 [<span data-ttu-id="156ea-147">建立自訂屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="156ea-147">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
 [<span data-ttu-id="156ea-148">使用反射存取屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="156ea-148">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
