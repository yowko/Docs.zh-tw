---
title: 字串與其他類型之間的轉換
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: ac2e8ce912080c284d8ba0228830dd6b3ddf5f6e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350129"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>字串與其他類型之間的轉換 (Visual Basic)
您可以將數值、`Boolean`或日期/時間值轉換成 `String`。 您也可以從字串值轉換成數位、`Boolean`或 `Date`，前提是字串的內容可以解讀為目的地資料類型的有效值。 如果不是，就會發生執行階段錯誤。  
  
 所有這些指派的轉換是以任一方向進行，都是縮小轉換。 您應該使用類型轉換關鍵字（`CBool`、`CByte`、`CDate`、`CDbl`、`CDec`、`CInt`、`CLng`、`CSByte`、`CShort`、`CSng`、`CStr`、`CUInt`、`CULng`、`CUShort`和 `CType`）。 <xref:Microsoft.VisualBasic.Strings.Format%2A> 和 <xref:Microsoft.VisualBasic.Conversion.Val%2A> 函數可讓您進一步控制字元串和數位之間的轉換。  
  
 如果您已定義類別或結構，您可以在 `String` 和類別或結構的類型之間定義類型轉換運算子。 如需詳細資訊，請參閱 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="conversion-of-numbers-to-strings"></a>將數位轉換成字串  
 您可以使用 `Format` 函式，將數位轉換成格式化字串，其中不僅可以包含適當的數位，也會將符號格式化，例如貨幣符號（例如 `$`）、千位分隔符號或*數位群組符號*（例如 `,`），以及十進位分隔符號（例如 `.`）。 `Format` 會根據 Windows [**控制台**] 中指定的 [**地區選項**] 設定，自動使用適當的符號。  
  
 請注意，串連（`&`）運算子可以隱含地將數位轉換成字串，如下列範例所示。  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>將字串轉換成數位  
 您可以使用 `Val` 函數，將字串中的數位明確轉換成數位。 `Val` 讀取字串，直到遇到數位、空格、定位字元、換行字元或句號以外的字元。 「& O」和「& H」順序會改變數字系統的基底，並終止掃描。 在它停止讀取之前，`Val` 會將所有適當的字元轉換為數值。 例如，下列語句會傳回 `141.825`的值。  
  
 `Val("   14   1.825 miles")`  
  
 當 Visual Basic 將字串轉換為數值時，會使用 Windows [**控制台**] 中指定的 [**地區選項**] 設定來解讀千位分隔符號、小數分隔符號和貨幣符號。 這表示轉換在一個設定下可能會成功，而不是另一個設定。 例如，`"$14.20"` 在英文（美國）地區設定中是可接受的，但不是任何法文地區設定。  
  
## <a name="see-also"></a>請參閱

- [Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [如何：在 Visual Basic 中將物件轉換為另一種類型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [資料類型](../../../../visual-basic/language-reference/data-types/index.md)
- [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [開發全球化和當地語系化應用程式](/visualstudio/ide/globalizing-and-localizing-applications)
