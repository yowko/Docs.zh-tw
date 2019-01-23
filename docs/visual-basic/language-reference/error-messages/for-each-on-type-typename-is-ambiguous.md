---
title: '&#39;每個&#39;類型&#39; &lt;typename&gt; &#39;模稜兩可，因為該類型實作多個執行個體&#39;System.Collections.Generic.IEnumerable (Of T)&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 7fd779ba34afa2a59fa6c42971597df8ce01495a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597342"
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>&#39;每個&#39;類型&#39; &lt;typename&gt; &#39;模稜兩可，因為該類型實作多個執行個體&#39;System.Collections.Generic.IEnumerable (Of T)&#39;
A`For Each`陳述式會指定具有一個以上的迭代器變數<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。  
  
 迭代器變數必須是型別可實作<xref:System.Collections.IEnumerable?displayProperty=nameWithType>或<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>中的其中一個介面`Collections`命名空間的[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。 可以實作多個建構泛型介面，使用不同的型別引數的每個建構類別。 如果此類別用於迭代器變數，該變數具有一個以上<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。 在此情況下，Visual Basic 無法選擇要呼叫的方法。  
  
 **錯誤 ID:** BC32096  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或是[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)轉型介面定義迭代器變數型別<xref:System.Collections.IEnumerable.GetEnumerator%2A>您想要使用的方法。  
  
## <a name="see-also"></a>另請參閱
- [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
