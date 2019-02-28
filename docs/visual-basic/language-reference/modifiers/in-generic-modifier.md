---
title: In (泛型修飾詞) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 91a0b9c1188820f8fc466ce1bb123b704fcd94b7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972506"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="9d70b-102">In (泛型修飾詞) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d70b-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="9d70b-103">若為泛型型別參數，`In` 關鍵字會指定型別參數是 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="9d70b-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d70b-104">備註</span><span class="sxs-lookup"><span data-stu-id="9d70b-104">Remarks</span></span>  
 <span data-ttu-id="9d70b-105">反變數可讓您使用比泛型參數指定的衍生程度更低的衍生類型。</span><span class="sxs-lookup"><span data-stu-id="9d70b-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="9d70b-106">這可隱含轉換實作 Variant 介面的類別和隱含轉換委派型別。</span><span class="sxs-lookup"><span data-stu-id="9d70b-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="9d70b-107">如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數 (C# 和 Visual Basic))。</span><span class="sxs-lookup"><span data-stu-id="9d70b-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9d70b-108">規則</span><span class="sxs-lookup"><span data-stu-id="9d70b-108">Rules</span></span>  
 <span data-ttu-id="9d70b-109">您可以在泛型介面及委派中使用 `In` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9d70b-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="9d70b-110">如果它是僅為方法引數的型別，不用為方法的傳回型別，類型參數可以宣告 contravariant 泛型介面或委派中。</span><span class="sxs-lookup"><span data-stu-id="9d70b-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="9d70b-111">`ByRef` 參數不可以是共變性或逆變性。</span><span class="sxs-lookup"><span data-stu-id="9d70b-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="9d70b-112">共變性與逆變性是參考型別支援和不支援的實值型別。</span><span class="sxs-lookup"><span data-stu-id="9d70b-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="9d70b-113">在 Visual Basic 中，您無法宣告 contravariant 介面中的事件，而不指定委派類型。</span><span class="sxs-lookup"><span data-stu-id="9d70b-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="9d70b-114">此外，類別、 列舉或結構，contravariant 介面不能有巢狀，但可以有巢狀介面。</span><span class="sxs-lookup"><span data-stu-id="9d70b-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9d70b-115">行為</span><span class="sxs-lookup"><span data-stu-id="9d70b-115">Behavior</span></span>  
 <span data-ttu-id="9d70b-116">具有 Contravariant 型別參數的介面可讓其方法接受衍生程度低於介面型別參數指定之衍生類型的引數。</span><span class="sxs-lookup"><span data-stu-id="9d70b-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="9d70b-117">例如，因為在 .NET Framework 4 的 <xref:System.Collections.Generic.IComparer%601> 介面中，類型 T 是 Contravariant，所以您可以不使用任何特殊的轉換方法，將 `IComparer(Of Person)` 類型的物件指派給 `IComparer(Of Employee)` 類型的物件 (如果 `Person` 繼承 `Employee`)。</span><span class="sxs-lookup"><span data-stu-id="9d70b-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="9d70b-118">您可以將類型相同但具有衍生程度較低之泛型型別參數的另一個委派指派給 Contravariant 委派。</span><span class="sxs-lookup"><span data-stu-id="9d70b-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d70b-119">範例</span><span class="sxs-lookup"><span data-stu-id="9d70b-119">Example</span></span>  
 <span data-ttu-id="9d70b-120">下例範例示範如何宣告、擴充及實作 Contravariant 泛型介面。</span><span class="sxs-lookup"><span data-stu-id="9d70b-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="9d70b-121">它也會示範如何針對實作此介面的類別使用隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="9d70b-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9d70b-122">範例</span><span class="sxs-lookup"><span data-stu-id="9d70b-122">Example</span></span>  
 <span data-ttu-id="9d70b-123">下例範例示範如何宣告、具現化及叫用 Contravariant 泛型委派。</span><span class="sxs-lookup"><span data-stu-id="9d70b-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="9d70b-124">它也會示範如何以隱含方式轉換委派類型。</span><span class="sxs-lookup"><span data-stu-id="9d70b-124">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9d70b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d70b-125">See also</span></span>
- [<span data-ttu-id="9d70b-126">泛型介面中的變異數</span><span class="sxs-lookup"><span data-stu-id="9d70b-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="9d70b-127">Out</span><span class="sxs-lookup"><span data-stu-id="9d70b-127">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
