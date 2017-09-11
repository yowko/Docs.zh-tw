---
title: "in (泛型修飾詞) (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: 17
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
ms.openlocfilehash: 893e3c58f5b20329916bb9d289f0bd4ac90286a2
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="60ada-102">in (泛型修飾詞) (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="60ada-102">in (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="60ada-103">若為泛型型別參數，`in` 關鍵字會指定型別參數是 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="60ada-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="60ada-104">您可以在泛型介面及委派中使用 `in` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="60ada-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="60ada-105">反變數可讓您使用比泛型參數指定的衍生程度更低的衍生類型。</span><span class="sxs-lookup"><span data-stu-id="60ada-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="60ada-106">這可隱含轉換實作 variant 介面的類別和隱含轉換委派類型。</span><span class="sxs-lookup"><span data-stu-id="60ada-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="60ada-107">參考型別支援在泛型型別參數中使用共變數和反變數，但實值型別則不支援。</span><span class="sxs-lookup"><span data-stu-id="60ada-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="60ada-108">如果類型只用作方法引數類型，而不用作方法傳回型別，則可以在泛型介面或委派中宣告為 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="60ada-108">A type can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="60ada-109">`Ref` 和 `out` 參數不可以是變數。</span><span class="sxs-lookup"><span data-stu-id="60ada-109">`Ref` and `out` parameters cannot be variant.</span></span>  
  
 <span data-ttu-id="60ada-110">具有 Contravariant 型別參數的介面可讓其方法接受衍生程度低於介面型別參數指定之衍生類型的引數。</span><span class="sxs-lookup"><span data-stu-id="60ada-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="60ada-111">例如，因為在 .NET Framework 4 的 <xref:System.Collections.Generic.IComparer%601> 介面中，類型 T 是 Contravariant，所以您可以不使用任何特殊的轉換方法，將 `IComparer(Of Person)` 類型的物件指派給 `IComparer(Of Employee)` 類型的物件 (如果 `Employee` 繼承 `Person`)。</span><span class="sxs-lookup"><span data-stu-id="60ada-111">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="60ada-112">您可以將類型相同但具有衍生程度較低之泛型型別參數的另一個委派指派給 Contravariant 委派。</span><span class="sxs-lookup"><span data-stu-id="60ada-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="60ada-113">如需詳細資訊，請參閱 [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) (共變數和反變數)。</span><span class="sxs-lookup"><span data-stu-id="60ada-113">For more information, see [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60ada-114">範例</span><span class="sxs-lookup"><span data-stu-id="60ada-114">Example</span></span>  
 <span data-ttu-id="60ada-115">下例範例示範如何宣告、擴充及實作 Contravariant 泛型介面。</span><span class="sxs-lookup"><span data-stu-id="60ada-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="60ada-116">它也會示範如何針對實作此介面的類別使用隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="60ada-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 <span data-ttu-id="60ada-117">[!code-cs[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="60ada-117">[!code-cs[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="60ada-118">範例</span><span class="sxs-lookup"><span data-stu-id="60ada-118">Example</span></span>  
 <span data-ttu-id="60ada-119">下例範例示範如何宣告、具現化及叫用 Contravariant 泛型委派。</span><span class="sxs-lookup"><span data-stu-id="60ada-119">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="60ada-120">它也會示範如何以隱含方式轉換委派類型。</span><span class="sxs-lookup"><span data-stu-id="60ada-120">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 <span data-ttu-id="60ada-121">[!code-cs[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="60ada-121">[!code-cs[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="60ada-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="60ada-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="60ada-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60ada-123">See Also</span></span>  
 <span data-ttu-id="60ada-124">[out](../../../csharp/language-reference/keywords/out-generic-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="60ada-124">[out](../../../csharp/language-reference/keywords/out-generic-modifier.md) </span></span>  
<span data-ttu-id="60ada-125"> [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) (共變數和反變數) </span><span class="sxs-lookup"><span data-stu-id="60ada-125"> [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) </span></span>  
<span data-ttu-id="60ada-126"> [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)</span><span class="sxs-lookup"><span data-stu-id="60ada-126"> [Modifiers](../../../csharp/language-reference/keywords/modifiers.md)</span></span>
