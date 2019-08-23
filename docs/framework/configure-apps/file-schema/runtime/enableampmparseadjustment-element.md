---
title: <EnableAmPmParseAdjustment> 項目
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46cf37ee800c05eb7fe12e8491ad3b2130c3a04d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920813"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="80b85-102">\<EnableAmPmParseAdjustment > 元素</span><span class="sxs-lookup"><span data-stu-id="80b85-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="80b85-103">判斷日期和時間剖析方法是否使用一組已調整的規則來剖析包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="80b85-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="80b85-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="80b85-104">\<configuration></span></span>  
 <span data-ttu-id="80b85-105">\<執行時間 ></span><span class="sxs-lookup"><span data-stu-id="80b85-105">\<runtime></span></span>  
<span data-ttu-id="80b85-106">\<EnableAmPmParseAdjustment></span><span class="sxs-lookup"><span data-stu-id="80b85-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80b85-107">語法</span><span class="sxs-lookup"><span data-stu-id="80b85-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80b85-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="80b85-108">Attributes and Elements</span></span>  
 <span data-ttu-id="80b85-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="80b85-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80b85-110">屬性</span><span class="sxs-lookup"><span data-stu-id="80b85-110">Attributes</span></span>  
  
|<span data-ttu-id="80b85-111">屬性</span><span class="sxs-lookup"><span data-stu-id="80b85-111">Attribute</span></span>|<span data-ttu-id="80b85-112">說明</span><span class="sxs-lookup"><span data-stu-id="80b85-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="80b85-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="80b85-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="80b85-114">指定日期和時間剖析方法是否使用一組已調整的規則來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="80b85-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="80b85-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="80b85-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="80b85-116">值</span><span class="sxs-lookup"><span data-stu-id="80b85-116">Value</span></span>|<span data-ttu-id="80b85-117">描述</span><span class="sxs-lookup"><span data-stu-id="80b85-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80b85-118">0</span><span class="sxs-lookup"><span data-stu-id="80b85-118">0</span></span>|<span data-ttu-id="80b85-119">日期和時間剖析方法不會使用已調整的規則來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="80b85-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="80b85-120">1</span><span class="sxs-lookup"><span data-stu-id="80b85-120">1</span></span>|<span data-ttu-id="80b85-121">日期和時間剖析方法會使用已調整的規則來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="80b85-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80b85-122">子元素</span><span class="sxs-lookup"><span data-stu-id="80b85-122">Child Elements</span></span>  
 <span data-ttu-id="80b85-123">無。</span><span class="sxs-lookup"><span data-stu-id="80b85-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80b85-124">父項目</span><span class="sxs-lookup"><span data-stu-id="80b85-124">Parent Elements</span></span>  
  
|<span data-ttu-id="80b85-125">項目</span><span class="sxs-lookup"><span data-stu-id="80b85-125">Element</span></span>|<span data-ttu-id="80b85-126">描述</span><span class="sxs-lookup"><span data-stu-id="80b85-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="80b85-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="80b85-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="80b85-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="80b85-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80b85-129">備註</span><span class="sxs-lookup"><span data-stu-id="80b85-129">Remarks</span></span>  
 <span data-ttu-id="80b85-130">`<EnableAmPmParseAdjustment>`元素會控制下列方法如何剖析包含數位日和月後接一小時和 AM/PM 指示項的日期字串 (例如 "4/10 6 AM"):</span><span class="sxs-lookup"><span data-stu-id="80b85-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="80b85-131">不會影響其他模式。</span><span class="sxs-lookup"><span data-stu-id="80b85-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="80b85-132"><xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>元素不會影響、 、<xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>和<xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>方法。 `<EnableAmPmParseAdjustment>`</span><span class="sxs-lookup"><span data-stu-id="80b85-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="80b85-133">在 .NET Core 和 .NET Native 中, 根據預設會啟用已調整的 AM/PM 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="80b85-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="80b85-134">如果未啟用剖析調整規則, 則會將字串的第一個數位視為12小時制的小時, 而除了 AM/PM 指示項以外的字串其餘部分會被忽略。</span><span class="sxs-lookup"><span data-stu-id="80b85-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="80b85-135">剖析方法所傳回的日期和時間是由目前的日期和從日期字串解壓縮的日小時所組成。</span><span class="sxs-lookup"><span data-stu-id="80b85-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="80b85-136">如果已啟用剖析調整規則, 剖析方法會將日期和月份解讀為屬於目前年份, 並將時間解讀為12小時制的小時。</span><span class="sxs-lookup"><span data-stu-id="80b85-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="80b85-137">下表說明<xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType>當使用方法將專案<xref:System.DateTime>的`enabled`屬性設定為 "0" 或 "1" 的字串 "" `<EnableAmPmParseAdjustment>` 4/10 6 AM "時, 值中的差異。</span><span class="sxs-lookup"><span data-stu-id="80b85-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="80b85-138">它假設今天的日期為2017年1月5日, 並顯示日期, 如同使用指定文化特性的 "G" 格式字串來格式化為止。</span><span class="sxs-lookup"><span data-stu-id="80b85-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="80b85-139">文化特性名稱</span><span class="sxs-lookup"><span data-stu-id="80b85-139">Culture name</span></span>|<span data-ttu-id="80b85-140">enabled = "0"</span><span class="sxs-lookup"><span data-stu-id="80b85-140">enabled="0"</span></span>|<span data-ttu-id="80b85-141">enabled = "1"</span><span class="sxs-lookup"><span data-stu-id="80b85-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="80b85-142">en-US</span><span class="sxs-lookup"><span data-stu-id="80b85-142">en-US</span></span>|<span data-ttu-id="80b85-143">上午 1/5/2017 4:00:00</span><span class="sxs-lookup"><span data-stu-id="80b85-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="80b85-144">上午 4/10/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="80b85-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="80b85-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="80b85-145">en-GB</span></span>|<span data-ttu-id="80b85-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="80b85-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="80b85-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="80b85-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80b85-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80b85-148">See also</span></span>

- [<span data-ttu-id="80b85-149">\<執行時間 > 元素</span><span class="sxs-lookup"><span data-stu-id="80b85-149">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="80b85-150">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="80b85-150">\<configuration> Element</span></span>](../configuration-element.md)
