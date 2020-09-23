---
title: 作法：將物件轉換成其他類型
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: b89e996324d9ec22fc243b59502f3d36fefdee60
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090218"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>如何：在 Visual Basic 中將物件轉換成其他類型

您可以 `Object` 使用轉換關鍵字（例如 [CType 函數](../../../language-reference/functions/ctype-function.md)）將變數轉換成另一種資料類型。  
  
## <a name="example"></a>範例  

 下列範例會將 `Object` 變數轉換成 `Integer` 和 `String` 。  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 如果您知道變數的內容 `Object` 是特定的資料類型，最好將變數轉換成該資料類型。 如果您繼續使用此 `Object` 變數，則會產生) 的數值型別或*晚期繫結* (（) 的參考型別）的 (的*裝箱*和*取消*加入。 這些作業都需要花費更多的執行時間，並讓您的效能變慢。  
  
## <a name="compile-the-code"></a>編譯程式碼  

 這個範例需要：  
  
- <xref:System?displayProperty=nameWithType> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Object>
- [Visual Basic 中的類型轉換](type-conversions.md)
- [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md)
- [隱含和明確轉換](implicit-and-explicit-conversions.md)
- [字串與其他類型之間的轉換](conversions-between-strings-and-other-types.md)
- [陣列轉換](array-conversions.md)
- [結構](structures.md)
- [Data types (資料類型)](../../../language-reference/data-types/index.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
