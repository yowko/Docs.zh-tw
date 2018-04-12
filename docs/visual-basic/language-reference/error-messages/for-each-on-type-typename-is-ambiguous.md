---
title: '&#39;每個 &#39;類型 &#39;&lt;typename&gt;&#39; 模稜兩可，因為該類型實作多個執行個體 &#39;System.collections.generic.ienumerable< (Of T) &#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a74178f3f0b2e7589b87046973473582993f3ed9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a><span data-ttu-id="15353-102">&#39;每個 &#39;類型 &#39;&lt;typename&gt;&#39; 模稜兩可，因為該類型實作多個執行個體 &#39;System.collections.generic.ienumerable< (Of T) &#39;</span><span class="sxs-lookup"><span data-stu-id="15353-102">&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;</span></span>
<span data-ttu-id="15353-103">A`For Each`陳述式所指定具有一個以上的迭代器變數<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="15353-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="15353-104">實作的類型必須是迭代器變數<xref:System.Collections.IEnumerable?displayProperty=nameWithType>或<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>其中一種介面`Collections`命名空間是[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="15353-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="15353-105">它是實作多個建構泛型介面，使用不同的型別引數的每個建構的類別。</span><span class="sxs-lookup"><span data-stu-id="15353-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="15353-106">如果此類別用於迭代器變數時，該變數具有一個以上<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="15353-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="15353-107">在這種情況下，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]無法選擇要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="15353-107">In such a case, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="15353-108">**錯誤 ID:** BC32096</span><span class="sxs-lookup"><span data-stu-id="15353-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="15353-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="15353-109">To correct this error</span></span>  
  
-   <span data-ttu-id="15353-110">使用[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)轉型介面定義迭代器變數型別<xref:System.Collections.IEnumerable.GetEnumerator%2A>您想要使用的方法。</span><span class="sxs-lookup"><span data-stu-id="15353-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15353-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15353-111">See Also</span></span>  
 [<span data-ttu-id="15353-112">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="15353-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="15353-113">介面</span><span class="sxs-lookup"><span data-stu-id="15353-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
