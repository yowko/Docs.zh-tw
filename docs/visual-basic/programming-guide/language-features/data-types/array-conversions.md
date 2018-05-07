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
ms.openlocfilehash: a179b7cf5b82132db88fb5412f0ca4be207f0987
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="array-conversions-visual-basic"></a>陣列轉換 (Visual Basic)
您可以將陣列型別轉換成不同的陣列類型，提供符合下列條件：  
  
-   **相等的陣序。** 兩個陣列的陣序規範必須相同，也就是說，它們必須具有相同的維度數目。 不過，個別維度的長度不需要相同。  
  
-   **項目資料類型。** 資料類型的兩個陣列的項目必須是參考類型。 您無法將轉換`Integer`陣列`Long`陣列，或甚至`Object`陣列，因為牽涉到至少一個實值型別。 如需詳細資訊，請參閱[實值類型和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
-   **轉換。** 轉換，以擴大或縮小，肯定是可能的兩個陣列項目類型之間。 此需求就會失敗的範例是嘗試之間的轉換`String`陣列和陣列的類別衍生自<xref:System.Attribute?displayProperty=nameWithType>。 這兩種類型沒有共通，和它們之間有沒有任何種類的轉換。  
  
 擴展或縮小取決於擴大或縮小的個別項目轉換到另一個陣列類型的轉換。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
## <a name="conversion-to-an-object-array"></a>物件陣列轉換  
 當您宣告`Object`但不初始化，其項目類型的陣列是`Object`，只要它就會維持未初始化。 當您設定特定類別的陣列時，會擔任該類別的型別。 不過，其基礎類型仍`Object`，以及您可以接著將它設定為不相關類別的另一個陣列。 因為所有的類別衍生自`Object`，您可以從任何類別變更陣列的項目類型的任何其他類別。  
  
 在下列範例中，沒有任何轉換存在類型之間`student`和`String`，但兩者都是衍生自`Object`，因此所有指派有效。  
  
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
 如果您原本宣告具有特定類別的陣列，其基礎的項目類型會是該類別。 如果您之後將它設定為另一個類別的陣列，必須有兩個類別之間的轉換。  
  
 在下列範例中，`students`是`student`陣列。 因為任何轉換不存在之間`String`和`student`，最後一個陳述式會失敗。  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [字串與其他類型之間的轉換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [如何： 將物件轉換成 Visual Basic 中的另一個類型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [資料類型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
