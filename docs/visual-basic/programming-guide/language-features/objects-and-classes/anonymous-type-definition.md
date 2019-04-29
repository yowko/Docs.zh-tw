---
title: 匿名類型定義 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 832d56f5c51aea87185f36ec306c3fec036a40e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780844"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="41192-102">匿名類型定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41192-102">Anonymous Type Definition (Visual Basic)</span></span>

<span data-ttu-id="41192-103">為了回應執行個體的匿名型別宣告，編譯器會建立新的類別定義，其中包含指定的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="41192-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="41192-104">編譯器產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="41192-104">Compiler-Generated Code</span></span>

<span data-ttu-id="41192-105">下列定義`product`，編譯器會建立新的類別定義，其中包含屬性`Name`， `Price`，和`OnHand`。</span><span class="sxs-lookup"><span data-stu-id="41192-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

<span data-ttu-id="41192-106">類別定義包含屬性定義如下所示。</span><span class="sxs-lookup"><span data-stu-id="41192-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="41192-107">請注意，有沒有`Set`索引鍵屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="41192-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="41192-108">索引鍵屬性的值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="41192-108">The values of key properties are read-only.</span></span>

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

<span data-ttu-id="41192-109">此外，匿名型別定義會包含預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="41192-109">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="41192-110">不允許使用需要參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="41192-110">Constructors that require parameters are not permitted.</span></span>

<span data-ttu-id="41192-111">匿名類型宣告包含至少一個索引鍵屬性，如果型別定義會覆寫三個成員繼承自<xref:System.Object>: <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。</span><span class="sxs-lookup"><span data-stu-id="41192-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="41192-112">如果沒有索引鍵的屬性宣告，只<xref:System.Object.ToString%2A>會覆寫。</span><span class="sxs-lookup"><span data-stu-id="41192-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="41192-113">覆寫提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="41192-113">The overrides provide the following functionality:</span></span>

- <span data-ttu-id="41192-114">`Equals` 傳回`True`兩個匿名型別執行個體是否相同的執行個體，或符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="41192-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>

  - <span data-ttu-id="41192-115">它們有相同數目的屬性。</span><span class="sxs-lookup"><span data-stu-id="41192-115">They have the same number of properties.</span></span>

  - <span data-ttu-id="41192-116">屬性的宣告順序相同，具有相同名稱和相同推斷的型別。</span><span class="sxs-lookup"><span data-stu-id="41192-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="41192-117">名稱比較不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="41192-117">Name comparisons are not case-sensitive.</span></span>

  - <span data-ttu-id="41192-118">至少其中一個屬性是索引鍵的屬性，而`Key`關鍵字是否套用至相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="41192-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>

  - <span data-ttu-id="41192-119">每個對應的配對的索引鍵屬性的比較會傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="41192-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>

    <span data-ttu-id="41192-120">例如，在下列範例中，`Equals`會傳回`True`僅適用於`employee01`和`employee08`。</span><span class="sxs-lookup"><span data-stu-id="41192-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="41192-121">之前每一行指定為什麼不相符的新執行個體的原因的註解`employee01`。</span><span class="sxs-lookup"><span data-stu-id="41192-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- <span data-ttu-id="41192-122">`GetHashcode` 提供適當的唯一的 GetHashCode 演算法。</span><span class="sxs-lookup"><span data-stu-id="41192-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="41192-123">此演算法會使用索引鍵的屬性，來計算雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="41192-123">The algorithm uses only the key properties to compute the hash code.</span></span>

- <span data-ttu-id="41192-124">`ToString` 傳回串連的屬性值的字串，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="41192-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="41192-125">會包含索引鍵和非索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="41192-125">Both key and non-key properties are included.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

<span data-ttu-id="41192-126">明確命名的匿名型別屬性不能與這些產生的方法衝突。</span><span class="sxs-lookup"><span data-stu-id="41192-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="41192-127">也就是說，您無法使用`.Equals`， `.GetHashCode`，或`.ToString`命名屬性。</span><span class="sxs-lookup"><span data-stu-id="41192-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>

<span data-ttu-id="41192-128">匿名類型定義，在包含至少一個索引鍵屬性也實作<xref:System.IEquatable%601?displayProperty=nameWithType>介面，其中`T`是匿名型別的型別。</span><span class="sxs-lookup"><span data-stu-id="41192-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>

> [!NOTE]
> <span data-ttu-id="41192-129">匿名類型宣告在它們出現在相同的組件、 其屬性具有相同名稱和相同推斷的型別、 屬性的宣告以相同的順序，和相同的屬性會標示為索引鍵屬性時，才可以建立相同匿名型別。</span><span class="sxs-lookup"><span data-stu-id="41192-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="41192-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41192-130">See also</span></span>

- [<span data-ttu-id="41192-131">匿名類型</span><span class="sxs-lookup"><span data-stu-id="41192-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="41192-132">如何：推斷屬性名稱和匿名類型宣告中的類型</span><span class="sxs-lookup"><span data-stu-id="41192-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
