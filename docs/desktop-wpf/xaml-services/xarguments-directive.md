---
title: x:Arguments 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071588"
---
# <a name="xarguments-directive"></a><span data-ttu-id="3c092-102">x:Arguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="3c092-102">x:Arguments Directive</span></span>

<span data-ttu-id="3c092-103">在 XAML 或工廠方法物件聲明中為非無參數構造函數物件元素聲明打包構造參數。</span><span class="sxs-lookup"><span data-stu-id="3c092-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>

## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="3c092-104">XAML 元素使用(無參數建構函數)</span><span class="sxs-lookup"><span data-stu-id="3c092-104">XAML Element Usage (Nonparameterless constructor)</span></span>

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="3c092-105">XAML 元素用法(工廠方法)</span><span class="sxs-lookup"><span data-stu-id="3c092-105">XAML Element Usage (factory method)</span></span>

```xaml
<object x:FactoryMethod="methodName"...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="3c092-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="3c092-106">XAML Values</span></span>

|||
|-|-|
|`oneOrMoreObjectElements`|<span data-ttu-id="3c092-107">指定要傳遞給支援的非無參數建構函數或工廠方法的參數的一個或多個物件元素。</span><span class="sxs-lookup"><span data-stu-id="3c092-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="3c092-108">典型用法是使用物件元素中的初始化文本來指定實際參數值。</span><span class="sxs-lookup"><span data-stu-id="3c092-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="3c092-109">請參閱示例部分。</span><span class="sxs-lookup"><span data-stu-id="3c092-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="3c092-110">元素的順序很重要。</span><span class="sxs-lookup"><span data-stu-id="3c092-110">The order of the elements is significant.</span></span> <span data-ttu-id="3c092-111">XAML 類型順序必須與後備構造函數或工廠方法重載的類型和類型順序匹配。</span><span class="sxs-lookup"><span data-stu-id="3c092-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|
|`methodName`|<span data-ttu-id="3c092-112">應處理任何`x:Arguments`參數的工廠方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c092-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="3c092-113">相依性</span><span class="sxs-lookup"><span data-stu-id="3c092-113">Dependencies</span></span>

<span data-ttu-id="3c092-114">`x:FactoryMethod`可以修改`x:Arguments`適用的範圍和行為。</span><span class="sxs-lookup"><span data-stu-id="3c092-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>

<span data-ttu-id="3c092-115">如果未`x:FactoryMethod`指定`x:Arguments`, 則應用於支援建構函數的備用(非預設)簽名。</span><span class="sxs-lookup"><span data-stu-id="3c092-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>

<span data-ttu-id="3c092-116">如果`x:FactoryMethod`指定,`x:Arguments`則應用於命名方法的重載。</span><span class="sxs-lookup"><span data-stu-id="3c092-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c092-117">備註</span><span class="sxs-lookup"><span data-stu-id="3c092-117">Remarks</span></span>

<span data-ttu-id="3c092-118">XAML 2006 可通過初始化文本支援非預設初始化。</span><span class="sxs-lookup"><span data-stu-id="3c092-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="3c092-119">然而,初始化文本構造技術的實際應用有限。</span><span class="sxs-lookup"><span data-stu-id="3c092-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="3c092-120">初始化文字被視為單個文字字串;因此,它僅添加單個參數初始化的功能,除非為構造行為定義類型轉換器,該構造行為可以從字串解析自定義資訊項和自定義分隔符。</span><span class="sxs-lookup"><span data-stu-id="3c092-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="3c092-121">此外,到物件邏輯的文本字串可能是給定的 XAML 解析器的本機預設類型轉換器,用於處理真字串以外的基元。</span><span class="sxs-lookup"><span data-stu-id="3c092-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>

<span data-ttu-id="3c092-122">`x:Arguments` XAML 用法在典型意義上不是屬性元素用法,因為指令標記不引用包含物件元素的類型。</span><span class="sxs-lookup"><span data-stu-id="3c092-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="3c092-123">它更類似於其他指令,例如`x:Code`元素將標記的範圍解釋為子內容的預設值以外的範圍。</span><span class="sxs-lookup"><span data-stu-id="3c092-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="3c092-124">在這種情況下,每個物件元素的 XAML 類型傳達有關參數類型的資訊,XAML 解析器`x:Arguments`使用該類型來確定 使用方法嘗試引用的特定構造函數工廠方法簽名。</span><span class="sxs-lookup"><span data-stu-id="3c092-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>

<span data-ttu-id="3c092-125">`x:Arguments`對於正在建構的物件元素,必須位於物件元素的任何其他屬性元素、內容、內部文本或初始化字串之前。</span><span class="sxs-lookup"><span data-stu-id="3c092-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="3c092-126">中`x:Arguments`的物件元素可以包括屬性和初始化字串,這是 XAML 類型及其支援構造函數或工廠方法所允許的。</span><span class="sxs-lookup"><span data-stu-id="3c092-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="3c092-127">對於物件或參數,可以通過引用已建立的首碼映射來指定自定義 XAML 類型或 XAML 類型,這些類型在預設 XAML 命名空間之外。</span><span class="sxs-lookup"><span data-stu-id="3c092-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>

<span data-ttu-id="3c092-128">XAML 處理器使用以下準則來確定如何在`x:Arguments`中 指定的參數用於構造物件。</span><span class="sxs-lookup"><span data-stu-id="3c092-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="3c092-129">如果`x:FactoryMethod`指定,則將資訊與指定`x:FactoryMethod`的 (請注意`x:FactoryMethod`,值 是方法名稱,並且命名方法可以具有重載。</span><span class="sxs-lookup"><span data-stu-id="3c092-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="3c092-130">如果未`x:FactoryMethod`指定,則將資訊與物件的所有公共構造函數重載集進行比較。</span><span class="sxs-lookup"><span data-stu-id="3c092-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="3c092-131">然後,XAML 處理邏輯比較參數數,並選擇具有匹配的參數的重載。</span><span class="sxs-lookup"><span data-stu-id="3c092-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="3c092-132">如果有多個匹配項,XAML 處理器應根據提供的物件元素的 XAML 類型比較參數類型。</span><span class="sxs-lookup"><span data-stu-id="3c092-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="3c092-133">如果仍然有多個匹配項,則未定義 XAML 處理器行為。</span><span class="sxs-lookup"><span data-stu-id="3c092-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="3c092-134">如果指定`x:FactoryMethod`了 ,但方法無法解決,XAML 處理器應引發異常。</span><span class="sxs-lookup"><span data-stu-id="3c092-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>

<span data-ttu-id="3c092-135">從技術上講,XAML`<x:Arguments>string</x:Arguments>`屬性使用是可能的。</span><span class="sxs-lookup"><span data-stu-id="3c092-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="3c092-136">但是,除了通過初始化文本和類型轉換器可以執行哪些功能之外,這沒有任何功能,使用此語法不是 XAML 2009 工廠方法功能的設計意圖。</span><span class="sxs-lookup"><span data-stu-id="3c092-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>

## <a name="examples"></a><span data-ttu-id="3c092-137">範例</span><span class="sxs-lookup"><span data-stu-id="3c092-137">Examples</span></span>

<span data-ttu-id="3c092-138">下面的範例顯示一個非無參數構造函數簽名,然後是該簽名的`x:Arguments`XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="3c092-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

```csharp
public class Food {
  private string _name;
  private Int32 _calories;
  public Food(string name, Int32 calories) {
      _name=name;
      _calories=calories;
  }
}
```

```xaml
<my:Food>
  <x:Arguments>
      <x:String>Apple</x:String>
      <x:Int32>150</x:Int32>
  </x:Arguments>
</my:Food>
```

<span data-ttu-id="3c092-139">下面的範例顯示目標工廠方法簽名,然後顯示該簽名的`x:Arguments`XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="3c092-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

```csharp
public Food TryLookupFood(string name)
{
switch (name) {
  case "Apple": return new Food("Apple",150);
  case "Chocolate": return new Food("Chocolate",200);
  case "Cheese": return new Food("Cheese", 450);
  default: {return new Food(name,0);
}
}
```

```xaml
<my:Food x:FactoryMethod="TryLookupFood">
  <x:Arguments>
      <x:String>Apple</x:String>
  </x:Arguments>
</my:Food>
```

## <a name="see-also"></a><span data-ttu-id="3c092-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c092-140">See also</span></span>

- [<span data-ttu-id="3c092-141">定義可搭配 .NET XAML 服務使用的自訂類型</span><span class="sxs-lookup"><span data-stu-id="3c092-141">Defining Custom Types for Use with .NET XAML Services</span></span>](define-custom-types.md)
- [<span data-ttu-id="3c092-142">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="3c092-142">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
