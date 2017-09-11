---
title: "void (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
dev_langs:
- CSharp
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 15
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: ce1f00c6ed10e4202602fc0b80e975effc1f52a4
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="void-c-reference"></a><span data-ttu-id="d2141-102">void (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d2141-102">void (C# Reference)</span></span>
<span data-ttu-id="d2141-103">當 `void` 作為方法的傳回型別時，其可指定方法不要傳回值。</span><span class="sxs-lookup"><span data-stu-id="d2141-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>  
  
 <span data-ttu-id="d2141-104">方法的參數清單中不允許 `void`。</span><span class="sxs-lookup"><span data-stu-id="d2141-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="d2141-105">如果某方法不採用任何參數，且不傳回任何值，其宣告方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d2141-105">A method that takes no parameters and returns no value is declared as follows:</span></span>  
  
```  
public void SampleMethod()  
{  
    // Body of the method.  
}  
```  
  
 <span data-ttu-id="d2141-106">`void` 也可用於不安全的內容中，以宣告未知類型的指標。</span><span class="sxs-lookup"><span data-stu-id="d2141-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="d2141-107">如需詳細資訊，請參閱[指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d2141-107">For more information, see [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
 <span data-ttu-id="d2141-108">`void` 是 .NET Framework <xref:System.Void?displayProperty=fullName> 類型的別名。</span><span class="sxs-lookup"><span data-stu-id="d2141-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=fullName> type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d2141-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d2141-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d2141-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2141-110">See Also</span></span>  
 <span data-ttu-id="d2141-111">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d2141-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="d2141-112"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d2141-112"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="d2141-113"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="d2141-113"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="d2141-114"> [參考型別](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="d2141-114"> [Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
<span data-ttu-id="d2141-115"> [實值型別](../../../csharp/language-reference/keywords/value-types.md) </span><span class="sxs-lookup"><span data-stu-id="d2141-115"> [Value Types](../../../csharp/language-reference/keywords/value-types.md) </span></span>  
<span data-ttu-id="d2141-116"> [方法](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="d2141-116"> [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
<span data-ttu-id="d2141-117"> [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)</span><span class="sxs-lookup"><span data-stu-id="d2141-117"> [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md)</span></span>

