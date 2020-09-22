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
ms.openlocfilehash: 0595356fb75fc0ac73a49622d71fe1d28fa7b648
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865906"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="a0ff7-102">Of 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0ff7-102">Of Clause (Visual Basic)</span></span>

<span data-ttu-id="a0ff7-103">引進 `Of` 子句，這個子句會識別*泛型*類別、結構、介面、委派或程式的*型別參數*。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="a0ff7-104">如需泛型型別的詳細資訊，請參閱 [Visual Basic 中的泛型型別](../../programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-104">For information on generic types, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="a0ff7-105">使用 of 關鍵字</span><span class="sxs-lookup"><span data-stu-id="a0ff7-105">Using the Of Keyword</span></span>  

 <span data-ttu-id="a0ff7-106">下列程式碼範例會使用 `Of` 關鍵字來定義採用兩個型別參數之類別的大綱。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="a0ff7-107">它*constrains*會限制 `keyType` 介面的參數 <xref:System.IComparable> ，這表示使用程式碼必須提供實作為的型別引數 <xref:System.IComparable> 。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="a0ff7-108">這是必要的，如此程式 `add` 才能呼叫 <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a0ff7-109">如需條件約束的詳細資訊，請參閱 [Type List](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-109">For more information on constraints, see [Type List](type-list.md).</span></span>  
  
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
  
 <span data-ttu-id="a0ff7-110">如果您完成上述類別定義，就可以 `dictionary` 從其建立各種類別。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="a0ff7-111">您提供給的 `entryType` 型別， `keyType` 會決定類別保存的專案類型，以及它與每個專案相關聯的索引鍵類型。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="a0ff7-112">由於條件約束的限制，您必須提供給實的 `keyType` 型別 <xref:System.IComparable> 。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="a0ff7-113">下列程式碼範例會建立保存專案的物件 `String` ，並將索引 `Integer` 鍵與每一個索引鍵產生關聯。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="a0ff7-114">`Integer`<xref:System.IComparable>在上執行，因此符合條件約束 `keyType` 。</span><span class="sxs-lookup"><span data-stu-id="a0ff7-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="a0ff7-115">`Of` 關鍵字可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="a0ff7-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a0ff7-116">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="a0ff7-116">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="a0ff7-117">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="a0ff7-117">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="a0ff7-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="a0ff7-118">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="a0ff7-119">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="a0ff7-119">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="a0ff7-120">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="a0ff7-120">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="a0ff7-121">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="a0ff7-121">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a0ff7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0ff7-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="a0ff7-123">Type List</span><span class="sxs-lookup"><span data-stu-id="a0ff7-123">Type List</span></span>](type-list.md)
- [<span data-ttu-id="a0ff7-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0ff7-124">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="a0ff7-125">位置</span><span class="sxs-lookup"><span data-stu-id="a0ff7-125">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="a0ff7-126">擴展</span><span class="sxs-lookup"><span data-stu-id="a0ff7-126">Out</span></span>](../modifiers/out-generic-modifier.md)
