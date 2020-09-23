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
ms.openlocfilehash: 823931f7d6beb8218e8b99d4a8d45716b7214304
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077146"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>字串與其他類型之間的轉換 (Visual Basic)

您可以將數值、 `Boolean` 或日期/時間值轉換成 `String` 。 您也可以反向轉換（從字串值到數值、 `Boolean` 或 `Date` ），前提是字串的內容可以解讀為目的地資料類型的有效值。 如果不是，就會發生執行階段錯誤。  
  
 上述所有指派的轉換都是縮小轉換。 您應該使用類型轉換關鍵字 (、、、、、、、、、、、、、 `CBool` `CByte` `CDate` `CDbl` `CDec` `CInt` `CLng` `CSByte` `CShort` `CSng` `CStr` `CUInt` `CULng` `CUShort` 和 `CType`) 。 和函式 <xref:Microsoft.VisualBasic.Strings.Format%2A> <xref:Microsoft.VisualBasic.Conversion.Val%2A> 可讓您進一步控制字元串與數位之間的轉換。  
  
 如果您已定義類別或結構，則可以在 `String` 和類別或結構的類型之間定義型別轉換運算子。 如需詳細資訊，請參閱 [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="conversion-of-numbers-to-strings"></a>將數位轉換成字串  

 您可以使用函式 `Format` ，將數位轉換成格式化的字串，其中不僅可以包含適當的數位，還可以將符號格式化，例如貨幣符號 (例如 `$`) 、千位分隔符號或 *數位群組符號* (例如 `,`) 和小數分隔符號 (例如 `.`) 。 `Format`會根據 Windows**主控台**中指定的**地區選項**設定，自動使用適當的符號。  
  
 請注意，串連 (`&`) 運算子可以隱含地將數位轉換成字串，如下列範例所示。  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>將字串轉換為數字  

 您可以使用 `Val` 函數，將字串中的數位明確轉換為數字。 `Val` 讀取字串，直到它遇到數位、空格、定位字元、換行字元或句號以外的字元為止。 序列 "&O" 和 "&H" 改變數字系統的基底，並結束掃描。 在停止讀取之前，會 `Val` 將所有適當的字元轉換成數值。 例如，下列語句會傳回值 `141.825` 。  
  
 `Val("   14   1.825 miles")`  
  
 當 Visual Basic 將字串轉換成數值時，它會使用 Windows**主控台**中指定的**地區選項**設定來解讀千位分隔符號、小數分隔符號和貨幣符號。 這表示轉換可能會在某個設定下成功，但不能在另一個設定下成功。 例如， `"$14.20"` 英文 (美國) 地區設定可接受，但在任何法文地區設定中則不接受。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的類型轉換](type-conversions.md)
- [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md)
- [隱含和明確轉換](implicit-and-explicit-conversions.md)
- [如何：在 Visual Basic 中將物件轉換成其他類型](how-to-convert-an-object-to-another-type.md)
- [陣列轉換](array-conversions.md)
- [Data types (資料類型)](../../../language-reference/data-types/index.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
- [開發全球化和當地語系化應用程式](/visualstudio/ide/globalizing-and-localizing-applications)
