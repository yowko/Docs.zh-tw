---
title: <EnableAmPmParseAdjustment> 項目
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f132ce0a114a6fc904d86ca3ce893c447366523f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252608"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="975b1-102">\<EnableAmPmParseAdjustment > 元素</span><span class="sxs-lookup"><span data-stu-id="975b1-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="975b1-103">判斷日期和時間剖析方法是否使用一組已調整的規則來剖析包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="975b1-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
<span data-ttu-id="975b1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="975b1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="975b1-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="975b1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="975b1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<EnableAmPmParseAdjustment>**</span><span class="sxs-lookup"><span data-stu-id="975b1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="975b1-107">語法</span><span class="sxs-lookup"><span data-stu-id="975b1-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="975b1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="975b1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="975b1-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="975b1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="975b1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="975b1-110">Attributes</span></span>  
  
|<span data-ttu-id="975b1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="975b1-111">Attribute</span></span>|<span data-ttu-id="975b1-112">說明</span><span class="sxs-lookup"><span data-stu-id="975b1-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="975b1-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="975b1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="975b1-114">指定日期和時間剖析方法是否使用一組已調整的規則來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="975b1-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="975b1-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="975b1-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="975b1-116">值</span><span class="sxs-lookup"><span data-stu-id="975b1-116">Value</span></span>|<span data-ttu-id="975b1-117">描述</span><span class="sxs-lookup"><span data-stu-id="975b1-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="975b1-118">0</span><span class="sxs-lookup"><span data-stu-id="975b1-118">0</span></span>|<span data-ttu-id="975b1-119">日期和時間剖析方法不會使用已調整的規則來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="975b1-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="975b1-120">1</span><span class="sxs-lookup"><span data-stu-id="975b1-120">1</span></span>|<span data-ttu-id="975b1-121">日期和時間剖析方法會使用已調整的規則來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="975b1-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="975b1-122">子元素</span><span class="sxs-lookup"><span data-stu-id="975b1-122">Child Elements</span></span>  
 <span data-ttu-id="975b1-123">無。</span><span class="sxs-lookup"><span data-stu-id="975b1-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="975b1-124">父項目</span><span class="sxs-lookup"><span data-stu-id="975b1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="975b1-125">項目</span><span class="sxs-lookup"><span data-stu-id="975b1-125">Element</span></span>|<span data-ttu-id="975b1-126">描述</span><span class="sxs-lookup"><span data-stu-id="975b1-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="975b1-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="975b1-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="975b1-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="975b1-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="975b1-129">備註</span><span class="sxs-lookup"><span data-stu-id="975b1-129">Remarks</span></span>  
 <span data-ttu-id="975b1-130">`<EnableAmPmParseAdjustment>`元素會控制下列方法如何剖析包含數位日和月後接一小時和 AM/PM 指示項的日期字串（例如 "4/10 6 AM"）：</span><span class="sxs-lookup"><span data-stu-id="975b1-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="975b1-131">不會影響其他模式。</span><span class="sxs-lookup"><span data-stu-id="975b1-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="975b1-132"><xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>元素不會影響、 、<xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>和<xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>方法。 `<EnableAmPmParseAdjustment>`</span><span class="sxs-lookup"><span data-stu-id="975b1-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="975b1-133">在 .NET Core 和 .NET Native 中，根據預設會啟用已調整的 AM/PM 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="975b1-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="975b1-134">如果未啟用剖析調整規則，則會將字串的第一個數位視為12小時制的小時，而除了 AM/PM 指示項以外的字串其餘部分會被忽略。</span><span class="sxs-lookup"><span data-stu-id="975b1-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="975b1-135">剖析方法所傳回的日期和時間是由目前的日期和從日期字串解壓縮的日小時所組成。</span><span class="sxs-lookup"><span data-stu-id="975b1-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="975b1-136">如果已啟用剖析調整規則，剖析方法會將日期和月份解讀為屬於目前年份，並將時間解讀為12小時制的小時。</span><span class="sxs-lookup"><span data-stu-id="975b1-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="975b1-137">下表說明<xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType>當使用方法將專案<xref:System.DateTime>的`enabled`屬性設定為 "0" 或 "1" 的字串 "" `<EnableAmPmParseAdjustment>` 4/10 6 AM "時，值中的差異。</span><span class="sxs-lookup"><span data-stu-id="975b1-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="975b1-138">它假設今天的日期為2017年1月5日，並顯示日期，如同使用指定文化特性的 "G" 格式字串來格式化為止。</span><span class="sxs-lookup"><span data-stu-id="975b1-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="975b1-139">文化特性名稱</span><span class="sxs-lookup"><span data-stu-id="975b1-139">Culture name</span></span>|<span data-ttu-id="975b1-140">enabled = "0"</span><span class="sxs-lookup"><span data-stu-id="975b1-140">enabled="0"</span></span>|<span data-ttu-id="975b1-141">enabled = "1"</span><span class="sxs-lookup"><span data-stu-id="975b1-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="975b1-142">en-US</span><span class="sxs-lookup"><span data-stu-id="975b1-142">en-US</span></span>|<span data-ttu-id="975b1-143">上午 1/5/2017 4:00:00</span><span class="sxs-lookup"><span data-stu-id="975b1-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="975b1-144">上午 4/10/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="975b1-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="975b1-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="975b1-145">en-GB</span></span>|<span data-ttu-id="975b1-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="975b1-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="975b1-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="975b1-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="975b1-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="975b1-148">See also</span></span>

- [<span data-ttu-id="975b1-149">\<執行時間 > 元素</span><span class="sxs-lookup"><span data-stu-id="975b1-149">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="975b1-150">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="975b1-150">\<configuration> Element</span></span>](../configuration-element.md)
