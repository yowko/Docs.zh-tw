---
title: "typeof (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- typeof
- typeof_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: 21
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 2032b38f0b5e38790c81bc88e949bc486b6586bb
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="typeof-c-reference"></a><span data-ttu-id="e306d-102">typeof (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e306d-102">typeof (C# Reference)</span></span>
<span data-ttu-id="e306d-103">用來取得類型的 `System.Type` 物件。</span><span class="sxs-lookup"><span data-stu-id="e306d-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="e306d-104">`typeof` 運算式有下列形式：</span><span class="sxs-lookup"><span data-stu-id="e306d-104">A `typeof` expression takes the following form:</span></span>  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="e306d-105">備註</span><span class="sxs-lookup"><span data-stu-id="e306d-105">Remarks</span></span>  
 <span data-ttu-id="e306d-106">若要取得運算式的執行階段類型，您可以使用 .NET Framework 方法 <xref:System.Object.GetType%2A>，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="e306d-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="e306d-107">無法多載 `typeof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="e306d-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="e306d-108">`typeof` 運算子也可以用於開放式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="e306d-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="e306d-109">在規格中，具有多個型別參數的類型必須具有適當數目的逗號。</span><span class="sxs-lookup"><span data-stu-id="e306d-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="e306d-110">下列範例示範如何判斷方法的傳回型別是否為泛型 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="e306d-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="e306d-111">假設方法是 MethodInfo 類型的執行個體︰</span><span class="sxs-lookup"><span data-stu-id="e306d-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="e306d-112">範例</span><span class="sxs-lookup"><span data-stu-id="e306d-112">Example</span></span>  
 <span data-ttu-id="e306d-113">[!code-cs[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e306d-113">[!code-cs[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="e306d-114">範例</span><span class="sxs-lookup"><span data-stu-id="e306d-114">Example</span></span>  
 <span data-ttu-id="e306d-115">這個範例使用 <xref:System.Object.GetType%2A> 方法，判斷用來包含數值計算結果的類型。</span><span class="sxs-lookup"><span data-stu-id="e306d-115">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="e306d-116">這取決於所產生數字的儲存需求。</span><span class="sxs-lookup"><span data-stu-id="e306d-116">This depends on the storage requirements of the resulting number.</span></span>  
  
 <span data-ttu-id="e306d-117">[!code-cs[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e306d-117">[!code-cs[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e306d-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e306d-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e306d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e306d-119">See Also</span></span>  
 <span data-ttu-id="e306d-120"><xref:System.Type?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="e306d-120"><xref:System.Type?displayProperty=fullName></span></span>   
<span data-ttu-id="e306d-121"> [C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e306d-121"> [C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="e306d-122"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e306d-122"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="e306d-123"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="e306d-123"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="e306d-124"> [is](../../../csharp/language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="e306d-124"> [is](../../../csharp/language-reference/keywords/is.md) </span></span>  
<span data-ttu-id="e306d-125"> [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)</span><span class="sxs-lookup"><span data-stu-id="e306d-125"> [Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md)</span></span>
