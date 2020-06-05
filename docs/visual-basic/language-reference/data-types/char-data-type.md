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
ms.openlocfilehash: 3dbbf9f6a2c4079775e05f5d2dcd8704c1ec4259
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387474"
---
# <a name="char-data-type-visual-basic"></a>Char 資料類型 (Visual Basic)

保留不帶正負號的16位（2位元組）程式碼點，範圍介於0到65535之間。 每個程式*代碼點*或字元碼都代表一個 Unicode 字元。

## <a name="remarks"></a>備註

`Char`當您只需要保存單一字元，而且不需要的額外負荷時，請使用資料類型 `String` 。 在某些情況下，您可以使用 `Char()` 元素陣列 `Char` 來保存多個字元。

的預設值 `Char` 是程式碼點為0的字元。

## <a name="unicode-characters"></a>Unicode 字元

Unicode 的第一個128程式碼點（0–127）對應到標準美式鍵盤上的字母和符號。 這些前128個程式碼點與 ASCII 字元集所定義的相同。 第二個128程式碼片段（128–255）代表特殊字元，例如以拉丁為基礎的字母、重音、貨幣符號和分數。 Unicode 會針對各種不同的符號使用其餘的程式碼點（256-65535），包括全球文字字元、變音符號和數學和技術符號。

您可以 <xref:System.Char.IsDigit%2A> 在變數上使用和之類的方法 <xref:System.Char.IsPunctuation%2A> `Char` 來判斷其 Unicode 分類。

## <a name="type-conversions"></a>類型轉換

Visual Basic 不會直接在 `Char` 和數數值型別之間進行轉換。 您可以使用 <xref:Microsoft.VisualBasic.Strings.Asc%2A> 或函 <xref:Microsoft.VisualBasic.Strings.AscW%2A> 式，將 `Char` 值轉換為 `Integer` 代表其程式碼點的。 您可以使用 <xref:Microsoft.VisualBasic.Strings.Chr%2A> 或 <xref:Microsoft.VisualBasic.Strings.ChrW%2A> 函數，將值轉換成 `Integer` `Char` 具有該程式碼點的。

如果類型檢查參數（ [Option Strict 語句](../statements/option-strict-statement.md)）為 on，您就必須將常數值型別字元附加至單一字元字串常值，以將它識別為 `Char` 資料類型。 下列範例將說明這點。 第一次指派變數時， `charVar` 會產生編譯器錯誤[BC30512](../../misc/bc30512.md) ，因為 `Option Strict` 是 on。 第二個編譯成功，因為 `c` 常數值型別字元會將常 `Char` 值識別為值。

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

- **負數。** `Char`是不帶正負號的類型，而且不能代表負值。 在任何情況下，您都不應該使用 `Char` 來保存數值。

- **Interop 考量：** 如果您使用不是針對 .NET Framework 所撰寫的元件（例如 Automation 或 COM 物件）來進行介面，請記住，在其他環境中，字元類型具有不同的資料寬度（8位）。 如果您將8位引數傳遞至這類元件，請 `Byte` `Char` 在新的 Visual Basic 程式碼中將它宣告為而不是。

- **加寬.** `Char`資料類型會擴大為 `String` 。 這表示您可以將轉換成 `Char` `String` ，而且不會遇到 <xref:System.OverflowException?displayProperty=nameWithType> 。

- **輸入字元。** 將常數值型別字元附加 `C` 至單一字元字串常值，會強制其成為 `Char` 資料類型。 `Char`沒有識別項型別字元。

- **架構類型：** 在 .NET Framework 中對應的類型為 <xref:System.Char?displayProperty=nameWithType> 結構。

## <a name="see-also"></a>另請參閱

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [資料類型](index.md)
- [String 資料類型](string-data-type.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [轉換摘要](../keywords/conversion-summary.md)
- [作法：呼叫不帶正負號的類型的 Windows 函式](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效率地使用資料類型](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
