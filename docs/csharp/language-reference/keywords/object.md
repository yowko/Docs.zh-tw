---
title: "object (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
dev_langs:
- CSharp
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 16
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
ms.openlocfilehash: 1ad59a058fe87aa76acbf3f6c63c186a47753ad4
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="object-c-reference"></a><span data-ttu-id="84f32-102">object (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="84f32-102">object (C# Reference)</span></span>
<span data-ttu-id="84f32-103">`object` 型別在 .NET Framework 中是 <xref:System.Object> 的別名。</span><span class="sxs-lookup"><span data-stu-id="84f32-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="84f32-104">在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="84f32-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="84f32-105">您可以將任何型別的值指派給 `object` 型別的變數。</span><span class="sxs-lookup"><span data-stu-id="84f32-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="84f32-106">當實值型別的變數轉換成物件時，即稱之為 *Boxed*。</span><span class="sxs-lookup"><span data-stu-id="84f32-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="84f32-107">當型別物件的變數轉換成實值型別時，即稱之為 *Unboxed*。</span><span class="sxs-lookup"><span data-stu-id="84f32-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="84f32-108">如需詳細資訊，請參閱 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)。</span><span class="sxs-lookup"><span data-stu-id="84f32-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="84f32-109">範例</span><span class="sxs-lookup"><span data-stu-id="84f32-109">Example</span></span>  
 <span data-ttu-id="84f32-110">以下範例示範 `object` 型別的變數如何接受任何資料類型的值，以及 `object` 型別的變數如何從 .NET Framework 對 <xref:System.Object> 使用方法。</span><span class="sxs-lookup"><span data-stu-id="84f32-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 <span data-ttu-id="84f32-111">[!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="84f32-111">[!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="84f32-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="84f32-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="84f32-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84f32-113">See Also</span></span>  
 <span data-ttu-id="84f32-114">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="84f32-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="84f32-115"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="84f32-115"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="84f32-116"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="84f32-116"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="84f32-117"> [參考型別](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="84f32-117"> [Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
<span data-ttu-id="84f32-118"> [實值型別](../../../csharp/language-reference/keywords/value-types.md)</span><span class="sxs-lookup"><span data-stu-id="84f32-118"> [Value Types](../../../csharp/language-reference/keywords/value-types.md)</span></span>
