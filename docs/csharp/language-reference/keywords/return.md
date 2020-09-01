---
description: return 陳述式 - C# 參考
title: return 陳述式 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 486db846304c0972942ff58f3d5b276083681abe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136993"
---
# <a name="return-c-reference"></a><span data-ttu-id="f0c83-103">return (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f0c83-103">return (C# Reference)</span></span>

<span data-ttu-id="f0c83-104">`return` 陳述式會終止執行在其中出現的方法，並且將控制權傳回給呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="f0c83-104">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="f0c83-105">它也可以傳回選擇性值。</span><span class="sxs-lookup"><span data-stu-id="f0c83-105">It can also return an optional value.</span></span> <span data-ttu-id="f0c83-106">如果方法是 `void` 類型，則可以省略 `return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0c83-106">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="f0c83-107">如果 return 陳述式位在 `try` 區塊內，則會先執行 `finally` 區塊 (如果存在的話)，控制權才會傳回到呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="f0c83-107">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="f0c83-108">範例</span><span class="sxs-lookup"><span data-stu-id="f0c83-108">Example</span></span>

 <span data-ttu-id="f0c83-109">在下列範例中，`CalculateArea()` 方法會將區域變數 `area` 傳回為 `double` 值。</span><span class="sxs-lookup"><span data-stu-id="f0c83-109">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="f0c83-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f0c83-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f0c83-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0c83-111">See also</span></span>

- [<span data-ttu-id="f0c83-112">C # 參考</span><span class="sxs-lookup"><span data-stu-id="f0c83-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f0c83-113">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f0c83-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f0c83-114">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f0c83-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f0c83-115">return 語句</span><span class="sxs-lookup"><span data-stu-id="f0c83-115">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
