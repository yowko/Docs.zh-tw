---
title: "泛型介面 (Visual Basic) 中的變異數 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c53c27bdb085213046553fc4b08f11336880a7c2
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-generic-interfaces-visual-basic"></a>泛型介面 (Visual Basic) 中的變異數
.NET framework 4 引入變異數支援數個現有的泛型介面。 變異數支援可讓實作這些介面的類別的隱含轉換。 下列介面是現在變異︰  
  
-   <xref:System.Collections.Generic.IEnumerable%601>（T 是共變數）</xref:System.Collections.Generic.IEnumerable%601>  
  
-   <xref:System.Collections.Generic.IEnumerator%601>（T 是共變數）</xref:System.Collections.Generic.IEnumerator%601>  
  
-   <xref:System.Linq.IQueryable%601>（T 是共變數）</xref:System.Linq.IQueryable%601>  
  
-   <xref:System.Linq.IGrouping%602>(`TKey`和`TElement`都是共變數)</xref:System.Linq.IGrouping%602>  
  
-   <xref:System.Collections.Generic.IComparer%601>（T 是 contravariant）</xref:System.Collections.Generic.IComparer%601>  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601>（T 是 contravariant）</xref:System.Collections.Generic.IEqualityComparer%601>  
  
-   <xref:System.IComparable%601>（T 是 contravariant）</xref:System.IComparable%601>  
  
 共變數允許具有衍生程度較大的傳回型別比介面的泛型型別參數所定義的方法。 若要說明共變異數項功能，請考慮下列這些泛型介面︰`IEnumerable(Of Object)`和`IEnumerable(Of String)`。 `IEnumerable(Of String)`介面不會繼承`IEnumerable(Of Object)`介面。 不過，`String`型別會繼承`Object`型別，在某些情況下，您可以將這些介面的物件指派給彼此。 這都是以下列程式碼範例所示。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 在舊版的.NET Framework 中，此程式碼會造成編譯錯誤，在 Visual Basic `Option Strict On`。 但現在您可以使用`strings`而不是`objects`如上述範例中，因為<xref:System.Collections.Generic.IEnumerable%601>介面是 covariant。</xref:System.Collections.Generic.IEnumerable%601>  
  
 反變數允許擁有較少衍生的介面的泛型參數所指定的引數型別方法。 為了說明反變數，我們假設您已建立`BaseComparer`類別的執行個體的比較`BaseClass`類別。 `BaseComparer` 類別會實作 `IEqualityComparer(Of BaseClass)` 介面。 因為<xref:System.Collections.Generic.IEqualityComparer%601>介面現在是反變數，您可以使用`BaseComparer`比較繼承的類別的執行個體`BaseClass`類別</xref:System.Collections.Generic.IEqualityComparer%601> 這都是以下列程式碼範例所示。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 如需詳細資訊，請參閱[使用泛型集合 (Visual Basic) 的介面中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)。  
  
 參考型別只支援泛型介面中的變異數。 實值型別不支援變異數。 例如，`IEnumerable(Of Integer)`無法隱含地轉換成`IEnumerable(Of Object)`，因為整數都由實值型別。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 它也是一定要記住，實作 variant 介面的類別仍然是不變。 例如，雖然<xref:System.Collections.Generic.List%601>實作 covariant 介面<xref:System.Collections.Generic.IEnumerable%601>，不能隱含轉換`List(Of Object)`到`List(Of String)`。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.Generic.List%601> 下列程式碼範例所示。  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a>另請參閱  
 [在介面中使用變異數的泛型集合 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)   
 [建立 Variant 泛型介面 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)   
 [泛型介面](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf)   
 [委派 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
