---
description: '參數陣列的 params 關鍵字-c # 參考'
title: '參數陣列的 params 關鍵字-c # 參考'
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: a2726c725508cd297001aaabddeff414704d1115
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134467"
---
# <a name="params-c-reference"></a><span data-ttu-id="1a105-103">params (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1a105-103">params (C# Reference)</span></span>

<span data-ttu-id="1a105-104">使用 `params` 關鍵字，您可以指定[方法參數](method-parameters.md)，其採用可變數目的引數。</span><span class="sxs-lookup"><span data-stu-id="1a105-104">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="1a105-105">參數類型必須是一維陣列。</span><span class="sxs-lookup"><span data-stu-id="1a105-105">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="1a105-106">在方法宣告中，`params` 關鍵字後面不允許任何其他參數，而且方法宣告中只允許一個 `params` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1a105-106">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="1a105-107">如果參數的宣告型別 `params` 不是一維陣列，就會發生編譯器錯誤 [CS0225](../../misc/cs0225.md) 。</span><span class="sxs-lookup"><span data-stu-id="1a105-107">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="1a105-108">當您使用參數呼叫方法時 `params` ，您可以傳入：</span><span class="sxs-lookup"><span data-stu-id="1a105-108">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="1a105-109">陣列元素型別的引數清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="1a105-109">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="1a105-110">指定之類型的引數陣列。</span><span class="sxs-lookup"><span data-stu-id="1a105-110">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="1a105-111">無引數。</span><span class="sxs-lookup"><span data-stu-id="1a105-111">No arguments.</span></span> <span data-ttu-id="1a105-112">如果不傳送任何引數，`params` 清單的長度為零。</span><span class="sxs-lookup"><span data-stu-id="1a105-112">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="1a105-113">範例</span><span class="sxs-lookup"><span data-stu-id="1a105-113">Example</span></span>

<span data-ttu-id="1a105-114">下例示範將引數傳送至 `params` 參數的各種方式。</span><span class="sxs-lookup"><span data-stu-id="1a105-114">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="1a105-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1a105-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1a105-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a105-116">See also</span></span>

- [<span data-ttu-id="1a105-117">C # 參考</span><span class="sxs-lookup"><span data-stu-id="1a105-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1a105-118">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1a105-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1a105-119">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1a105-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1a105-120">方法參數</span><span class="sxs-lookup"><span data-stu-id="1a105-120">Method Parameters</span></span>](method-parameters.md)
