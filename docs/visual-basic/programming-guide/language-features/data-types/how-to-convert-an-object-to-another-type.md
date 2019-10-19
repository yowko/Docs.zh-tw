---
title: 如何：在 Visual Basic 中將物件轉換成其他類型
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 39083fc55d30e24c357ec162a15466f81655f4c8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582333"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>如何：在 Visual Basic 中將物件轉換成其他類型
您可以使用轉換關鍵字（例如[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)），將 `Object` 變數轉換成另一個資料類型。  
  
## <a name="example"></a>範例  
 下列範例會將 `Object` 變數轉換成 `Integer` 和 `String`。  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 如果您知道 `Object` 變數的內容是特定的資料類型，最好將變數轉換成該資料類型。 如果您繼續使用 `Object` 變數，則會產生*裝箱*和*取消裝箱*（適用于實值型別）或*晚期繫結*（針對引用型別）。 這些作業都需要額外的執行時間，讓您的效能變慢。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- <xref:System?displayProperty=nameWithType> 命名空間的參考。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Object>
- [Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [字串與其他類型之間的轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
