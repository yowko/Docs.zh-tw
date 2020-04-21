---
title: 參數陣列的參數關鍵字 - C# 引用
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738827"
---
# <a name="params-c-reference"></a><span data-ttu-id="94961-102">params (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="94961-102">params (C# Reference)</span></span>

<span data-ttu-id="94961-103">使用 `params` 關鍵字，您可以指定[方法參數](method-parameters.md)，其採用可變數目的引數。</span><span class="sxs-lookup"><span data-stu-id="94961-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="94961-104">參數類型必須是單維陣組。</span><span class="sxs-lookup"><span data-stu-id="94961-104">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="94961-105">在方法宣告中，`params` 關鍵字後面不允許任何其他參數，而且方法宣告中只允許一個 `params` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="94961-105">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="94961-106">如果`params`參數聲明的類型不是單維陣列,則會發生編譯器錯誤[CS0225。](../../misc/cs0225.md)</span><span class="sxs-lookup"><span data-stu-id="94961-106">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="94961-107">使用`params`參數呼叫方法時,可以傳遞:</span><span class="sxs-lookup"><span data-stu-id="94961-107">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="94961-108">陣列元素類型的參數的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="94961-108">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="94961-109">指定類型的參數陣列。</span><span class="sxs-lookup"><span data-stu-id="94961-109">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="94961-110">無引數。</span><span class="sxs-lookup"><span data-stu-id="94961-110">No arguments.</span></span> <span data-ttu-id="94961-111">如果不傳送任何引數，`params` 清單的長度為零。</span><span class="sxs-lookup"><span data-stu-id="94961-111">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="94961-112">範例</span><span class="sxs-lookup"><span data-stu-id="94961-112">Example</span></span>

<span data-ttu-id="94961-113">下例示範將引數傳送至 `params` 參數的各種方式。</span><span class="sxs-lookup"><span data-stu-id="94961-113">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="94961-114">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="94961-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="94961-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94961-115">See also</span></span>

- [<span data-ttu-id="94961-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="94961-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="94961-117">C# 編程指南</span><span class="sxs-lookup"><span data-stu-id="94961-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="94961-118">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="94961-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="94961-119">方法參數</span><span class="sxs-lookup"><span data-stu-id="94961-119">Method Parameters</span></span>](method-parameters.md)
