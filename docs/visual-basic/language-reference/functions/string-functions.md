---
title: 字串函式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 917797700c3e403971ce6f48174a282b1102f127
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799316"
---
# <a name="string-functions-visual-basic"></a>字串函式 (Visual Basic)

下表列出 Visual Basic 在<xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>類別中提供用來搜尋和操作字串的函式。 它們可以視為 Visual Basic 內建函式;也就是說，您不需要將它們當做類別的明確成員呼叫，如範例所示。 <xref:System.String?displayProperty=nameWithType>類別中也提供其他方法，在某些情況下互補方法。 
  
|.NET Framework 方法|說明|  
|---------------------------|-----------------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>、 <xref:Microsoft.VisualBasic.Strings.AscW%2A>|`Integer`傳回值，表示對應至字元的字元碼。|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>、 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|傳回與指定的字元碼相關聯的字元。|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|根據指定的`String`篩選準則，傳回以零為基底的陣列，其中包含陣列的子集。|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|傳回根據格式`String`運算式中包含的指示格式化的字串。|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|使用系統控制台中定義的貨幣符號，傳回格式化為貨幣值的運算式。|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|傳回表示日期/時間值的字串運算式。|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|傳回格式化為數位的運算式。|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|傳回格式化為百分比 (也就是乘以 100) 且尾端包含 % 字元的運算式。|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|傳回整數，指定一個字串在另一個字串中第一次出現的開始位置。|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|從字串的右邊開始，傳回一個字串在另一個字串中第一次出現的位置。|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|傳回由聯結陣列中包含的多個子字串所建立的字串。|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|傳回轉換成小寫的字串或字元。|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|從字串的左邊傳回包含指定字元數的字串。|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|傳回一個整數，其中包含字串中的字元數。|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|傳回靠左對齊的字串，其中包含已調整為指定之長度的指定字串。|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|傳回字串，其中包含指定之字串的複本，但沒有開頭空白。|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|從字串中傳回包含指定字元數的字串。|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|傳回字串，其中指定的子字串已由另一個子字串取代為指定的次數。|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|從字串的右邊傳回包含指定字元數的字串。|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|傳回靠右對齊的字串，其中包含已調整為指定之長度的指定字串。|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|傳回字串，其中包含指定之字串的複本，但沒有尾端空格。|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|傳回由指定的空格數目所組成的字串。|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|傳回以零為基底的一維陣列，其中包含指定數目的子字串。|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|根據字串比較的結果，傳回-1、0或1。|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|傳回以指定方式轉換的字串。|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|傳回由重複指定次數的指定字元所組成的字串或物件。|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|傳回字串，其中指定之字串的字元順序會反轉。|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|傳回字串，其中包含指定字串的複本，其中沒有開頭或尾端空格。|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|傳回字串或字元，其中包含轉換成大寫的指定字串。|  
  
 您可以使用[Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)語句來設定是否要使用由系統的地區設定（`Text`）所決定的區分大小寫文字排序次序，或字元（`Binary`）的內部二進位標記法來比較字串。 預設的文字比較方法是`Binary`。  
  
## <a name="example-ucase"></a>範例：UCase

這個範例會使用`UCase`函數來傳回字串的大寫版本。  
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]  
  
## <a name="example-ltrim"></a>範例：LTrim

這個範例會使用`LTrim`函式來去除開頭空格`RTrim`和函式，以去除字串變數的尾端空格。 它會使用`Trim`函式來去除這兩種類型的空間。  
  
[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]  
  
## <a name="example-mid"></a>範例：大中型

這個範例會使用`Mid`函數，從字串中傳回指定的字元數。  

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]  

## <a name="example-len"></a>範例：長度

這個範例會`Len`使用來傳回字串中的字元數。  
  
[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]  
  
## <a name="example-instr"></a>範例：InStr

這個範例會使用`InStr`函數來傳回另一個字串在另一個字串中第一次出現的位置。  
  
[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]  
  
## <a name="example-format"></a>範例：格式

這個範例示範`String`使用格式和使用者`Format`定義格式來格式化值的各種函數。 針對`/`日期分隔符號（）、時間分隔符號（`:`）和 AM/PM 指標（`t`和`tt`），您系統所顯示的實際格式化輸出取決於程式碼所使用的地區設定。 在開發環境中顯示時間和日期時，會使用程式碼地區設定的簡短時間格式和簡短日期格式。  
  
> [!NOTE]
> 針對使用24小時制的地區設定，AM/PM 指標（`t`和`tt`）不會顯示任何內容。  
  
 [!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>另請參閱

- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic 執行階段程式庫成員](../../../visual-basic/language-reference/runtime-library-members.md)
- [字串操作摘要](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
- [System.string 類別方法]<xref:System.String#methods?displayProperty=nameWithType>
