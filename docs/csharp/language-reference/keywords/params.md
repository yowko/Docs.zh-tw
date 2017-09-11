---
title: "params (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5999911b96d17c710096e74c8f3da65223e778fc
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="params-c-reference"></a><span data-ttu-id="6100b-102">params (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6100b-102">params (C# Reference)</span></span>
<span data-ttu-id="6100b-103">使用 `params` 關鍵字，您可以指定[方法參數](../../../csharp/language-reference/keywords/method-parameters.md)，其採用可變數目的引數。</span><span class="sxs-lookup"><span data-stu-id="6100b-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="6100b-104">您可以傳送在參數宣告或指定型別的引數陣列中指定的型別引數的逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="6100b-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="6100b-105">您也可以不傳送任何引數。</span><span class="sxs-lookup"><span data-stu-id="6100b-105">You also can send no arguments.</span></span> <span data-ttu-id="6100b-106">如果不傳送任何引數，`params` 清單的長度為零。</span><span class="sxs-lookup"><span data-stu-id="6100b-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="6100b-107">在方法宣告中，`params` 關鍵字後面不允許任何其他參數，而且方法宣告中只允許一個 `params` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6100b-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6100b-108">範例</span><span class="sxs-lookup"><span data-stu-id="6100b-108">Example</span></span>  
 <span data-ttu-id="6100b-109">下例示範將引數傳送至 `params` 參數的各種方式。</span><span class="sxs-lookup"><span data-stu-id="6100b-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 <span data-ttu-id="6100b-110">[!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6100b-110">[!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6100b-111">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6100b-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6100b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6100b-112">See Also</span></span>  
 <span data-ttu-id="6100b-113">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6100b-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6100b-114">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6100b-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6100b-115">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="6100b-115">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="6100b-116">方法參數</span><span class="sxs-lookup"><span data-stu-id="6100b-116">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)

