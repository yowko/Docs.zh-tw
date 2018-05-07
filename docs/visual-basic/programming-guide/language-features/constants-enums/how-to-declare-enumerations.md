---
title: 如何：宣告列舉 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: e2dbdbbf6bf7fe3e4b71cbe7edc7a19b18f96ef2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-enumerations-visual-basic"></a>如何：宣告列舉 (Visual Basic)
建立列舉，含`Enum`陳述式的宣告區段中的類別或模組。 您無法宣告列舉型別方法內。 若要指定適當的存取層級，請使用`Private`， `Protected`， `Friend`，或`Public`。  
  
 `Enum`型別具有名稱、 基礎類型和一組欄位，各代表常數。 名稱必須是有效的 Visual Basic.NET 限定詞。 基礎類型必須是整數類型的其中一個 —`Byte`， `Short`，`Long`或`Integer`。 `Integer` 是預設值。 列舉型別一律強型別和不可互換的整數數字類型。  
  
 列舉型別不能有浮點值。 如果列舉指派的浮點值`Option Strict On`，造成編譯器錯誤。 如果`Option Strict`是`Off`，值會自動轉換為`Enum`型別。  
  
 如需名稱資訊，以及如何使用`Imports`陳述式來進行名稱限定不必要的請參閱[列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
### <a name="to-declare-an-enumeration"></a>宣告列舉  
  
1.  撰寫包含程式碼存取層級中，宣告`Enum`關鍵字和有效的名稱，如同下列範例中，其中每個宣告不同`Enum`。  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  列舉型別中定義的常數。 根據預設，第一個常數列舉型別會初始化為`0`，而後續的常數會初始化為值大於先前的常數。 例如，下列的列舉， `Days`，包含名為常數`Sunday`值`0`，名為`Monday`值`1`，名為`Tuesday`值`2`，依此類推。  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  您可以使用在指派陳述式明確指派常數列舉中的值。 您可以指派任何整數值，包含負號。 例如，您可以具有值小於零，表示錯誤狀況的常數。 在下列的列舉常數`Invalid`明確指派值`–1`，和常數`Sunday`被指派的值`0`。 因為它是在列舉中，第一個常數`Saturday`也會初始化為值`0`。 值`Monday`是`1`(的值大於`Sunday`); 的值`Tuesday`是`2`，依此類推。  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>宣告列舉為明確的類型  
  
-   使用指定的列舉類型`As`子句，如下列範例所示。  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [如何：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [如何： 逐一查看 Visual Basic 中列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [如何：決定與列舉值相關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [何時使用列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
