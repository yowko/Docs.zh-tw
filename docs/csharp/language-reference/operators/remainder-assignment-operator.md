---
title: '%= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: d0732f9578b64c894ecc1d3bb15cee11a8d5b6a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245557"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0a48d-102">%= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0a48d-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="0a48d-103">餘數指派運算子。</span><span class="sxs-lookup"><span data-stu-id="0a48d-103">The remainder assignment operator.</span></span>

<span data-ttu-id="0a48d-104">使用 `%=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="0a48d-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="0a48d-105">相當於</span><span class="sxs-lookup"><span data-stu-id="0a48d-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="0a48d-106">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="0a48d-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="0a48d-107">[餘數運算子](remainder-operator.md) `%` 會計算其運算元進行除法運算之後的餘數。</span><span class="sxs-lookup"><span data-stu-id="0a48d-107">The [remainder operator](remainder-operator.md) `%` computes the remainder after division of its operands.</span></span> <span data-ttu-id="0a48d-108">所有數值型別都支援。</span><span class="sxs-lookup"><span data-stu-id="0a48d-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="0a48d-109">如果使用者定義型別[多載](../keywords/operator.md)[餘數運算子](remainder-operator.md) `%`，餘數指派運算子 `%=` 會隱含多載。</span><span class="sxs-lookup"><span data-stu-id="0a48d-109">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="0a48d-110">下列範例示範 `%=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="0a48d-110">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="0a48d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a48d-111">See also</span></span>

- [<span data-ttu-id="0a48d-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0a48d-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0a48d-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0a48d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0a48d-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="0a48d-114">C# Operators</span></span>](index.md)
