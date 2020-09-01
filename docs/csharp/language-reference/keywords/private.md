---
description: private 關鍵字 - C# 參考
title: private 關鍵字 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: e6f40712fd2cca6d7b1f64760f1c6c5dd5c71370
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139394"
---
# <a name="private-c-reference"></a><span data-ttu-id="5d80b-103">private (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5d80b-103">private (C# Reference)</span></span>

<span data-ttu-id="5d80b-104">`private` 關鍵字是成員存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="5d80b-104">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="5d80b-105">此頁面涵蓋 `private` 存取。</span><span class="sxs-lookup"><span data-stu-id="5d80b-105">This page covers `private` access.</span></span> <span data-ttu-id="5d80b-106">`private`關鍵字也是存取修飾詞的一部分 [`private protected`](./private-protected.md) 。</span><span class="sxs-lookup"><span data-stu-id="5d80b-106">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="5d80b-107">私用存取是最嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="5d80b-107">Private access is the least permissive access level.</span></span> <span data-ttu-id="5d80b-108">私用成員只能在宣告它們的類別主體或結構主體內存取，如本範例所示：</span><span class="sxs-lookup"><span data-stu-id="5d80b-108">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="5d80b-109">相同主體內的巢狀型別也可以存取這些私用成員。</span><span class="sxs-lookup"><span data-stu-id="5d80b-109">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="5d80b-110">在宣告私用成員的類別或結構外部參考私用成員是編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="5d80b-110">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="5d80b-111">如需 `private` 和其他存取修飾詞的比較，請參閱[存取範圍層級](accessibility-levels.md)和[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="5d80b-111">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="5d80b-112">範例</span><span class="sxs-lookup"><span data-stu-id="5d80b-112">Example</span></span>

<span data-ttu-id="5d80b-113">在此範例中，`Employee` 類別包含兩個私用資料成員：`name` 和 `salary`。</span><span class="sxs-lookup"><span data-stu-id="5d80b-113">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="5d80b-114">作為私用成員，只有成員方法能加以存取。</span><span class="sxs-lookup"><span data-stu-id="5d80b-114">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="5d80b-115">因此會新增名為 `GetName` 和 `Salary` 的公用方法，以允許對這些私用成員的控制存取。</span><span class="sxs-lookup"><span data-stu-id="5d80b-115">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="5d80b-116">`name` 成員是透過公用方法存取，`salary` 成員則是透過公用唯讀屬性存取</span><span class="sxs-lookup"><span data-stu-id="5d80b-116">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="5d80b-117">(如需詳細資訊，請參閱[屬性](../../programming-guide/classes-and-structs/properties.md))。</span><span class="sxs-lookup"><span data-stu-id="5d80b-117">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="5d80b-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5d80b-118">C# language specification</span></span>  

<span data-ttu-id="5d80b-119">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[已宣告存取範圍](~/_csharplang/spec/basic-concepts.md#declared-accessibility)。</span><span class="sxs-lookup"><span data-stu-id="5d80b-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="5d80b-120">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="5d80b-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d80b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d80b-121">See also</span></span>

- [<span data-ttu-id="5d80b-122">C # 參考</span><span class="sxs-lookup"><span data-stu-id="5d80b-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5d80b-123">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5d80b-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5d80b-124">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="5d80b-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5d80b-125">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="5d80b-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="5d80b-126">協助工具層級</span><span class="sxs-lookup"><span data-stu-id="5d80b-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="5d80b-127">修飾詞</span><span class="sxs-lookup"><span data-stu-id="5d80b-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="5d80b-128">public</span><span class="sxs-lookup"><span data-stu-id="5d80b-128">public</span></span>](public.md)
- [<span data-ttu-id="5d80b-129">protected</span><span class="sxs-lookup"><span data-stu-id="5d80b-129">protected</span></span>](protected.md)
- [<span data-ttu-id="5d80b-130">internal</span><span class="sxs-lookup"><span data-stu-id="5d80b-130">internal</span></span>](internal.md)
