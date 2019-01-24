---
title: ?? 運算子 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: b96fe4790aac7ff5ff5394cbaaeaddc1e334e96c
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333209"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2c3b9-103">??</span><span class="sxs-lookup"><span data-stu-id="2c3b9-103">??</span></span> <span data-ttu-id="2c3b9-104">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2c3b9-104">operator (C# Reference)</span></span>

<span data-ttu-id="2c3b9-105">`??` 運算子稱為 null 聯合運算子。</span><span class="sxs-lookup"><span data-stu-id="2c3b9-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="2c3b9-106">如果運算元不是 null，則會傳回左方運算元，否則傳回右方運算元。</span><span class="sxs-lookup"><span data-stu-id="2c3b9-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c3b9-107">備註</span><span class="sxs-lookup"><span data-stu-id="2c3b9-107">Remarks</span></span>

<span data-ttu-id="2c3b9-108">可為 Null 的類型可以表示來自類型網域的值，或值可以是未定義 (這種情況下，值為 null)。</span><span class="sxs-lookup"><span data-stu-id="2c3b9-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="2c3b9-109">當左方運算元是可為 Null 的型別且其值為 null 時，您可使用 `??` 運算子的語法表達能力傳回適當的值 (右方運算元)。</span><span class="sxs-lookup"><span data-stu-id="2c3b9-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="2c3b9-110">如果您嘗試在不使用 `??` 運算子的情況下，將可為 null 的實值類型指派給不可為 null 的實值類型，則會產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="2c3b9-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="2c3b9-111">如果您使用轉型，而可為 null 的實值類型目前為未定義，則會擲回 `InvalidOperationException` 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2c3b9-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>

<span data-ttu-id="2c3b9-112">如需詳細資訊，請參閱[可為 Null 的型別](../../programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2c3b9-112">For more information, see [Nullable Types](../../programming-guide/nullable-types/index.md).</span></span>

<span data-ttu-id="2c3b9-113">?? 運算子的結果</span><span class="sxs-lookup"><span data-stu-id="2c3b9-113">The result of a ??</span></span> <span data-ttu-id="2c3b9-114">不視為常數，即使它的兩個引數都是常數。</span><span class="sxs-lookup"><span data-stu-id="2c3b9-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>

## <a name="example"></a><span data-ttu-id="2c3b9-115">範例</span><span class="sxs-lookup"><span data-stu-id="2c3b9-115">Example</span></span>

[!code-csharp[csRefOperators#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#53)]

## <a name="c-language-specification"></a><span data-ttu-id="2c3b9-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2c3b9-116">C# language specification</span></span>

<span data-ttu-id="2c3b9-117">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [null 聯合運算子](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)。</span><span class="sxs-lookup"><span data-stu-id="2c3b9-117">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="2c3b9-118">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="2c3b9-118">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c3b9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c3b9-119">See also</span></span>

- [<span data-ttu-id="2c3b9-120">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2c3b9-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2c3b9-121">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2c3b9-121">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2c3b9-122">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="2c3b9-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="2c3b9-123">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="2c3b9-123">Nullable Types</span></span>](../../programming-guide/nullable-types/index.md)
- [<span data-ttu-id="2c3b9-124">「增益」(Lift) 的真正意義是什麼？</span><span class="sxs-lookup"><span data-stu-id="2c3b9-124">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)