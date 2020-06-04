---
title: 機碼
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 5b060f5fa0042dfb8ffa6876f5e172d3bcda67a3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396216"
---
# <a name="key-visual-basic"></a><span data-ttu-id="163e0-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="163e0-102">Key (Visual Basic)</span></span>
<span data-ttu-id="163e0-103">`Key`關鍵字可讓您指定匿名型別屬性的行為。</span><span class="sxs-lookup"><span data-stu-id="163e0-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="163e0-104">只有您指定為索引鍵屬性的屬性，才會參與匿名型別實例之間的相等測試，或計算雜湊碼值。</span><span class="sxs-lookup"><span data-stu-id="163e0-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="163e0-105">無法變更索引鍵屬性的值。</span><span class="sxs-lookup"><span data-stu-id="163e0-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="163e0-106">將關鍵字放 `Key` 在初始化清單中其宣告的前方，即可將匿名型別的屬性指定為索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="163e0-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="163e0-107">在下列範例中， `Airline` 和 `FlightNo` 是索引鍵屬性，但 `Gate` 不是。</span><span class="sxs-lookup"><span data-stu-id="163e0-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="163e0-108">建立新的匿名型別時，它會直接繼承自 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="163e0-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="163e0-109">編譯器會覆寫三個繼承的成員： <xref:System.Object.Equals%2A> 、 <xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.ToString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="163e0-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="163e0-110">針對和所產生的覆寫程式碼是以索引 <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> 鍵屬性為基礎。</span><span class="sxs-lookup"><span data-stu-id="163e0-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="163e0-111">如果類型中沒有索引鍵屬性， <xref:System.Object.GetHashCode%2A> 而且 <xref:System.Object.Equals%2A> 不會覆寫。</span><span class="sxs-lookup"><span data-stu-id="163e0-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="163e0-112">等式</span><span class="sxs-lookup"><span data-stu-id="163e0-112">Equality</span></span>  
 <span data-ttu-id="163e0-113">如果兩個匿名型別實例都是相同類型的實例，而且其索引鍵屬性的值相等，則兩者相等。</span><span class="sxs-lookup"><span data-stu-id="163e0-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="163e0-114">在下列範例中， `flight2` 等於 `flight1` 上一個範例中的，因為它們是相同匿名型別的實例，而且它們的索引鍵屬性具有相符的值。</span><span class="sxs-lookup"><span data-stu-id="163e0-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="163e0-115">不過， `flight3` 不等於， `flight1` 因為它的索引鍵屬性有不同的值 `FlightNo` 。</span><span class="sxs-lookup"><span data-stu-id="163e0-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="163e0-116">實例 `flight4` 的類型與相同， `flight1` 因為它們會將不同的屬性指定為索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="163e0-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="163e0-117">如果兩個實例僅使用非索引鍵屬性來宣告，則名稱、類型、順序和值都相同，這兩個實例不相等。</span><span class="sxs-lookup"><span data-stu-id="163e0-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="163e0-118">沒有索引鍵屬性的實例只等於其本身。</span><span class="sxs-lookup"><span data-stu-id="163e0-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="163e0-119">如需有關兩個匿名型別實例在相同匿名型別實例之下的條件的詳細資訊，請參閱[匿名型別](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="163e0-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="163e0-120">雜湊程式碼計算</span><span class="sxs-lookup"><span data-stu-id="163e0-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="163e0-121">就像一樣 <xref:System.Object.Equals%2A> ，在中針對匿名型別定義的雜湊函 <xref:System.Object.GetHashCode%2A> 式是以型別的索引鍵屬性為基礎。</span><span class="sxs-lookup"><span data-stu-id="163e0-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="163e0-122">下列範例會顯示索引鍵屬性與雜湊碼值之間的互動。</span><span class="sxs-lookup"><span data-stu-id="163e0-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="163e0-123">匿名型別的實例若具有相同的雜湊碼值，則所有索引鍵屬性的值都相同，即使非索引鍵屬性沒有相符的值。</span><span class="sxs-lookup"><span data-stu-id="163e0-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="163e0-124">下列陳述式會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="163e0-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="163e0-125">匿名型別的實例若具有一或多個索引鍵屬性的不同值，就會有不同的雜湊碼值。</span><span class="sxs-lookup"><span data-stu-id="163e0-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="163e0-126">下列陳述式會傳回 `False`。</span><span class="sxs-lookup"><span data-stu-id="163e0-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="163e0-127">將不同屬性指定為索引鍵屬性的匿名型別實例不是相同類型的實例。</span><span class="sxs-lookup"><span data-stu-id="163e0-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="163e0-128">即使所有屬性的名稱和值都相同，它們也有不同的雜湊碼值。</span><span class="sxs-lookup"><span data-stu-id="163e0-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="163e0-129">下列陳述式會傳回 `False`。</span><span class="sxs-lookup"><span data-stu-id="163e0-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="163e0-130">唯讀值</span><span class="sxs-lookup"><span data-stu-id="163e0-130">Read-Only Values</span></span>  
 <span data-ttu-id="163e0-131">無法變更索引鍵屬性的值。</span><span class="sxs-lookup"><span data-stu-id="163e0-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="163e0-132">例如，在 `flight1` 先前的範例中， `Airline` 和 `FlightNo` 欄位是唯讀的，但 `Gate` 可以變更。</span><span class="sxs-lookup"><span data-stu-id="163e0-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="163e0-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="163e0-133">See also</span></span>

- [<span data-ttu-id="163e0-134">匿名型別定義</span><span class="sxs-lookup"><span data-stu-id="163e0-134">Anonymous Type Definition</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="163e0-135">如何：在匿名類型宣告中推斷屬性名稱和類型</span><span class="sxs-lookup"><span data-stu-id="163e0-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="163e0-136">匿名類型</span><span class="sxs-lookup"><span data-stu-id="163e0-136">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
