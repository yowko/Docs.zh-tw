---
title: "如何：在 Visual Basic 中排序陣列"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 310c2dacb384de49c80073840c6c58d37f3937d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>如何：在 Visual Basic 中排序陣列
這個範例會宣告陣列`String`物件命名`zooAnimals`，會填入它，然後再依字母順序排序。  
  
## <a name="example"></a>範例  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   存取 Mscorlib.dll 和<xref:System>命名空間。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   陣列是空的 (<xref:System.ArgumentNullException>類別)  
  
-   陣列是多維 (<xref:System.RankException>類別)  
  
-   不會實作一個或多個陣列項目的<xref:System.IComparable>介面 (<xref:System.InvalidOperationException>類別)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [陣列的疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
