---
description: partial 方法 - C# 參考
title: partial 方法 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: d6c433fd30f6ec51355bdefee90d815783487c1b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134376"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="83c48-103">partial 方法 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="83c48-103">partial method (C# Reference)</span></span>

<span data-ttu-id="83c48-104">部分方法會在部分型別的某一部分中定義其簽章，並在類型的另一部分中定義其實作。</span><span class="sxs-lookup"><span data-stu-id="83c48-104">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="83c48-105">部分方法可讓類別設計工具提供方法攔截程序，類似於事件處理常式，開發人員可以決定是否實作。</span><span class="sxs-lookup"><span data-stu-id="83c48-105">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="83c48-106">如果開發人員未提供實作，編譯器會在編譯時期移除簽章。</span><span class="sxs-lookup"><span data-stu-id="83c48-106">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="83c48-107">下列條件適用於部分方法：</span><span class="sxs-lookup"><span data-stu-id="83c48-107">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="83c48-108">部分型別的兩個部分中的簽章必須相符。</span><span class="sxs-lookup"><span data-stu-id="83c48-108">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="83c48-109">此方法必須傳回 void。</span><span class="sxs-lookup"><span data-stu-id="83c48-109">The method must return void.</span></span>

- <span data-ttu-id="83c48-110">不允許存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="83c48-110">No access modifiers are allowed.</span></span> <span data-ttu-id="83c48-111">部分方法都是隱含私用。</span><span class="sxs-lookup"><span data-stu-id="83c48-111">Partial methods are implicitly private.</span></span>

<span data-ttu-id="83c48-112">下列範例顯示部分類別之兩個部分中定義的部分方法：</span><span class="sxs-lookup"><span data-stu-id="83c48-112">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="83c48-113">如需詳細資訊，請參閱[部分類別和方法](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="83c48-113">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="83c48-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83c48-114">See also</span></span>

- [<span data-ttu-id="83c48-115">C # 參考</span><span class="sxs-lookup"><span data-stu-id="83c48-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="83c48-116">部分類型</span><span class="sxs-lookup"><span data-stu-id="83c48-116">partial type</span></span>](partial-type.md)
