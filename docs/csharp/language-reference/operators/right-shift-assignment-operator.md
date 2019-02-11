---
title: '>>= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 8cc341c14ee1b90fde2abb369c187e57b4ce5c00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278976"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e6961-102">>>= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e6961-102">>>= operator (C# Reference)</span></span>

<span data-ttu-id="e6961-103">右移指派運算子。</span><span class="sxs-lookup"><span data-stu-id="e6961-103">The right-shift assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6961-104">備註</span><span class="sxs-lookup"><span data-stu-id="e6961-104">Remarks</span></span>

<span data-ttu-id="e6961-105">以下格式的運算式</span><span class="sxs-lookup"><span data-stu-id="e6961-105">An expression of the form</span></span>

```csharp
x >>= y
```

<span data-ttu-id="e6961-106">評估為</span><span class="sxs-lookup"><span data-stu-id="e6961-106">is evaluated as</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="e6961-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="e6961-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="e6961-108">[>> 運算子](right-shift-operator.md)會將 `x` 右移 `y` 所指定的數量。</span><span class="sxs-lookup"><span data-stu-id="e6961-108">The [>> operator](right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>

<span data-ttu-id="e6961-109">無法直接多載 >>= 運算子，但使用者定義型別可以多載 [>> 運算子](right-shift-operator.md) (請參閱 [operator](../keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="e6961-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](right-shift-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="e6961-110">範例</span><span class="sxs-lookup"><span data-stu-id="e6961-110">Example</span></span>

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a><span data-ttu-id="e6961-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6961-111">See also</span></span>

- [<span data-ttu-id="e6961-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e6961-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e6961-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e6961-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e6961-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="e6961-114">C# operators</span></span>](index.md)