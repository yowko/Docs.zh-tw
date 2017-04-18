---
title: "DateTime XAML 語法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DateTime XAML 語法 [WPF]"
  - "DateTime XAML 語法 [WPF], 格式字串"
  - "DateTime XAML 語法 [WPF], 字串"
  - "DateTime XAML 語法 [WPF], 使用位置"
  - "DateTime XAML 文字 [WPF]"
  - "簡短日期格式 [WPF], DateTime"
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# DateTime XAML 語法
一些控制項，如<xref:System.Windows.Controls.Calendar>和<xref:System.Windows.Controls.DatePicker> 含有使用<xref:System.DateTime>類型的屬性。  雖然您通常可以在執行階段在後置程式碼中指定這些控制項的初始日期或時間，但您也可以在 XAML 中指定初始日期或時間。  WPF XAML 剖析器會使用內建的 XAML 文字語法處理 <xref:System.DateTime> 值的剖析。  本主題描述 <xref:System.DateTime> XAML 文字語法的細節。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="where_datetime_xaml_syntax_is_used"></a>   
## 何時使用 DateTime XAML 語法  
 不見得需要在 XAML 中設定日期，甚至最好不要。  例如，您可以使用<xref:System.DateTime.Now%2A?displayProperty=fullName>屬性在執行階段初始化一個日期，也可以根據使用者輸入在程式碼後置調整所有日曆的日期。  不過，有些情況下，您可能要將日期硬編碼到控制項範本中的 <xref:System.Windows.Controls.Calendar>和<xref:System.Windows.Controls.DatePicker>。  <xref:System.DateTime> XAML 語法必須用於這些情節。  
  
### DateTime XAML 語法是原生行為  
 <xref:System.DateTime> 是在 CLR 的基底類別程式庫中定義的類別。  因為基底類別庫與其餘 CLR 的相關方式，因此不可能將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至類別並使用型別轉換子處理來自 XAML 的字串，並將它們轉換成執行階段物件模型中的 <xref:System.DateTime>。  沒有任何提供轉換行為的 `DateTimeConverter` 類別。本主題中描述的轉換行為是 WPF XAML 剖析器的原生行為。  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## DateTime XAML 語法的格式字串  
 您可以透過格式字串指定 <xref:System.DateTime> 的格式。  格式字串會使可用於建立値的文字與法成形。  現有 WPF 控制項的 <xref:System.DateTime> 値通常只使用 <xref:System.DateTime> 的日期元件而不使用時間元件。  
  
 在 XAML 中指定 <xref:System.DateTime> 時, 可以交替使用任何格式字串。  
  
 您也可以使用本主題未特別說明的格式和格式字串。  技術上，任何指定且由 WPF XAML 剖析程式剖析的 <xref:System.DateTime> 值，都會使用對 <xref:System.DateTime.Parse%2A?displayProperty=fullName> 的內部呼叫，因此您可以使用 <xref:System.DateTime.Parse%2A?displayProperty=fullName> 可接受的任何字串做為 XAML 輸入。  如需詳細資訊，請參閱 <xref:System.DateTime.Parse%2A?displayProperty=fullName>。  
  
> [!IMPORTANT]
>  DateTime XAML 語法一定會使用 `en-us` 做為其原生轉換的  <xref:System.Globalization.CultureInfo>。  這並非受 <xref:System.Windows.FrameworkElement.Language%2A> 值或 XAML 中的 `xml:lang` 值影響，因為 XAML 屬性層級的型別轉換可在沒有該內容的情況下運作。  請勿嘗試插入此處音文化特性差異而顯示的格式字串，例如日和月出現的順序。  此處所顯示的格式字串即為剖析 XAML 時使用的格式字串 \(不論其他文化特性設定\)。  
  
 下列各節說明一些常見的 <xref:System.DateTime> 格式字串。  
  
### 簡短日期模式 \("d"\)。  
 以下顯示 <xref:System.DateTime> 在 XAML 中的簡短日期格式：  
  
 `M/d/YYYY`  
  
 這是最簡單的形式，可指定 WPF 控制項一般使用方式的所有必要資訊，而且不會受意外時區位移與時間元件影響，因此建議使用此格式取代其他格式。  
  
 例如，若要指定 2010 年 6 月 1 這個日期，請使用下列字串：  
  
 `3/1/2010`  
  
 如需詳細資訊，請參閱 <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=fullName>。  
  
### 可排序 DateTime 模式 \("s"\)。  
 以下顯示 XAML 中的可排序 <xref:System.DateTime> 模式：  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 例如，若要指定 2010 年 6 月 1 這個日期，請使用下列字串 \(時間元件均輸入 0\)：  
  
 `2010-06-01T000:00:00`  
  
### RFC1123 模式 \("r"\)  
 RFC1123 模式非常有用，因為它可以是從其他同樣基於不因文化特性而異的因素而使用 RFC1123 模式的日期產生器的輸入字串。  以下顯示 XAML 中的 RFC1123 <xref:System.DateTime> 模式：  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 例如，若要指定 2010 年 6 月 1 這個日期，請使用下列字串 \(時間元件均輸入 0\)：  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### 其他格式及模式  
 如前所述，可以將 XAML 中的 <xref:System.DateTime> 指定為任何可做為 <xref:System.DateTime.Parse%2A?displayProperty=fullName> 輸入的字串。  這包括其他正式的格式 \(例如 <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>\)，以及未正式化為特定 <xref:System.Globalization.DateTimeFormatInfo> 表單的格式。  例如，表單 `YYYY/mm/dd` 是可接受的 <xref:System.DateTime.Parse%2A?displayProperty=fullName> 輸入。  本主題不會嘗試描述該工作所有可能的格式，而會建議以簡短日期模式進行做為標準練習。  
  
## 請參閱  
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)