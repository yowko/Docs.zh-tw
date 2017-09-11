---
title: "&quot;For Each 型別 &quot;&lt;typename&gt;&quot; 模稜兩可，因為該型別實作多個執行個體的 &quot;System.Collections.Generic.IEnumerable (Of T)&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32096
- bc32096
dev_langs:
- VB
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 783c741a8acb0d27ef6ff5c52939bd12a026ba74
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a><span data-ttu-id="bb6c7-102">'For Each 型別 '&lt;typename&gt;' 模稜兩可，因為該型別實作多個執行個體的 'System.Collections.Generic.IEnumerable (Of T)'</span><span class="sxs-lookup"><span data-stu-id="bb6c7-102">&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;</span></span>
<span data-ttu-id="bb6c7-103">A`For Each`陳述式會指定具有一個以上的迭代器變數<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</xref:System.Collections.IEnumerable.GetEnumerator%2A></span><span class="sxs-lookup"><span data-stu-id="bb6c7-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="bb6c7-104">迭代器變數必須實作的型別<xref:System.Collections.IEnumerable?displayProperty=fullName>或<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>中的其中一個介面`Collections`命名空間的[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]。</xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> </xref:System.Collections.IEnumerable?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bb6c7-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=fullName> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="bb6c7-105">就可以實作一個以上建構泛型介面，使用不同的型別引數的每個建構的類別。</span><span class="sxs-lookup"><span data-stu-id="bb6c7-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="bb6c7-106">如果此類別用於迭代器變數，該變數具有一個以上<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</xref:System.Collections.IEnumerable.GetEnumerator%2A></span><span class="sxs-lookup"><span data-stu-id="bb6c7-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="bb6c7-107">在這種情況下，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]無法選擇要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="bb6c7-107">In such a case, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="bb6c7-108">**錯誤識別碼︰** BC32096</span><span class="sxs-lookup"><span data-stu-id="bb6c7-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bb6c7-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bb6c7-109">To correct this error</span></span>  
  
-   <span data-ttu-id="bb6c7-110">使用[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)介面定義的迭代器變數類型轉換<xref:System.Collections.IEnumerable.GetEnumerator%2A>您想要使用的方法。</xref:System.Collections.IEnumerable.GetEnumerator%2A></span><span class="sxs-lookup"><span data-stu-id="bb6c7-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6c7-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb6c7-111">See Also</span></span>  
 <span data-ttu-id="bb6c7-112">[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bb6c7-112">[For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="bb6c7-113"> [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span><span class="sxs-lookup"><span data-stu-id="bb6c7-113"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span></span>
