---
title: -&gt; 運算子 (C# 參考)
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 178724ede105d809bd812461121a38d5a0e90517
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144126"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="f3751-102">-&gt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f3751-102">-&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="f3751-103">指標成員存取運算子 `->` 結合了指標間接取值和成員存取。</span><span class="sxs-lookup"><span data-stu-id="f3751-103">The pointer member access operator `->` combines pointer indirection and member access.</span></span>

<span data-ttu-id="f3751-104">如果 `x` 是 `T*` 型別的指標，而 `y` 是 `T` 的可存取成員，則以下形式的運算式</span><span class="sxs-lookup"><span data-stu-id="f3751-104">If `x` is a pointer of the type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="f3751-105">相當於</span><span class="sxs-lookup"><span data-stu-id="f3751-105">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="f3751-106">`->` 運算子需要 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="f3751-106">The `->` operator requires [unsafe](../keywords/unsafe.md) context.</span></span>

<span data-ttu-id="f3751-107">如需詳細資訊，請參閱[如何：使用指標存取成員](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md)。</span><span class="sxs-lookup"><span data-stu-id="f3751-107">For more information, see [How to: access a member with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f3751-108">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="f3751-108">Operator overloadability</span></span>

<span data-ttu-id="f3751-109">無法多載 `->` 運算子。</span><span class="sxs-lookup"><span data-stu-id="f3751-109">The `->` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f3751-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f3751-110">C# language specification</span></span>

<span data-ttu-id="f3751-111">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[指標成員存取](~/_csharplang/spec/unsafe-code.md#pointer-member-access)一節。</span><span class="sxs-lookup"><span data-stu-id="f3751-111">For more information, see the [Pointer member access](~/_csharplang/spec/unsafe-code.md#pointer-member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3751-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3751-112">See also</span></span>

- [<span data-ttu-id="f3751-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f3751-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f3751-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f3751-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f3751-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="f3751-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="f3751-116">指標型別</span><span class="sxs-lookup"><span data-stu-id="f3751-116">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
