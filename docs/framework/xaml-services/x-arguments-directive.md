---
title: x:Arguments 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: e0e7f380ec176e80d2422878a2e676d64985d660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564870"
---
# <a name="xarguments-directive"></a><span data-ttu-id="aeaab-102">x:Arguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="aeaab-102">x:Arguments Directive</span></span>
<span data-ttu-id="aeaab-103">在 XAML 中、 非預設建構函式物件項目宣告或 factory 方法物件宣告，封裝建構引數。</span><span class="sxs-lookup"><span data-stu-id="aeaab-103">Packages construction arguments for a non-default constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nondefault-constructor"></a><span data-ttu-id="aeaab-104">（非預設建構函式） 的 XAML 項目用法</span><span class="sxs-lookup"><span data-stu-id="aeaab-104">XAML Element Usage (Nondefault constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="aeaab-105">XAML 項目使用方式 （處理站方法）</span><span class="sxs-lookup"><span data-stu-id="aeaab-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="aeaab-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="aeaab-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="aeaab-107">一或多個物件項目指定要傳遞至支援非預設建構函式或 factory 方法的引數。</span><span class="sxs-lookup"><span data-stu-id="aeaab-107">One or more object elements that specify arguments to be passed to the backing non-default constructor or factory method.</span></span><br /><br /> <span data-ttu-id="aeaab-108">一般用法是，使用指定的實際引數的值的物件項目內的初始文字。</span><span class="sxs-lookup"><span data-stu-id="aeaab-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="aeaab-109">請參閱範例 > 一節。</span><span class="sxs-lookup"><span data-stu-id="aeaab-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="aeaab-110">項目的順序很重要。</span><span class="sxs-lookup"><span data-stu-id="aeaab-110">The order of the elements is significant.</span></span> <span data-ttu-id="aeaab-111">在順序中的 XAML 型別必須符合類型，然後輸入備份建構函式或 factory 方法多載的順序。</span><span class="sxs-lookup"><span data-stu-id="aeaab-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="aeaab-112">應該處理任何的 factory 方法的名稱`x:Arguments`引數。</span><span class="sxs-lookup"><span data-stu-id="aeaab-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="aeaab-113">相依性</span><span class="sxs-lookup"><span data-stu-id="aeaab-113">Dependencies</span></span>  
 <span data-ttu-id="aeaab-114">`x:FactoryMethod` 範圍和行為可以修改其中`x:Arguments`套用。</span><span class="sxs-lookup"><span data-stu-id="aeaab-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="aeaab-115">如果沒有`x:FactoryMethod`指定，則`x:Arguments`適用於支援建構函式的替代 （非預設值） 簽章。</span><span class="sxs-lookup"><span data-stu-id="aeaab-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="aeaab-116">如果`x:FactoryMethod`指定，則`x:Arguments`適用於具名方法的多載。</span><span class="sxs-lookup"><span data-stu-id="aeaab-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeaab-117">備註</span><span class="sxs-lookup"><span data-stu-id="aeaab-117">Remarks</span></span>  
 <span data-ttu-id="aeaab-118">XAML 2006 可支援透過初始文字的非預設值初始化。</span><span class="sxs-lookup"><span data-stu-id="aeaab-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="aeaab-119">不過，實際的應用程式的初始化文字建構項技術是限制。</span><span class="sxs-lookup"><span data-stu-id="aeaab-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="aeaab-120">初始文字會被視為單一文字字串;因此，它只會將單一參數初始設定的功能，除非建構行為可以剖析自訂的資訊項目以及從字串的自訂分隔符號定義型別轉換子。</span><span class="sxs-lookup"><span data-stu-id="aeaab-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="aeaab-121">此外，邏輯物件的文字字串可能會處理原始物件，則為 true 的字串以外的給定的 XAML 剖析器的原生的預設型別轉換子。</span><span class="sxs-lookup"><span data-stu-id="aeaab-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="aeaab-122">`x:Arguments` XAML 用法不是屬性項目用法中的一般意義，因為指示詞標記未參考包含物件項目類型。</span><span class="sxs-lookup"><span data-stu-id="aeaab-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="aeaab-123">例如，它是比較類似於其他指示詞`x:Code`其中的項目 demarks 所在標記應該解譯為以外子內容的預設值的範圍。</span><span class="sxs-lookup"><span data-stu-id="aeaab-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="aeaab-124">在此情況下，XAML 類型的每個物件項目傳達資訊引數類型的 XAML 剖析器用來判斷哪一個特定的建構函式的 factory 方法簽章`x:Arguments`使用量嘗試參考。</span><span class="sxs-lookup"><span data-stu-id="aeaab-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="aeaab-125">`x:Arguments` 物件項目所建構應優先於其他任何屬性項目、 內容、 內部文字或初始化字串的物件項目。</span><span class="sxs-lookup"><span data-stu-id="aeaab-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="aeaab-126">中的物件項目`x:Arguments`可以包括屬性和初始化字串所允許的該 XAML 類型和其支援的建構函式或 factory 方法。</span><span class="sxs-lookup"><span data-stu-id="aeaab-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="aeaab-127">物件或引數，您可以指定自訂的 XAML 型別或 XAML 類型，否則預設 XAML 命名空間外部參考已建立的前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="aeaab-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="aeaab-128">XAML 處理器會使用下列指導方針來判斷如何在中指定的引數`x:Arguments`應該用來建構物件。</span><span class="sxs-lookup"><span data-stu-id="aeaab-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="aeaab-129">如果`x:FactoryMethod`指定，則資訊進行比較的指定`x:FactoryMethod`(請注意，值`x:FactoryMethod`是方法名稱，而具名的方法的多載。</span><span class="sxs-lookup"><span data-stu-id="aeaab-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="aeaab-130">如果`x:FactoryMethod`未指定，資訊進行比較的物件的所有公用建構函式多載的集合。</span><span class="sxs-lookup"><span data-stu-id="aeaab-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="aeaab-131">然後，XAML 處理邏輯會比較的參數數目，並選取具有相符引數數目的多載。</span><span class="sxs-lookup"><span data-stu-id="aeaab-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="aeaab-132">如果有多個相符項目，XAML 處理器應該比較根據提供的物件項目的 XAML 型別參數的類型。</span><span class="sxs-lookup"><span data-stu-id="aeaab-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="aeaab-133">如果沒有仍然超過一個符合項目，XAML 處理器的行為未定義。</span><span class="sxs-lookup"><span data-stu-id="aeaab-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="aeaab-134">如果`x:FactoryMethod`指定，但此方法無法解決，XAML 處理器應該擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="aeaab-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="aeaab-135">XAML 屬性使用方式`<x:Arguments>string</x:Arguments>`是可行的。</span><span class="sxs-lookup"><span data-stu-id="aeaab-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="aeaab-136">不過，這會提供任何功能什麼無法透過否則初始化文字和類型轉換器，並使用此語法不是 XAML 2009 的 factory 方法功能的設計目的。</span><span class="sxs-lookup"><span data-stu-id="aeaab-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="aeaab-137">範例</span><span class="sxs-lookup"><span data-stu-id="aeaab-137">Examples</span></span>  
 <span data-ttu-id="aeaab-138">下列範例顯示的非預設建構函式簽章，則的 XAML 用法`x:Arguments`，用來存取該簽章。</span><span class="sxs-lookup"><span data-stu-id="aeaab-138">The following example shows a non-default constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="aeaab-139">下列範例顯示目標的 factory 方法簽章然後的 XAML 用法`x:Arguments`，用來存取該簽章。</span><span class="sxs-lookup"><span data-stu-id="aeaab-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aeaab-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aeaab-140">See Also</span></span>  
 [<span data-ttu-id="aeaab-141">定義可搭配 .NET Framework XAML 服務使用的自訂類型</span><span class="sxs-lookup"><span data-stu-id="aeaab-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [<span data-ttu-id="aeaab-142">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="aeaab-142">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
