---
title: x:FactoryMethod 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071532"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="34fe6-102">x:FactoryMethod 指示詞</span><span class="sxs-lookup"><span data-stu-id="34fe6-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="34fe6-103">指定 XAML 處理器應在解析物件支援類型後使用來初始化物件的構造函數以外的方法。</span><span class="sxs-lookup"><span data-stu-id="34fe6-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="34fe6-104">XAML 屬性用法,無 x:參數</span><span class="sxs-lookup"><span data-stu-id="34fe6-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="34fe6-105">XAML 屬性用法,x:參數作為元素</span><span class="sxs-lookup"><span data-stu-id="34fe6-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="34fe6-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="34fe6-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="34fe6-107">XAML 處理器呼叫的方法的字串方法名稱,用於初始化指定為`object`的實例。</span><span class="sxs-lookup"><span data-stu-id="34fe6-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="34fe6-108">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="34fe6-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="34fe6-109">指定工廠方法參數的物件的一個或多個物件元素。</span><span class="sxs-lookup"><span data-stu-id="34fe6-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="34fe6-110">訂單很重要;它表示參數應傳遞給工廠方法的順序。</span><span class="sxs-lookup"><span data-stu-id="34fe6-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34fe6-111">備註</span><span class="sxs-lookup"><span data-stu-id="34fe6-111">Remarks</span></span>  
 <span data-ttu-id="34fe6-112">如果是`methodname`實例方法,則無法限定它。</span><span class="sxs-lookup"><span data-stu-id="34fe6-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="34fe6-113">支持作為工廠方法的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="34fe6-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="34fe6-114">如果是`methodname`靜態方法`methodname`,`typeName.methodName`則作為 組合`typeName`提供,其中 命名定義靜態工廠方法的類。</span><span class="sxs-lookup"><span data-stu-id="34fe6-114">If `methodname` is a static method, `methodname` is provided as a `typeName.methodName` combination, where `typeName` names the class that defines the static factory method.</span></span> <span data-ttu-id="34fe6-115">`typeName`如果引用映射的 xmlns 中的類型,則可以在前綴限定。</span><span class="sxs-lookup"><span data-stu-id="34fe6-115">`typeName` can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="34fe6-116">`typeName`可以是與`typeof(object)`不同的類型。</span><span class="sxs-lookup"><span data-stu-id="34fe6-116">`typeName` can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="34fe6-117">工廠方法必須是支持相關物件元素的類型聲明的公共方法。</span><span class="sxs-lookup"><span data-stu-id="34fe6-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="34fe6-118">工廠方法必須返回可分配給相關對象的實例。</span><span class="sxs-lookup"><span data-stu-id="34fe6-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="34fe6-119">工廠方法絕不應返回 null。</span><span class="sxs-lookup"><span data-stu-id="34fe6-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="34fe6-120">`x:Arguments`操作的原則是最佳匹配工廠方法的簽名。</span><span class="sxs-lookup"><span data-stu-id="34fe6-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="34fe6-121">匹配首先計算參數計數。</span><span class="sxs-lookup"><span data-stu-id="34fe6-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="34fe6-122">如果參數計數有多個可能的匹配項,則計算參數類型並確定最佳匹配。</span><span class="sxs-lookup"><span data-stu-id="34fe6-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="34fe6-123">如果在此評估階段之後仍有歧義,則未定義 XAML 處理器行為。</span><span class="sxs-lookup"><span data-stu-id="34fe6-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="34fe6-124">元素`x:FactoryMethod`用法在典型意義上不是屬性元素用法,因為指令標記不引用包含物件元素的類型。</span><span class="sxs-lookup"><span data-stu-id="34fe6-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="34fe6-125">預計元素使用比屬性用法少。</span><span class="sxs-lookup"><span data-stu-id="34fe6-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="34fe6-126">`x:Arguments`(屬性或元素用法)可以隨元素使用一`x:FactoryMethod`起使用,但"使用"部分沒有具體顯示。</span><span class="sxs-lookup"><span data-stu-id="34fe6-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="34fe6-127">`x:FactoryMethod`作為元素必須位於任何其他屬性元素之前,必須位於任何`x:Arguments`也作為元素提供的元素之前,並且必須位於任何內容/內部文本/初始化文本之前。</span><span class="sxs-lookup"><span data-stu-id="34fe6-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34fe6-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34fe6-128">See also</span></span>

- [<span data-ttu-id="34fe6-129">x:Arguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="34fe6-129">x:Arguments Directive</span></span>](xarguments-directive.md)
