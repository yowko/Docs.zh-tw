---
title: 運算子關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- keywords [C#], operators
- operators [C#], keywords
ms.assetid: f745c81f-f8d8-4673-86a1-0f3a85cc63c3
ms.openlocfilehash: e03e1c930b452cf5e4f2c4bb1d06d5363f20c991
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243594"
---
# <a name="operator-keywords-c-reference"></a><span data-ttu-id="d2f28-102">運算子關鍵字 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d2f28-102">Operator Keywords (C# Reference)</span></span>

<span data-ttu-id="d2f28-103">用來執行其他動作，例如建立物件、檢查物件的執行階段類型，取得類型的大小和其他動作。</span><span class="sxs-lookup"><span data-stu-id="d2f28-103">Used to perform miscellaneous actions such as creating objects, checking the run-time type of an object, obtaining the size of a type, and other actions.</span></span> <span data-ttu-id="d2f28-104">本節將介紹下列關鍵字：</span><span class="sxs-lookup"><span data-stu-id="d2f28-104">This section introduces the following keywords:</span></span>

- <span data-ttu-id="d2f28-105">[as](as.md) 將物件轉換為相容類型。</span><span class="sxs-lookup"><span data-stu-id="d2f28-105">[as](as.md) Converts an object to a compatible type.</span></span>

- <span data-ttu-id="d2f28-106">[await](await.md) 暫止 [async](async.md) 方法，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="d2f28-106">[await](await.md) Suspends an [async](async.md) method until an awaited task is completed.</span></span>

- <span data-ttu-id="d2f28-107">[is](is.md) 檢查物件的執行階段類型，或 (從 C# 7.0 開始) 根據模式來測試運算式。</span><span class="sxs-lookup"><span data-stu-id="d2f28-107">[is](is.md) Checks the run-time type of an object, or (starting with C# 7.0) tests an expression against a pattern.</span></span>

- [<span data-ttu-id="d2f28-108">new</span><span class="sxs-lookup"><span data-stu-id="d2f28-108">new</span></span>](new.md)

  - <span data-ttu-id="d2f28-109">[new 運算子](new-operator.md) 建立物件。</span><span class="sxs-lookup"><span data-stu-id="d2f28-109">[new Operator](new-operator.md) Creates objects.</span></span>

  - <span data-ttu-id="d2f28-110">[new 修飾詞](new-modifier.md) 隱藏繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="d2f28-110">[new Modifier](new-modifier.md) Hides an inherited member.</span></span>

  - <span data-ttu-id="d2f28-111">[new 條件約束](new-constraint.md) 限定型別參數。</span><span class="sxs-lookup"><span data-stu-id="d2f28-111">[new Constraint](new-constraint.md) Qualifies a type parameter.</span></span>

- <span data-ttu-id="d2f28-112">[nameof](nameof.md) 取得變數、類型或成員的簡單 (不完整) 字串名稱。</span><span class="sxs-lookup"><span data-stu-id="d2f28-112">[nameof](nameof.md) Obtains the simple (unqualified) string name of a variable, type, or member.</span></span>

- <span data-ttu-id="d2f28-113">[sizeof](sizeof.md)取得 Unmanaged 類型的大小。</span><span class="sxs-lookup"><span data-stu-id="d2f28-113">[sizeof](sizeof.md) Obtains the size of an unmanaged type.</span></span>  

- <span data-ttu-id="d2f28-114">[typeof](typeof.md) 取得類型的 <xref:System.Type?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="d2f28-114">[typeof](typeof.md) Obtains the <xref:System.Type?displayProperty=nameWithType> object for a type.</span></span>  

- [<span data-ttu-id="d2f28-115">true</span><span class="sxs-lookup"><span data-stu-id="d2f28-115">true</span></span>](true.md)  

  - <span data-ttu-id="d2f28-116">[true 運算子](true-false-operators.md) 傳回 [bool](bool.md) 值 `true` 以指出運算元必然為 true。</span><span class="sxs-lookup"><span data-stu-id="d2f28-116">[true Operator](true-false-operators.md) Returns the [bool](bool.md) value `true` to indicate that the operand is definitely true.</span></span>

  - <span data-ttu-id="d2f28-117">[true 常值](true-literal.md) 代表 [bool](bool.md) 值 `true`。</span><span class="sxs-lookup"><span data-stu-id="d2f28-117">[true Literal](true-literal.md) Represents the [bool](bool.md) value `true`.</span></span>

- [<span data-ttu-id="d2f28-118">false</span><span class="sxs-lookup"><span data-stu-id="d2f28-118">false</span></span>](false.md)  

  - <span data-ttu-id="d2f28-119">[false 運算子](true-false-operators.md) 傳回 [bool](bool.md) 值 `true` 以指出運算元必然為 false。</span><span class="sxs-lookup"><span data-stu-id="d2f28-119">[false Operator](true-false-operators.md) Returns the [bool](bool.md) value `true` to indicate that the operand is definitely false.</span></span>

  - <span data-ttu-id="d2f28-120">[false 常值](false-literal.md) 代表 [bool](bool.md) 值 `false`。</span><span class="sxs-lookup"><span data-stu-id="d2f28-120">[false Literal](false-literal.md) Represents the [bool](bool.md) value `false`.</span></span>

- <span data-ttu-id="d2f28-121">[stackalloc](stackalloc.md) 配置堆疊上的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="d2f28-121">[stackalloc](stackalloc.md) Allocates a block of memory on the stack.</span></span>  

<span data-ttu-id="d2f28-122">[陳述式](statement-keywords.md)一節涵蓋了可作為運算子和陳述式的下列關鍵字：</span><span class="sxs-lookup"><span data-stu-id="d2f28-122">The following keywords, which can be used as operators and as statements, are covered in the [Statements](statement-keywords.md) section:</span></span>

- <span data-ttu-id="d2f28-123">[checked](checked.md) 指定 checked 內容。</span><span class="sxs-lookup"><span data-stu-id="d2f28-123">[checked](checked.md) Specifies checked context.</span></span>  

- <span data-ttu-id="d2f28-124">[unchecked](unchecked.md) 指定 unchecked 內容。</span><span class="sxs-lookup"><span data-stu-id="d2f28-124">[unchecked](unchecked.md) Specifies unchecked context.</span></span>  

## <a name="see-also"></a><span data-ttu-id="d2f28-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2f28-125">See also</span></span>

- [<span data-ttu-id="d2f28-126">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d2f28-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d2f28-127">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d2f28-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d2f28-128">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d2f28-128">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d2f28-129">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="d2f28-129">C# Operators</span></span>](../operators/index.md)
