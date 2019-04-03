---
title: 陣列轉換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 88002e2c099ed9503beddb190d243aadcc1087fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830197"
---
# <a name="array-conversions-visual-basic"></a>陣列轉換 (Visual Basic)
您可以將陣列型別轉換成不同的陣列型別，提供符合下列條件：  
  
-   **相等的順位。** 兩個陣列的陣序規範必須相同，也就是它們必須具有相同的維度數目。 不過，個別的維度的長度不需要相同。  
  
-   **項目資料型別。** 兩個陣列元素的資料類型必須是參考型別。 您無法轉換`Integer`陣列`Long`陣列、 或甚至`Object`陣列，因為牽涉到至少一個實值型別。 如需詳細資訊，請參閱 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
-   **可轉換性。** 轉換，以擴大或縮小，必須能夠在兩個陣列項目類型之間。 舉例來說，未通過這項需求是嘗試之間的轉換`String`陣列和陣列的類別衍生自<xref:System.Attribute?displayProperty=nameWithType>。 這兩種類型沒有任何共通點，並沒有任何類型的轉換之間存在。  
  
 擴展或縮小取決於個別的項目轉換是否會擴大或縮小到另一個陣列類型的轉換。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
## <a name="conversion-to-an-object-array"></a>轉換成物件陣列  
 當您宣告`Object`但不初始化，其項目類型的陣列是`Object`，只要它會保持未初始化。 當您設定特定類別的陣列時，它會在該類別的型別。 不過，其基礎類型仍`Object`，以及您可以接著將它設定為不相關的類別的另一個陣列。 因為所有的類別衍生自`Object`，您可以從任何類別變更陣列的項目類型，與任何其他類別。  
  
 在下列範例中，沒有任何轉換存在型別之間`student`並`String`，但都是衍生自`Object`，因此所有指派都都有效。  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>陣列的基礎類型  
 如果您原本宣告具有特定類別的陣列，其基礎的項目類型會是該類別。 如果您接著將它設定為另一個類別的陣列，必須有兩個類別之間的轉換。  
  
 在下列範例中，`students`是`student`陣列。 因為沒有任何轉換存在之間`String`和`student`，最後一個陳述式會失敗。  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>另請參閱

- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [在 Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [字串與其他類型之間的轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [如何：將物件轉換成 Visual Basic 中的另一個類型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
