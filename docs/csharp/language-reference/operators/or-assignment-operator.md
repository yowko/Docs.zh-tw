---
title: '|= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: f4f7806c8679af400a371decd0c367929b3fb81d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333261"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a4318-102">|= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a4318-102">|= operator (C# Reference)</span></span>

<span data-ttu-id="a4318-103">OR 指派運算子。</span><span class="sxs-lookup"><span data-stu-id="a4318-103">The OR assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4318-104">備註</span><span class="sxs-lookup"><span data-stu-id="a4318-104">Remarks</span></span>

<span data-ttu-id="a4318-105">使用 `|=` 指派運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="a4318-105">An expression using the `|=` assignment operator, such as</span></span>

```csharp
x |= y
```

<span data-ttu-id="a4318-106">相當於</span><span class="sxs-lookup"><span data-stu-id="a4318-106">is equivalent to</span></span>

```csharp
x = x | y
```

<span data-ttu-id="a4318-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="a4318-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="a4318-108">[&#124; 運算子](or-operator.md) 在整數運算元上執行位元邏輯 OR 運算，在 bool 運算元上執行邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="a4318-108">The [&#124; operator](or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>

<span data-ttu-id="a4318-109">無法直接多載 `|=` 運算子，但使用者定義型別可以多載 [&#124; 運算子](or-operator.md) (請參閱 [operator](../keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="a4318-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](or-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="a4318-110">範例</span><span class="sxs-lookup"><span data-stu-id="a4318-110">Example</span></span>

[!code-csharp[csRefOperators#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#10)]

## <a name="see-also"></a><span data-ttu-id="a4318-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4318-111">See also</span></span>

- [<span data-ttu-id="a4318-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a4318-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a4318-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a4318-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a4318-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="a4318-114">C# operators</span></span>](index.md)