---
title: <EnableAmPmParseAdjustment> 項目
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: 8920e51fcaaca5cb78b80a99ea321163c9b5240f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117362"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="ce038-102">\<EnableAmPmParseAdjustment> 項目</span><span class="sxs-lookup"><span data-stu-id="ce038-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="ce038-103">判斷日期和時間剖析方法是否使用一組已調整的規則來剖析包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="ce038-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="ce038-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce038-104">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce038-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ce038-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ce038-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ce038-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce038-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ce038-107">Attributes</span></span>  
  
|<span data-ttu-id="ce038-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ce038-108">Attribute</span></span>|<span data-ttu-id="ce038-109">描述</span><span class="sxs-lookup"><span data-stu-id="ce038-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ce038-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ce038-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce038-111">指定日期和時間剖析方法是否使用一組已調整的規則來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="ce038-111">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="ce038-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="ce038-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="ce038-113">值</span><span class="sxs-lookup"><span data-stu-id="ce038-113">Value</span></span>|<span data-ttu-id="ce038-114">描述</span><span class="sxs-lookup"><span data-stu-id="ce038-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce038-115">0</span><span class="sxs-lookup"><span data-stu-id="ce038-115">0</span></span>|<span data-ttu-id="ce038-116">日期和時間剖析方法不會使用已調整的規則來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="ce038-116">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="ce038-117">1</span><span class="sxs-lookup"><span data-stu-id="ce038-117">1</span></span>|<span data-ttu-id="ce038-118">日期和時間剖析方法會使用已調整的規則來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="ce038-118">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce038-119">子元素</span><span class="sxs-lookup"><span data-stu-id="ce038-119">Child Elements</span></span>  
 <span data-ttu-id="ce038-120">無。</span><span class="sxs-lookup"><span data-stu-id="ce038-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce038-121">父項目</span><span class="sxs-lookup"><span data-stu-id="ce038-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ce038-122">元素</span><span class="sxs-lookup"><span data-stu-id="ce038-122">Element</span></span>|<span data-ttu-id="ce038-123">描述</span><span class="sxs-lookup"><span data-stu-id="ce038-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ce038-124">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ce038-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ce038-125">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="ce038-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce038-126">備註</span><span class="sxs-lookup"><span data-stu-id="ce038-126">Remarks</span></span>  
 <span data-ttu-id="ce038-127">`<EnableAmPmParseAdjustment>`元素會控制下列方法如何剖析包含數位日和月後接一小時和 AM/PM 指示項的日期字串（例如 "4/10 6 AM"）：</span><span class="sxs-lookup"><span data-stu-id="ce038-127">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="ce038-128">不會影響其他模式。</span><span class="sxs-lookup"><span data-stu-id="ce038-128">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="ce038-129">`<EnableAmPmParseAdjustment>`元素不會影響 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> 、 <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> 、 <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ce038-129">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ce038-130">在 .NET Core 和 .NET Native 中，根據預設會啟用已調整的 AM/PM 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="ce038-130">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="ce038-131">如果未啟用剖析調整規則，則會將字串的第一個數位視為12小時制的小時，而除了 AM/PM 指示項以外的字串其餘部分會被忽略。</span><span class="sxs-lookup"><span data-stu-id="ce038-131">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="ce038-132">剖析方法所傳回的日期和時間是由目前的日期和從日期字串解壓縮的日小時所組成。</span><span class="sxs-lookup"><span data-stu-id="ce038-132">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="ce038-133">如果已啟用剖析調整規則，剖析方法會將日期和月份解讀為屬於目前年份，並將時間解讀為12小時制的小時。</span><span class="sxs-lookup"><span data-stu-id="ce038-133">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="ce038-134">下表說明 <xref:System.DateTime> 當 <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> 使用方法將專案 `<EnableAmPmParseAdjustment>` 的 `enabled` 屬性設定為 "0" 或 "1" 的字串 "" 4/10 6 AM "時，值中的差異。</span><span class="sxs-lookup"><span data-stu-id="ce038-134">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="ce038-135">它假設今天的日期為2017年1月5日，並顯示日期，如同使用指定文化特性的 "G" 格式字串來格式化為止。</span><span class="sxs-lookup"><span data-stu-id="ce038-135">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="ce038-136">文化特性名稱</span><span class="sxs-lookup"><span data-stu-id="ce038-136">Culture name</span></span>|<span data-ttu-id="ce038-137">enabled = "0"</span><span class="sxs-lookup"><span data-stu-id="ce038-137">enabled="0"</span></span>|<span data-ttu-id="ce038-138">enabled = "1"</span><span class="sxs-lookup"><span data-stu-id="ce038-138">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="ce038-139">zh-TW</span><span class="sxs-lookup"><span data-stu-id="ce038-139">en-US</span></span>|<span data-ttu-id="ce038-140">上午 1/5/2017 4:00:00</span><span class="sxs-lookup"><span data-stu-id="ce038-140">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="ce038-141">上午 4/10/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="ce038-141">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="ce038-142">en-GB</span><span class="sxs-lookup"><span data-stu-id="ce038-142">en-GB</span></span>|<span data-ttu-id="ce038-143">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="ce038-143">5/1/2017 6:00:00</span></span>|<span data-ttu-id="ce038-144">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="ce038-144">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce038-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce038-145">See also</span></span>

- [<span data-ttu-id="ce038-146">\<runtime>元素</span><span class="sxs-lookup"><span data-stu-id="ce038-146">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="ce038-147">\<configuration>元素</span><span class="sxs-lookup"><span data-stu-id="ce038-147">\<configuration> Element</span></span>](../configuration-element.md)
