---
title: "Of 子句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ef3ac4ac88727b1dcae50fa14abde03f29a16fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="2165c-102">Of 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2165c-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="2165c-103">導入了`Of`子句，用來識別*型別參數*上*泛型*類別、 結構、 介面、 委派或程序。</span><span class="sxs-lookup"><span data-stu-id="2165c-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="2165c-104">在泛型類型上的資訊，請參閱[Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2165c-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="2165c-105">使用的關鍵字</span><span class="sxs-lookup"><span data-stu-id="2165c-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="2165c-106">下列程式碼範例使用`Of`關鍵字來定義外框的可接受兩個類型參數的類別。</span><span class="sxs-lookup"><span data-stu-id="2165c-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="2165c-107">它*限制*`keyType`參數<xref:System.IComparable>介面，這表示使用的程式碼必須提供實作的型別引數<xref:System.IComparable>。</span><span class="sxs-lookup"><span data-stu-id="2165c-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="2165c-108">這是必要的讓`add`程序可以呼叫<xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="2165c-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2165c-109">如需有關條件約束的詳細資訊，請參閱[型別清單](../../../visual-basic/language-reference/statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="2165c-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
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
  
 <span data-ttu-id="2165c-110">如果您完成上述類別定義，您可以建構各種`dictionary`從它的類別。</span><span class="sxs-lookup"><span data-stu-id="2165c-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="2165c-111">您提供給型別`entryType`和`keyType`判斷何種類型的項目類別保存，而且它將與每個項目索引鍵的類型。</span><span class="sxs-lookup"><span data-stu-id="2165c-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="2165c-112">由於條件約束，您必須提供給`keyType`實作的型別<xref:System.IComparable>。</span><span class="sxs-lookup"><span data-stu-id="2165c-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="2165c-113">下列程式碼範例會建立物件以保留`String`項目並將相關聯`Integer`每個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2165c-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="2165c-114">`Integer`實作<xref:System.IComparable>並因此滿足條件約束上`keyType`。</span><span class="sxs-lookup"><span data-stu-id="2165c-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="2165c-115">`Of` 關鍵字可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="2165c-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2165c-116">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="2165c-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="2165c-117">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="2165c-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="2165c-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="2165c-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="2165c-119">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="2165c-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="2165c-120">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="2165c-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="2165c-121">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="2165c-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2165c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2165c-122">See Also</span></span>  
 <xref:System.IComparable>  
 [<span data-ttu-id="2165c-123">類型清單</span><span class="sxs-lookup"><span data-stu-id="2165c-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="2165c-124">Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="2165c-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="2165c-125">In</span><span class="sxs-lookup"><span data-stu-id="2165c-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [<span data-ttu-id="2165c-126">Out</span><span class="sxs-lookup"><span data-stu-id="2165c-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
