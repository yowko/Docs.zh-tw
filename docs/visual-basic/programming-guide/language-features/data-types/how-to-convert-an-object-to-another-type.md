---
title: HOW TO：將物件轉換成 Visual Basic 中的另一個類型
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: d80dc542f71aaf3eec6891006d77c5d39c985abf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600997"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>HOW TO：將物件轉換成 Visual Basic 中的另一個類型
您將轉換`Object`變數設為另一個資料類型，例如使用轉換關鍵字[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)。  
  
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
  
 如果您知道的內容`Object`變數是特定的資料類型，最好是將變數轉換成該資料型別。 如果您繼續使用`Object`變數，您會產生其中一個*boxing*並*unboxing* （適用於實值型別） 或*晚期繫結*（適用於參考型別）。 這些作業全部需要額外的執行時間，並讓您的效能降低。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- <xref:System?displayProperty=nameWithType> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Object>
- [在 Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [字串與其他類型之間的轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
