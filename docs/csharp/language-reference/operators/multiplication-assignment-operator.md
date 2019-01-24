---
title: '*= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 2038f3b55d46f3503496275b3d25b17663b8c1db
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333430"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7b998-102">\*= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7b998-102">\*= Operator (C# Reference)</span></span>

<span data-ttu-id="7b998-103">二進位乘法指派運算子。</span><span class="sxs-lookup"><span data-stu-id="7b998-103">The binary multiplication assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b998-104">備註</span><span class="sxs-lookup"><span data-stu-id="7b998-104">Remarks</span></span>

<span data-ttu-id="7b998-105">使用 `*=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="7b998-105">An expression using the `*=` assignment operator, such as</span></span>

```csharp
x *= y
```

<span data-ttu-id="7b998-106">相當於</span><span class="sxs-lookup"><span data-stu-id="7b998-106">is equivalent to</span></span>

```csharp
x = x * y
```

<span data-ttu-id="7b998-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="7b998-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="7b998-108">對於對要執行乘法的數值類型，已預先定義 [\* 運算子](multiplication-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="7b998-108">The [\* operator](multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>

<span data-ttu-id="7b998-109">無法直接多載 `*=` 運算子，但使用者定義型別可以多載 [\* 運算子](multiplication-operator.md) (請參閱 [operator](../keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="7b998-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [\* operator](multiplication-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="7b998-110">範例</span><span class="sxs-lookup"><span data-stu-id="7b998-110">Example</span></span>

[!code-csharp[csRefOperators#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#13)]

## <a name="see-also"></a><span data-ttu-id="7b998-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b998-111">See also</span></span>

- [<span data-ttu-id="7b998-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="7b998-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7b998-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7b998-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7b998-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="7b998-114">C# Operators</span></span>](index.md)
