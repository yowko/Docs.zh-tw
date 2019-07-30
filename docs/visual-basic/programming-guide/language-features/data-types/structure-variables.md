---
title: 結構變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: a86a60def9ac1b8140194ecb6f5e784c62a0e101
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630963"
---
# <a name="structure-variables-visual-basic"></a>結構變數 (Visual Basic)

建立結構之後, 您可以將程式層級和模組層級變數宣告為該類型。 例如, 您可以建立一個結構來記錄電腦系統的相關資訊。 下列範例為其示範。

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

您現在可以宣告該類型的變數。 下列宣告說明這種情況。

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> 在類別和模組中, 使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)宣告的結構會預設為公用存取。 如果您想要將結構設為私用, 請務必使用[private](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字來宣告。

## <a name="access-to-structure-values"></a>結構值的存取權

若要從結構變數的元素指派和抓取值, 您可以使用與用來設定和取得物件屬性的相同語法。 您可以將成員存取運算子 (`.`) 放在結構變數名稱和元素名稱之間。 下列範例會存取先前宣告為類型`systemInfo`之變數的元素。

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a>指派結構變數

如果兩者都是相同的結構類型, 您也可以將一個變數指派給另一個。 這會將一個結構的所有專案複製到另一個結構中的對應元素。 下列宣告說明這種情況。

```vb
yourSystem = mySystem
```

如果結構專案是參考型別 (例如`String`、 `Object`或陣列), 則會複製資料的指標。 在上述範例中, 如果`systemInfo`已包含物件變數, 則先前的範例會將的指標從`mySystem`複製到`yourSystem`, 而在存取物件的資料時, 透過某個結構進行的變更將會生效透過另一個結構。

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
