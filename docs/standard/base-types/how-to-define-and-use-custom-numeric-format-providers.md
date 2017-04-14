---
title: "如何：定義和使用自訂數值格式提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自訂格式字串"
  - "自訂數值格式字串"
  - "顯示日期和時間資料"
  - "格式提供者 [.NET Framework]"
  - "格式化 [.NET Framework], 數字"
  - "數字格式化 [.NET Framework]"
  - "數字 [.NET Framework], 自訂數值格式字串"
  - "數值格式字串 [.NET Framework]"
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：定義和使用自訂數值格式提供者
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 可讓您有效掌控數值的字串表示。  它支援以下自訂數值格式的功能：  
  
-   標準數值格式字串，這些字串提供預先定義的格式集，可將數字轉換成其字串表示。  您可以使用這些字串搭配任何擁有 `format` 參數的數值格式化方法，例如 <xref:System.Decimal.ToString%28System.String%29?displayProperty=fullName>。  如需詳細資訊，請參閱 [標準數值格式字串](../../../docs/standard/base-types/standard-numeric-format-strings.md)。  
  
-   自訂數值格式字串，這些字串提供能夠合併的符號集，可用來定義自訂數值格式規範。  這些字串可以搭配任何擁有 `format` 參數的數值格式化方法使用，例如 <xref:System.Decimal.ToString%28System.String%29?displayProperty=fullName>。  如需詳細資訊，請參閱 [自訂數值格式字串](../../../docs/standard/base-types/custom-numeric-format-strings.md)。  
  
-   自訂 <xref:System.Globalization.CultureInfo> 或是 <xref:System.Globalization.NumberFormatInfo> 物件，該物件定義用來顯示數值之字串表示的符號和格式模式。  您可以使用這些模式搭配任何擁有 `provider` 參數的數值格式化方法，例如 <xref:System.Int32.ToString%2A>。  通常 `provider` 參數會用來指定文化特性專屬的格式設定。  
  
 在某些情況下，這三項技術並不適用 \(例如，應用程式必須顯示格式化帳號、身分證號碼或是郵遞區號時\)。  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 還可讓您定義決定如何格式化數值的格式化物件，該物件既不是 <xref:System.Globalization.CultureInfo> 也不是 <xref:System.Globalization.NumberFormatInfo> 物件。  本主題將提供實作這類物件的逐步指示，以及提供格式化電話號碼的範例。  
  
### 定義自訂格式提供者  
  
1.  定義實作 <xref:System.IFormatProvider> 和 <xref:System.ICustomFormatter> 介面的類別。  
  
2.  實作 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=fullName> 方法。  <xref:System.IFormatProvider.GetFormat%2A> 是格式化方法 \(例如 [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> 方法\) 叫用的回呼方法，用來擷取實際負責執行自訂格式顯示的物件。  <xref:System.IFormatProvider.GetFormat%2A> 的一般實作會執行下列操作：  
  
    1.  判斷做為方法參數傳遞的 <xref:System.Type> 物件是否代表 <xref:System.ICustomFormatter> 介面。  
  
    2.  如果參數確實代表 <xref:System.ICustomFormatter> 介面，則 <xref:System.IFormatProvider.GetFormat%2A> 會傳回實作 <xref:System.ICustomFormatter> 介面的物件，該介面負責提供自訂的格式顯示。  通常，自訂格式顯示物件會自行傳回。  
  
    3.  如果參數不代表 <xref:System.ICustomFormatter> 介面，則 <xref:System.IFormatProvider.GetFormat%2A> 會傳回 `null`。  
  
3.  實作 <xref:System.ICustomFormatter.Format%2A> 方法。  這個方法是由 [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> 方法呼叫，並且負責傳回數字的字串表示。  實作這個方法通常包含下列各項：  
  
    1.  \(選用\) 檢查 `provider` 參數，確認這個方法的合法目的為提供格式化服務。  針對實作 <xref:System.IFormatProvider> 與 <xref:System.ICustomFormatter> 的格式化物件，這項檢查包含測試 `provider` 參數是否與目前的格式設定物件相等。  
  
    2.  決定格式化物件是否應支援自訂格式規範 \(例如， 「N」格式規範可能表示應使用 NANP 格式輸出美國電話號碼，而「I」可能表示使用 ITU\-T Recommendation E.123 格式輸出\)。如果使用格式規範，則這個方法應處理特定格式規範。  格式規範會隨 `format` 參數傳遞至方法。  如果沒有規範，則 `format` 參數值為 <xref:System.String.Empty?displayProperty=fullName>。  
  
    3.  擷取做為 `arg` 參數傳遞至方法的數值。  執行必要的處理方式，將它轉換成其字串表示。  
  
    4.  傳回 `arg` 參數的字串表示。  
  
### 使用自訂數值格式化物件  
  
1.  建立自訂格式類別的新執行個體。  
  
2.  呼叫 [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> 格式化方法，將自訂格式物件、格式規範 \(沒有使用的話則為 <xref:System.String.Empty?displayProperty=fullName>\) 及要格式化的數值傳遞給該方法。  
  
## 範例  
 下列範例定義數字轉換成美國電話號碼的數字轉換成 NANP 或 E.123 格式的 `TelephoneFormatter`自訂數值格式提供者名稱 。  這個方法會處理兩種格式規範："N" \(輸出 NANP 格式\) 和 "I" \(輸出國際 E.123 格式\)。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 自訂數值格式提供者只能搭配 [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> 方法使用。  其他擁有 <xref:System.IFormatProvider> 型別參數的數值格式化方法多載 \(例如 `ToString`\)，全都會將代表 <xref:System.Globalization.NumberFormatInfo> 型別的 <xref:System.Type> 物件傳遞給 <xref:System.IFormatProvider.GetFormat%2A?displayProperty=fullName> 實作。  接著這些多載會期待方法傳回 <xref:System.Globalization.NumberFormatInfo> 物件。  如果方法未傳回該物件，則會忽略自訂數值格式提供者，並且使用目前文化特性的 <xref:System.Globalization.NumberFormatInfo> 物件取代。  在本範例中，`TelephoneFormatter.GetFormat` 方法會檢查方法參數及傳回 `null` \(如果其代表 <xref:System.ICustomFormatter> 以外的型別\)，藉此處理可能不當傳遞至數值格式化方法的情況。  
  
 自訂數值格式提供者支援格式規範集時，如果 [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> 方法呼叫中使用的格式項目未提供格式規範，則務必確實提供預設的行為。  在本範例中，"N" 為預設的格式規範。  如此即可提供明確格式規範，將數字轉換成格式化的電話號碼。  以下範例將說明這類方法呼叫。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 不過，它也會允許在沒有格式規範的情況下進行轉換。  以下範例將說明這類方法呼叫。  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 如果未定義預設的格式規範，您的 <xref:System.ICustomFormatter.Format%2A?displayProperty=fullName> 方法實作就應包含下面所示的程式碼，如此 .NET Framework 才能提供您的程式碼不支援的格式。  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 在本範例的案例中，實作 <xref:System.ICustomFormatter.Format%2A?displayProperty=fullName> 的方法將做為 [String.Format\(IFormatProvider, String, Object\<xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName> 方法的回呼方法。  因此，它會檢查 `formatProvider` 參數，以判斷其中是否包含目前 `TelephoneFormatter` 物件的參考。  不過，這個方法也可以直接從程式碼呼叫。  在這種情況下，您可以使用 `formatProvider` 參數提供 <xref:System.Globalization.CultureInfo> 或 <xref:System.Globalization.NumberFormatInfo> 物件，該物件會提供文化特性專屬的格式資訊。  
  
## 編譯程式碼  
 使用 csc.exe 或 vb.exe 在命令列編輯程式碼。  若要編譯 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中的程式碼，請將程式碼放在主控台應用程式專案範本中。  
  
## 請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)