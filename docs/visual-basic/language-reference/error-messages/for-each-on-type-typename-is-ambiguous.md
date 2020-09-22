---
title: 類型 '<typename>' 上的 'For Each'模稜兩可，因為該類型實作了 'System.Collections.Generic.IEnumerable(Of T)' 的多個執行個體化
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: d04a77291ecf09f88ad189667540e9e353246f28
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874085"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="236b2-102">類型 '\<typename>' 上的 'For Each'模稜兩可，因為該類型實作了 'System.Collections.Generic.IEnumerable(Of T)' 的多個執行個體化</span><span class="sxs-lookup"><span data-stu-id="236b2-102">'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>

<span data-ttu-id="236b2-103">`For Each`語句會指定具有一個以上方法的 iterator 變數 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 。</span><span class="sxs-lookup"><span data-stu-id="236b2-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="236b2-104">反覆運算器變數的型別必須是在 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> .NET Framework 其中一個命名空間中的或介面 `Collections` 。</span><span class="sxs-lookup"><span data-stu-id="236b2-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the .NET Framework.</span></span> <span data-ttu-id="236b2-105">類別可以針對每個結構使用不同的型別引數，來執行一個以上的結構化泛型介面。</span><span class="sxs-lookup"><span data-stu-id="236b2-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="236b2-106">如果執行此程式的類別用於反覆運算器變數，該變數就會有一個以上的 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="236b2-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="236b2-107">在這種情況下，Visual Basic 無法選擇要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="236b2-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="236b2-108">**錯誤識別碼：** BC32096</span><span class="sxs-lookup"><span data-stu-id="236b2-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="236b2-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="236b2-109">To correct this error</span></span>  
  
- <span data-ttu-id="236b2-110">使用 [DirectCast 運算子](../operators/directcast-operator.md) 或 [TryCast 運算子](../operators/trycast-operator.md) ，將反覆運算器變數型別轉換為定義 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 您想要使用之方法的介面。</span><span class="sxs-lookup"><span data-stu-id="236b2-110">Use [DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236b2-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="236b2-111">See also</span></span>

- [<span data-ttu-id="236b2-112">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="236b2-112">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="236b2-113">介面</span><span class="sxs-lookup"><span data-stu-id="236b2-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
