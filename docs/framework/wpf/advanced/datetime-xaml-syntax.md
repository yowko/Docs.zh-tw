---
title: DateTime XAML 語法
ms.date: 03/30/2017
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
ms.openlocfilehash: 286117cc0cce9fb54ea2c372360b13865fba77ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML 語法
某些控制項，例如<xref:System.Windows.Controls.Calendar>和<xref:System.Windows.Controls.DatePicker>，其屬性可使用<xref:System.DateTime>型別。 雖然您通常會在執行階段時，於程式碼後置中指定這些控制項的初始日期或時間，但仍可在 XAML 中指定初始的日期或時間。 剖析 WPF XAML 剖析器會處理<xref:System.DateTime>使用內建 XAML 文字語法值。 本主題描述的特性<xref:System.DateTime>XAML 文字語法。  
  
  
<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>使用 DateTime XAML 語法的時機  
 在 XAML 中設定日期不是必要的，甚至可能不需要。 例如，您可以使用<xref:System.DateTime.Now%2A?displayProperty=nameWithType>初始化在執行的階段，或您的日期屬性無法進行程式碼後置根據使用者輸入中的行事曆的所有日期調整。 不過，在的案例中，您可能以硬式編碼日期到<xref:System.Windows.Controls.Calendar>和<xref:System.Windows.Controls.DatePicker>控制項樣板中。 <xref:System.DateTime>必須針對這些案例使用 XAML 語法。  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML 語法是原生的行為  
 <xref:System.DateTime> 是 CLR 的基底類別程式庫中定義的類別。 由於如何基底類別庫與相關聯的 CLR 其餘部分，不能套用<xref:System.ComponentModel.TypeConverterAttribute>類別和使用類型轉換器，處理從 XAML 的字串，並將它們轉換成<xref:System.DateTime>執行的階段物件模型中。 沒有可提供轉換行為的 `DateTimeConverter`，本主題中描述的轉換行為是 WPF XAML 剖析器的原生行為。  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML 語法的格式字串  
 您可以指定的格式<xref:System.DateTime>使用的格式字串。 格式字串會正規化可用來建立值的文字語法。 <xref:System.DateTime> 值，針對現有 WPF 控制項通常只能使用的日期元件<xref:System.DateTime>和時間元件。  
  
 當指定<xref:System.DateTime>在 XAML 中，您可以將格式字串的任何交換使用。  
  
 您也可以使用本主題中未特意顯示的格式和格式字串。 技術上來說，針對任何 XAML<xref:System.DateTime>值，指定和 WPF XAML 剖析器會剖析使用的內部呼叫<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>，因此您無法使用所接受的任何字串<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>的 XAML 輸入。 如需詳細資訊，請參閱<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>。  
  
> [!IMPORTANT]
>  一律會使用 DateTime XAML 語法`en-us`為<xref:System.Globalization.CultureInfo>其原生的轉換。 這不會受到<xref:System.Windows.FrameworkElement.Language%2A>值或`xml:lang`值在 XAML 中，因為 XAML 屬性層級類型的轉換都會沒有該內容。 因為文化特性多變，例如日期和月份的顯示順序，請勿嘗試插入此處顯示的格式字串。 此處顯示的格式字串正是剖析 XAML 時使用的格式字串，無論其他文化特性設定為何。  
  
 下列章節將說明一些常見<xref:System.DateTime>格式字串。  
  
### <a name="short-date-pattern-d"></a>簡短日期模式 ("d")  
 下圖顯示的簡短日期格式<xref:System.DateTime>在 XAML 中：  
  
 `M/d/YYYY`  
  
 這是依 WPF 控制項指定一般用法所有必要資訊的最簡單形式，不會受到意外時區位移與時間元件的影響；因此，建議優先選用此格式。  
  
 例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串︰  
  
 `3/1/2010`  
  
 如需詳細資訊，請參閱<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>。  
  
### <a name="sortable-datetime-pattern-s"></a>可排序的 DateTime 模式 ("s")  
 下列範例示範可排序<xref:System.DateTime>在 XAML 中的模式：  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串 (時間元件全都輸入 0)︰  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 模式 ("r")  
 RFC1123 模式之所以有用，是因為它可能是來自有後列情況的其他日期產生器的字串輸入：也因為文化特性多變的原因而使用 RFC1123 模式。 下列範例示範 RFC1123<xref:System.DateTime>在 XAML 中的模式：  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串 (時間元件全都輸入 0)︰  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>其他格式與模式  
 如前所述，<xref:System.DateTime>在 XAML 中可以指定為任何可接受的字串作為輸入的<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>。 這包括其他正式的格式 (例如<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>)，並不會正式為特定的格式<xref:System.Globalization.DateTimeFormatInfo>表單。 例如，表單`YYYY/mm/dd`是可接受作為輸入的<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>。 本主題不會嘗試說明所有可能作用的格式，而是建議使用簡短日期模式為標準做法。  
  
## <a name="see-also"></a>另請參閱  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
