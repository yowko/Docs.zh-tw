---
title: "匿名類型定義 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8b5b7eba55d719c1482b7224ecffc78b776feb00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="951e5-102">匿名類型定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="951e5-102">Anonymous Type Definition (Visual Basic)</span></span>
<span data-ttu-id="951e5-103">為了回應執行個體的匿名類型宣告，編譯器會建立新的類別定義，其中包含指定的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="951e5-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>  
  
## <a name="compiler-generated-code"></a><span data-ttu-id="951e5-104">編譯器產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="951e5-104">Compiler-Generated Code</span></span>  
 <span data-ttu-id="951e5-105">下列定義的`product`，編譯器會建立新的類別定義，其中包含屬性`Name`， `Price`，和`OnHand`。</span><span class="sxs-lookup"><span data-stu-id="951e5-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
 <span data-ttu-id="951e5-106">類別定義包含類似下列的屬性定義。</span><span class="sxs-lookup"><span data-stu-id="951e5-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="951e5-107">請注意，有任何`Set`索引鍵屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="951e5-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="951e5-108">索引鍵屬性的值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="951e5-108">The values of key properties are read-only.</span></span>  
  
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
  
 <span data-ttu-id="951e5-109">此外，匿名類型定義包含預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="951e5-109">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="951e5-110">不允許使用需要參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="951e5-110">Constructors that require parameters are not permitted.</span></span>  
  
 <span data-ttu-id="951e5-111">匿名類型宣告包含至少一個索引鍵內容，如果型別定義會覆寫繼承自的三個成員<xref:System.Object>: <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。</span><span class="sxs-lookup"><span data-stu-id="951e5-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="951e5-112">如果沒有索引鍵屬性宣告，只<xref:System.Object.ToString%2A>會覆寫。</span><span class="sxs-lookup"><span data-stu-id="951e5-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="951e5-113">覆寫中提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="951e5-113">The overrides provide the following functionality:</span></span>  
  
-   <span data-ttu-id="951e5-114">`Equals`傳回`True`兩個匿名型別執行個體是否相同的執行個體，或若符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="951e5-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>  
  
    -   <span data-ttu-id="951e5-115">它們有相同數目的屬性。</span><span class="sxs-lookup"><span data-stu-id="951e5-115">They have the same number of properties.</span></span>  
  
    -   <span data-ttu-id="951e5-116">屬性的宣告以相同的順序，使用相同的名稱和相同推斷的型別。</span><span class="sxs-lookup"><span data-stu-id="951e5-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="951e5-117">名稱比較不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="951e5-117">Name comparisons are not case-sensitive.</span></span>  
  
    -   <span data-ttu-id="951e5-118">至少其中一個屬性是索引鍵屬性，而`Key`關鍵字套用至相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="951e5-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>  
  
    -   <span data-ttu-id="951e5-119">比較每個對應的配對的索引鍵屬性會傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="951e5-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>  
  
     <span data-ttu-id="951e5-120">例如，在下列範例中，`Equals`傳回`True`僅適用於`employee01`和`employee08`。</span><span class="sxs-lookup"><span data-stu-id="951e5-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="951e5-121">之前的每一行指定為什麼不相符的新執行個體的原因的註解`employee01`。</span><span class="sxs-lookup"><span data-stu-id="951e5-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   <span data-ttu-id="951e5-122">`GetHashcode`提供的適當唯一 GetHashCode 演算法。</span><span class="sxs-lookup"><span data-stu-id="951e5-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="951e5-123">此演算法會使用索引鍵的屬性，用來計算雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="951e5-123">The algorithm uses only the key properties to compute the hash code.</span></span>  
  
-   <span data-ttu-id="951e5-124">`ToString`傳回串連的屬性值的字串，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="951e5-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="951e5-125">索引鍵和非索引鍵屬性會包含項目。</span><span class="sxs-lookup"><span data-stu-id="951e5-125">Both key and non-key properties are included.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 <span data-ttu-id="951e5-126">明確命名的匿名類型屬性不能與這些產生的方法衝突。</span><span class="sxs-lookup"><span data-stu-id="951e5-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="951e5-127">也就是說，您無法使用`.Equals`， `.GetHashCode`，或`.ToString`命名屬性。</span><span class="sxs-lookup"><span data-stu-id="951e5-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="951e5-128">在包含至少一個的匿名型別定義的索引鍵屬性也實作<xref:System.IEquatable%601?displayProperty=nameWithType>介面，其中`T`是匿名類型的類型。</span><span class="sxs-lookup"><span data-stu-id="951e5-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="951e5-129">匿名類型宣告在它們出現在相同的組件、 其屬性具有相同名稱和相同推斷的型別、 屬性的宣告以相同的順序，和相同的屬性會標示為索引鍵屬性時，才可以建立相同匿名類型。</span><span class="sxs-lookup"><span data-stu-id="951e5-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="951e5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="951e5-130">See Also</span></span>  
 [<span data-ttu-id="951e5-131">匿名類型</span><span class="sxs-lookup"><span data-stu-id="951e5-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="951e5-132">如何：在匿名類型宣告中推斷屬性名稱和類型</span><span class="sxs-lookup"><span data-stu-id="951e5-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
