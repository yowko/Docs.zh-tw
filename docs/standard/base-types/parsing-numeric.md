---
title: "在 .NET Framework 中剖析數值字串 | Microsoft Docs"
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
  - "剖析字串，數值字串"
  - "數值字串"
  - "列舉 [.NET Framework]，剖析字串"
  - "基底類型，剖析字串"
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# 在 .NET Framework 中剖析數值字串
所有數值型別都有兩個靜態剖析方法 `Parse` 和 `TryParse`，您可以使用這兩種方法將數字的字串表示轉換成數字型別。  這些方法可讓您剖析使用[標準數值格式字串](../../../docs/standard/base-types/standard-numeric-format-strings.md)和[自訂數值格式字串](../../../docs/standard/base-types/custom-numeric-format-strings.md)中記載的格式字串所產生的字串。  根據域設，`Parse` 和 `TryParse` 方法能夠成功將只包含整數十進位數字的字串轉換成整數值。  這兩種方法可成功將包含整數和小數十進位數字、群組分隔符號和小數分隔符號的字串轉換成浮點值。  如果作業失敗，`Parse` 方法會擲回例外狀況，而 `TryParse` 方法會傳回 `false`。  
  
## 剖析和格式提供者  
 通常數值的字串表示會因文化特性而異。  數值字串的項目都會因文化特性而有所不同，包括貨幣符號、群組 \(或千分位\) 分隔符號以及小數分隔符號。  剖析方法會隱含或明確地使用辨識這些文化特性專屬變化的格式提供者。  如果 `Parse` 或 `TryParse` 的呼叫中未指定格式提供者，則會使用與目前執行緒文化特性 \(<xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=fullName> 屬性傳回的 <xref:System.Globalization.NumberFormatInfo> 物件\) 相關聯的格式提供者。  
  
 格式提供者是由 <xref:System.IFormatProvider> 實作表示。  這個介面擁有單一成員，也就是 <xref:System.IFormatProvider.GetFormat%2A> 方法，其單一參數為代表要格式化之型別的 <xref:System.Type> 物件。  這個方法會傳回提供格式資訊的物件。  .NET Framework 支援下面兩個剖析數值字串的 <xref:System.IFormatProvider> 實作：  
  
-   <xref:System.Globalization.CultureInfo> 方法，其 <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=fullName> 方法會傳回提供特定文化特性格式資訊的 <xref:System.Globalization.NumberFormatInfo> 物件。  
  
-   <xref:System.Globalization.NumberFormatInfo> 物件，其 <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=fullName> 方法會傳回自己本身。  
  
 下列範例會嘗試將陣列中的每個字串轉換成 <xref:System.Double> 值。  它會先嘗試使用反映英文 \(美國\) 文化特性之慣例的格式提供者剖析字串。  如果這個作業擲回 <xref:System.FormatException>，它會先嘗試使用反映法文 \(法國\) 文化特性之慣例的格式提供者剖析字串。  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## 剖析和 NumberStyles 值  
 剖析作業可以處理的樣式項目 \(例如泛空白字元、群組分隔符號和小數分隔符號\) 是由 <xref:System.Globalization.NumberStyles> 列舉值所定義。  根據預設，代表整數值的字串是使用 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 值剖析，這樣只會允許數字、前置和尾端空白字元，以及前置正負號。  代表浮點值的字串是使用 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 和 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 值的組合進行剖析，這個複合樣式允許十進位數字與前置和尾端空白字元、前置正負號、小數分隔符號、群組分隔符號及指數。  藉由呼叫包含 <xref:System.Globalization.NumberStyles> 型別之參數的 `Parse` 或 `TryParse` 方法多載，以及設定一個或多個 <xref:System.Globalization.NumberStyles> 旗標，您就可以控制能夠出現在字串中，使剖析作業成功的樣式項目。  
  
 例如，包含群組分隔符號的字串，無法使用 <xref:System.Int32.Parse%28System.String%29?displayProperty=fullName> 方法來轉換為 <xref:System.Int32> 值。  然而，如果您使用 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 旗標，如下列範例所示，則轉換成功。  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  剖析作業永遠使用特定文化特性的格式慣例。  如果您不是用傳遞 <xref:System.Globalization.CultureInfo> 或 <xref:System.Globalization.NumberFormatInfo> 物件的方式來指定文化特性，則會使用與目前執行緒相關聯的文化特性。  
  
 下表列出 <xref:System.Globalization.NumberStyles> 列舉型別的成員，並且描述這些成員對剖析作業的影響。  
  
|NumberStyles 值|對於要剖析之字串的影響|  
|--------------------|-----------------|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|只允許數字。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|允許小數分隔符號和小數點後數字。  若為整數值，則僅允許零做為小數點後數字。  有效的小數分隔符號是由 <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=fullName> 或 <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=fullName> 屬性決定。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|"e" 或 "E" 字元可以用來表示指數標記法。  如需詳細資訊，請參閱 <xref:System.Globalization.NumberStyles>。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|允許前置空白字元。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|允許尾端空白字元。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|數字前面可以加上正負號。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|數字後面可以加上正負號。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|可以使用括號表示負值。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|允許群組分隔符號。  群組分隔符號字元是由 <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=fullName> 或 <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=fullName> 屬性決定。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|允許貨幣符號。  貨幣符號是由 <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=fullName> 屬性所定義。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|要剖析的字串會解譯為十六進位數字。  該字串可包含十六進位數字 0\-9、A\-F 和 a\-f。  這個旗標只可用來剖析整數值。|  
  
 此外，<xref:System.Globalization.NumberStyles> 列舉型別還提供下列複合樣式，這些樣式中包括多個 <xref:System.Globalization.NumberStyles> 旗標。  
  
|複合的 NumberStyles 值|包括成員|  
|------------------------|----------|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|包括 <xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName> 和 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 樣式。  這是用來剖析整數值的預設樣式。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|包括 <xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName> 和 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 樣式。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|包括 <xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName> 和 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 樣式。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|包括所有樣式，除了 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 和 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 之外。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|包括所有樣式，除了 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 之外。|  
|<xref:System.Globalization.NumberStyles?displayProperty=fullName>|包括 <xref:System.Globalization.NumberStyles?displayProperty=fullName>、<xref:System.Globalization.NumberStyles?displayProperty=fullName> 和 <xref:System.Globalization.NumberStyles?displayProperty=fullName> 樣式。|  
  
## 剖析和 Unicode 數字  
 Unicode 標準會定義各種書寫系統中數字的字碼指標。  例如，U\+0030 到 U\+0039 的字碼指標表示基本拉丁文數字 0 到 9，U\+09E6 到 U\+09EF 字碼指標表示孟加拉文數字 0 到 9，而 U\+FF10 到 U\+FF19 字碼指數表示全形數字 0 到 9。  不過，剖析方法唯一能夠辨識的數字為字碼指標 U\+0030 到 U\+0039 的基本拉丁數字 0 到 9。  如果傳遞包含任何其他數字的字串給數值剖析方法，則該方法會擲回 <xref:System.FormatException>。  
  
 下列範例使用 <xref:System.Int32.Parse%2A?displayProperty=fullName> 方法剖析由不同書寫系統的數字所組成的字串。  如範例的輸出所示，嘗試剖析基本拉丁數字會成功，而嘗試剖析全型、阿拉伯\-印度和孟加拉數字則會失敗。  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## 請參閱  
 <xref:System.Globalization.NumberStyles>   
 [剖析字串](../../../docs/standard/base-types/parsing-strings.md)   
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)