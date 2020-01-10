---
title: return 陳述式 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713127"
---
# <a name="return-c-reference"></a><span data-ttu-id="d8f7e-102">return (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d8f7e-102">return (C# Reference)</span></span>

<span data-ttu-id="d8f7e-103">`return` 陳述式會終止執行在其中出現的方法，並且將控制權傳回給呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="d8f7e-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="d8f7e-104">它也可以傳回選擇性值。</span><span class="sxs-lookup"><span data-stu-id="d8f7e-104">It can also return an optional value.</span></span> <span data-ttu-id="d8f7e-105">如果方法是 `void` 類型，則可以省略 `return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d8f7e-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="d8f7e-106">如果 return 陳述式位在 `try` 區塊內，則會先執行 `finally` 區塊 (如果存在的話)，控制權才會傳回到呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="d8f7e-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="d8f7e-107">範例</span><span class="sxs-lookup"><span data-stu-id="d8f7e-107">Example</span></span>

 <span data-ttu-id="d8f7e-108">在下列範例中，`CalculateArea()` 方法會將區域變數 `area` 傳回為 `double` 值。</span><span class="sxs-lookup"><span data-stu-id="d8f7e-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="d8f7e-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d8f7e-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d8f7e-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8f7e-110">See also</span></span>

- [<span data-ttu-id="d8f7e-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d8f7e-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d8f7e-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d8f7e-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d8f7e-113">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d8f7e-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d8f7e-114">return 陳述式</span><span class="sxs-lookup"><span data-stu-id="d8f7e-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
