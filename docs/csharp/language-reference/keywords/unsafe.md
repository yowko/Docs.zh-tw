---
title: unsafe (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: b4615021a4fc3391ac0ae703b6c97301b44aa60e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191437"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="51420-102">unsafe (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="51420-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="51420-103">`unsafe` 關鍵字表示任何與指標有關的作業都需要的不安全內容。</span><span class="sxs-lookup"><span data-stu-id="51420-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="51420-104">如需詳細資訊，請參閱[不安全的程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="51420-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="51420-105">您可以在類型或成員的宣告中使用 `unsafe` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="51420-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="51420-106">類型或成員的整個文字範圍因此視為不安全內容。</span><span class="sxs-lookup"><span data-stu-id="51420-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="51420-107">例如，下列是使用 `unsafe` 修飾詞所宣告的方法︰</span><span class="sxs-lookup"><span data-stu-id="51420-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```csharp  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="51420-108">不安全內容的範圍是從參數清單延伸到方法結尾，因此也可以在參數清單中使用指標︰</span><span class="sxs-lookup"><span data-stu-id="51420-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```csharp  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="51420-109">您也可以使用不安全區塊，以在這個區塊內使用不安全程式碼。</span><span class="sxs-lookup"><span data-stu-id="51420-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="51420-110">例如: </span><span class="sxs-lookup"><span data-stu-id="51420-110">For example:</span></span>  
  
```csharp  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="51420-111">若要編譯不安全的程式碼，您必須指定 [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="51420-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="51420-112">Common Language Runtime 不會驗證不安全的程式碼。</span><span class="sxs-lookup"><span data-stu-id="51420-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51420-113">範例</span><span class="sxs-lookup"><span data-stu-id="51420-113">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="51420-114">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="51420-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="51420-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="51420-115">See Also</span></span>

- [<span data-ttu-id="51420-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="51420-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="51420-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="51420-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="51420-118">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="51420-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="51420-119">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="51420-119">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="51420-120">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="51420-120">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="51420-121">固定大小的緩衝區</span><span class="sxs-lookup"><span data-stu-id="51420-121">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
