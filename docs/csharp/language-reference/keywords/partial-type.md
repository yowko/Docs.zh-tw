---
title: "partial (類型) (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
caps.latest.revision: 24
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
ms.openlocfilehash: 5405455d933f6512cfa3a18e1a545556c5715151
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="partial-type-c-reference"></a><span data-ttu-id="3d16b-102">partial (類型) (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3d16b-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="3d16b-103">部分型別定義允許將類別、結構或介面定義分割成多個檔案。</span><span class="sxs-lookup"><span data-stu-id="3d16b-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="3d16b-104">在 File1.cs 中：</span><span class="sxs-lookup"><span data-stu-id="3d16b-104">In File1.cs:</span></span>  
  
 <span data-ttu-id="3d16b-105">[!code-cs[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3d16b-105">[!code-cs[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]</span></span>  
  
 <span data-ttu-id="3d16b-106">在 File2.cs 中宣告︰</span><span class="sxs-lookup"><span data-stu-id="3d16b-106">In File2.cs the declaration:</span></span>  
  
 <span data-ttu-id="3d16b-107">[!code-cs[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="3d16b-107">[!code-cs[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d16b-108">備註</span><span class="sxs-lookup"><span data-stu-id="3d16b-108">Remarks</span></span>  
 <span data-ttu-id="3d16b-109">將類別、結構或介面型別分割成數個檔案在處理大型專案，或者處理自動產生的程式碼，例如 [Windows Forms 設計工具](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15)提供的程式碼時，會很有用。</span><span class="sxs-lookup"><span data-stu-id="3d16b-109">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).</span></span> <span data-ttu-id="3d16b-110">部分類別可包含[部分方法](../../../csharp/language-reference/keywords/partial-method.md)。</span><span class="sxs-lookup"><span data-stu-id="3d16b-110">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="3d16b-111">如需詳細資訊，請參閱[部分類別與方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="3d16b-111">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3d16b-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3d16b-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d16b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d16b-113">See Also</span></span>  
 <span data-ttu-id="3d16b-114">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="3d16b-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="3d16b-115">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3d16b-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="3d16b-116">[修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="3d16b-116">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="3d16b-117">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="3d16b-117">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)

