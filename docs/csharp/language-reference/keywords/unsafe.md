---
title: "unsafe (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
dev_langs:
- CSharp
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
caps.latest.revision: 19
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ceba9e518caf6618cf2f457b930ce08f18273d8c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="unsafe-c-reference"></a><span data-ttu-id="34eb0-102">unsafe (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="34eb0-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="34eb0-103">`unsafe` 關鍵字表示任何與指標有關的作業都需要的不安全內容。</span><span class="sxs-lookup"><span data-stu-id="34eb0-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="34eb0-104">如需詳細資訊，請參閱[不安全的程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="34eb0-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="34eb0-105">您可以在類型或成員的宣告中使用 `unsafe` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="34eb0-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="34eb0-106">類型或成員的整個文字範圍因此視為不安全內容。</span><span class="sxs-lookup"><span data-stu-id="34eb0-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="34eb0-107">例如，下列是使用 `unsafe` 修飾詞所宣告的方法︰</span><span class="sxs-lookup"><span data-stu-id="34eb0-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="34eb0-108">不安全內容的範圍是從參數清單延伸到方法結尾，因此也可以在參數清單中使用指標︰</span><span class="sxs-lookup"><span data-stu-id="34eb0-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="34eb0-109">您也可以使用不安全區塊，以在這個區塊內使用不安全程式碼。</span><span class="sxs-lookup"><span data-stu-id="34eb0-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="34eb0-110">例如: </span><span class="sxs-lookup"><span data-stu-id="34eb0-110">For example:</span></span>  
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="34eb0-111">若要編譯不安全的程式碼，您必須指定 [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="34eb0-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="34eb0-112">Common Language Runtime 不會驗證不安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="34eb0-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34eb0-113">範例</span><span class="sxs-lookup"><span data-stu-id="34eb0-113">Example</span></span>  
 <span data-ttu-id="34eb0-114">[!code-cs[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="34eb0-114">[!code-cs[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="34eb0-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="34eb0-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="34eb0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34eb0-116">See Also</span></span>  
 <span data-ttu-id="34eb0-117">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="34eb0-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="34eb0-118">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="34eb0-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="34eb0-119">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="34eb0-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="34eb0-120">[fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="34eb0-120">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 <span data-ttu-id="34eb0-121">[不安全的程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="34eb0-121">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 [<span data-ttu-id="34eb0-122">固定大小的緩衝區</span><span class="sxs-lookup"><span data-stu-id="34eb0-122">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

