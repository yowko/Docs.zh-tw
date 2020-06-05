---
title: Of 子句
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
ms.openlocfilehash: 8497f46453d586fb94e1f7c82c81c6b923dd6f60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404417"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="d6de1-102">Of 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6de1-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="d6de1-103">引進 `Of` 子句，它會識別*泛型*類別、結構、介面、委派或程式上的*型別參數*。</span><span class="sxs-lookup"><span data-stu-id="d6de1-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="d6de1-104">如需泛型型別的詳細資訊，請參閱[Visual Basic 中的泛型型別](../../programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d6de1-104">For information on generic types, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="d6de1-105">使用 of 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d6de1-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="d6de1-106">下列程式碼範例會使用 `Of` 關鍵字來定義接受兩個型別參數之類別的外框。</span><span class="sxs-lookup"><span data-stu-id="d6de1-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="d6de1-107">它*constrains*會 `keyType` 根據介面來限制參數 <xref:System.IComparable> ，這表示取用的程式碼必須提供實作為型別引數 <xref:System.IComparable> 。</span><span class="sxs-lookup"><span data-stu-id="d6de1-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="d6de1-108">這是必要的，如此程式 `add` 才能呼叫 <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="d6de1-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d6de1-109">如需條件約束的詳細資訊，請參閱 [Type List](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="d6de1-109">For more information on constraints, see [Type List](type-list.md).</span></span>  
  
```vb  
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
  
 <span data-ttu-id="d6de1-110">如果您完成上述類別定義，您可以 `dictionary` 從它建立各種類別。</span><span class="sxs-lookup"><span data-stu-id="d6de1-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="d6de1-111">您提供給的類型 `entryType` ，並 `keyType` 決定類別所保留的專案類型，以及與每個專案相關聯的索引鍵類型。</span><span class="sxs-lookup"><span data-stu-id="d6de1-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="d6de1-112">由於條件約束的原因，您必須提供給實 `keyType` 作為型別 <xref:System.IComparable> 。</span><span class="sxs-lookup"><span data-stu-id="d6de1-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="d6de1-113">下列程式碼範例會建立一個物件，它會保存 `String` 專案並將索引 `Integer` 鍵與每一個金鑰產生關聯。</span><span class="sxs-lookup"><span data-stu-id="d6de1-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="d6de1-114">`Integer`會執行 <xref:System.IComparable> 並因此滿足的條件約束 `keyType` 。</span><span class="sxs-lookup"><span data-stu-id="d6de1-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="d6de1-115">`Of` 關鍵字可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="d6de1-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d6de1-116">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="d6de1-116">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="d6de1-117">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="d6de1-117">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="d6de1-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d6de1-118">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="d6de1-119">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="d6de1-119">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="d6de1-120">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="d6de1-120">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="d6de1-121">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d6de1-121">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d6de1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6de1-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="d6de1-123">Type List</span><span class="sxs-lookup"><span data-stu-id="d6de1-123">Type List</span></span>](type-list.md)
- [<span data-ttu-id="d6de1-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6de1-124">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="d6de1-125">位於</span><span class="sxs-lookup"><span data-stu-id="d6de1-125">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="d6de1-126">脫銷</span><span class="sxs-lookup"><span data-stu-id="d6de1-126">Out</span></span>](../modifiers/out-generic-modifier.md)
