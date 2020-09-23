---
title: 陣列轉換
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
ms.openlocfilehash: 375c75c954f3be535272d674d9b786cad46b1a01
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077185"
---
# <a name="array-conversions-visual-basic"></a>陣列轉換 (Visual Basic)

如果您符合下列條件，您可以將陣列類型轉換成不同的陣列類型：  
  
- **相等的順位。** 這兩個數組的等級必須相同，也就是它們必須具有相同的維度數目。 不過，個別維度的長度不一定要相同。  
  
- **元素資料類型。** 這兩個數組的專案資料類型必須是參考型別。 您無法將陣列轉換成 `Integer` `Long` 陣列，甚至 `Object` 是陣列，因為至少有一個實值型別參與。 如需詳細資訊，請參閱 [Value Types and Reference Types](value-types-and-reference-types.md)。  
  
- **自由 兌換。** 轉換（擴大或縮小）必須能夠在兩個數組的元素類型之間進行。 失敗這項需求的範例是在 `String` 陣列和衍生自的類別陣列之間嘗試轉換 <xref:System.Attribute?displayProperty=nameWithType> 。 這兩種類型沒有任何共同的類型，而且它們之間不會有任何種類的轉換。  
  
 將某個陣列類型轉換成另一個陣列類型時，會根據個別元素的轉換是擴展或縮小而進行擴展或縮小。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md)。  
  
## <a name="conversion-to-an-object-array"></a>轉換成物件陣列  

 當您宣告 `Object` 陣列但未將它初始化時，它的專案型別會 `Object` 維持未初始化的狀態。 當您將它設定為特定類別的陣列時，它會採用該類別的型別。 不過，其基礎類型仍然是 `Object` ，而且您可以接著將它設定為不相關類別的另一個陣列。 由於所有類別都是衍生自 `Object` ，因此您可以將陣列的元素類型從任何類別變更為其他任何類別。  
  
 在下列範例中，類型與之間不會有任何轉換 `student` `String` ，但兩者都是衍生自 `Object` ，因此所有指派都是有效的。  
  
```vb  
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

 如果您原先宣告具有特定類別的陣列，其基礎元素類型就是該類別。 如果您之後將它設定為另一個類別的陣列，則這兩個類別之間必須有轉換。  
  
 在下列範例中， `students` 是 `student` 陣列。 由於和之間沒有任何轉換存在 `String` `student` ，最後一個語句會失敗。  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>另請參閱

- [Data types (資料類型)](index.md)
- [Visual Basic 中的類型轉換](type-conversions.md)
- [隱含和明確轉換](implicit-and-explicit-conversions.md)
- [字串與其他類型之間的轉換](conversions-between-strings-and-other-types.md)
- [如何：在 Visual Basic 中將物件轉換成其他類型](how-to-convert-an-object-to-another-type.md)
- [Data types (資料類型)](../../../language-reference/data-types/index.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
- [陣列](../arrays/index.md)
