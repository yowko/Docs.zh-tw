---
title: '* 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: f4490c4632d9344eb879ea55c20787b838781d91
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333729"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ba7ad-102">\* 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ba7ad-102">\* operator (C# Reference)</span></span>

<span data-ttu-id="ba7ad-103">乘法運算子 (`*`)，它會計算其運算元的乘積。</span><span class="sxs-lookup"><span data-stu-id="ba7ad-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="ba7ad-104">所有數字類型都有預先定義的乘法運算子。</span><span class="sxs-lookup"><span data-stu-id="ba7ad-104">All numeric types have predefined multiplication operators.</span></span>

<span data-ttu-id="ba7ad-105">`*` 也可做為取值運算子，其允許讀取和寫入指標中。</span><span class="sxs-lookup"><span data-stu-id="ba7ad-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba7ad-106">備註</span><span class="sxs-lookup"><span data-stu-id="ba7ad-106">Remarks</span></span>

<span data-ttu-id="ba7ad-107">`*` 運算子也可以用來宣告指標類型，並對指標取值 (Dereference)。</span><span class="sxs-lookup"><span data-stu-id="ba7ad-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="ba7ad-108">此運算子只可用於 Unsafe 內容中，並透過使用 [unsafe](../keywords/unsafe.md) 關鍵字及需要 [/unsafe](../compiler-options/unsafe-compiler-option.md) 編譯器選項來表示。</span><span class="sxs-lookup"><span data-stu-id="ba7ad-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../keywords/unsafe.md) keyword, and requiring the [/unsafe](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="ba7ad-109">取值運算子也稱作間接運算子。</span><span class="sxs-lookup"><span data-stu-id="ba7ad-109">The dereference operator is also known as the indirection operator.</span></span>

<span data-ttu-id="ba7ad-110">使用者定義型別可以多載二進位 `*` 運算子 (請參閱 [operator](../keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="ba7ad-110">User-defined types can overload the binary `*` operator (see [operator](../keywords/operator.md)).</span></span> <span data-ttu-id="ba7ad-111">二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="ba7ad-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="ba7ad-112">範例</span><span class="sxs-lookup"><span data-stu-id="ba7ad-112">Example</span></span>

[!code-csharp-interactive[csRefOperators#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#50)]

## <a name="example"></a><span data-ttu-id="ba7ad-113">範例</span><span class="sxs-lookup"><span data-stu-id="ba7ad-113">Example</span></span>

[!code-csharp[csRefOperators#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#51)]

## <a name="see-also"></a><span data-ttu-id="ba7ad-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba7ad-114">See also</span></span>

- [<span data-ttu-id="ba7ad-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ba7ad-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ba7ad-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ba7ad-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ba7ad-117">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="ba7ad-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="ba7ad-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="ba7ad-118">C# Operators</span></span>](index.md)