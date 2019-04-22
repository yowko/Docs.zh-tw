---
title: Key (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: e13a773f0b585a5c8803a77c7aaad441d90dfe75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842300"
---
# <a name="key-visual-basic"></a><span data-ttu-id="60e96-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60e96-102">Key (Visual Basic)</span></span>
<span data-ttu-id="60e96-103">`Key`關鍵字可讓您指定之屬性的匿名型別行為。</span><span class="sxs-lookup"><span data-stu-id="60e96-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="60e96-104">只有屬性指定為索引鍵屬性中的匿名型別執行個體或計算的雜湊程式碼的值之間的等號比較測試。</span><span class="sxs-lookup"><span data-stu-id="60e96-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="60e96-105">無法變更索引鍵屬性的值。</span><span class="sxs-lookup"><span data-stu-id="60e96-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="60e96-106">您將匿名類型的屬性指定為索引鍵屬性上加上關鍵字`Key`前面其宣告的初始化清單中。</span><span class="sxs-lookup"><span data-stu-id="60e96-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="60e96-107">在下列範例中，`Airline`並`FlightNo`是索引鍵屬性，但`Gate`不是。</span><span class="sxs-lookup"><span data-stu-id="60e96-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="60e96-108">建立新的匿名型別時，它會直接繼承<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="60e96-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="60e96-109">編譯器會覆寫三個繼承的成員： <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。</span><span class="sxs-lookup"><span data-stu-id="60e96-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="60e96-110">產生的覆寫程式碼<xref:System.Object.Equals%2A>和<xref:System.Object.GetHashCode%2A>根據索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="60e96-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="60e96-111">如果類型中沒有索引鍵屬性<xref:System.Object.GetHashCode%2A>和<xref:System.Object.Equals%2A>不會覆寫。</span><span class="sxs-lookup"><span data-stu-id="60e96-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="60e96-112">相等</span><span class="sxs-lookup"><span data-stu-id="60e96-112">Equality</span></span>  
 <span data-ttu-id="60e96-113">兩個匿名型別執行個體相等，如果它們是相同類型的執行個體，而且其索引鍵屬性的值是否相等。</span><span class="sxs-lookup"><span data-stu-id="60e96-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="60e96-114">在下列範例中，`flight2`等於`flight1`上一個範例中因為它們是執行個體的相同匿名型別，而且它們有相符的索引鍵屬性的值。</span><span class="sxs-lookup"><span data-stu-id="60e96-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="60e96-115">不過，`flight3`不等於`flight1`因為它有不同的值，針對索引鍵的屬性， `FlightNo`。</span><span class="sxs-lookup"><span data-stu-id="60e96-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="60e96-116">執行個體`flight4`不是相同的型別`flight1`因為它們將不同的屬性指定為索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="60e96-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="60e96-117">只有非索引鍵屬性，相同的名稱、 類型、 順序和值，以宣告兩個執行個體的兩個執行個體不相等。</span><span class="sxs-lookup"><span data-stu-id="60e96-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="60e96-118">沒有索引鍵屬性的執行個體等於只有本身。</span><span class="sxs-lookup"><span data-stu-id="60e96-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="60e96-119">如需詳細的條件下這兩個匿名型別執行個體有相同匿名型別的執行個體的詳細資訊，請參閱[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="60e96-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="60e96-120">計算雜湊程式碼</span><span class="sxs-lookup"><span data-stu-id="60e96-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="60e96-121">像是<xref:System.Object.Equals%2A>，定義於雜湊函式<xref:System.Object.GetHashCode%2A>匿名型別是根據索引鍵屬性的型別。</span><span class="sxs-lookup"><span data-stu-id="60e96-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="60e96-122">下列範例顯示程式碼值的雜湊索引鍵屬性之間的互動。</span><span class="sxs-lookup"><span data-stu-id="60e96-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="60e96-123">具有所有索引鍵屬性的相同值的匿名型別執行個體中將有相同的雜湊碼值，即使非索引鍵屬性沒有相符的值。</span><span class="sxs-lookup"><span data-stu-id="60e96-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="60e96-124">下列陳述式會傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="60e96-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="60e96-125">匿名類型的一或多個索引鍵屬性的值不同的執行個體具有不同的雜湊碼值。</span><span class="sxs-lookup"><span data-stu-id="60e96-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="60e96-126">下列陳述式會傳回`False`。</span><span class="sxs-lookup"><span data-stu-id="60e96-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="60e96-127">將不同的屬性指定為索引鍵屬性的匿名型別的執行個體不是相同類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="60e96-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="60e96-128">名稱和值的所有屬性都相同，即使具有不同的雜湊程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="60e96-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="60e96-129">下列陳述式會傳回`False`。</span><span class="sxs-lookup"><span data-stu-id="60e96-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="60e96-130">唯讀的值</span><span class="sxs-lookup"><span data-stu-id="60e96-130">Read-Only Values</span></span>  
 <span data-ttu-id="60e96-131">無法變更索引鍵屬性的值。</span><span class="sxs-lookup"><span data-stu-id="60e96-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="60e96-132">例如，在`flight1`在先前範例中，`Airline`並`FlightNo`欄位是唯讀的但`Gate`可以變更。</span><span class="sxs-lookup"><span data-stu-id="60e96-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="60e96-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60e96-133">See also</span></span>

- [<span data-ttu-id="60e96-134">匿名類型定義</span><span class="sxs-lookup"><span data-stu-id="60e96-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="60e96-135">如何：推斷屬性名稱和匿名類型宣告中的類型</span><span class="sxs-lookup"><span data-stu-id="60e96-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="60e96-136">匿名類型</span><span class="sxs-lookup"><span data-stu-id="60e96-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
