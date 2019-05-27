---
title: 作法：定義和使用自訂數值格式提供者
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- custom numeric format strings
- numbers [.NET Framework], custom numeric format strings
- displaying date and time data
- format providers [.NET Framework]
- custom format strings
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3898caa90c695ae681c2d9b20abbba57a2a9f61
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590466"
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>作法：定義和使用自訂數值格式提供者
.NET Framework 可讓您有效掌控數值的字串表示。 它支援以下自訂數值格式的功能：  
  
- 標準數值格式字串，這些字串提供預先定義的格式集，可將數字轉換成其字串表示。 您可以使用它們搭配任何擁有 `format` 參數的數值格式化方法，例如 <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>。 如需詳細資訊，請參閱[標準數值格式字串](../../../docs/standard/base-types/standard-numeric-format-strings.md)。  
  
- 自訂數值格式字串，這些字串提供能夠合併的符號集，可用來定義自訂數值格式規範。 它們也可以搭配任何擁有 `format` 參數的數值格式化方法使用，例如 <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>。 如需詳細資訊，請參閱[自訂數值格式字串](../../../docs/standard/base-types/custom-numeric-format-strings.md)。  
  
- 自訂的 <xref:System.Globalization.CultureInfo> 或 <xref:System.Globalization.NumberFormatInfo> 物件，這類物件會定義用來顯示數值字串表示的符號和格式模式。 您可以使用它們搭配任何擁有 `provider` 參數的數值格式化方法，例如 <xref:System.Int32.ToString%2A>。 一般而言，會使用 `provider` 參數來指定文化特性特定的格式。  
  
 在某些情況下，這三項技術並不適用 (例如，應用程式必須顯示格式化帳號、身分證號碼或是郵遞區號時)。 .NET Framework 還可讓您定義既不是 <xref:System.Globalization.CultureInfo> 也不是 <xref:System.Globalization.NumberFormatInfo> 物件的格式物件，以判斷如何將數值格式化。 本主題提供實作這類物件的逐步指示，並提供格式化電話號碼的範例。  
  
### <a name="to-define-a-custom-format-provider"></a>定義自訂格式提供者  
  
1. 定義實作 <xref:System.IFormatProvider> 和 <xref:System.ICustomFormatter> 介面的類別。  
  
2. 實作 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 方法。 <xref:System.IFormatProvider.GetFormat%2A> 是一個回呼方法，格式化方法 (例如 <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法) 可叫用來擷取實際負責執行自訂格式的物件。 <xref:System.IFormatProvider.GetFormat%2A> 的一般實作會執行下列操作：  
  
    1. 判斷作為方法參數傳遞的 <xref:System.Type> 物件是否代表 <xref:System.ICustomFormatter> 介面。  
  
    2. 如果參數確實代表 <xref:System.ICustomFormatter> 介面，則 <xref:System.IFormatProvider.GetFormat%2A> 會傳回實作 <xref:System.ICustomFormatter> 介面的物件，該介面負責提供自訂格式。 一般而言，自訂格式物件會自行傳回。  
  
    3. 如果參數不代表 <xref:System.ICustomFormatter> 介面，<xref:System.IFormatProvider.GetFormat%2A> 就會傳回 `null`。  
  
3. 實作 <xref:System.ICustomFormatter.Format%2A> 方法。 這個方法會由 <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法呼叫，並負責傳回數字的字串表示。 實作這個方法通常包含下列各項：  
  
    1. (選擇性) 藉由檢查 `provider` 參數，來確認這個方法的合法目的為提供格式化服務。 針對實作 <xref:System.IFormatProvider> 與 <xref:System.ICustomFormatter> 的格式物件，這項檢查包含測試 `provider` 參數是否與目前的格式物件相等。  
  
    2. 決定格式物件是否應支援自訂格式規範 (例如，"N" 格式規範可能表示應使用 NANP 格式輸出美國電話號碼，而 "I" 可能表示使用 ITU-T Recommendation E.123 格式輸出)。如果使用格式規範，則這個方法應處理特定格式規範。 格式規範會隨 `format` 參數傳遞至方法。 如果沒有規範，則 `format` 參數值為 <xref:System.String.Empty?displayProperty=nameWithType>。  
  
    3. 擷取作為 `arg` 參數傳遞至方法的數值。 執行任何必要的操作，將它轉換成其字串表示。  
  
    4. 傳回 `arg` 參數的字串表示。  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>使用自訂數值格式物件  
  
1. 建立自訂格式類別的新執行個體。  
  
2. 呼叫 <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 格式化方法，將自訂格式物件、格式規範 (如果未使用，則為 <xref:System.String.Empty?displayProperty=nameWithType>) 及要格式化的數值傳遞給該方法。  
  
## <a name="example"></a>範例  
 下列範例會定義名為 `TelephoneFormatter` 的自訂數值格式提供者，它會將代表美國電話號碼的數字轉換成 NANP 或 E.123 格式。 這個方法會處理兩種格式規範："N" (輸出 NANP 格式) 和 "I" (輸出國際 E.123 格式)。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 自訂數值格式提供者只能與 <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法搭配使用。 其他擁有 <xref:System.IFormatProvider> 類型參數的數值格式化方法多載 (例如 `ToString`)，全都會將代表 <xref:System.Globalization.NumberFormatInfo> 類型的 <xref:System.Type> 物件傳遞給 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> 實作。 接著，它們預期方法會傳回 <xref:System.Globalization.NumberFormatInfo> 物件。 如果未傳回，則會忽略自訂數值格式提供者，並使用目前文化特性的 <xref:System.Globalization.NumberFormatInfo> 物件來取代。 在此範例中，`TelephoneFormatter.GetFormat` 方法會檢查方法參數並傳回 `null` (如果其代表 <xref:System.ICustomFormatter> 以外的類型)，藉以處理可能不當傳遞至數值格式化方法的情況。  
  
 當自訂數值格式提供者支援一組格式規範時，如果 <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法呼叫中使用的格式項目內並未提供格式規範，請務必確定會提供預設的行為。 在此範例中，"N" 是預設的格式規範。 如此即可提供明確格式規範，將數字轉換成格式化的電話號碼。 下列範例說明這類方法呼叫。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 不過，它也允許在沒有格式規範的情況下進行轉換。 下列範例說明這類方法呼叫。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 如果未定義預設的格式規範，您的 <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> 方法實作就應包含如下面所示的程式碼，如此 .NET 才能提供您程式碼不支援的格式。  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 在此範例中，實作 <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> 的方法是用來作為 <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法的回呼方法。 因此，它會檢查 `formatProvider` 參數，以判斷其中是否包含目前 `TelephoneFormatter` 物件的參考。 不過，此方法也可以直接從程式碼呼叫。 在此情況下，您可以使用 `formatProvider` 參數來提供 <xref:System.Globalization.CultureInfo> 或 <xref:System.Globalization.NumberFormatInfo> 物件，該物件會提供文化特性特定的格式資訊。  
  
## <a name="see-also"></a>另請參閱

- [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)
