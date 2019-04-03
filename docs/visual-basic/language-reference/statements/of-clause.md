---
title: Of 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823437"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="46f16-102">Of 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46f16-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="46f16-103">導入了`Of`子句中，用來識別*型別參數*上*泛型*類別、 結構、 介面、 委派或程序。</span><span class="sxs-lookup"><span data-stu-id="46f16-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="46f16-104">如需泛型型別資訊，請參閱[在 Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="46f16-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="46f16-105">使用的關鍵字</span><span class="sxs-lookup"><span data-stu-id="46f16-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="46f16-106">下列程式碼範例使用`Of`關鍵字來定義外框的兩個類型參數的類別。</span><span class="sxs-lookup"><span data-stu-id="46f16-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="46f16-107">它*限制*`keyType`參數<xref:System.IComparable>介面，這表示使用的程式碼必須提供實作的類型引數<xref:System.IComparable>。</span><span class="sxs-lookup"><span data-stu-id="46f16-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="46f16-108">這是必要的讓`add`程序可以呼叫<xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="46f16-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="46f16-109">如需條件約束的詳細資訊，請參閱 [Type List](../../../visual-basic/language-reference/statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="46f16-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="46f16-110">如果您完成上述的類別定義，您可以建構各種`dictionary`從它的類別。</span><span class="sxs-lookup"><span data-stu-id="46f16-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="46f16-111">您提供的型別`entryType`和`keyType`判斷何種項目類別保存，而且它與每個項目關聯的索引鍵類型。</span><span class="sxs-lookup"><span data-stu-id="46f16-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="46f16-112">將條件約束，因為您必須提供給`keyType`可實作型別<xref:System.IComparable>。</span><span class="sxs-lookup"><span data-stu-id="46f16-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="46f16-113">下列程式碼範例會建立物件，持有`String`項目並將相關聯`Integer`每個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="46f16-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="46f16-114">`Integer` 會實作<xref:System.IComparable>因此在符合條件約束和`keyType`。</span><span class="sxs-lookup"><span data-stu-id="46f16-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="46f16-115">`Of` 關鍵字可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="46f16-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="46f16-116">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="46f16-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="46f16-117">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="46f16-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="46f16-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="46f16-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="46f16-119">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="46f16-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="46f16-120">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="46f16-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="46f16-121">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="46f16-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="46f16-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46f16-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="46f16-123">類型清單</span><span class="sxs-lookup"><span data-stu-id="46f16-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="46f16-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46f16-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="46f16-125">In</span><span class="sxs-lookup"><span data-stu-id="46f16-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="46f16-126">Out</span><span class="sxs-lookup"><span data-stu-id="46f16-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
