---
title: 傳遞參數 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 1c42ce7b258ca35d4e91e1ef28c71b60fe1f01de
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596249"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="1a430-102">傳遞參數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="1a430-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="1a430-103">在 C# 中，引數可以由傳值或傳址方式傳遞至參數。</span><span class="sxs-lookup"><span data-stu-id="1a430-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="1a430-104">以傳址方式傳遞，可讓函式成員、方法、屬性、索引子、運算子及建構函式變更參數的值，並在呼叫環境中保存該變更。</span><span class="sxs-lookup"><span data-stu-id="1a430-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="1a430-105">若要以傳址方式傳遞參數，且目的是變更該值，請使用 `ref` 或 `out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1a430-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="1a430-106">若以傳址方式傳遞之目的是不要發生複製的情況，但不變更該值，請使用 `in` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="1a430-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="1a430-107">為簡化起見，本主題的範例中只使用 `ref` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1a430-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="1a430-108">如需 `in`、`ref` 與 `out` 之間差異的詳細資訊，請參閱 [in](../../language-reference/keywords/in-parameter-modifier.md)、[ref](../../language-reference/keywords/ref.md) 和 [out](../../language-reference/keywords/out-parameter-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="1a430-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="1a430-109">下例會說明值和參考參數之間的差異。</span><span class="sxs-lookup"><span data-stu-id="1a430-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="1a430-110">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="1a430-110">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="1a430-111">傳遞實值型別參數</span><span class="sxs-lookup"><span data-stu-id="1a430-111">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="1a430-112">傳遞參考型別參數</span><span class="sxs-lookup"><span data-stu-id="1a430-112">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="1a430-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1a430-113">C# Language Specification</span></span>  

<span data-ttu-id="1a430-114">如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)中的[引數清單](~/_csharplang/spec/expressions.md#argument-lists)。</span><span class="sxs-lookup"><span data-stu-id="1a430-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="1a430-115">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="1a430-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1a430-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a430-116">See also</span></span>

- [<span data-ttu-id="1a430-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1a430-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1a430-118">方法</span><span class="sxs-lookup"><span data-stu-id="1a430-118">Methods</span></span>](./methods.md)
