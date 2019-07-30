---
title: Char 資料類型 (Visual Basic)
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
ms.openlocfilehash: ca40e6c8dcba3da29bdb68b29c91c852e477f8f7
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512783"
---
# <a name="char-data-type-visual-basic"></a>Char 資料類型 (Visual Basic)

保留不帶正負號的16位 (2 位元組) 程式碼點, 範圍介於0到65535之間。 每個程式*代碼點*或字元碼都代表一個 Unicode 字元。

## <a name="remarks"></a>備註

當您只需要保存單一字元, 而且不需要的`String`額外負荷時, 請使用資料類型。`Char` 在某些情況下, 您`Char()`可以使用`Char`元素陣列來保存多個字元。

的預設值`Char`是程式碼點為0的字元。

## <a name="unicode-characters"></a>Unicode 字元

Unicode 的第一個128程式碼點 (0 – 127) 對應到標準美式鍵盤上的字母和符號。 這些前128個程式碼點與 ASCII 字元集所定義的相同。 第二個128程式碼片段 (128 – 255) 代表特殊字元, 例如以拉丁為基礎的字母、重音、貨幣符號和分數。 Unicode 會針對各種不同的符號使用其餘的程式碼點 (256-65535), 包括全球文字字元、變音符號和數學和技術符號。

您可以在<xref:System.Char.IsDigit%2A> `Char`變數上使用<xref:System.Char.IsPunctuation%2A>和之類的方法來判斷其 Unicode 分類。

## <a name="type-conversions"></a>類型轉換

Visual Basic 不會直接在和`Char`數數值型別之間進行轉換。 您可以使用<xref:Microsoft.VisualBasic.Strings.Asc%2A>或<xref:Microsoft.VisualBasic.Strings.AscW%2A>函`Char` 式`Integer` , 將值轉換為代表其程式碼點的。 您可以使用<xref:Microsoft.VisualBasic.Strings.Chr%2A>或<xref:Microsoft.VisualBasic.Strings.ChrW%2A>函數`Integer` ,`Char`將值轉換成具有該程式碼點的。

如果類型檢查參數 ([Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是 on, 您就必須將常數值型別字元附加至單一字元字串常值, 以將它識別`Char`為資料類型。 下列範例將說明這點。

```vb
Option Strict On
Dim charVar As Char
' The following statement attempts to convert a String literal to Char.
' Because Option Strict is On, it generates a compiler error.
charVar = "Z"
' The following statement succeeds because it specifies a Char literal.
charVar = "Z"C
```

## <a name="programming-tips"></a>程式設計提示

- **負數。** `Char`是不帶正負號的類型, 而且不能代表負值。 在任何情況下, 您都不`Char`應該使用來保存數值。

- **Interop 考慮。** 如果您使用不是針對 .NET Framework 所撰寫的元件 (例如 Automation 或 COM 物件) 來進行介面, 請記住, 在其他環境中, 字元類型具有不同的資料寬度 (8 位)。 如果您將8位引數傳遞至這類元件, 請在新`Byte`的`Char` Visual Basic 程式碼中將它宣告為而不是。

- **加寬.** 資料類型會擴大為`String`。 `Char` 這表示您可以將`Char`轉換`String`成<xref:System.OverflowException?displayProperty=nameWithType> , 而且不會遇到錯誤。

- **輸入字元。** 將常數值型別字元`C`附加至單一字元字串常值, 會強制其`Char`成為資料類型。 `Char`沒有識別項型別字元。

- **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Char?displayProperty=nameWithType> 結構。

## <a name="see-also"></a>另請參閱

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [String 資料類型](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [如何：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
