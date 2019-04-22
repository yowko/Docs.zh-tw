---
title: 類型 '<typename>' 上的 'For Each'模稜兩可，因為該類型實作了 'System.Collections.Generic.IEnumerable(Of T)' 的多個執行個體化
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 6c34ca43decc3c5d8c72b529d8f51d7cc3b0c6b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833382"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="60a50-102">'For Each' 類型 '\<類型名稱 >' 模稜兩可，因為該類型實作多個 'System.Collections.Generic.IEnumerable (Of T)' 執行個體化</span><span class="sxs-lookup"><span data-stu-id="60a50-102">'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>
<span data-ttu-id="60a50-103">A`For Each`陳述式會指定具有一個以上的迭代器變數<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="60a50-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="60a50-104">迭代器變數必須是型別可實作<xref:System.Collections.IEnumerable?displayProperty=nameWithType>或<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>中的其中一個介面`Collections`命名空間的[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="60a50-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="60a50-105">可以實作多個建構泛型介面，使用不同的型別引數的每個建構類別。</span><span class="sxs-lookup"><span data-stu-id="60a50-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="60a50-106">如果此類別用於迭代器變數，該變數具有一個以上<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="60a50-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="60a50-107">在此情況下，Visual Basic 無法選擇要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="60a50-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="60a50-108">**錯誤 ID:** BC32096</span><span class="sxs-lookup"><span data-stu-id="60a50-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60a50-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="60a50-109">To correct this error</span></span>  
  
-   <span data-ttu-id="60a50-110">使用[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或是[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)轉型介面定義迭代器變數型別<xref:System.Collections.IEnumerable.GetEnumerator%2A>您想要使用的方法。</span><span class="sxs-lookup"><span data-stu-id="60a50-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60a50-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60a50-111">See also</span></span>

- [<span data-ttu-id="60a50-112">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="60a50-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="60a50-113">介面</span><span class="sxs-lookup"><span data-stu-id="60a50-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
