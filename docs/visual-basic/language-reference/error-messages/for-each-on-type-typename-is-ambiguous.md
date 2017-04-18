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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6177b48cdc3bc4085cecb6d73c164684ef1c0bc6
ms.lasthandoff: 03/13/2017

---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a>'For Each 型別 '&lt;typename&gt;' 模稜兩可，因為該型別實作多個執行個體的 'System.Collections.Generic.IEnumerable (Of T)'
A`For Each`陳述式會指定具有一個以上的迭代器變數<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</xref:System.Collections.IEnumerable.GetEnumerator%2A>  
  
 迭代器變數必須實作的型別<xref:System.Collections.IEnumerable?displayProperty=fullName>或<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>中的其中一個介面`Collections`命名空間的[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]。</xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> </xref:System.Collections.IEnumerable?displayProperty=fullName> 就可以實作一個以上建構泛型介面，使用不同的型別引數的每個建構的類別。 如果此類別用於迭代器變數，該變數具有一個以上<xref:System.Collections.IEnumerable.GetEnumerator%2A>方法。</xref:System.Collections.IEnumerable.GetEnumerator%2A> 在這種情況下，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]無法選擇要呼叫的方法。  
  
 **錯誤識別碼︰** BC32096  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)介面定義的迭代器變數類型轉換<xref:System.Collections.IEnumerable.GetEnumerator%2A>您想要使用的方法。</xref:System.Collections.IEnumerable.GetEnumerator%2A>  
  
## <a name="see-also"></a>另請參閱  
 [每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
