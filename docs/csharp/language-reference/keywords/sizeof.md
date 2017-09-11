---
title: "sizeof (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
dev_langs:
- CSharp
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
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
ms.openlocfilehash: 4c9dbff5329f76f1bd86a7ebe22833fcc4ae985b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="sizeof-c-reference"></a><span data-ttu-id="f6c3f-102">sizeof (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f6c3f-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="f6c3f-103">用來取得 Unmanaged 類型的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="f6c3f-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="f6c3f-104">Unmanaged 類型包含下表所列的內建類型，也包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="f6c3f-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="f6c3f-105">列舉型別</span><span class="sxs-lookup"><span data-stu-id="f6c3f-105">Enum types</span></span>  
  
-   <span data-ttu-id="f6c3f-106">指標類型</span><span class="sxs-lookup"><span data-stu-id="f6c3f-106">Pointer types</span></span>  
  
-   <span data-ttu-id="f6c3f-107">未包含本身為參考類型的任何欄位或屬性的使用者定義結構</span><span class="sxs-lookup"><span data-stu-id="f6c3f-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="f6c3f-108">下列範例示範如何擷取 `int` 的大小：</span><span class="sxs-lookup"><span data-stu-id="f6c3f-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="f6c3f-109">備註</span><span class="sxs-lookup"><span data-stu-id="f6c3f-109">Remarks</span></span>  
 <span data-ttu-id="f6c3f-110">從 C# 2.0 版開始，將 `sizeof` 套用至內建類型不再需要使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 模式。</span><span class="sxs-lookup"><span data-stu-id="f6c3f-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="f6c3f-111">無法多載 `sizeof` 運算子。</span><span class="sxs-lookup"><span data-stu-id="f6c3f-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="f6c3f-112">`sizeof` 運算子所傳回值的類型為 `int`。</span><span class="sxs-lookup"><span data-stu-id="f6c3f-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="f6c3f-113">下表所顯示的常數值會替代將特定內建類型當作運算元的 `sizeof` 運算式。</span><span class="sxs-lookup"><span data-stu-id="f6c3f-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="f6c3f-114">運算式</span><span class="sxs-lookup"><span data-stu-id="f6c3f-114">Expression</span></span>|<span data-ttu-id="f6c3f-115">常數值</span><span class="sxs-lookup"><span data-stu-id="f6c3f-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="f6c3f-116">1</span><span class="sxs-lookup"><span data-stu-id="f6c3f-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="f6c3f-117">1</span><span class="sxs-lookup"><span data-stu-id="f6c3f-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="f6c3f-118">2</span><span class="sxs-lookup"><span data-stu-id="f6c3f-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="f6c3f-119">2</span><span class="sxs-lookup"><span data-stu-id="f6c3f-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="f6c3f-120">4</span><span class="sxs-lookup"><span data-stu-id="f6c3f-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="f6c3f-121">4</span><span class="sxs-lookup"><span data-stu-id="f6c3f-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="f6c3f-122">8</span><span class="sxs-lookup"><span data-stu-id="f6c3f-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="f6c3f-123">8</span><span class="sxs-lookup"><span data-stu-id="f6c3f-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="f6c3f-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="f6c3f-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="f6c3f-125">4</span><span class="sxs-lookup"><span data-stu-id="f6c3f-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="f6c3f-126">8</span><span class="sxs-lookup"><span data-stu-id="f6c3f-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="f6c3f-127">16</span><span class="sxs-lookup"><span data-stu-id="f6c3f-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="f6c3f-128">1</span><span class="sxs-lookup"><span data-stu-id="f6c3f-128">1</span></span>|  
  
 <span data-ttu-id="f6c3f-129">對於所有其他類型 (包含結構)，`sizeof` 運算子都只能用於 unsafe 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="f6c3f-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="f6c3f-130">雖然您可以使用 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> 方法，但是這個方法所傳回的值不一定與 `sizeof` 所傳回的值相同。</span><span class="sxs-lookup"><span data-stu-id="f6c3f-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="f6c3f-131">封送處理類型之後，<xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> 會傳回大小，而 `sizeof` 會傳回 Common Language Runtime 所配置的大小，包括任何填補字元。</span><span class="sxs-lookup"><span data-stu-id="f6c3f-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6c3f-132">範例</span><span class="sxs-lookup"><span data-stu-id="f6c3f-132">Example</span></span>  
 <span data-ttu-id="f6c3f-133">[!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f6c3f-133">[!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f6c3f-134">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f6c3f-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6c3f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6c3f-135">See Also</span></span>  
 <span data-ttu-id="f6c3f-136">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f6c3f-136">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="f6c3f-137"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f6c3f-137"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="f6c3f-138"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f6c3f-138"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="f6c3f-139"> [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="f6c3f-139"> [Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
<span data-ttu-id="f6c3f-140"> [enum](../../../csharp/language-reference/keywords/enum.md) </span><span class="sxs-lookup"><span data-stu-id="f6c3f-140"> [enum](../../../csharp/language-reference/keywords/enum.md) </span></span>  
<span data-ttu-id="f6c3f-141"> [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="f6c3f-141"> [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
<span data-ttu-id="f6c3f-142"> [結構](../../../csharp/programming-guide/classes-and-structs/structs.md) </span><span class="sxs-lookup"><span data-stu-id="f6c3f-142"> [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span></span>  
<span data-ttu-id="f6c3f-143"> [常數](../../../csharp/programming-guide/classes-and-structs/constants.md)</span><span class="sxs-lookup"><span data-stu-id="f6c3f-143"> [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md)</span></span>
