---
title: HOW TO：宣告列舉 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: c74b75adf0f56dd198375cb1ff24656d39ec074c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610570"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>HOW TO：宣告列舉 (Visual Basic)
您建立的列舉`Enum`「 宣告 」 區段中的類別或模組的陳述式。 您無法宣告列舉型別方法內。 若要指定適當的存取等級，請使用`Private`， `Protected`， `Friend`，或`Public`。  
  
 `Enum`型別具有名稱、 基礎類型和一組欄位，每個均代表一個常數。 名稱必須是有效的 Visual Basic.NET 限定詞。 基礎類型必須是整數型別 —`Byte`， `Short`，`Long`或`Integer`。 `Integer` 預設值。 列舉型別一律強型別，並不能互換使用整數數字類型。  
  
 列舉型別不能有浮點值。 如果列舉型別指派的浮點值`Option Strict On`，造成編譯器錯誤。 如果`Option Strict`已`Off`，值會自動轉換為`Enum`型別。  
  
 如需名稱資訊，以及如何使用`Imports`陳述式，使名稱限定性條件不必要的請參閱[列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
### <a name="to-declare-an-enumeration"></a>來宣告列舉  
  
1. 撰寫包含程式碼存取層級中，宣告`Enum`關鍵字，且有效的名稱，如下列範例中，其中每個宣告不同`Enum`。  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. 列舉中定義的常數。 根據預設，第一個常數，列舉型別會初始化為`0`，且後續的常數會初始化為值大於先前的常數。 比方說，下列的列舉， `Days`，包含名為的常數`Sunday`具有值`0`，名為常數`Monday`值`1`，名為常數`Tuesday`值`2`等等。  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. 您可以使用指派陳述式明確地指派常數列舉中的值。 您可以指派任何整數值，包括負數的數字。 比方說，您可以使用值小於零，表示錯誤狀況的常數。 在下列的列舉常數`Invalid`被明確指派的值`–1`，和常數`Sunday`的值會指派給`0`。 因為它是在列舉中，第一個常數`Saturday`也會初始化為值`0`。 值`Monday`是`1`(其中的值超過`Sunday`); 的值`Tuesday`是`2`，依此類推。  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>若要宣告明確的型別為列舉型別  
  
- 使用指定的列舉型別`As`子句，如下列範例所示。  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [如何：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [如何：逐一查看 Visual Basic 中列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [如何：決定與列舉值關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [何時使用列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
