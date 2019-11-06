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
ms.openlocfilehash: c9fb030e6f819b1ca463199a76acd32cb1865f33
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458935"
---
# <a name="datetime-xaml-syntax"></a>DateTime XAML 語法
某些控制項（例如 <xref:System.Windows.Controls.Calendar> 和 <xref:System.Windows.Controls.DatePicker>）具有使用 <xref:System.DateTime> 類型的屬性。 雖然您通常會在執行階段時，於程式碼後置中指定這些控制項的初始日期或時間，但仍可在 XAML 中指定初始的日期或時間。 WPF XAML 剖析器會使用內建 XAML 文字語法來處理 <xref:System.DateTime> 值的剖析。 本主題描述 <xref:System.DateTime> XAML 文字語法的細節。  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>使用 DateTime XAML 語法的時機  
 在 XAML 中設定日期不是必要的，甚至可能不需要。 例如，您可以使用 [<xref:System.DateTime.Now%2A?displayProperty=nameWithType>] 屬性在執行時間初始化日期，也可以根據使用者輸入，在程式碼後置中為行事曆執行所有的日期調整。 不過，在某些情況下，您可能會想要將日期硬式編碼成 <xref:System.Windows.Controls.Calendar>，並在控制項範本中 <xref:System.Windows.Controls.DatePicker>。 在這些情況下，必須使用 <xref:System.DateTime> XAML 語法。  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>DateTime XAML 語法是原生的行為  
 <xref:System.DateTime> 是在 CLR 的基類程式庫中定義的類別。 由於基類庫與 CLR 其餘部分之間的關係，因此無法將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至類別，並使用類型轉換器來處理 XAML 中的字串，並將它們轉換成執行時間物件模型中的 <xref:System.DateTime>。 沒有可提供轉換行為的 `DateTimeConverter`，本主題中描述的轉換行為是 WPF XAML 剖析器的原生行為。  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>DateTime XAML 語法的格式字串  
 您可以使用格式字串來指定 <xref:System.DateTime> 的格式。 格式字串會正規化可用來建立值的文字語法。 現有 WPF 控制項的 <xref:System.DateTime> 值通常只會使用 <xref:System.DateTime> 的日期元件，而不是時間元件。  
  
 在 XAML 中指定 <xref:System.DateTime> 時，您可以交換使用任何格式字串。  
  
 您也可以使用本主題中未特意顯示的格式和格式字串。 就技術上而言，WPF XAML 剖析器所指定然後剖析之任何 <xref:System.DateTime> 值的 XAML 都會使用內部呼叫 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>，因此您可以使用 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 針對 XAML 輸入所接受的任何字串。 如需詳細資訊，請參閱<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>。  
  
> [!IMPORTANT]
> DateTime XAML 語法一律會使用 `en-us` 做為其原生轉換的 <xref:System.Globalization.CultureInfo>。 這不會受到 XAML 中 <xref:System.Windows.FrameworkElement.Language%2A> 值或 `xml:lang` 值的影響，因為 XAML 屬性層級類型轉換會在沒有該內容的情況下運作。 因為文化特性多變，例如日期和月份的顯示順序，請勿嘗試插入此處顯示的格式字串。 此處顯示的格式字串正是剖析 XAML 時使用的格式字串，無論其他文化特性設定為何。  
  
 下列各節將說明一些常見的 <xref:System.DateTime> 格式字串。  
  
### <a name="short-date-pattern-d"></a>簡短日期模式 ("d")  
 以下顯示 XAML 中 <xref:System.DateTime> 的簡短日期格式：  
  
 `M/d/YYYY`  
  
 這是依 WPF 控制項指定一般用法所有必要資訊的最簡單形式，不會受到意外時區位移與時間元件的影響；因此，建議優先選用此格式。  
  
 例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串︰  
  
 `3/1/2010`  
  
 如需詳細資訊，請參閱<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>。  
  
### <a name="sortable-datetime-pattern-s"></a>可排序的 DateTime 模式 ("s")  
 以下顯示 XAML 中可排序的 <xref:System.DateTime> 模式：  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串 (時間元件全都輸入 0)︰  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>RFC1123 模式 ("r")  
 RFC1123 模式之所以有用，是因為它可能是來自有後列情況的其他日期產生器的字串輸入：也因為文化特性多變的原因而使用 RFC1123 模式。 以下顯示 XAML 中的 RFC1123 <xref:System.DateTime> 模式：  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串 (時間元件全都輸入 0)︰  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>其他格式與模式  
 如先前所述，XAML 中的 <xref:System.DateTime> 可以指定為可接受做為 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>輸入的任何字串。 這包括其他正式格式（例如 <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>），以及未正規化為特定 <xref:System.Globalization.DateTimeFormatInfo> 格式的格式。 例如，可以接受表單 `YYYY/mm/dd` 做為 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>的輸入。 本主題不會嘗試說明所有可能作用的格式，而是建議使用簡短日期模式為標準做法。  
  
## <a name="see-also"></a>請參閱

- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
