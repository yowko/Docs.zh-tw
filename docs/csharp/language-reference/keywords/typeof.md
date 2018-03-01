---
title: "typeof (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: be24740ea7f6fbe8780dd9cac58b7dea9aaf6872
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-c-reference"></a><span data-ttu-id="46ee5-102">typeof (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="46ee5-102">typeof (C# Reference)</span></span>
<span data-ttu-id="46ee5-103">用來取得類型的 `System.Type` 物件。</span><span class="sxs-lookup"><span data-stu-id="46ee5-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="46ee5-104">`typeof` 運算式有下列形式：</span><span class="sxs-lookup"><span data-stu-id="46ee5-104">A `typeof` expression takes the following form:</span></span>  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="46ee5-105">備註</span><span class="sxs-lookup"><span data-stu-id="46ee5-105">Remarks</span></span>  
 <span data-ttu-id="46ee5-106">若要取得運算式的執行階段類型，您可以使用 .NET Framework 方法 <xref:System.Object.GetType%2A>，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="46ee5-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="46ee5-107">`typeof` 運算子無法多載。</span><span class="sxs-lookup"><span data-stu-id="46ee5-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="46ee5-108">`typeof` 運算子也可以用於開放式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="46ee5-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="46ee5-109">在規格中，具有多個型別參數的類型必須具有適當數目的逗號。</span><span class="sxs-lookup"><span data-stu-id="46ee5-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="46ee5-110">下列範例示範如何判斷方法的傳回型別是否為泛型 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="46ee5-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="46ee5-111">假設方法是 MethodInfo 類型的執行個體︰</span><span class="sxs-lookup"><span data-stu-id="46ee5-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="46ee5-112">範例</span><span class="sxs-lookup"><span data-stu-id="46ee5-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="46ee5-113">範例</span><span class="sxs-lookup"><span data-stu-id="46ee5-113">Example</span></span>  
 <span data-ttu-id="46ee5-114">這個範例使用 <xref:System.Object.GetType%2A> 方法，判斷用來包含數值計算結果的類型。</span><span class="sxs-lookup"><span data-stu-id="46ee5-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="46ee5-115">這取決於所產生數字的儲存需求。</span><span class="sxs-lookup"><span data-stu-id="46ee5-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="46ee5-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="46ee5-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="46ee5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46ee5-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="46ee5-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="46ee5-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="46ee5-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="46ee5-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="46ee5-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="46ee5-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="46ee5-121">is</span><span class="sxs-lookup"><span data-stu-id="46ee5-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="46ee5-122">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="46ee5-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
