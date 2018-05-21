---
title: typeof (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 4203b597d7045a13ffed9e61ddbbde57e2113c23
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="typeof-c-reference"></a><span data-ttu-id="0114a-102">typeof (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0114a-102">typeof (C# Reference)</span></span>
<span data-ttu-id="0114a-103">用來取得類型的 `System.Type` 物件。</span><span class="sxs-lookup"><span data-stu-id="0114a-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="0114a-104">`typeof` 運算式有下列形式：</span><span class="sxs-lookup"><span data-stu-id="0114a-104">A `typeof` expression takes the following form:</span></span>  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="0114a-105">備註</span><span class="sxs-lookup"><span data-stu-id="0114a-105">Remarks</span></span>  
 <span data-ttu-id="0114a-106">若要取得運算式的執行階段類型，您可以使用 .NET Framework 方法 <xref:System.Object.GetType%2A>，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="0114a-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="0114a-107">無法多載 `typeof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="0114a-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="0114a-108">`typeof` 運算子也可以用於開放式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="0114a-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="0114a-109">在規格中，具有多個型別參數的類型必須具有適當數目的逗號。</span><span class="sxs-lookup"><span data-stu-id="0114a-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="0114a-110">下列範例示範如何判斷方法的傳回型別是否為泛型 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="0114a-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="0114a-111">假設方法是 MethodInfo 類型的執行個體︰</span><span class="sxs-lookup"><span data-stu-id="0114a-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```csharp  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="0114a-112">範例</span><span class="sxs-lookup"><span data-stu-id="0114a-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="0114a-113">範例</span><span class="sxs-lookup"><span data-stu-id="0114a-113">Example</span></span>  
 <span data-ttu-id="0114a-114">這個範例使用 <xref:System.Object.GetType%2A> 方法，判斷用來包含數值計算結果的類型。</span><span class="sxs-lookup"><span data-stu-id="0114a-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="0114a-115">這取決於所產生數字的儲存需求。</span><span class="sxs-lookup"><span data-stu-id="0114a-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0114a-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0114a-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0114a-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="0114a-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="0114a-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0114a-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0114a-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0114a-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0114a-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="0114a-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0114a-121">is</span><span class="sxs-lookup"><span data-stu-id="0114a-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="0114a-122">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="0114a-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
