---
title: as (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: aee80b3262ccd9432d7c311dddec47185b66d05f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47216172"
---
# <a name="as-c-reference"></a><span data-ttu-id="da60d-102">as (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="da60d-102">as (C# Reference)</span></span>
<span data-ttu-id="da60d-103">您可以使用 `as` 運算子，以在相容的參考型別或[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)之間執行特定轉換類型。</span><span class="sxs-lookup"><span data-stu-id="da60d-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="da60d-104">下列程式碼示範範例。</span><span class="sxs-lookup"><span data-stu-id="da60d-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]
  
## <a name="remarks"></a><span data-ttu-id="da60d-105">備註</span><span class="sxs-lookup"><span data-stu-id="da60d-105">Remarks</span></span>  
 <span data-ttu-id="da60d-106">`as` 運算子就像轉型運算。</span><span class="sxs-lookup"><span data-stu-id="da60d-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="da60d-107">不過，如果無法進行轉換，則 `as` 會傳回 `null`，而不是引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="da60d-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="da60d-108">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="da60d-108">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="da60d-109">這個程式碼相當於下列運算式，差異在於只會評估 `expression` 變數一次。</span><span class="sxs-lookup"><span data-stu-id="da60d-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="da60d-110">請注意，`as` 運算子只會執行參考轉換、可為 Null 的轉換以及 Boxing 轉換。</span><span class="sxs-lookup"><span data-stu-id="da60d-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="da60d-111">`as` 運算子無法執行其他轉換，例如使用者定義的轉換，就應該改為使用轉換運算式來執行。</span><span class="sxs-lookup"><span data-stu-id="da60d-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da60d-112">範例</span><span class="sxs-lookup"><span data-stu-id="da60d-112">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="da60d-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="da60d-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="da60d-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="da60d-114">See Also</span></span>  
- [<span data-ttu-id="da60d-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="da60d-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="da60d-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="da60d-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="da60d-117">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="da60d-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="da60d-118">is</span><span class="sxs-lookup"><span data-stu-id="da60d-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="da60d-119">?: 運算子</span><span class="sxs-lookup"><span data-stu-id="da60d-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
- [<span data-ttu-id="da60d-120">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="da60d-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
