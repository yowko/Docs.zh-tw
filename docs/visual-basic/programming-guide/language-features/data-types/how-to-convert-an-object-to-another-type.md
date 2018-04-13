---
title: 如何：在 Visual Basic 中將物件轉換成其他類型
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 053c93e7cf842138f5b9299cd2fcfa56342dd40b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>如何：在 Visual Basic 中將物件轉換成其他類型
您將轉換`Object`變數設為另一種資料類型，使用轉換關鍵字，例如[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)。  
  
## <a name="example"></a>範例  
 下列範例會將轉換`Object`變數設為`Integer`和`String`。  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 如果您已了解的內容`Object`變數都是特定資料類型，最好是將變數轉換成該資料類型。 如果您繼續使用`Object`變數時，您會產生  *boxing*和*unboxing* （適用於實值類型） 或*晚期繫結*（適用於參考型別）。 這些作業採用額外的執行時間，並提升效能。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   <xref:System?displayProperty=nameWithType> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Object>  
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [字串與其他類型之間的轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [資料類型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
