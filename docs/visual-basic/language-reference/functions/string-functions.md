---
title: 字串函式
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 778e57eadd75baf1aabd100f9d8d41a490f79a04
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406284"
---
# <a name="string-functions-visual-basic"></a>字串函式 (Visual Basic)

下表列出 Visual Basic 在類別中提供用 <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> 來搜尋和操作字串的函式。 它們可以視為 Visual Basic 內建函式;也就是說，您不需要將它們當做類別的明確成員呼叫，如範例所示。 類別中也提供其他方法，在某些情況下互補方法 <xref:System.String?displayProperty=nameWithType> 。

|.NET Framework 方法|Description|
|---------------------------|-----------------|
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|傳回 `Integer` 值，表示對應至字元的字元碼。|
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|傳回與指定的字元碼關聯的字元。|
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|傳回以零起始的陣列，其中包含以指定篩選準則為依據的 `String` 陣列子集。|
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|傳回字串，其格式化方式是根據格式 `String` 運算式內包含的指令。|
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|使用 [系統] 控制台中定義的貨幣符號，傳回格式化成貨幣值的運算式。|
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|傳回表示日期/時間值的字串運算式。|
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|傳回格式化成數字的運算式。|
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|傳回格式化為百分比 (也就是乘以 100) 且尾端包含 % 字元的運算式。|
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|傳回整數，指定一個字串在另一個字串內第一次出現的起始位置。|
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|傳回某個字串在另一個字串中第一次出現的位置，從字串的右邊開始。|
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|傳回結合包含在陣列中幾個子字串所建立的字串。|
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|傳回已轉換成小寫的字串或字元。|
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|傳回字串，其中包含從字串的左邊開始的指定數目的字元。|
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|傳回一個整數，其中包含字串中的字元數。|
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|傳回靠左對齊的字串，其中包含調整為指定之長度的指定字串。|
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|傳回字串，其中包含指定之字串的複本，但沒有開頭空白。|
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|從字串中傳回包含指定字元數的字串。|
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|傳回字串，其中的指定之子字串已經被另一個子字串取代了指定的次數。|
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|傳回字串，其中包含從字串的右邊開始的指定數目的字元。|
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|傳回靠右對齊的字串，其中包含調整為指定之長度的指定字串。|
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|傳回字串，其中包含指定之字串的複本，但沒有尾端空格。|
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|傳回字串，此字串是由指定之空格數所組成。|
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|傳回以零起始的一維陣列，其中包含指定之子字串數目。|
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|根據字串比較的結果傳回 -1、0 或 1。|
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|傳回依照指定方式轉換的字串。|
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|傳回由重複指定次數的指定字元所組成的字串或物件。|
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|傳回字串，其中的指定之字串的字元順序會顛倒。|
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|傳回字串，其中包含指定字串的複本，其中沒有開頭或尾端空格。|
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|傳回包含已轉換成大寫之指定字串的字串或字元。|

您可以使用[Option Compare](../statements/option-compare-statement.md)語句來設定是否要使用由系統的地區設定（）所決定的區分大小寫文字排序次序， `Text` 或字元（）的內部二進位標記法來比較字串 `Binary` 。 預設的文字比較方法是 `Binary` 。

## <a name="example-ucase"></a>範例： UCase

此範例使用 `UCase` 函式，傳回大寫字母版本的字串。
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]

## <a name="example-ltrim"></a>範例： LTrim

此範例使用 `LTrim` 函式刪除字串變數中的前置空格，並使用 `RTrim` 函式刪除字串變數中的尾端空格。 它會使用 `Trim` 函式刪除這兩種類型的空格。

[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]

## <a name="example-mid"></a>範例：中間

這個範例會使用 `Mid` 函數，從字串中傳回指定的字元數。

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]

## <a name="example-len"></a>範例： Len

這個範例使用 `Len` 傳回字串中的字元數。

[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]

## <a name="example-instr"></a>範例： InStr

此範例使用 `InStr` 函式傳回某個字串在另一個字串中第一次出現的位置。

[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]

## <a name="example-format"></a>範例：格式

此範例將示範 `Format` 函式的各種使用方式，以透過 `String` 格式及使用者定義的格式，將值格式化。 對於日期分隔符號 (`/`)、時間分隔符號 (`:`) 和 AM/PM 指示器 (`t` 和 `tt`) 而言，系統顯示的實際格式化輸出需視程式碼使用的地區設定而定。 當時間和日期顯示在開發環境內時，會使用程式碼地區設定的簡短時間格式和簡短日期格式。

> [!NOTE]
> 若為使用 24 小時制的地區設定，AM/PM 指示器 (`t` 和 `tt`) 不會顯示任何內容。

[!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]

## <a name="see-also"></a>另請參閱

- [關鍵字](../keywords/index.md)
- [Visual Basic 執行階段程式庫成員](../runtime-library-members.md)
- [字串操作摘要](../keywords/string-manipulation-summary.md)
- [System.string 類別方法](xref:System.String#methods)
