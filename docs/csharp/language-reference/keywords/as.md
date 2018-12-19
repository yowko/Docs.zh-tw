---
title: as - C# 參考
ms.custom: seodec18
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 7559c24151a3c9acc79c0554112c923a23a88564
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244345"
---
# <a name="as-c-reference"></a><span data-ttu-id="d8280-102">as (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d8280-102">as (C# Reference)</span></span>
<span data-ttu-id="d8280-103">您可以使用 `as` 運算子，以在相容的參考型別或[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)之間執行特定轉換類型。</span><span class="sxs-lookup"><span data-stu-id="d8280-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="d8280-104">下列程式碼示範範例。</span><span class="sxs-lookup"><span data-stu-id="d8280-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

<span data-ttu-id="d8280-105">如範例所示，您需要將 `as` 陳述式的結果與 `null` 比較，以檢查轉換是否成功。</span><span class="sxs-lookup"><span data-stu-id="d8280-105">As the example shows, you need to compare the result of the `as` expression with `null` to check if a conversion is successful.</span></span> <span data-ttu-id="d8280-106">從 C# 7.0 開始，您可以使用 [is](is.md) 陳述式來測試轉換是否成功，以及當轉換成功時有條件地指派變數。</span><span class="sxs-lookup"><span data-stu-id="d8280-106">Beginning with C# 7.0, you can use the [is](is.md) expression both to test that a conversion succeeds and conditionally assign a variable when the conversion succeeds.</span></span> <span data-ttu-id="d8280-107">在許多情況下，這比使用 `as` 運算子更精簡。</span><span class="sxs-lookup"><span data-stu-id="d8280-107">In many scenarios, it's more concise than using the `as` operator.</span></span> <span data-ttu-id="d8280-108">如需詳細資訊，請參閱 [`is` 運算子](is.md)一文的[類型模式](is.md#type)小節。</span><span class="sxs-lookup"><span data-stu-id="d8280-108">For more information, see the [Type pattern](is.md#type) section of the [`is` operator](is.md) article.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="d8280-109">備註</span><span class="sxs-lookup"><span data-stu-id="d8280-109">Remarks</span></span>  
 <span data-ttu-id="d8280-110">`as` 運算子就像轉型運算。</span><span class="sxs-lookup"><span data-stu-id="d8280-110">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="d8280-111">不過，如果無法進行轉換，則 `as` 會傳回 `null`，而不是引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d8280-111">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="d8280-112">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="d8280-112">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="d8280-113">這個程式碼相當於下列運算式，差異在於只會評估 `expression` 變數一次。</span><span class="sxs-lookup"><span data-stu-id="d8280-113">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="d8280-114">請注意，`as` 運算子只會執行參考轉換、可為 Null 的轉換以及 Boxing 轉換。</span><span class="sxs-lookup"><span data-stu-id="d8280-114">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="d8280-115">`as` 運算子無法執行其他轉換，例如使用者定義的轉換，就應該改為使用轉換運算式來執行。</span><span class="sxs-lookup"><span data-stu-id="d8280-115">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8280-116">範例</span><span class="sxs-lookup"><span data-stu-id="d8280-116">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="d8280-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d8280-117">C# Language Specification</span></span>  

<span data-ttu-id="d8280-118">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [as 運算子](~/_csharplang/spec/expressions.md#the-as-operator)。</span><span class="sxs-lookup"><span data-stu-id="d8280-118">For more information, see [The as operator](~/_csharplang/spec/expressions.md#the-as-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="d8280-119">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="d8280-119">The language specification is the definitive source for C# syntax and usage.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="d8280-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8280-120">See Also</span></span>  
- [<span data-ttu-id="d8280-121">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d8280-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="d8280-122">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d8280-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d8280-123">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d8280-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="d8280-124">is</span><span class="sxs-lookup"><span data-stu-id="d8280-124">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="d8280-125">?:運算子</span><span class="sxs-lookup"><span data-stu-id="d8280-125">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
- [<span data-ttu-id="d8280-126">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="d8280-126">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
