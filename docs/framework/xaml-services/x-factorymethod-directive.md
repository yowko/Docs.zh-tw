---
title: x:FactoryMethod 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053782"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="85462-102">x:FactoryMethod 指示詞</span><span class="sxs-lookup"><span data-stu-id="85462-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="85462-103">指定 XAML 處理器在解析其支援型別之後，要用來初始化物件的函式以外的方法。</span><span class="sxs-lookup"><span data-stu-id="85462-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="85462-104">XAML 屬性使用方式，無 x:Arguments</span><span class="sxs-lookup"><span data-stu-id="85462-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="85462-105">XAML 屬性使用方式，x:Arguments 為元素</span><span class="sxs-lookup"><span data-stu-id="85462-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="85462-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="85462-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="85462-107">XAML 處理器呼叫來初始化指定為`object`之實例的方法的字串方法名稱。</span><span class="sxs-lookup"><span data-stu-id="85462-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="85462-108">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="85462-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="85462-109">指定 factory 方法參數之物件的一或多個物件元素。</span><span class="sxs-lookup"><span data-stu-id="85462-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="85462-110">順序很重要;它表示引數傳遞至 factory 方法的順序。</span><span class="sxs-lookup"><span data-stu-id="85462-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85462-111">備註</span><span class="sxs-lookup"><span data-stu-id="85462-111">Remarks</span></span>  
 <span data-ttu-id="85462-112">如果`methodname`是實例方法，則不能是限定的。</span><span class="sxs-lookup"><span data-stu-id="85462-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="85462-113">可支援靜態方法做為 factory 方法。</span><span class="sxs-lookup"><span data-stu-id="85462-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="85462-114">如果`methodname`是靜態方法， `methodname`則會以*typeName*的形式提供。*方法*名稱組合，其中*typeName*會將定義靜態 factory 方法的類別命名為。</span><span class="sxs-lookup"><span data-stu-id="85462-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="85462-115">如果在對應的 xmlns 中參考型別，則*typeName*可以是前置詞限定的。</span><span class="sxs-lookup"><span data-stu-id="85462-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="85462-116">*typeName*可以是與`typeof(object)`不同的類型。</span><span class="sxs-lookup"><span data-stu-id="85462-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="85462-117">Factory 方法必須是可支援相關物件元素之類型的已宣告公用方法。</span><span class="sxs-lookup"><span data-stu-id="85462-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="85462-118">Factory 方法必須傳回可指派給相關物件的實例。</span><span class="sxs-lookup"><span data-stu-id="85462-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="85462-119">Factory 方法絕對不應傳回 null。</span><span class="sxs-lookup"><span data-stu-id="85462-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="85462-120">`x:Arguments`會針對 factory 方法的簽章，操作最符合的原則。</span><span class="sxs-lookup"><span data-stu-id="85462-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="85462-121">比對會先評估參數計數。</span><span class="sxs-lookup"><span data-stu-id="85462-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="85462-122">如果有一個以上的參數計數可能相符，則會評估參數類型，並決定最符合的值。</span><span class="sxs-lookup"><span data-stu-id="85462-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="85462-123">如果在這個評估階段之後仍有不明確的情況，XAML 處理器行為會是未定義的。</span><span class="sxs-lookup"><span data-stu-id="85462-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="85462-124">`x:FactoryMethod`由於指示詞標記不會參考包含物件專案的類型，因此專案使用方式不是一般意義中的屬性元素用法。</span><span class="sxs-lookup"><span data-stu-id="85462-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="85462-125">預期元素的使用方式不如屬性使用方式一般。</span><span class="sxs-lookup"><span data-stu-id="85462-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="85462-126">`x:Arguments`（屬性或專案使用方式）可與`x:FactoryMethod`專案使用方法一起使用，但不會特別顯示在 [使用方式] 區段中。</span><span class="sxs-lookup"><span data-stu-id="85462-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="85462-127">`x:FactoryMethod`當專案必須在任何其他屬性專案之前，必須在任何`x:Arguments`也提供作為元素的前面，而且必須在任何內容/內部文字/初始化文字之前。</span><span class="sxs-lookup"><span data-stu-id="85462-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85462-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85462-128">See also</span></span>

- [<span data-ttu-id="85462-129">x:Arguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="85462-129">x:Arguments Directive</span></span>](x-arguments-directive.md)
