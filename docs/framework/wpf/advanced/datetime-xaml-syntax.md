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
# <a name="datetime-xaml-syntax"></a><span data-ttu-id="f7f59-102">DateTime XAML 語法</span><span class="sxs-lookup"><span data-stu-id="f7f59-102">DateTime XAML Syntax</span></span>
<span data-ttu-id="f7f59-103">某些控制項（例如 <xref:System.Windows.Controls.Calendar> 和 <xref:System.Windows.Controls.DatePicker>）具有使用 <xref:System.DateTime> 類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="f7f59-103">Some controls, such as <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>, have properties that use the <xref:System.DateTime> type.</span></span> <span data-ttu-id="f7f59-104">雖然您通常會在執行階段時，於程式碼後置中指定這些控制項的初始日期或時間，但仍可在 XAML 中指定初始的日期或時間。</span><span class="sxs-lookup"><span data-stu-id="f7f59-104">Although you typically specify an initial date or time for these controls in the code-behind at run time, you can specify an initial date or time in XAML.</span></span> <span data-ttu-id="f7f59-105">WPF XAML 剖析器會使用內建 XAML 文字語法來處理 <xref:System.DateTime> 值的剖析。</span><span class="sxs-lookup"><span data-stu-id="f7f59-105">The WPF XAML parser handles parsing of <xref:System.DateTime> values using a built-in XAML text syntax.</span></span> <span data-ttu-id="f7f59-106">本主題描述 <xref:System.DateTime> XAML 文字語法的細節。</span><span class="sxs-lookup"><span data-stu-id="f7f59-106">This topic describes the specifics of the <xref:System.DateTime> XAML text syntax.</span></span>  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a><span data-ttu-id="f7f59-107">使用 DateTime XAML 語法的時機</span><span class="sxs-lookup"><span data-stu-id="f7f59-107">When To Use DateTime XAML Syntax</span></span>  
 <span data-ttu-id="f7f59-108">在 XAML 中設定日期不是必要的，甚至可能不需要。</span><span class="sxs-lookup"><span data-stu-id="f7f59-108">Setting dates in XAML is not always necessary and may not even be desirable.</span></span> <span data-ttu-id="f7f59-109">例如，您可以使用 [<xref:System.DateTime.Now%2A?displayProperty=nameWithType>] 屬性在執行時間初始化日期，也可以根據使用者輸入，在程式碼後置中為行事曆執行所有的日期調整。</span><span class="sxs-lookup"><span data-stu-id="f7f59-109">For example, you could use the <xref:System.DateTime.Now%2A?displayProperty=nameWithType> property to initialize a date at run time, or you could do all your date adjustments for a calendar in the code-behind based on user input.</span></span> <span data-ttu-id="f7f59-110">不過，在某些情況下，您可能會想要將日期硬式編碼成 <xref:System.Windows.Controls.Calendar>，並在控制項範本中 <xref:System.Windows.Controls.DatePicker>。</span><span class="sxs-lookup"><span data-stu-id="f7f59-110">However, there are scenarios where you may want to hard-code dates into a <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker> in a control template.</span></span> <span data-ttu-id="f7f59-111">在這些情況下，必須使用 <xref:System.DateTime> XAML 語法。</span><span class="sxs-lookup"><span data-stu-id="f7f59-111">The <xref:System.DateTime> XAML syntax must be used for these scenarios.</span></span>  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a><span data-ttu-id="f7f59-112">DateTime XAML 語法是原生的行為</span><span class="sxs-lookup"><span data-stu-id="f7f59-112">DateTime XAML Syntax is a Native Behavior</span></span>  
 <span data-ttu-id="f7f59-113"><xref:System.DateTime> 是在 CLR 的基類程式庫中定義的類別。</span><span class="sxs-lookup"><span data-stu-id="f7f59-113"><xref:System.DateTime> is a class that is defined in the base class libraries of the CLR.</span></span> <span data-ttu-id="f7f59-114">由於基類庫與 CLR 其餘部分之間的關係，因此無法將 <xref:System.ComponentModel.TypeConverterAttribute> 套用至類別，並使用類型轉換器來處理 XAML 中的字串，並將它們轉換成執行時間物件模型中的 <xref:System.DateTime>。</span><span class="sxs-lookup"><span data-stu-id="f7f59-114">Because of how the base class libraries relate to the rest of the CLR, it is not possible to apply <xref:System.ComponentModel.TypeConverterAttribute> to the class and use a type converter to process strings from XAML and convert them to <xref:System.DateTime> in the run time object model.</span></span> <span data-ttu-id="f7f59-115">沒有可提供轉換行為的 `DateTimeConverter`，本主題中描述的轉換行為是 WPF XAML 剖析器的原生行為。</span><span class="sxs-lookup"><span data-stu-id="f7f59-115">There is no `DateTimeConverter` class that provides the conversion behavior; the conversion behavior described in this topic is native to the WPF XAML parser.</span></span>  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a><span data-ttu-id="f7f59-116">DateTime XAML 語法的格式字串</span><span class="sxs-lookup"><span data-stu-id="f7f59-116">Format Strings for DateTime XAML Syntax</span></span>  
 <span data-ttu-id="f7f59-117">您可以使用格式字串來指定 <xref:System.DateTime> 的格式。</span><span class="sxs-lookup"><span data-stu-id="f7f59-117">You can specify the format of a <xref:System.DateTime> with a format string.</span></span> <span data-ttu-id="f7f59-118">格式字串會正規化可用來建立值的文字語法。</span><span class="sxs-lookup"><span data-stu-id="f7f59-118">Format strings formalize the text syntax that can be used to create a value.</span></span> <span data-ttu-id="f7f59-119">現有 WPF 控制項的 <xref:System.DateTime> 值通常只會使用 <xref:System.DateTime> 的日期元件，而不是時間元件。</span><span class="sxs-lookup"><span data-stu-id="f7f59-119"><xref:System.DateTime> values for the existing WPF controls generally only use the date components of <xref:System.DateTime> and not the time components.</span></span>  
  
 <span data-ttu-id="f7f59-120">在 XAML 中指定 <xref:System.DateTime> 時，您可以交換使用任何格式字串。</span><span class="sxs-lookup"><span data-stu-id="f7f59-120">When specifying a <xref:System.DateTime> in XAML, you can use any of the format strings interchangeably.</span></span>  
  
 <span data-ttu-id="f7f59-121">您也可以使用本主題中未特意顯示的格式和格式字串。</span><span class="sxs-lookup"><span data-stu-id="f7f59-121">You can also use formats and format strings that are not specifically shown in this topic.</span></span> <span data-ttu-id="f7f59-122">就技術上而言，WPF XAML 剖析器所指定然後剖析之任何 <xref:System.DateTime> 值的 XAML 都會使用內部呼叫 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>，因此您可以使用 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 針對 XAML 輸入所接受的任何字串。</span><span class="sxs-lookup"><span data-stu-id="f7f59-122">Technically, the XAML for any <xref:System.DateTime> value that is specified and then parsed by the WPF XAML parser uses an internal  call to <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, therefore you could use any string accepted by <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> for your XAML input.</span></span> <span data-ttu-id="f7f59-123">如需詳細資訊，請參閱<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f7f59-123">For more information, see <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f7f59-124">DateTime XAML 語法一律會使用 `en-us` 做為其原生轉換的 <xref:System.Globalization.CultureInfo>。</span><span class="sxs-lookup"><span data-stu-id="f7f59-124">The DateTime XAML syntax always uses `en-us` as the <xref:System.Globalization.CultureInfo> for its native conversion.</span></span> <span data-ttu-id="f7f59-125">這不會受到 XAML 中 <xref:System.Windows.FrameworkElement.Language%2A> 值或 `xml:lang` 值的影響，因為 XAML 屬性層級類型轉換會在沒有該內容的情況下運作。</span><span class="sxs-lookup"><span data-stu-id="f7f59-125">This is not influenced by <xref:System.Windows.FrameworkElement.Language%2A> value or `xml:lang` value in the XAML, because XAML attribute-level type conversion acts without that context.</span></span> <span data-ttu-id="f7f59-126">因為文化特性多變，例如日期和月份的顯示順序，請勿嘗試插入此處顯示的格式字串。</span><span class="sxs-lookup"><span data-stu-id="f7f59-126">Do not attempt to interpolate the format strings shown here due to cultural variations, such as the order in which day and month appear.</span></span> <span data-ttu-id="f7f59-127">此處顯示的格式字串正是剖析 XAML 時使用的格式字串，無論其他文化特性設定為何。</span><span class="sxs-lookup"><span data-stu-id="f7f59-127">The format strings shown here are the exact format strings used when parsing the XAML regardless of other culture settings.</span></span>  
  
 <span data-ttu-id="f7f59-128">下列各節將說明一些常見的 <xref:System.DateTime> 格式字串。</span><span class="sxs-lookup"><span data-stu-id="f7f59-128">The following sections describe some of the common <xref:System.DateTime> format strings.</span></span>  
  
### <a name="short-date-pattern-d"></a><span data-ttu-id="f7f59-129">簡短日期模式 ("d")</span><span class="sxs-lookup"><span data-stu-id="f7f59-129">Short Date Pattern ("d")</span></span>  
 <span data-ttu-id="f7f59-130">以下顯示 XAML 中 <xref:System.DateTime> 的簡短日期格式：</span><span class="sxs-lookup"><span data-stu-id="f7f59-130">The following shows the short date format for a <xref:System.DateTime> in XAML:</span></span>  
  
 `M/d/YYYY`  
  
 <span data-ttu-id="f7f59-131">這是依 WPF 控制項指定一般用法所有必要資訊的最簡單形式，不會受到意外時區位移與時間元件的影響；因此，建議優先選用此格式。</span><span class="sxs-lookup"><span data-stu-id="f7f59-131">This is the simplest form that specifies all necessary information for typical usages by WPF controls, and cannot be influenced by accidental time zone offsets versus a time component, and is therefore recommended over the other formats.</span></span>  
  
 <span data-ttu-id="f7f59-132">例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串︰</span><span class="sxs-lookup"><span data-stu-id="f7f59-132">For example, to specify the date of June 1, 2010, use the following string:</span></span>  
  
 `3/1/2010`  
  
 <span data-ttu-id="f7f59-133">如需詳細資訊，請參閱<xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f7f59-133">For more information, see <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="sortable-datetime-pattern-s"></a><span data-ttu-id="f7f59-134">可排序的 DateTime 模式 ("s")</span><span class="sxs-lookup"><span data-stu-id="f7f59-134">Sortable DateTime Pattern ("s")</span></span>  
 <span data-ttu-id="f7f59-135">以下顯示 XAML 中可排序的 <xref:System.DateTime> 模式：</span><span class="sxs-lookup"><span data-stu-id="f7f59-135">The following shows the sortable <xref:System.DateTime> pattern in XAML:</span></span>  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 <span data-ttu-id="f7f59-136">例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串 (時間元件全都輸入 0)︰</span><span class="sxs-lookup"><span data-stu-id="f7f59-136">For example, to specify the date of June 1, 2010, use the following string (time components are all entered as 0):</span></span>  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a><span data-ttu-id="f7f59-137">RFC1123 模式 ("r")</span><span class="sxs-lookup"><span data-stu-id="f7f59-137">RFC1123 Pattern ("r")</span></span>  
 <span data-ttu-id="f7f59-138">RFC1123 模式之所以有用，是因為它可能是來自有後列情況的其他日期產生器的字串輸入：也因為文化特性多變的原因而使用 RFC1123 模式。</span><span class="sxs-lookup"><span data-stu-id="f7f59-138">The RFC1123 pattern is useful because it could be a string input from other date generators that also use the RFC1123 pattern for culture invariant reasons.</span></span> <span data-ttu-id="f7f59-139">以下顯示 XAML 中的 RFC1123 <xref:System.DateTime> 模式：</span><span class="sxs-lookup"><span data-stu-id="f7f59-139">The following shows the RFC1123 <xref:System.DateTime> pattern in XAML:</span></span>  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 <span data-ttu-id="f7f59-140">例如，若要指定日期 2010 年 6 月 1 日，請使用下列字串 (時間元件全都輸入 0)︰</span><span class="sxs-lookup"><span data-stu-id="f7f59-140">For example, to specify the date of June 1, 2010, use the following string (time components are all entered as 0):</span></span>  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a><span data-ttu-id="f7f59-141">其他格式與模式</span><span class="sxs-lookup"><span data-stu-id="f7f59-141">Other Formats and Patterns</span></span>  
 <span data-ttu-id="f7f59-142">如先前所述，XAML 中的 <xref:System.DateTime> 可以指定為可接受做為 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>輸入的任何字串。</span><span class="sxs-lookup"><span data-stu-id="f7f59-142">As stated previously, a <xref:System.DateTime> in XAML can be specified as any string that is acceptable as input for <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7f59-143">這包括其他正式格式（例如 <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>），以及未正規化為特定 <xref:System.Globalization.DateTimeFormatInfo> 格式的格式。</span><span class="sxs-lookup"><span data-stu-id="f7f59-143">This includes other formalized formats (for example <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>), and formats that are not formalized as a particular <xref:System.Globalization.DateTimeFormatInfo> form.</span></span> <span data-ttu-id="f7f59-144">例如，可以接受表單 `YYYY/mm/dd` 做為 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>的輸入。</span><span class="sxs-lookup"><span data-stu-id="f7f59-144">For example, the form `YYYY/mm/dd` is acceptable as input for <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7f59-145">本主題不會嘗試說明所有可能作用的格式，而是建議使用簡短日期模式為標準做法。</span><span class="sxs-lookup"><span data-stu-id="f7f59-145">This topic does not attempt to describe all possible formats that work, and instead recommends the short date pattern as a standard practice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f59-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="f7f59-146">See also</span></span>

- [<span data-ttu-id="f7f59-147">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="f7f59-147">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
