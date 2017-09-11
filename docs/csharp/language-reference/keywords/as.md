---
title: "as (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7a55c696ac295eee8d5d35ed56038f3c4a90b215
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="as-c-reference"></a><span data-ttu-id="6db96-102">as (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6db96-102">as (C# Reference)</span></span>
<span data-ttu-id="6db96-103">您可以使用 `as` 運算子，以在相容的參考型別或[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)之間執行特定轉換類型。</span><span class="sxs-lookup"><span data-stu-id="6db96-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="6db96-104">下列程式碼示範範例。</span><span class="sxs-lookup"><span data-stu-id="6db96-104">The following code shows an example.</span></span>  
  
 <span data-ttu-id="6db96-105">[!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6db96-105">[!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6db96-106">備註</span><span class="sxs-lookup"><span data-stu-id="6db96-106">Remarks</span></span>  
 <span data-ttu-id="6db96-107">`as` 運算子就像轉型運算。</span><span class="sxs-lookup"><span data-stu-id="6db96-107">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="6db96-108">不過，如果無法進行轉換，則 `as` 會傳回 `null`，而不是引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6db96-108">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="6db96-109">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="6db96-109">Consider the following example:</span></span>  
  
```  
expression as type  
```  
  
 <span data-ttu-id="6db96-110">這個程式碼相當於下列運算式，差異在於只會評估 `expression` 變數一次。</span><span class="sxs-lookup"><span data-stu-id="6db96-110">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="6db96-111">請注意，`as` 運算子只會執行參考轉換、可為 Null 的轉換以及 Boxing 轉換。</span><span class="sxs-lookup"><span data-stu-id="6db96-111">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="6db96-112">`as` 運算子無法執行其他轉換，例如使用者定義的轉換，就應該改為使用轉換運算式來執行。</span><span class="sxs-lookup"><span data-stu-id="6db96-112">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6db96-113">範例</span><span class="sxs-lookup"><span data-stu-id="6db96-113">Example</span></span>  
 <span data-ttu-id="6db96-114">[!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6db96-114">[!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6db96-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6db96-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6db96-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6db96-116">See Also</span></span>  
 <span data-ttu-id="6db96-117">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6db96-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6db96-118">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6db96-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6db96-119">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="6db96-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="6db96-120">[is](../../../csharp/language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="6db96-120">[is](../../../csharp/language-reference/keywords/is.md) </span></span>  
 <span data-ttu-id="6db96-121">[?: 運算子](../../../csharp/language-reference/operators/conditional-operator.md) </span><span class="sxs-lookup"><span data-stu-id="6db96-121">[?: Operator](../../../csharp/language-reference/operators/conditional-operator.md) </span></span>  
 [<span data-ttu-id="6db96-122">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="6db96-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)

