---
title: partial 方法 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 14bcd3329b6ca8e46f6c180c97174a561108d143
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633363"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="8f79d-102">partial 方法 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8f79d-102">partial method (C# Reference)</span></span>

<span data-ttu-id="8f79d-103">部分方法會在部分型別的某一部分中定義其簽章，並在類型的另一部分中定義其實作。</span><span class="sxs-lookup"><span data-stu-id="8f79d-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="8f79d-104">部分方法可讓類別設計工具提供方法攔截程序，類似於事件處理常式，開發人員可以決定是否實作。</span><span class="sxs-lookup"><span data-stu-id="8f79d-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="8f79d-105">如果開發人員未提供實作，編譯器會在編譯時期移除簽章。</span><span class="sxs-lookup"><span data-stu-id="8f79d-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="8f79d-106">下列條件適用於部分方法：</span><span class="sxs-lookup"><span data-stu-id="8f79d-106">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="8f79d-107">部分型別的兩個部分中的簽章必須相符。</span><span class="sxs-lookup"><span data-stu-id="8f79d-107">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="8f79d-108">此方法必須傳回 void。</span><span class="sxs-lookup"><span data-stu-id="8f79d-108">The method must return void.</span></span>

- <span data-ttu-id="8f79d-109">不允許存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="8f79d-109">No access modifiers are allowed.</span></span> <span data-ttu-id="8f79d-110">部分方法都是隱含私用。</span><span class="sxs-lookup"><span data-stu-id="8f79d-110">Partial methods are implicitly private.</span></span>

<span data-ttu-id="8f79d-111">下列範例顯示部分類別之兩個部分中定義的部分方法：</span><span class="sxs-lookup"><span data-stu-id="8f79d-111">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="8f79d-112">如需詳細資訊，請參閱[部分類別和方法](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="8f79d-112">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f79d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f79d-113">See also</span></span>

- [<span data-ttu-id="8f79d-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8f79d-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8f79d-115">partial 類型</span><span class="sxs-lookup"><span data-stu-id="8f79d-115">partial type</span></span>](partial-type.md)
