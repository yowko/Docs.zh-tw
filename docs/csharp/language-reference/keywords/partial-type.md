---
title: partial (類型) (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5212984cc577ce05fc4697e0d648fb5545528562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="91288-102">partial (類型) (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="91288-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="91288-103">部分型別定義允許將類別、結構或介面定義分割成多個檔案。</span><span class="sxs-lookup"><span data-stu-id="91288-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="91288-104">在 File1.cs 中：</span><span class="sxs-lookup"><span data-stu-id="91288-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="91288-105">在 File2.cs 中宣告︰</span><span class="sxs-lookup"><span data-stu-id="91288-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="91288-106">備註</span><span class="sxs-lookup"><span data-stu-id="91288-106">Remarks</span></span>  
 <span data-ttu-id="91288-107">將類別、結構或介面型別分割成數個檔案在處理大型專案，或者處理自動產生的程式碼，例如 [Windows Forms 設計工具](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)提供的程式碼時，會很有用。</span><span class="sxs-lookup"><span data-stu-id="91288-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="91288-108">部分類別可包含[部分方法](../../../csharp/language-reference/keywords/partial-method.md)。</span><span class="sxs-lookup"><span data-stu-id="91288-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="91288-109">如需詳細資訊，請參閱[部分類別與方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="91288-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="91288-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="91288-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="91288-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91288-111">See Also</span></span>  
 [<span data-ttu-id="91288-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="91288-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="91288-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="91288-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="91288-114">修飾詞</span><span class="sxs-lookup"><span data-stu-id="91288-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="91288-115">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="91288-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
