---
title: In （泛型修飾詞）-Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 9c0f7d454767112e1e309af81407b5fdef22eee9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004877"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="3fa4d-102">In (泛型修飾詞) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fa4d-102">In (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="3fa4d-103">若為泛型型別參數，`In` 關鍵字會指定型別參數是 Contravariant。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="3fa4d-104">備註</span><span class="sxs-lookup"><span data-stu-id="3fa4d-104">Remarks</span></span>

<span data-ttu-id="3fa4d-105">反變數可讓您使用比泛型參數指定的衍生程度更低的衍生類型。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="3fa4d-106">這可隱含轉換實作 Variant 介面的類別和隱含轉換委派型別。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="3fa4d-107">如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數 (C# 和 Visual Basic))。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="3fa4d-108">規則</span><span class="sxs-lookup"><span data-stu-id="3fa4d-108">Rules</span></span>

<span data-ttu-id="3fa4d-109">您可以在泛型介面及委派中使用 `In` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>
  
<span data-ttu-id="3fa4d-110">如果型別參數僅做為方法引數的型別，而不當做方法的傳回型別使用，則可以在泛型介面或委派中宣告為逆變。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="3fa4d-111">`ByRef` 參數不可以是協變數或逆變性。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>

<span data-ttu-id="3fa4d-112">參考型別支援共變數和反變數，而實數值型別則不支援。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>

<span data-ttu-id="3fa4d-113">在 Visual Basic 中，您不能在不指定委派類型的情況下，于逆變性介面中宣告事件。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="3fa4d-114">此外，逆變性介面不能有嵌套的類別、列舉或結構，但它們可以有嵌套介面。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="3fa4d-115">行為</span><span class="sxs-lookup"><span data-stu-id="3fa4d-115">Behavior</span></span>

<span data-ttu-id="3fa4d-116">具有 Contravariant 型別參數的介面可讓其方法接受衍生程度低於介面型別參數指定之衍生類型的引數。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="3fa4d-117">例如，因為在 .NET Framework 4 中，在 <xref:System.Collections.Generic.IComparer%601> 介面中，類型 T 是逆變的，您可以將 `IComparer(Of Person)` 類型的物件指派給 `IComparer(Of Employee)` 類型的物件，而不需使用任何特殊轉換方法（如果 `Employee` 繼承自 `Person`）。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits from `Person`.</span></span>

<span data-ttu-id="3fa4d-118">您可以將類型相同但具有衍生程度較低之泛型型別參數的另一個委派指派給 Contravariant 委派。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

## <a name="example---contravariant-generic-interface"></a><span data-ttu-id="3fa4d-119">範例-逆變性泛型介面</span><span class="sxs-lookup"><span data-stu-id="3fa4d-119">Example - contravariant generic interface</span></span>

<span data-ttu-id="3fa4d-120">下例範例示範如何宣告、擴充及實作 Contravariant 泛型介面。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="3fa4d-121">它也會示範如何針對實作此介面的類別使用隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a><span data-ttu-id="3fa4d-122">範例-逆變性泛型委派</span><span class="sxs-lookup"><span data-stu-id="3fa4d-122">Example - contravariant generic delegate</span></span>

<span data-ttu-id="3fa4d-123">下例範例示範如何宣告、具現化及叫用 Contravariant 泛型委派。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="3fa4d-124">它也會示範如何以隱含方式轉換委派類型。</span><span class="sxs-lookup"><span data-stu-id="3fa4d-124">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="3fa4d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fa4d-125">See also</span></span>

- [<span data-ttu-id="3fa4d-126">泛型介面中的變異數</span><span class="sxs-lookup"><span data-stu-id="3fa4d-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="3fa4d-127">Out</span><span class="sxs-lookup"><span data-stu-id="3fa4d-127">Out</span></span>](out-generic-modifier.md)
