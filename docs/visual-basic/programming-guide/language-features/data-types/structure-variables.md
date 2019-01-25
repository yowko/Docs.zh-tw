---
title: 結構變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: f9cc6d0165b0eda8358d250c37910b1362473ab1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640598"
---
# <a name="structure-variables-visual-basic"></a>結構變數 (Visual Basic)
當您建立結構之後時，您可以為該型別來宣告程序層級和模組層級變數。 例如，您可以建立結構的電腦系統的相關記錄資訊。 下列範例為其示範。  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 您現在可以宣告該類型的變數。 下列宣告將說明這點。  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  在類別和模組中，使用宣告的結構[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)預設為公用存取。 如果您想要為私用的結構，請確定您使用宣告[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字。  
  
## <a name="access-to-structure-values"></a>結構值的存取權  
 若要指派及擷取結構變數的項目中的值，您會使用相同的語法，如同您使用來設定和取得屬性的物件上。 您將成員存取運算子 (`.`) 結構的變數名稱之間的項目名稱。 下列範例會存取變數先前宣告為類型的項目`systemInfo`。  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>指派結構變數  
 您也可以指派到另一個變數，如果兩個都是相同的結構類型。 這會將一個結構的所有項目複製到其他的對應項目。 下列宣告將說明這點。  
  
```  
yourSystem = mySystem  
```  
  
 如果結構項目是參考類型，如`String`， `Object`，或複製的資料指標的陣列。 在上述範例中，如果`systemInfo`已包含物件變數，則會將上述範例中會複製從指標`mySystem`到`yourSystem`，並透過一個結構物件的資料變更會是作用中時存取透過其他的結構。  
  
## <a name="see-also"></a>另請參閱
- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [結構和其他程式設計項目](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [結構和類別](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
