---
title: "x:FactoryMethod 指示詞"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58349c5440d0062c64346933e48b64de6c4c7b60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="c92f9-102">x:FactoryMethod 指示詞</span><span class="sxs-lookup"><span data-stu-id="c92f9-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="c92f9-103">指定 XAML 處理器必須用來解決它支援的型別之後初始化物件的建構函式以外的方法。</span><span class="sxs-lookup"><span data-stu-id="c92f9-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="c92f9-104">XAML 屬性使用方式，不使用 x： 引數</span><span class="sxs-lookup"><span data-stu-id="c92f9-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="c92f9-105">XAML 屬性使用方式，為元素的 x： 引數</span><span class="sxs-lookup"><span data-stu-id="c92f9-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c92f9-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="c92f9-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="c92f9-107">XAML 處理器呼叫初始化為指定的執行個體方法的字串方法名稱`object`。</span><span class="sxs-lookup"><span data-stu-id="c92f9-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="c92f9-108">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="c92f9-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="c92f9-109">一或多個物件項目指定處理站方法參數的物件。</span><span class="sxs-lookup"><span data-stu-id="c92f9-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="c92f9-110">順序是很重要。它表示在其中引數應該傳遞給的 factory 方法的順序。</span><span class="sxs-lookup"><span data-stu-id="c92f9-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c92f9-111">備註</span><span class="sxs-lookup"><span data-stu-id="c92f9-111">Remarks</span></span>  
 <span data-ttu-id="c92f9-112">如果`methodname`是執行個體方法，無法加以限定。</span><span class="sxs-lookup"><span data-stu-id="c92f9-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="c92f9-113">支援的 factory 方法為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="c92f9-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="c92f9-114">如果`methodname`是靜態方法，`methodname`依現狀*typeName*。*methodName*組合，其中*typeName*名稱定義的靜態 factory 方法的類別。</span><span class="sxs-lookup"><span data-stu-id="c92f9-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="c92f9-115">*typeName*可以是如果參考類型中對應的 xmlns 前置詞限定。</span><span class="sxs-lookup"><span data-stu-id="c92f9-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="c92f9-116">*typeName*可以是類型不同於`typeof(``object``)`。</span><span class="sxs-lookup"><span data-stu-id="c92f9-116">*typeName* can be a different type than `typeof(``object``)`.</span></span>  
  
 <span data-ttu-id="c92f9-117">Factory 方法，必須是宣告的公用方法的型別之備份的相關物件項目。</span><span class="sxs-lookup"><span data-stu-id="c92f9-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="c92f9-118">處理站方法必須傳回可指派至相關物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c92f9-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="c92f9-119">Factory 方法，應該永遠不會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="c92f9-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="c92f9-120">`x:Arguments`最符合的 factory 方法的簽章的原則上運作。</span><span class="sxs-lookup"><span data-stu-id="c92f9-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="c92f9-121">比對參數計數會先評估。</span><span class="sxs-lookup"><span data-stu-id="c92f9-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="c92f9-122">如果有多個可能的相符項目參數計數的參數類型為則取決於評估及最佳的相符項目。</span><span class="sxs-lookup"><span data-stu-id="c92f9-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="c92f9-123">如果此評估階段之後仍有模稜兩可，XAML 處理器的行為是未定義的。</span><span class="sxs-lookup"><span data-stu-id="c92f9-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="c92f9-124">`x:FactoryMethod`項目使用方式不是屬性項目用法中的一般意義，因為指示詞標記未參考包含物件項目類型。</span><span class="sxs-lookup"><span data-stu-id="c92f9-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="c92f9-125">預期的項目用法是較不常見，比屬性使用方式。</span><span class="sxs-lookup"><span data-stu-id="c92f9-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="c92f9-126">`x:Arguments`可以使用 （屬性或項目使用方式），連同`x:FactoryMethod`項目使用方式，但這不特別會顯示在使用方式區段。</span><span class="sxs-lookup"><span data-stu-id="c92f9-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="c92f9-127">`x:FactoryMethod`當項目必須在任何其他屬性項目之前，必須優先於任何`x:Arguments`也提供做為項目，而且必須在前面的任何內容/內部文字/初始化文字。</span><span class="sxs-lookup"><span data-stu-id="c92f9-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c92f9-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="c92f9-128">See Also</span></span>  
 [<span data-ttu-id="c92f9-129">x:Arguments 指示詞</span><span class="sxs-lookup"><span data-stu-id="c92f9-129">x:Arguments Directive</span></span>](../../../docs/framework/xaml-services/x-arguments-directive.md)
