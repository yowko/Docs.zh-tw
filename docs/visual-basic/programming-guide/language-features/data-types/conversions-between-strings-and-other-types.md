---
title: 字串與其他類型之間的轉換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 38acd9056f9517e6d8b62691cdeb1a2960bec800
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516570"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>字串與其他類型之間的轉換 (Visual Basic)
您可以將轉換數字`Boolean`，或日期/時間值`String`。 您也可以反向轉換，從數值字串值`Boolean`，或`Date`— 提供字串的內容可以解譯為有效的值的目的地資料類型。 如果它們無法在執行階段錯誤發生。  
  
 所有這些指派，任一方向的轉換縮小轉換。 您應該使用類型轉換關鍵字 (`CBool`， `CByte`， `CDate`， `CDbl`， `CDec`， `CInt`， `CLng`， `CSByte`， `CShort`， `CSng`， `CStr`，`CUInt`， `CULng`， `CUShort`，和`CType`)。 <xref:Microsoft.VisualBasic.Strings.Format%2A>和<xref:Microsoft.VisualBasic.Conversion.Val%2A>函式可讓您進一步控制字串和數字之間的轉換。  
  
 如果您已定義類別或結構，您可以定義之間的型別轉換運算子`String`和您的類別或結構的類型。 如需詳細資訊，請參閱 <<c0> [ 如何： 定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="conversion-of-numbers-to-strings"></a>數字轉換為字串  
 您可以使用`Format`函式，將數字轉換為格式化的字串，其中可以包括不僅適當的數字，但也格式化符號，例如貨幣符號 (例如`$`)，千分位分隔符號或*數字分位符號*(例如`,`)，以及小數分隔符號 (例如`.`)。 `Format` 會自動使用適當的符號，根據**地區選項**Windows 控制台中**控制台**。  
  
 請注意，串連 (`&`) 運算子可以將數字轉換成字串以隱含方式，如下列範例所示。  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>字串轉換成數字  
 您可以使用`Val`函式來明確地轉換為數字的字串中的數字。 `Val` 讀取的字串，直到遇到數字、 空格、 索引標籤、 換行字元或句號以外的字元。 序列"& O"和"& H"alter 基底的數字系統，並終止掃描。 它會停止讀取，直到`Val`將所有適當的字元轉換為數值。 例如，下列陳述式會傳回值`141.825`。  
  
 `Val("   14   1.825 miles")`  
  
 當 Visual Basic 會將字串轉換為數字值時，它會使用**地區選項**指定在 Windows 中設定**控制台**解譯千分位分隔符號，十進位分隔符號，並貨幣符號。 這表示，轉換可能成功下其中一個設定。 比方說，`"$14.20"`是可接受在英文 （美國） 地區設定，但不是在法文地區設定。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [如何： 將物件轉換成 Visual Basic 中的另一個類型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [資料類型](../../../../visual-basic/language-reference/data-types/index.md)  
 [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [以 .NET Framework 為基礎的國際應用程式簡介](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
