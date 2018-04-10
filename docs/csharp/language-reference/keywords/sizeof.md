---
title: sizeof (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0148ae8381804ca9286315251582c8ab40778369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="17a7a-102">sizeof (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="17a7a-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="17a7a-103">用來取得 Unmanaged 類型的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="17a7a-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="17a7a-104">Unmanaged 類型包含下表所列的內建類型，也包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="17a7a-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="17a7a-105">列舉型別</span><span class="sxs-lookup"><span data-stu-id="17a7a-105">Enum types</span></span>  
  
-   <span data-ttu-id="17a7a-106">指標類型</span><span class="sxs-lookup"><span data-stu-id="17a7a-106">Pointer types</span></span>  
  
-   <span data-ttu-id="17a7a-107">未包含本身為參考類型的任何欄位或屬性的使用者定義結構</span><span class="sxs-lookup"><span data-stu-id="17a7a-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="17a7a-108">下列範例示範如何擷取 `int` 的大小：</span><span class="sxs-lookup"><span data-stu-id="17a7a-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="17a7a-109">備註</span><span class="sxs-lookup"><span data-stu-id="17a7a-109">Remarks</span></span>  
 <span data-ttu-id="17a7a-110">從 C# 2.0 版開始，將 `sizeof` 套用至內建類型不再需要使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 模式。</span><span class="sxs-lookup"><span data-stu-id="17a7a-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="17a7a-111">無法多載 `sizeof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="17a7a-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="17a7a-112">`sizeof` 運算子所傳回值的類型為 `int`。</span><span class="sxs-lookup"><span data-stu-id="17a7a-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="17a7a-113">下表所顯示的常數值會替代將特定內建類型當作運算元的 `sizeof` 運算式。</span><span class="sxs-lookup"><span data-stu-id="17a7a-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="17a7a-114">運算式</span><span class="sxs-lookup"><span data-stu-id="17a7a-114">Expression</span></span>|<span data-ttu-id="17a7a-115">常數值</span><span class="sxs-lookup"><span data-stu-id="17a7a-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="17a7a-116">1</span><span class="sxs-lookup"><span data-stu-id="17a7a-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="17a7a-117">1</span><span class="sxs-lookup"><span data-stu-id="17a7a-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="17a7a-118">2</span><span class="sxs-lookup"><span data-stu-id="17a7a-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="17a7a-119">2</span><span class="sxs-lookup"><span data-stu-id="17a7a-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="17a7a-120">4</span><span class="sxs-lookup"><span data-stu-id="17a7a-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="17a7a-121">4</span><span class="sxs-lookup"><span data-stu-id="17a7a-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="17a7a-122">8</span><span class="sxs-lookup"><span data-stu-id="17a7a-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="17a7a-123">8</span><span class="sxs-lookup"><span data-stu-id="17a7a-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="17a7a-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="17a7a-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="17a7a-125">4</span><span class="sxs-lookup"><span data-stu-id="17a7a-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="17a7a-126">8</span><span class="sxs-lookup"><span data-stu-id="17a7a-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="17a7a-127">16</span><span class="sxs-lookup"><span data-stu-id="17a7a-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="17a7a-128">1</span><span class="sxs-lookup"><span data-stu-id="17a7a-128">1</span></span>|  
  
 <span data-ttu-id="17a7a-129">對於所有其他類型 (包含結構)，`sizeof` 運算子都只能用於 unsafe 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="17a7a-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="17a7a-130">雖然您可以使用 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> 方法，但是這種方法所傳回的值不一定與 `sizeof` 所傳回的值相同。</span><span class="sxs-lookup"><span data-stu-id="17a7a-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="17a7a-131">封送處理類型之後，<xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> 會傳回大小，而 `sizeof` 會傳回 Common Language Runtime 所配置的大小，包括任何填補字元。</span><span class="sxs-lookup"><span data-stu-id="17a7a-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17a7a-132">範例</span><span class="sxs-lookup"><span data-stu-id="17a7a-132">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="17a7a-133">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="17a7a-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="17a7a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17a7a-134">See Also</span></span>  
 [<span data-ttu-id="17a7a-135">C# 參考</span><span class="sxs-lookup"><span data-stu-id="17a7a-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="17a7a-136">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="17a7a-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="17a7a-137">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="17a7a-137">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="17a7a-138">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="17a7a-138">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="17a7a-139">enum</span><span class="sxs-lookup"><span data-stu-id="17a7a-139">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
 [<span data-ttu-id="17a7a-140">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="17a7a-140">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="17a7a-141">結構</span><span class="sxs-lookup"><span data-stu-id="17a7a-141">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="17a7a-142">常數</span><span class="sxs-lookup"><span data-stu-id="17a7a-142">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)
