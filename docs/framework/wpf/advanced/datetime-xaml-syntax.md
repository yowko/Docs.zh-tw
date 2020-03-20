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
ms.openlocfilehash: 57b73d3b80f0392b99aacfbfac4d8709f72d52e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186323"
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML 語法
某些控制項（如<xref:System.Windows.Controls.Calendar>和<xref:System.Windows.Controls.DatePicker>） 具有使用<xref:System.DateTime>類型的屬性。 雖然您通常會在執行階段時，於程式碼後置中指定這些控制項的初始日期或時間，但仍可在 XAML 中指定初始的日期或時間。 WPF XAML 解析器使用內置的<xref:System.DateTime>XAML 文本語法處理值解析。 本主題介紹<xref:System.DateTime>XAML 文本語法的具體細節。  

<a name="where_datetime_xaml_syntax_is_used"></a>
## <a name="when-to-use-datetime-xaml-syntax"></a>使用 DateTime XAML 語法的時機  
 在 XAML 中設定日期不是必要的，甚至可能不需要。 例如，可以使用 屬性<xref:System.DateTime.Now%2A?displayProperty=nameWithType>在運行時初始化日期，也可以根據使用者輸入在代碼後面執行日曆的所有日期調整。 但是，在某些情況下，您可能希望將日期硬編碼到<xref:System.Windows.Controls.Calendar>和<xref:System.Windows.Controls.DatePicker>控制項範本中。 <xref:System.DateTime> XAML 語法必須用於這些方案。  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML 語法是原生的行為  
 <xref:System.DateTime>是在 CLR 的基類庫中定義的類。 由於基類庫與 CLR 的其餘部分的關係，因此無法應用於<xref:System.ComponentModel.TypeConverterAttribute>類並使用類型轉換器處理來自 XAML 的字串並將其轉換為<xref:System.DateTime>運行時物件模型中的字串。 沒有可提供轉換行為的 `DateTimeConverter`，本主題中描述的轉換行為是 WPF XAML 剖析器的原生行為。  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML 語法的格式字串  
 可以使用格式字串指定 的<xref:System.DateTime>格式。 格式字串會正規化可用來建立值的文字語法。 <xref:System.DateTime>現有 WPF 控制項的值通常只使用 時間元件的日期元件<xref:System.DateTime>，而不是時間元件的日期元件。  
  
 在 XAML 中指定 時<xref:System.DateTime>，可以互換使用任何格式字串。  
  
 您也可以使用本主題中未特意顯示的格式和格式字串。 從技術上講，WPF XAML<xref:System.DateTime>解析器指定然後解析的任何值的 XAML 都使用 內部調用 ，<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>因此可以使用 XAML 輸入接受<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>的任何字串。 如需詳細資訊，請參閱 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>。  
  
> [!IMPORTANT]
> DateTime XAML 語法始終`en-us`用作<xref:System.Globalization.CultureInfo>本機轉換。 這不受 XAML <xref:System.Windows.FrameworkElement.Language%2A> `xml:lang`中的值或值的影響，因為 XAML 屬性級別類型轉換在沒有該上下文的情況下進行。 因為文化特性多變，例如日期和月份的顯示順序，請勿嘗試插入此處顯示的格式字串。 此處顯示的格式字串正是剖析 XAML 時使用的格式字串，無論其他文化特性設定為何。  
  
 以下各節介紹一些常見的<xref:System.DateTime>格式字串。  
  
### <a name="short-date-pattern-d"></a>簡短日期模式 ("d")  
 下面顯示了 XAML 中<xref:System.DateTime>a 的短日期格式：  
  
 `M/d/YYYY`  
  
 這是依 WPF 控制項指定一般用法所有必要資訊的最簡單形式，不會受到意外時區位移與時間元件的影響；因此，建議優先選用此格式。  
  
 例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串︰  
  
 `3/1/2010`  
  
 如需詳細資訊，請參閱 <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>。  
  
### <a name="sortable-datetime-pattern-s"></a>可排序的 DateTime 模式 ("s")  
 下面顯示了 XAML<xref:System.DateTime>中的可排序模式：  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串 (時間元件全都輸入 0)︰  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 模式 ("r")  
 RFC1123 模式之所以有用，是因為它可能是來自有後列情況的其他日期產生器的字串輸入：也因為文化特性多變的原因而使用 RFC1123 模式。 下面顯示了 XAML 中的 RFC1123<xref:System.DateTime>模式：  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串 (時間元件全都輸入 0)︰  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>其他格式與模式  
 如前所述，XAML 中可以<xref:System.DateTime>指定為可作為<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>輸入的任何字串。 這包括其他形式化格式（例如<xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>）和未正式作為特定<xref:System.Globalization.DateTimeFormatInfo>格式的格式。 例如，表單`YYYY/mm/dd`可以接受為<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>的輸入。 本主題不會嘗試說明所有可能作用的格式，而是建議使用簡短日期模式為標準做法。  
  
## <a name="see-also"></a>另請參閱

- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
