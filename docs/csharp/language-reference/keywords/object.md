---
title: object (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 67eaf7f1fd2f01e433395ed21701c3b7fad7c7b4
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199247"
---
# <a name="object-c-reference"></a><span data-ttu-id="c1e24-102">object (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c1e24-102">object (C# Reference)</span></span>
<span data-ttu-id="c1e24-103">`object` 類型是 <xref:System.Object> 在 .NET Framework 中的別名。</span><span class="sxs-lookup"><span data-stu-id="c1e24-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="c1e24-104">在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="c1e24-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="c1e24-105">您可以將任何型別的值指派給 `object` 型別的變數。</span><span class="sxs-lookup"><span data-stu-id="c1e24-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="c1e24-106">當實值型別的變數轉換成物件時，即稱之為 *Boxed*。</span><span class="sxs-lookup"><span data-stu-id="c1e24-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="c1e24-107">當型別物件的變數轉換成實值型別時，即稱之為 *Unboxed*。</span><span class="sxs-lookup"><span data-stu-id="c1e24-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="c1e24-108">如需詳細資訊，請參閱 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)。</span><span class="sxs-lookup"><span data-stu-id="c1e24-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1e24-109">範例</span><span class="sxs-lookup"><span data-stu-id="c1e24-109">Example</span></span>  
 <span data-ttu-id="c1e24-110">以下範例示範 `object` 類型的變數如何接受任何資料類型的值，以及 `object` 類型的變數如何從 .NET Framework 對 <xref:System.Object> 使用方法。</span><span class="sxs-lookup"><span data-stu-id="c1e24-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c1e24-111">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c1e24-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c1e24-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="c1e24-112">See Also</span></span>  
 [<span data-ttu-id="c1e24-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c1e24-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c1e24-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c1e24-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c1e24-115">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c1e24-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c1e24-116">參考型別</span><span class="sxs-lookup"><span data-stu-id="c1e24-116">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="c1e24-117">實值型別</span><span class="sxs-lookup"><span data-stu-id="c1e24-117">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
