---
description: in (泛型修飾詞) - C# 參考
title: in (泛型修飾詞) - C# 參考
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: feae17be7bdf29f6bc90e8c85b3878d4714699f4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118451"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="28e48-103">in (泛型修飾詞) (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="28e48-103">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="28e48-104">若為泛型型別參數，`in` 關鍵字會指定型別參數是 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="28e48-104">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="28e48-105">您可以在泛型介面及委派中使用 `in` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="28e48-105">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="28e48-106">反變數可讓您使用比泛型參數指定的衍生程度更低的衍生類型。</span><span class="sxs-lookup"><span data-stu-id="28e48-106">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="28e48-107">這可隱含轉換實作 Contravariant 介面的類別和隱含轉換委派類型。</span><span class="sxs-lookup"><span data-stu-id="28e48-107">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="28e48-108">參考型別支援在泛型型別參數中使用共變數和反變數，但實值型別則不支援。</span><span class="sxs-lookup"><span data-stu-id="28e48-108">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="28e48-109">只有當某一類型會定義方法參數的類型，且並非為方法的傳回類型時，才可在泛型介面或委派中，將類型宣告為 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="28e48-109">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="28e48-110">`In`、`ref` 及 `out` 參數不得變更，這表示它們都不會是 covariant 或 contravariant。</span><span class="sxs-lookup"><span data-stu-id="28e48-110">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="28e48-111">具有 Contravariant 型別參數的介面可讓其方法接受衍生程度低於介面型別參數指定之衍生類型的引數。</span><span class="sxs-lookup"><span data-stu-id="28e48-111">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="28e48-112">例如，在 <xref:System.Collections.Generic.IComparer%601> 介面中，類型 T 為 Contravariant，所以您可以不使用任何特殊的轉換方法，即能將 `IComparer<Person>` 類型的物件指派給 `IComparer<Employee>` 類型的物件 (如果 `Employee` 繼承 `Person`)。</span><span class="sxs-lookup"><span data-stu-id="28e48-112">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="28e48-113">您可以將類型相同但具有衍生程度較低之泛型型別參數的另一個委派指派給 Contravariant 委派。</span><span class="sxs-lookup"><span data-stu-id="28e48-113">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="28e48-114">如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數 (C# 和 Visual Basic))。</span><span class="sxs-lookup"><span data-stu-id="28e48-114">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="28e48-115">Contravariant 泛型介面</span><span class="sxs-lookup"><span data-stu-id="28e48-115">Contravariant generic interface</span></span>

<span data-ttu-id="28e48-116">下例範例示範如何宣告、擴充及實作 Contravariant 泛型介面。</span><span class="sxs-lookup"><span data-stu-id="28e48-116">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="28e48-117">它也會示範如何針對實作此介面的類別使用隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="28e48-117">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="28e48-118">Contravariant 泛型委派</span><span class="sxs-lookup"><span data-stu-id="28e48-118">Contravariant generic delegate</span></span>

<span data-ttu-id="28e48-119">下例範例示範如何宣告、具現化及叫用 Contravariant 泛型委派。</span><span class="sxs-lookup"><span data-stu-id="28e48-119">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="28e48-120">它也會示範如何以隱含方式轉換委派類型。</span><span class="sxs-lookup"><span data-stu-id="28e48-120">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="28e48-121">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="28e48-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="28e48-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28e48-122">See also</span></span>

- [<span data-ttu-id="28e48-123">擴展</span><span class="sxs-lookup"><span data-stu-id="28e48-123">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="28e48-124">共變數和反變數</span><span class="sxs-lookup"><span data-stu-id="28e48-124">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="28e48-125">修飾詞</span><span class="sxs-lookup"><span data-stu-id="28e48-125">Modifiers</span></span>](index.md)
