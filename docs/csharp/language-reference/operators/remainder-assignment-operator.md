---
title: '%= 運算子 (C# 參考)'
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: c475517666bdadaa457dbb4188808b3a96fcdf0e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085636"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0bece-102">%= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0bece-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="0bece-103">餘數指派運算子。</span><span class="sxs-lookup"><span data-stu-id="0bece-103">The remainder assignment operator.</span></span>

<span data-ttu-id="0bece-104">使用 `%=` 運算子的運算式，例如</span><span class="sxs-lookup"><span data-stu-id="0bece-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="0bece-105">相當於</span><span class="sxs-lookup"><span data-stu-id="0bece-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="0bece-106">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="0bece-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="0bece-107">所有數字類型都支援[餘數運算子](remainder-operator.md) `%`，並在除以其運算元後計算餘數。</span><span class="sxs-lookup"><span data-stu-id="0bece-107">The [remainder operator](remainder-operator.md) `%` is supported by all numeric types and computes the remainder after division of its operands.</span></span>

<span data-ttu-id="0bece-108">如果使用者定義型別[多載](../keywords/operator.md)[餘數運算子](remainder-operator.md) `%`，餘數指派運算子 `%=` 會隱含多載。</span><span class="sxs-lookup"><span data-stu-id="0bece-108">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="0bece-109">下列範例示範 `%=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="0bece-109">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="0bece-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bece-110">See also</span></span>

- [<span data-ttu-id="0bece-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0bece-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0bece-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0bece-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0bece-113">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="0bece-113">C# Operators</span></span>](index.md)
