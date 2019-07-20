---
title: x:Arguments 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5bcd629e306169c1f7a61a316d76203827a2d0fe
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364276"
---
# <a name="xarguments-directive"></a><span data-ttu-id="24563-102">x:Arguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="24563-102">x:Arguments Directive</span></span>
<span data-ttu-id="24563-103">封裝 XAML 或 factory 方法物件宣告中非無參數之函式物件專案宣告的結構引數。</span><span class="sxs-lookup"><span data-stu-id="24563-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="24563-104">XAML 元素使用方式 (Nonparameterless 的函式)</span><span class="sxs-lookup"><span data-stu-id="24563-104">XAML Element Usage (Nonparameterless constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="24563-105">XAML 元素使用方式 (factory 方法)</span><span class="sxs-lookup"><span data-stu-id="24563-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="24563-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="24563-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="24563-107">一或多個物件專案, 指定要傳遞給支援非參數的函式或 factory 方法的引數。</span><span class="sxs-lookup"><span data-stu-id="24563-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="24563-108">一般用法是在物件元素內使用初始化文字, 以指定實際的引數值。</span><span class="sxs-lookup"><span data-stu-id="24563-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="24563-109">請參閱範例一節。</span><span class="sxs-lookup"><span data-stu-id="24563-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="24563-110">元素的順序很重要。</span><span class="sxs-lookup"><span data-stu-id="24563-110">The order of the elements is significant.</span></span> <span data-ttu-id="24563-111">順序中的 XAML 類型必須符合支援的函式或 factory 方法多載的類型和類型順序。</span><span class="sxs-lookup"><span data-stu-id="24563-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="24563-112">應該處理任何`x:Arguments`引數的 factory 方法名稱。</span><span class="sxs-lookup"><span data-stu-id="24563-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="24563-113">相依性</span><span class="sxs-lookup"><span data-stu-id="24563-113">Dependencies</span></span>  
 <span data-ttu-id="24563-114">`x:FactoryMethod`可以修改`x:Arguments`套用的範圍和行為。</span><span class="sxs-lookup"><span data-stu-id="24563-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="24563-115">如果未`x:FactoryMethod`指定, `x:Arguments`則會套用至支援之函式的替代 (非預設) 簽章。</span><span class="sxs-lookup"><span data-stu-id="24563-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="24563-116">如果`x:FactoryMethod`指定, `x:Arguments`則會套用至已命名方法的多載。</span><span class="sxs-lookup"><span data-stu-id="24563-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24563-117">備註</span><span class="sxs-lookup"><span data-stu-id="24563-117">Remarks</span></span>  
 <span data-ttu-id="24563-118">XAML 2006 可以透過初始化文字支援非預設初始化。</span><span class="sxs-lookup"><span data-stu-id="24563-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="24563-119">不過, 初始化文字結構化技術的實際應用會受到限制。</span><span class="sxs-lookup"><span data-stu-id="24563-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="24563-120">初始化文字會被視為單一文字字串;因此, 它只會加入單一參數初始化的功能, 除非已針對可從字串剖析自訂資訊專案和自訂分隔符號的結構行為定義類型轉換器。</span><span class="sxs-lookup"><span data-stu-id="24563-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="24563-121">此外, 文字字串至物件邏輯可能是指定的 XAML 剖析器的原生預設類型轉換器, 用於處理 true 字串以外的基本專案。</span><span class="sxs-lookup"><span data-stu-id="24563-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="24563-122">`x:Arguments` XAML 用法不是一般意義的屬性專案使用方式, 因為指示詞標記不會參考包含物件專案的類型。</span><span class="sxs-lookup"><span data-stu-id="24563-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="24563-123">它更類似于其他指示詞, 例如`x:Code` , 專案 demarks 的範圍, 其中的標記應解讀為子系內容的預設值。</span><span class="sxs-lookup"><span data-stu-id="24563-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="24563-124">在此情況下, 每個物件專案的 XAML 類型都會傳達引數類型的相關資訊, 而 xaml 剖析器會使用這些參數來判斷`x:Arguments`使用方式嘗試參考的特定「處理站」 factory 方法簽章。</span><span class="sxs-lookup"><span data-stu-id="24563-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="24563-125">`x:Arguments`針對所要建立的物件專案, 必須在物件元素的任何其他屬性專案、內容、內部文字或初始化字串之前。</span><span class="sxs-lookup"><span data-stu-id="24563-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="24563-126">內`x:Arguments`的物件元素可以包含屬性和初始化字串, 如該 XAML 類型和其支援的函數或 factory 方法所允許。</span><span class="sxs-lookup"><span data-stu-id="24563-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="24563-127">針對物件或引數, 您可以藉由參考已建立的前置詞對應, 指定預設 XAML 命名空間以外的自訂 XAML 類型或 XAML 類型。</span><span class="sxs-lookup"><span data-stu-id="24563-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="24563-128">XAML 處理器會使用下列指導方針來決定應該如何使用中`x:Arguments`指定的引數來建立物件。</span><span class="sxs-lookup"><span data-stu-id="24563-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="24563-129">如果`x:FactoryMethod`指定了, 就會將資訊與指定`x:FactoryMethod`的 ( `x:FactoryMethod`請注意, 的值是方法名稱, 而命名的方法可以有多載。</span><span class="sxs-lookup"><span data-stu-id="24563-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="24563-130">如果`x:FactoryMethod`未指定, 則會將資訊與物件之所有公用函式多載的集合進行比較。</span><span class="sxs-lookup"><span data-stu-id="24563-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="24563-131">然後, XAML 處理邏輯會比較參數數目, 並選取具有相符 arity 的多載。</span><span class="sxs-lookup"><span data-stu-id="24563-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="24563-132">如果有多個相符專案, XAML 處理器應該根據所提供之物件元素的 XAML 類型來比較參數的類型。</span><span class="sxs-lookup"><span data-stu-id="24563-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="24563-133">如果仍然有一個以上的相符項, XAML 處理器行為會是未定義的。</span><span class="sxs-lookup"><span data-stu-id="24563-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="24563-134">`x:FactoryMethod`如果指定了, 但無法解析方法, XAML 處理器應該會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24563-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="24563-135">在技術上, `<x:Arguments>string</x:Arguments>` XAML 屬性使用方式是可行的。</span><span class="sxs-lookup"><span data-stu-id="24563-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="24563-136">不過, 這不會提供除了透過初始化文字和類型轉換器以外的其他功能, 而且使用此語法並不是 XAML 2009 factory 方法功能的設計意圖。</span><span class="sxs-lookup"><span data-stu-id="24563-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="24563-137">範例</span><span class="sxs-lookup"><span data-stu-id="24563-137">Examples</span></span>  
 <span data-ttu-id="24563-138">下列範例`x:Arguments`會顯示非參數的函式簽章, 然後是存取該簽章的 XAML 使用方式。</span><span class="sxs-lookup"><span data-stu-id="24563-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="24563-139">下列範例示範目標 factory 方法簽章, 然後是`x:Arguments`會存取該簽章的 XAML 使用方式。</span><span class="sxs-lookup"><span data-stu-id="24563-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24563-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24563-140">See also</span></span>

- [<span data-ttu-id="24563-141">定義可搭配 .NET Framework XAML 服務使用的自訂類型</span><span class="sxs-lookup"><span data-stu-id="24563-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="24563-142">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="24563-142">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
