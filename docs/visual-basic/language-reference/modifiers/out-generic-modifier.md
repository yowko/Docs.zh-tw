---
title: "Out (泛型修飾詞) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e54504cd65b78846af41692f39899140a6d99b5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="b03ab-102">Out (泛型修飾詞) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b03ab-102">Out (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="b03ab-103">泛型型別參數`Out`關鍵字可讓您指定的型別是 covariant。</span><span class="sxs-lookup"><span data-stu-id="b03ab-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b03ab-104">備註</span><span class="sxs-lookup"><span data-stu-id="b03ab-104">Remarks</span></span>  
 <span data-ttu-id="b03ab-105">共變數可讓您使用比泛型參數指定的衍生程度更高的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="b03ab-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="b03ab-106">這可隱含轉換實作 Variant 介面的類別和隱含轉換委派型別。</span><span class="sxs-lookup"><span data-stu-id="b03ab-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="b03ab-107">如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數 (C# 和 Visual Basic))。</span><span class="sxs-lookup"><span data-stu-id="b03ab-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b03ab-108">規則</span><span class="sxs-lookup"><span data-stu-id="b03ab-108">Rules</span></span>  
 <span data-ttu-id="b03ab-109">您可以在泛型介面及委派中使用 `Out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b03ab-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="b03ab-110">在泛型介面中，型別參數如果滿足下列條件即可宣告為 Covariant︰</span><span class="sxs-lookup"><span data-stu-id="b03ab-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="b03ab-111">型別參數僅用為介面方法的傳回型別，不用為方法引數的型別。</span><span class="sxs-lookup"><span data-stu-id="b03ab-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b03ab-112">這個規則只有一個例外。</span><span class="sxs-lookup"><span data-stu-id="b03ab-112">There is one exception to this rule.</span></span> <span data-ttu-id="b03ab-113">如果您在 Covariant 介面中以 Contravariant 泛型委派作為方法參數，則可將 Covariant 型別用為此委派的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="b03ab-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="b03ab-114">如需 Covariant 和 Contravariant 泛型委派的詳細資訊，請參閱 [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) (委派中的變異數) 和 [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md) (針對 Func 與 Action 委派使用變異數)。</span><span class="sxs-lookup"><span data-stu-id="b03ab-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="b03ab-115">型別參數不是用為介面方法的泛型條件約束。</span><span class="sxs-lookup"><span data-stu-id="b03ab-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
 <span data-ttu-id="b03ab-116">在泛型委派中，型別參數可以宣告 covariant 如果只當做方法的傳回型別，而且不用於方法引數。</span><span class="sxs-lookup"><span data-stu-id="b03ab-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
 <span data-ttu-id="b03ab-117">參考型別支援共變數和反變數，但實值型別不支援它們。</span><span class="sxs-lookup"><span data-stu-id="b03ab-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="b03ab-118">在 Visual Basic 中，您無法宣告 covariant 介面中的事件，而不指定委派類型。</span><span class="sxs-lookup"><span data-stu-id="b03ab-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="b03ab-119">此外，類別、 列舉或結構，covariant 介面不能有巢狀，但可以有巢狀介面。</span><span class="sxs-lookup"><span data-stu-id="b03ab-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="b03ab-120">行為</span><span class="sxs-lookup"><span data-stu-id="b03ab-120">Behavior</span></span>  
 <span data-ttu-id="b03ab-121">具有 Covariant 型別參數的介面可讓其方法傳回的衍生型別，衍生程度高過型別參數指定的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="b03ab-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="b03ab-122">例如，因為在 .NET Framework 4 的 <xref:System.Collections.Generic.IEnumerable%601> 中，T 類型是 Covariant，所以您可以不使用任何特殊的轉換方法，將 `IEnumerabe(Of String)` 類型的物件指派給 `IEnumerable(Of Object)` 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="b03ab-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="b03ab-123">Covariant 委派可以指派給同型別的另一個委派，但具有衍生程度較大的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="b03ab-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b03ab-124">範例</span><span class="sxs-lookup"><span data-stu-id="b03ab-124">Example</span></span>  
 <span data-ttu-id="b03ab-125">下例會示範如何宣告、擴充及實作 Covariant 泛型介面。</span><span class="sxs-lookup"><span data-stu-id="b03ab-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="b03ab-126">它也會示範如何針對實作 Covariant 介面的類別使用隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="b03ab-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="b03ab-127">範例</span><span class="sxs-lookup"><span data-stu-id="b03ab-127">Example</span></span>  
 <span data-ttu-id="b03ab-128">下例會示範如何宣告、具現化及叫用 Covariant 泛型委派。</span><span class="sxs-lookup"><span data-stu-id="b03ab-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="b03ab-129">它也會顯示如何使用隱含轉換為委派類型。</span><span class="sxs-lookup"><span data-stu-id="b03ab-129">It also shows how you can use implicit conversion for delegate types.</span></span>  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b03ab-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="b03ab-130">See Also</span></span>  
 [<span data-ttu-id="b03ab-131">泛型介面中的變異數</span><span class="sxs-lookup"><span data-stu-id="b03ab-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="b03ab-132">In</span><span class="sxs-lookup"><span data-stu-id="b03ab-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
