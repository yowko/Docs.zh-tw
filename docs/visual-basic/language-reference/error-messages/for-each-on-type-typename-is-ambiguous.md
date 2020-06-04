---
title: 類型 '<typename>' 上的 'For Each'模稜兩可，因為該類型實作了 'System.Collections.Generic.IEnumerable(Of T)' 的多個執行個體化
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 153a2640d66f48660f21339aaf0ecc8eaa10f51f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402962"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="1ac74-102">類型 '\<typename>' 上的 'For Each'模稜兩可，因為該類型實作了 'System.Collections.Generic.IEnumerable(Of T)' 的多個執行個體化</span><span class="sxs-lookup"><span data-stu-id="1ac74-102">'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>
<span data-ttu-id="1ac74-103">`For Each`語句會指定具有一個以上方法的反覆運算器變數 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1ac74-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="1ac74-104">Iterator 變數必須是在 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> .NET Framework 的其中一個命名空間中，實作為或介面的型別 `Collections` 。</span><span class="sxs-lookup"><span data-stu-id="1ac74-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the .NET Framework.</span></span> <span data-ttu-id="1ac74-105">類別可以使用不同的型別引數，針對每個結構來執行一個以上的結構化泛型介面。</span><span class="sxs-lookup"><span data-stu-id="1ac74-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="1ac74-106">如果執行這個的類別用於反覆運算器變數，該變數會有一個以上的 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1ac74-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="1ac74-107">在這種情況下，Visual Basic 無法選擇要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="1ac74-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="1ac74-108">**錯誤識別碼：** BC32096</span><span class="sxs-lookup"><span data-stu-id="1ac74-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1ac74-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1ac74-109">To correct this error</span></span>  
  
- <span data-ttu-id="1ac74-110">使用[DirectCast 運算子](../operators/directcast-operator.md)或[TryCast 運算子](../operators/trycast-operator.md)，將反覆運算器變數類型轉換為定義 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 您要使用之方法的介面。</span><span class="sxs-lookup"><span data-stu-id="1ac74-110">Use [DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac74-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ac74-111">See also</span></span>

- [<span data-ttu-id="1ac74-112">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="1ac74-112">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="1ac74-113">介面</span><span class="sxs-lookup"><span data-stu-id="1ac74-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
