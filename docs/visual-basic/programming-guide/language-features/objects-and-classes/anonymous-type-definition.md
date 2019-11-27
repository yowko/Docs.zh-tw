---
title: 匿名型別定義
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: f8ac26577a7fbef865605a7ecf643fa733b2c2c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344921"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="f4063-102">匿名類型定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4063-102">Anonymous Type Definition (Visual Basic)</span></span>

<span data-ttu-id="f4063-103">為了回應匿名型別的實例宣告，編譯器會建立新的類別定義，其中包含型別的指定屬性。</span><span class="sxs-lookup"><span data-stu-id="f4063-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="f4063-104">編譯器產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="f4063-104">Compiler-Generated Code</span></span>

<span data-ttu-id="f4063-105">針對 `product`的下列定義，編譯器會建立新的類別定義，其中包含 `Name`、`Price`和 `OnHand`的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4063-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

<span data-ttu-id="f4063-106">類別定義包含如下所示的屬性定義。</span><span class="sxs-lookup"><span data-stu-id="f4063-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="f4063-107">請注意，索引鍵屬性沒有 `Set` 方法。</span><span class="sxs-lookup"><span data-stu-id="f4063-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="f4063-108">索引鍵屬性的值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="f4063-108">The values of key properties are read-only.</span></span>

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

<span data-ttu-id="f4063-109">此外，匿名型別定義包含無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="f4063-109">In addition, anonymous type definitions contain a parameterless constructor.</span></span> <span data-ttu-id="f4063-110">不允許需要參數的函式。</span><span class="sxs-lookup"><span data-stu-id="f4063-110">Constructors that require parameters are not permitted.</span></span>

<span data-ttu-id="f4063-111">如果匿名型別宣告至少包含一個索引鍵屬性，則型別定義會覆寫三個繼承自 <xref:System.Object>的成員： <xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A>和 <xref:System.Object.ToString%2A>。</span><span class="sxs-lookup"><span data-stu-id="f4063-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="f4063-112">如果未宣告任何索引鍵屬性，則只會覆寫 <xref:System.Object.ToString%2A>。</span><span class="sxs-lookup"><span data-stu-id="f4063-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="f4063-113">覆寫會提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="f4063-113">The overrides provide the following functionality:</span></span>

- <span data-ttu-id="f4063-114">如果兩個匿名型別實例是相同的實例，或如果符合下列條件，`Equals` 會傳回 `True`：</span><span class="sxs-lookup"><span data-stu-id="f4063-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>

  - <span data-ttu-id="f4063-115">它們具有相同數目的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4063-115">They have the same number of properties.</span></span>

  - <span data-ttu-id="f4063-116">屬性會以相同的順序宣告，並具有相同的名稱和相同的推斷類型。</span><span class="sxs-lookup"><span data-stu-id="f4063-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="f4063-117">名稱比較不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f4063-117">Name comparisons are not case-sensitive.</span></span>

  - <span data-ttu-id="f4063-118">至少其中一個屬性是索引鍵屬性，而且 `Key` 關鍵字會套用至相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4063-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>

  - <span data-ttu-id="f4063-119">比較每個對應的索引鍵屬性會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="f4063-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>

    <span data-ttu-id="f4063-120">例如，在下列範例中，`Equals` 只會傳回 `employee01` 和 `employee08`的 `True`。</span><span class="sxs-lookup"><span data-stu-id="f4063-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="f4063-121">每一行的批註會指定新實例不符合 `employee01`的原因。</span><span class="sxs-lookup"><span data-stu-id="f4063-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- <span data-ttu-id="f4063-122">`GetHashcode` 提供適當的唯一 GetHashCode 演算法。</span><span class="sxs-lookup"><span data-stu-id="f4063-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="f4063-123">演算法只會使用索引鍵屬性來計算雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="f4063-123">The algorithm uses only the key properties to compute the hash code.</span></span>

- <span data-ttu-id="f4063-124">`ToString` 會傳回串連屬性值的字串，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f4063-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="f4063-125">同時包含索引鍵和非索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="f4063-125">Both key and non-key properties are included.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

<span data-ttu-id="f4063-126">匿名型別的明確命名屬性不能與這些產生的方法衝突。</span><span class="sxs-lookup"><span data-stu-id="f4063-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="f4063-127">也就是說，您無法使用 `.Equals`、`.GetHashCode`或 `.ToString` 來命名屬性。</span><span class="sxs-lookup"><span data-stu-id="f4063-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>

<span data-ttu-id="f4063-128">包含至少一個索引鍵屬性的匿名型別定義也會執行 <xref:System.IEquatable%601?displayProperty=nameWithType> 介面，其中 `T` 是匿名型別的型別。</span><span class="sxs-lookup"><span data-stu-id="f4063-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>

> [!NOTE]
> <span data-ttu-id="f4063-129">匿名型別宣告只有在相同的元件中發生時，才會建立相同的匿名型別、其屬性具有相同的名稱和相同的推斷類型、屬性是以相同的順序宣告，而且相同的屬性會標示為索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="f4063-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4063-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4063-130">See also</span></span>

- [<span data-ttu-id="f4063-131">匿名類型</span><span class="sxs-lookup"><span data-stu-id="f4063-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="f4063-132">如何：在匿名類型宣告中推斷屬性名稱和類型</span><span class="sxs-lookup"><span data-stu-id="f4063-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
