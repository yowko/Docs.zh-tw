---
title: new 條件約束 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 2aa68bec13322e332bfe3841bc99403f72301183
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421795"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="3fdb6-102">new 條件約束 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3fdb6-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="3fdb6-103">`new` 條件約束指定泛型類別宣告中的任何型別引數都必須有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="3fdb6-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="3fdb6-104">若要使用新的條件約束，型別不能為抽象。</span><span class="sxs-lookup"><span data-stu-id="3fdb6-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="3fdb6-105">範例</span><span class="sxs-lookup"><span data-stu-id="3fdb6-105">Example</span></span>

<span data-ttu-id="3fdb6-106">當泛型類別建立新的型別執行個體時，將 `new` 條件約束套用至型別參數，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="3fdb6-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="3fdb6-107">範例</span><span class="sxs-lookup"><span data-stu-id="3fdb6-107">Example</span></span>

<span data-ttu-id="3fdb6-108">當您使用 `new()` 條件約束與其他條件約束時，它必須是最後一個指定的︰</span><span class="sxs-lookup"><span data-stu-id="3fdb6-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="3fdb6-109">如需詳細資訊，請參閱[型別參數的條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="3fdb6-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3fdb6-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3fdb6-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3fdb6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fdb6-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="3fdb6-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3fdb6-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="3fdb6-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3fdb6-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3fdb6-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="3fdb6-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3fdb6-115">泛型</span><span class="sxs-lookup"><span data-stu-id="3fdb6-115">Generics</span></span>](../../programming-guide/generics/index.md)
