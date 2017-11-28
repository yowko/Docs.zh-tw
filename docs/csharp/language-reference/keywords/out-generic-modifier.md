---
title: "out (泛型修飾詞) (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5c63fe2229d4b7190397d3ba98fa150c84a12fb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="073c9-102">out (泛型修飾詞) (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="073c9-102">out (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="073c9-103">若為泛型型別參數，`out` 關鍵字會指定型別參數是 Covariant。</span><span class="sxs-lookup"><span data-stu-id="073c9-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="073c9-104">您可以在泛型介面及委派中使用 `out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="073c9-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="073c9-105">共變數可讓您使用比泛型參數指定的衍生程度更高的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="073c9-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="073c9-106">這可隱含轉換實作 Variant 介面的類別和隱含轉換委派型別。</span><span class="sxs-lookup"><span data-stu-id="073c9-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="073c9-107">參考型別支援共變數和反變數，但實值型別不支援它們。</span><span class="sxs-lookup"><span data-stu-id="073c9-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="073c9-108">具有 Covariant 型別參數的介面可讓其方法傳回的衍生型別，衍生程度高過型別參數指定的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="073c9-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="073c9-109">例如，因為在 .NET Framework 4 的 <xref:System.Collections.Generic.IEnumerable%601> 中，T 類型是 Covariant，所以您可以不使用任何特殊的轉換方法，將 `IEnumerabe(Of String)` 類型的物件指派給 `IEnumerable(Of Object)` 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="073c9-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="073c9-110">Covariant 委派可以指派給同型別的另一個委派，但具有衍生程度較大的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="073c9-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
 <span data-ttu-id="073c9-111">如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數 (C# 和 Visual Basic))。</span><span class="sxs-lookup"><span data-stu-id="073c9-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="073c9-112">範例</span><span class="sxs-lookup"><span data-stu-id="073c9-112">Example</span></span>  
 <span data-ttu-id="073c9-113">下例會示範如何宣告、擴充及實作 Covariant 泛型介面。</span><span class="sxs-lookup"><span data-stu-id="073c9-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="073c9-114">它也會示範如何針對實作 Covariant 介面的類別使用隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="073c9-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 <span data-ttu-id="073c9-115">在泛型介面中，型別參數如果滿足下列條件即可宣告為 Covariant︰</span><span class="sxs-lookup"><span data-stu-id="073c9-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="073c9-116">型別參數僅用為介面方法的傳回型別，不用為方法引數的型別。</span><span class="sxs-lookup"><span data-stu-id="073c9-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="073c9-117">這個規則只有一個例外。</span><span class="sxs-lookup"><span data-stu-id="073c9-117">There is one exception to this rule.</span></span> <span data-ttu-id="073c9-118">如果您在 Covariant 介面中以 Contravariant 泛型委派作為方法參數，則可將 Covariant 型別用為此委派的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="073c9-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="073c9-119">如需 Covariant 和 Contravariant 泛型委派的詳細資訊，請參閱 [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) (委派中的變異數) 和 [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md) (針對 Func 與 Action 委派使用變異數)。</span><span class="sxs-lookup"><span data-stu-id="073c9-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="073c9-120">型別參數不是用為介面方法的泛型條件約束。</span><span class="sxs-lookup"><span data-stu-id="073c9-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="073c9-121">範例</span><span class="sxs-lookup"><span data-stu-id="073c9-121">Example</span></span>  
 <span data-ttu-id="073c9-122">下例會示範如何宣告、具現化及叫用 Covariant 泛型委派。</span><span class="sxs-lookup"><span data-stu-id="073c9-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="073c9-123">它也會顯示如何以隱含方式轉換委派型別。</span><span class="sxs-lookup"><span data-stu-id="073c9-123">It also shows how to implicitly convert delegate types.</span></span>  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 <span data-ttu-id="073c9-124">在泛型委派中，如果型別只用為方法傳回型別，不用於方法引數，則可以宣告為 Covariant。</span><span class="sxs-lookup"><span data-stu-id="073c9-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="073c9-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="073c9-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="073c9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="073c9-126">See Also</span></span>  
 [<span data-ttu-id="073c9-127">泛型介面中的變異數</span><span class="sxs-lookup"><span data-stu-id="073c9-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="073c9-128">in</span><span class="sxs-lookup"><span data-stu-id="073c9-128">in</span></span>](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [<span data-ttu-id="073c9-129">修飾詞</span><span class="sxs-lookup"><span data-stu-id="073c9-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
