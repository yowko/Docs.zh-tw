---
title: '&lt;&lt;= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 4513c4b78dea3e8102c72a43249b4a44ffa2421d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333248"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="f2359-102">&lt;&lt;= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f2359-102">&lt;&lt;= operator (C# Reference)</span></span>

<span data-ttu-id="f2359-103">左移指派運算子。</span><span class="sxs-lookup"><span data-stu-id="f2359-103">The left-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2359-104">備註</span><span class="sxs-lookup"><span data-stu-id="f2359-104">Remarks</span></span>

<span data-ttu-id="f2359-105">以下格式的運算式</span><span class="sxs-lookup"><span data-stu-id="f2359-105">An expression of the form</span></span>

```csharp
x <<= y
```

<span data-ttu-id="f2359-106">評估為</span><span class="sxs-lookup"><span data-stu-id="f2359-106">is evaluated as</span></span>

```csharp
x = x << y
```

<span data-ttu-id="f2359-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="f2359-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f2359-108">[<< 運算子](left-shift-operator.md)會將 `x` 左移 `y` 所指定的位元數。</span><span class="sxs-lookup"><span data-stu-id="f2359-108">The [<< operator](left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>

<span data-ttu-id="f2359-109">無法直接多載 `<<=` 運算子，但使用者定義型別可以多載 [<< 運算子](left-shift-operator.md) (請參閱 [operator](../keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="f2359-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](left-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="f2359-110">範例</span><span class="sxs-lookup"><span data-stu-id="f2359-110">Example</span></span>

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a><span data-ttu-id="f2359-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2359-111">See also</span></span>

- [<span data-ttu-id="f2359-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f2359-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f2359-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f2359-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f2359-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="f2359-114">C# Operators</span></span>](index.md)
