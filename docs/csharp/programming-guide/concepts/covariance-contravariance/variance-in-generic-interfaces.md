---
title: "泛型介面中的差異 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40daaa3d008a93ab48d0d74894f60f0baca1d12b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="variance-in-generic-interfaces-c"></a>泛型介面中的差異 (C#)
.NET Framework 4 針對數個現有泛型介面推出了差異支援。 差異支援可讓實作這些介面的類別以隱含方式轉換。 下列介面現在都是 Variant︰  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T 是 Covariant)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T 是 Covariant)  
  
-   <xref:System.Linq.IQueryable%601> (T 是 Covariant)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` 和 `TElement` 是 Covariant)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T 是 Contravariant)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T 是 Contravariant)  
  
-   <xref:System.IComparable%601> (T 是 Contravariant)  
  
 共變數允許方法具有比介面泛型型別參數所定義之衍生程度更大的傳回型別。 若要示範共變數功能，請考慮這些泛型介面︰`IEnumerable<Object>` 和 `IEnumerable<String>`。 `IEnumerable<String>` 介面不會繼承 `IEnumerable<Object>` 介面。 不過，`String` 型別確實會繼承`Object` 型別，而且在某些情況下，您可能希望將這些介面的物件指派給彼此。 這會顯示在以下程式碼範例中。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 在舊版的 .NET Framework 中，此程式碼會造成 C# 使用 `Option Strict On` 的編譯錯誤。 但現在您可以使用 `strings`，不使用 `objects`，如上例所示，因為 <xref:System.Collections.Generic.IEnumerable%601> 介面是 Covariant。  
  
 反變數允許方法具有比介面泛型參數所指定之衍生程度更小的引數型別。 為示範反變數，我們假設您已建立 `BaseComparer` 類別來比較 `BaseClass` 類別的執行個體。 `BaseComparer` 類別會實作 `IEqualityComparer<BaseClass>` 介面。 因為 <xref:System.Collections.Generic.IEqualityComparer%601> 介面現在是 Contravariant，所以您可以使用 `BaseComparer` 比較繼承了 `BaseClass` 類別的類別執行個體。 這會顯示在以下程式碼範例中。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 如需更多範例，請參閱[針對泛型集合使用介面中的差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)。  
  
 僅參考型別支援泛型介面的差異。 實值型別不支援差異。 例如，`IEnumerable<int>` 無法以隱含方式轉換成 `IEnumerable<object>`，因為整數是以實值型別表示。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 請務必牢記，實作 Variant 介面的類別仍然是非變異的。 例如，雖然 <xref:System.Collections.Generic.List%601> 實作 Covariant 介面 <xref:System.Collections.Generic.IEnumerable%601>，但您不能以隱含方式將 `List<Object>` 轉換成 `List<String>`。 下列程式碼範例說明此情形。  
  
```cs  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a>另請參閱  
 [針對泛型集合使用介面中的差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)   
 [建立 Variant 泛型介面 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)   
 [泛型介面](../../../../standard/generics/interfaces.md)   
 [委派中的差異 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)

