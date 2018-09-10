---
title: new 條件約束 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 9948fc65030a4636c5d23db4ef8c3a584018d2f5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087007"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="82540-102">new 條件約束 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="82540-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="82540-103">`new` 條件約束指定泛型類別宣告中的任何型別引數都必須有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="82540-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="82540-104">若要使用新的條件約束，型別不能為抽象。</span><span class="sxs-lookup"><span data-stu-id="82540-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="82540-105">範例</span><span class="sxs-lookup"><span data-stu-id="82540-105">Example</span></span>

<span data-ttu-id="82540-106">當泛型類別建立新的型別執行個體時，將 `new` 條件約束套用至型別參數，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="82540-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="82540-107">範例</span><span class="sxs-lookup"><span data-stu-id="82540-107">Example</span></span>

<span data-ttu-id="82540-108">當您使用 `new()` 條件約束與其他條件約束時，它必須是最後一個指定的︰</span><span class="sxs-lookup"><span data-stu-id="82540-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="82540-109">如需詳細資訊，請參閱[型別參數的條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="82540-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="82540-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="82540-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="82540-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82540-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="82540-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="82540-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="82540-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="82540-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="82540-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="82540-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="82540-115">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="82540-115">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="82540-116">泛型</span><span class="sxs-lookup"><span data-stu-id="82540-116">Generics</span></span>](../../programming-guide/generics/index.md)