---
title: params 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 089e31f3aad12c2303619e2a1998d0d6a5a0ad86
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44222392"
---
# <a name="params-c-reference"></a><span data-ttu-id="23c64-102">params (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="23c64-102">params (C# Reference)</span></span>

<span data-ttu-id="23c64-103">使用 `params` 關鍵字，您可以指定[方法參數](method-parameters.md)，其採用可變數目的引數。</span><span class="sxs-lookup"><span data-stu-id="23c64-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="23c64-104">您可以傳送在參數宣告或指定型別的引數陣列中指定的型別引數的逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="23c64-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="23c64-105">您也可以不傳送任何引數。</span><span class="sxs-lookup"><span data-stu-id="23c64-105">You also can send no arguments.</span></span> <span data-ttu-id="23c64-106">如果不傳送任何引數，`params` 清單的長度為零。</span><span class="sxs-lookup"><span data-stu-id="23c64-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="23c64-107">在方法宣告中，`params` 關鍵字後面不允許任何其他參數，而且方法宣告中只允許一個 `params` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="23c64-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="23c64-108">`params` 參數的宣告類型必須是一維陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="23c64-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="23c64-109">否則，就會發生編譯器錯誤 [CS0225](../../misc/cs0225.md)。</span><span class="sxs-lookup"><span data-stu-id="23c64-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="23c64-110">範例</span><span class="sxs-lookup"><span data-stu-id="23c64-110">Example</span></span>

<span data-ttu-id="23c64-111">下例示範將引數傳送至 `params` 參數的各種方式。</span><span class="sxs-lookup"><span data-stu-id="23c64-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a><span data-ttu-id="23c64-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="23c64-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="23c64-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23c64-113">See also</span></span>

- [<span data-ttu-id="23c64-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="23c64-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="23c64-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="23c64-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="23c64-116">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="23c64-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="23c64-117">方法參數</span><span class="sxs-lookup"><span data-stu-id="23c64-117">Method Parameters</span></span>](method-parameters.md)