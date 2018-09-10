---
title: typeof (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 2493e78fd0782eebee17afd979e1c429339d0a3f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529204"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="2986b-102">typeof (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2986b-102">typeof (C# Reference)</span></span>
<span data-ttu-id="2986b-103">用來取得類型的 `System.Type` 物件。</span><span class="sxs-lookup"><span data-stu-id="2986b-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="2986b-104">`typeof` 運算式有下列形式：</span><span class="sxs-lookup"><span data-stu-id="2986b-104">A `typeof` expression takes the following form:</span></span>  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="2986b-105">備註</span><span class="sxs-lookup"><span data-stu-id="2986b-105">Remarks</span></span>  
 <span data-ttu-id="2986b-106">若要取得運算式的執行階段類型，您可以使用 .NET Framework 方法 <xref:System.Object.GetType%2A>，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="2986b-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="2986b-107">無法多載 `typeof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="2986b-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="2986b-108">`typeof` 運算子也可以用於開放式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="2986b-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="2986b-109">在規格中，具有多個型別參數的類型必須具有適當數目的逗號。</span><span class="sxs-lookup"><span data-stu-id="2986b-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="2986b-110">下列範例示範如何判斷方法的傳回型別是否為泛型 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="2986b-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="2986b-111">如果傳回型別不是 <xref:System.Collections.Generic.IEnumerable%601> 泛型型別，<xref:System.Type.GetInterface%2A?displayProperty=nameWithType> 會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="2986b-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>
  
 [!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]   
  
## <a name="example"></a><span data-ttu-id="2986b-112">範例</span><span class="sxs-lookup"><span data-stu-id="2986b-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="2986b-113">範例</span><span class="sxs-lookup"><span data-stu-id="2986b-113">Example</span></span>  
 <span data-ttu-id="2986b-114">這個範例使用 <xref:System.Object.GetType%2A> 方法，判斷用來包含數值計算結果的類型。</span><span class="sxs-lookup"><span data-stu-id="2986b-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="2986b-115">這取決於所產生數字的儲存需求。</span><span class="sxs-lookup"><span data-stu-id="2986b-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2986b-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2986b-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2986b-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="2986b-117">See Also</span></span>

- <xref:System.Type?displayProperty=nameWithType>  
- [<span data-ttu-id="2986b-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2986b-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2986b-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2986b-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2986b-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="2986b-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="2986b-121">is</span><span class="sxs-lookup"><span data-stu-id="2986b-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="2986b-122">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="2986b-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
