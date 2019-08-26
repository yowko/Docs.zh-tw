---
title: private 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a20c0a6fd729c2fc34449167eb92cb774bc3b84e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602019"
---
# <a name="private-c-reference"></a><span data-ttu-id="ee8e1-102">private (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ee8e1-102">private (C# Reference)</span></span>

<span data-ttu-id="ee8e1-103">`private` 關鍵字是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="ee8e1-104">此頁面涵蓋 `private` 存取。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-104">This page covers `private` access.</span></span> <span data-ttu-id="ee8e1-105">`private` 關鍵字也是屬於 [`private protected`](./private-protected.md) 存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="ee8e1-106">私用存取是最嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="ee8e1-107">私用成員只能在宣告它們的類別主體或結構主體內存取，如本範例所示：</span><span class="sxs-lookup"><span data-stu-id="ee8e1-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="ee8e1-108">相同主體內的巢狀型別也可以存取這些私用成員。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="ee8e1-109">在宣告私用成員的類別或結構外部參考私用成員是編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="ee8e1-110">如需 `private` 和其他存取修飾詞的比較，請參閱[存取範圍層級](accessibility-levels.md)和[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="ee8e1-111">範例</span><span class="sxs-lookup"><span data-stu-id="ee8e1-111">Example</span></span>

<span data-ttu-id="ee8e1-112">在此範例中，`Employee` 類別包含兩個私用資料成員：`name` 和 `salary`。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="ee8e1-113">作為私用成員，只有成員方法能加以存取。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="ee8e1-114">因此會新增名為 `GetName` 和 `Salary` 的公用方法，以允許對這些私用成員的控制存取。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="ee8e1-115">`name` 成員是透過公用方法存取，`salary` 成員則是透過公用唯讀屬性存取</span><span class="sxs-lookup"><span data-stu-id="ee8e1-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="ee8e1-116">(如需詳細資訊，請參閱[屬性](../../programming-guide/classes-and-structs/properties.md))。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="ee8e1-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ee8e1-117">C# language specification</span></span>  

<span data-ttu-id="ee8e1-118">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[已宣告存取範圍](~/_csharplang/spec/basic-concepts.md#declared-accessibility)。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="ee8e1-119">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="ee8e1-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee8e1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee8e1-120">See also</span></span>

- [<span data-ttu-id="ee8e1-121">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ee8e1-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ee8e1-122">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ee8e1-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ee8e1-123">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ee8e1-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ee8e1-124">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="ee8e1-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="ee8e1-125">存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="ee8e1-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="ee8e1-126">修飾詞</span><span class="sxs-lookup"><span data-stu-id="ee8e1-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="ee8e1-127">public</span><span class="sxs-lookup"><span data-stu-id="ee8e1-127">public</span></span>](public.md)
- [<span data-ttu-id="ee8e1-128">protected</span><span class="sxs-lookup"><span data-stu-id="ee8e1-128">protected</span></span>](protected.md)
- [<span data-ttu-id="ee8e1-129">internal</span><span class="sxs-lookup"><span data-stu-id="ee8e1-129">internal</span></span>](internal.md)
