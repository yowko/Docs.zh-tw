---
title: ^= 運算子 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 12189d6469a9716d3b7ebcffef23423a75692d1a
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333547"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="29daf-102">^= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="29daf-102">^= operator (C# Reference)</span></span>

<span data-ttu-id="29daf-103">互斥 OR 指派運算子。</span><span class="sxs-lookup"><span data-stu-id="29daf-103">The exclusive-OR assignment operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="29daf-104">備註</span><span class="sxs-lookup"><span data-stu-id="29daf-104">Remarks</span></span>

<span data-ttu-id="29daf-105">以下格式的運算式</span><span class="sxs-lookup"><span data-stu-id="29daf-105">An expression of the form</span></span>

```csharp
x ^= y
```

<span data-ttu-id="29daf-106">評估為</span><span class="sxs-lookup"><span data-stu-id="29daf-106">is evaluated as</span></span>

```csharp
x = x ^ y
```

<span data-ttu-id="29daf-107">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="29daf-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="29daf-108">[^ 運算子](xor-operator.md)會在整數運算元上執行位元互斥 OR 運算，以及在 [bool](../keywords/bool.md) 運算元上執行邏輯互斥 OR。</span><span class="sxs-lookup"><span data-stu-id="29daf-108">The [^ operator](xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="29daf-109">無法直接多載 ^= 運算子，但使用者定義型別可以多載 [^ 運算子](xor-operator.md) (請參閱 [operator](../keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="29daf-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](xor-operator.md) (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="29daf-110">範例</span><span class="sxs-lookup"><span data-stu-id="29daf-110">Example</span></span>

[!code-csharp[csRefOperators#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#23)]

## <a name="see-also"></a><span data-ttu-id="29daf-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29daf-111">See also</span></span>

- [<span data-ttu-id="29daf-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="29daf-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="29daf-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="29daf-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="29daf-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="29daf-114">C# operators</span></span>](index.md)