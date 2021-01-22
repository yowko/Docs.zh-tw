---
title: 在 .NET 中顯示和保存格式化資料的最佳作法
description: 瞭解如何在 .NET 應用程式中有效地顯示和保存數值和日期資料。
ms.date: 05/01/2019
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.openlocfilehash: dd2e85ed695072da24b6b25b187810a109b89b25
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693120"
---
# <a name="best-practices-for-displaying-and-persisting-formatted-data"></a>顯示和保存格式化資料的最佳作法

本文將檢查格式化資料（例如數值資料和日期和時間資料）如何針對顯示和儲存進行處理。

當您使用 .NET 進行開發時，請使用區分文化特性的格式，在使用者介面中顯示非字串資料，例如數位和日期。 使用不因 [文化](xref:System.Globalization.CultureInfo.InvariantCulture) 特性而異的格式，以字串形式保存非字串資料。 請勿使用區分文化特性的格式來保存字串格式的數值或日期和時間資料。

## <a name="displaying-formatted-data"></a>顯示格式化的資料

當您向使用者顯示非字串資料 (例如數字及日期和時間) 時，請採用使用者的文化特性設定進行格式化。 根據預設，下列所有項目都會在格式化作業中使用目前執行緒文化特性：

- [C#](../../csharp/language-reference/tokens/interpolated.md) 和 [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) 編譯器支援的插入字串。
- 使用 [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) 或 [Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) 串連運算子或直接呼叫 <xref:System.String.Concat%2A?displayProperty=nameWithType> 方法的字串串連作業。
- <xref:System.String.Format%2A?displayProperty=nameWithType> 方法
- 數值類型以及日期和時間類型的 `ToString` 方法。

若要明確指定應使用指定的文化特性慣例或[不因文化特性而異](xref:System.Globalization.CultureInfo.InvariantCulture)來格式化字串，您可以執行下列動作：

- 使用 <xref:System.String.Format%2A?displayProperty=nameWithType> 和 `ToString` 方法時，呼叫具有 `provider` 參數的多載 (例如 <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 或 <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>)，並為該多載傳遞給 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性 (表示所需文化特性的 <xref:System.Globalization.CultureInfo> 執行個體) 或 <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType> 屬性。

- 針對字串串連，不允許編譯器執行任何隱含的轉換。 反之，藉由呼叫具有 `provider` 參數的 `ToString` 多載來執行明確轉換。 例如，在 <xref:System.Double> 下列程式碼中將值轉換成字串時，編譯器會隱含地使用目前的文化特性：

  [!code-csharp[Implicit String Conversion](./snippets/best-practices-strings/csharp/tostring/Program.cs#1)]
  [!code-vb[Implicit String Conversion](./snippets/best-practices-strings/vb/tostring/Program.vb#1)]

  相反地，您可以藉由呼叫方法，明確地指定要在轉換中使用其格式化慣例的文化特性 <xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType> ，如下列程式碼所示：

  [!code-csharp[Explicit String Conversion](./snippets/best-practices-strings/csharp/tostring/Program.cs#2)]
  [!code-vb[Implicit String Conversion](./snippets/best-practices-strings/vb/tostring/Program.vb#2)]

- 針對字串內插補點，請將插入字串指派給 <xref:System.FormattableString> 執行個體，而非 <xref:System.String>。 接著，您可以呼叫其 <xref:System.FormattableString.ToString?displayProperty=nameWithType> 方法產生會反映目前文化特性慣例的結果字串，也可以呼叫 <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> 方法產生會反映指定文化特性慣例的結果字串。 您也可以將可格式化字串傳遞給靜態的 <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> 方法，以產生會反映不因文化特性而異之慣例的結果字串。 下列範例將示範這個方法。 (此範例的輸出反映 en-US 目前文化特性。)

  [!code-csharp[String interpolation](./snippets/best-practices-strings/csharp/formattable/Program.cs)]
  [!code-vb[String interpolation](./snippets/best-practices-strings/vb/formattable/Program.vb)]

## <a name="persisting-formatted-data"></a>保存格式化的資料

您可將非字串資料保存為二進位資料或格式化的資料。 如果您選擇將它儲存為格式化的資料，您應該呼叫包含 `provider` 參數之格式化方法的多載，並將 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 屬性傳遞給它。 針對獨立於文化特性和機器的格式化資料，不因國別而異的文化特性可提供一致的格式。 相較之下，如果資料並非使用不因國別而異的文化特性，而是使用其他文化特性來進行格式化，這類資料的保存會有許多限制：

- 如果在具有不同文化特性的系統上擷取資料，或者，目前系統的使用者變更目前的文化特性，並嘗試擷取資料時，該資料可能會無法使用。
- 特定電腦上的文化特性屬性可能不同於標準值。 使用者可以隨時自訂區分文化特性的顯示設定。 因為這個緣故，使用者自訂文化特性設定之後，可能無法讀取系統上儲存的格式化資料。 格式化資料在電腦之間的可攜性可能會有更多限制。
- 當數字或日期和時間格式的規範標準 (不論全球、地區或國際標準) 隨著時間變更時，這些變更會併入 Windows 作業系統更新當中。 當格式化慣例改變時，使用先前慣例來格式化的資料可能會變成無法讀取。

下列範例說明使用區分文化特性的格式來保存資料時產生的可攜性限制。 此範例會將日期和時間值陣列儲存至檔案。 這些值是使用英文 (美國) 文化特性的慣例來進行格式化。 當應用程式將目前執行緒文化特性變更為法文 (瑞士) 後，它會嘗試使用目前文化特性的格式化慣例來讀取儲存的值。 嘗試讀取這兩樣資料項目後，會擲回 <xref:System.FormatException> 例外狀況，且日期陣列現在會包含兩個等於 <xref:System.DateTime.MinValue>的不正確項目。

[!code-csharp[Conceptual.Strings.BestPractices#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
[!code-vb[Conceptual.Strings.BestPractices#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]

但是，如果您將的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性取代 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 為對和的 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 呼叫 <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ，則會成功還原持續性的日期和時間資料，如下列輸出所示：

```console
06.05.1758 21:26
05.05.1818 07:19
22.04.1870 23:54
08.09.1890 06:47
18.02.1905 15:12
```
