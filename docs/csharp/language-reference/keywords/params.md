---
title: params (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: d7e0094d0f60aa201ae7229983f3e4b9764d2cbc
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960191"
---
# <a name="params-c-reference"></a><span data-ttu-id="17e74-102">params (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="17e74-102">params (C# Reference)</span></span>
<span data-ttu-id="17e74-103">使用 `params` 關鍵字，您可以指定[方法參數](../../../csharp/language-reference/keywords/method-parameters.md)，其採用可變數目的引數。</span><span class="sxs-lookup"><span data-stu-id="17e74-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="17e74-104">您可以傳送在參數宣告或指定型別的引數陣列中指定的型別引數的逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="17e74-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="17e74-105">您也可以不傳送任何引數。</span><span class="sxs-lookup"><span data-stu-id="17e74-105">You also can send no arguments.</span></span> <span data-ttu-id="17e74-106">如果不傳送任何引數，`params` 清單的長度為零。</span><span class="sxs-lookup"><span data-stu-id="17e74-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="17e74-107">在方法宣告中，`params` 關鍵字後面不允許任何其他參數，而且方法宣告中只允許一個 `params` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="17e74-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17e74-108">範例</span><span class="sxs-lookup"><span data-stu-id="17e74-108">Example</span></span>  
 <span data-ttu-id="17e74-109">下例示範將引數傳送至 `params` 參數的各種方式。</span><span class="sxs-lookup"><span data-stu-id="17e74-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="17e74-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="17e74-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="17e74-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="17e74-111">See Also</span></span>  
 [<span data-ttu-id="17e74-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="17e74-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="17e74-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="17e74-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="17e74-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="17e74-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="17e74-115">方法參數</span><span class="sxs-lookup"><span data-stu-id="17e74-115">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
