---
title: partial (類型) (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 4f57149dd18deb08aa11b72d0a6d5f71b3838bd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="e0aef-102">partial (類型) (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e0aef-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="e0aef-103">部分型別定義允許將類別、結構或介面定義分割成多個檔案。</span><span class="sxs-lookup"><span data-stu-id="e0aef-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="e0aef-104">在 File1.cs 中：</span><span class="sxs-lookup"><span data-stu-id="e0aef-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="e0aef-105">在 File2.cs 中宣告︰</span><span class="sxs-lookup"><span data-stu-id="e0aef-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="e0aef-106">備註</span><span class="sxs-lookup"><span data-stu-id="e0aef-106">Remarks</span></span>  
 <span data-ttu-id="e0aef-107">將類別、結構或介面型別分割成數個檔案在處理大型專案，或者處理自動產生的程式碼，例如 [Windows Forms 設計工具](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)提供的程式碼時，會很有用。</span><span class="sxs-lookup"><span data-stu-id="e0aef-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="e0aef-108">部分類別可包含[部分方法](../../../csharp/language-reference/keywords/partial-method.md)。</span><span class="sxs-lookup"><span data-stu-id="e0aef-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="e0aef-109">如需詳細資訊，請參閱[部分類別和方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="e0aef-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e0aef-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e0aef-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e0aef-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0aef-111">See Also</span></span>  
 [<span data-ttu-id="e0aef-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e0aef-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e0aef-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e0aef-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e0aef-114">修飾詞</span><span class="sxs-lookup"><span data-stu-id="e0aef-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="e0aef-115">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="e0aef-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
