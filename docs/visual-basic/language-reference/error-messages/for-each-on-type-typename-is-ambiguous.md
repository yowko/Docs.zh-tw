---
title: '&#39;每個&#39;類型&#39; &lt;typename&gt; &#39;模稜兩可，因為該類型實作多個執行個體&#39;System.Collections.Generic.IEnumerable (Of T)&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 8c48a7134eb8da83fb418b9aa91d55dcbe8e8bcb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456301"
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a><span data-ttu-id="e718d-102">&#39;每個&#39;類型&#39; &lt;typename&gt; &#39;模稜兩可，因為該類型實作多個執行個體&#39;System.Collections.Generic.IEnumerable (Of T)&#39;</span><span class="sxs-lookup"><span data-stu-id="e718d-102">&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;</span></span>
<span data-ttu-id="e718d-103">A`For Each`陳述式會指定具有一個以上的迭代器變數<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e718d-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="e718d-104">迭代器變數必須是型別可實作<xref:System.Collections.IEnumerable?displayProperty=nameWithType>或<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>中的其中一個介面`Collections`命名空間的[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e718d-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="e718d-105">可以實作多個建構泛型介面，使用不同的型別引數的每個建構類別。</span><span class="sxs-lookup"><span data-stu-id="e718d-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="e718d-106">如果此類別用於迭代器變數，該變數具有一個以上<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e718d-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="e718d-107">在此情況下，Visual Basic 無法選擇要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="e718d-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="e718d-108">**錯誤 ID:** BC32096</span><span class="sxs-lookup"><span data-stu-id="e718d-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e718d-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e718d-109">To correct this error</span></span>  
  
-   <span data-ttu-id="e718d-110">使用[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或是[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)轉型介面定義迭代器變數型別<xref:System.Collections.IEnumerable.GetEnumerator%2A>您想要使用的方法。</span><span class="sxs-lookup"><span data-stu-id="e718d-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e718d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e718d-111">See Also</span></span>  
 [<span data-ttu-id="e718d-112">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="e718d-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="e718d-113">介面</span><span class="sxs-lookup"><span data-stu-id="e718d-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
