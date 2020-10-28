---
title: 列舉格式字串
description: 使用 .NET 中的列舉. ToString 方法來建立列舉格式字串。 格式化列舉成員的數值、十六進位或字串值。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
ms.openlocfilehash: e4d8ca27d99c211653269b2477be8f5632b78229
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888655"
---
# <a name="enumeration-format-strings"></a>列舉格式字串

您可以使用 <xref:System.Enum.ToString%2A?displayProperty=nameWithType> 方法來建立新的字串物件，以表示列舉成員的數值、十六進位值或字串值。 這個方法會採用其中一個列舉格式字串，來指定您想要傳回的值。

下列各節列出列舉格式字串及其傳回的值。 這些格式規範不區分大小寫。

## <a name="g-or-g"></a>G 或 g

盡可能以字串值來顯示列舉項目；如果不可能，則會顯示目前執行個體的整數值。 如果列舉是使用 **Flags** 屬性集來定義，每個有效項目的字串值會串連在一起，並以逗號分隔。 如果未設定 **Flags** 屬性，則會以數值項目顯示無效的值。 下列範例說明 G 格式規範。

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a>F 或 f

盡可能以字串值來顯示列舉項目。 如果此值可完整顯示為列舉中的項目總合 (即使 **Flags** 屬性不存在)，每個有效項目的字串值會串連在一起，並以逗號分隔。 如果該值不完全取決於列舉項目，則會格式化為整數值。 下列範例說明 F 格式規範。

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a>D 或 d

盡可能以最短的整數值表示來顯示列舉項目。 下列範例說明 D 格式規範。

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a>X 或 x

以十六進位值來顯示列舉項目。 值在必要的情況下會以前置零來表示，以確保結果字串使用兩個字元代表列舉類型之[底層數值類型](xref:System.Enum.GetUnderlyingType%2A)每個位元組。 下列範例說明 X 格式規範。 在範例中，<xref:System.ConsoleColor> 與 <xref:System.IO.FileAttributes> 兩者的底層類型是 <xref:System.Int32>，或 32 位元 (或 4 位元) 整數，這會產生 8 個字元的結果字串。

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>範例

下列範例會定義名為 `Colors` 的列舉，該列舉是由三個項目所組成︰`Red`、`Blue` 和 `Green`。

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

定義列舉之後，可利用下列方式宣告執行個體。

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

然後可使用 `Color.ToString(System.String)` 方法，根據傳遞給列舉值的格式規範，以不同的方式來顯示列舉值。

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>請參閱

- [格式化類型](formatting-types.md)
