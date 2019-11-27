---
title: Char 資料類型
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 1ed5b19a307d094fc1d5a6bb0251c57052dc9bc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344053"
---
# <a name="char-data-type-visual-basic"></a>Char 資料類型 (Visual Basic)

保留不帶正負號的16位（2位元組）程式碼點，範圍介於0到65535之間。 每個程式*代碼點*或字元碼都代表一個 Unicode 字元。

## <a name="remarks"></a>備註

當您只需要保存單一字元，而且不需要 `String`的額外負荷時，請使用 `Char` 資料類型。 在某些情況下，您可以使用 `Char()`（`Char` 元素陣列）來保存多個字元。

`Char` 的預設值是程式碼點為0的字元。

## <a name="unicode-characters"></a>Unicode 字元

Unicode 的第一個128程式碼點（0–127）對應到標準美式鍵盤上的字母和符號。 這些前128個程式碼點與 ASCII 字元集所定義的相同。 第二個128程式碼片段（128–255）代表特殊字元，例如以拉丁為基礎的字母、重音、貨幣符號和分數。 Unicode 會針對各種不同的符號使用其餘的程式碼點（256-65535），包括全球文字字元、變音符號和數學和技術符號。

您可以使用 <xref:System.Char.IsDigit%2A> 之類的方法，並在 `Char` 變數上 <xref:System.Char.IsPunctuation%2A>，以判斷其 Unicode 分類。

## <a name="type-conversions"></a>類型轉換

Visual Basic 不會直接在 `Char` 和數數值型別之間進行轉換。 您可以使用 <xref:Microsoft.VisualBasic.Strings.Asc%2A> 或 <xref:Microsoft.VisualBasic.Strings.AscW%2A> 函數，將 `Char` 值轉換為代表其程式碼點的 `Integer`。 您可以使用 <xref:Microsoft.VisualBasic.Strings.Chr%2A> 或 <xref:Microsoft.VisualBasic.Strings.ChrW%2A> 函數，將 `Integer` 值轉換為具有該程式碼點的 `Char`。

如果類型檢查參數（ [Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)）為 on，您就必須將常數值型別字元附加至單一字元字串常值，以將它識別為 `Char` 資料類型。 下列範例將說明這點。 第一次指派 `charVar` 變數會產生編譯器錯誤[BC30512](../../misc/bc30512.md) ，因為 `Option Strict` 是 on。 第二個編譯成功，因為 `c` 的常數值型別字元將常值識別為 `Char` 值。

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a>程式設計提示

- **負數。** `Char` 是不帶正負號的類型，而且不能代表負值。 在任何情況下，您不應該使用 `Char` 來保存數值。

- **Interop 考慮。** 如果您使用不是針對 .NET Framework 所撰寫的元件（例如 Automation 或 COM 物件）來進行介面，請記住，在其他環境中，字元類型具有不同的資料寬度（8位）。 如果您將8位引數傳遞給這類元件，請將它宣告為 `Byte`，而不是在新的 Visual Basic 程式碼中 `Char`。

- **加寬.** `Char` 資料類型會擴大至 `String`。 這表示您可以將 `Char` 轉換成 `String`，而且不會遇到 <xref:System.OverflowException?displayProperty=nameWithType>。

- **輸入字元。** 將常數值型別字元 `C` 附加至單一字元字串常值，會強制其成為 `Char` 的資料類型。 `Char` 沒有識別項型別字元。

- **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Char?displayProperty=nameWithType> 結構。

## <a name="see-also"></a>請參閱

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [String 資料類型](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
