---
title: <EnableAmPmParseAdjustment> 項目
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: f935f213e1bca8dac7a5401970bc6183575e2301
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167225"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="fc428-102">\<EnableAmPmParseAdjustment> 項目</span><span class="sxs-lookup"><span data-stu-id="fc428-102">\<EnableAmPmParseAdjustment> Element</span></span>

<span data-ttu-id="fc428-103">判斷日期和時間剖析方法是否使用一組已調整的規則，來剖析包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="fc428-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="fc428-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fc428-104">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc428-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fc428-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fc428-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fc428-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc428-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fc428-107">Attributes</span></span>  
  
|<span data-ttu-id="fc428-108">屬性</span><span class="sxs-lookup"><span data-stu-id="fc428-108">Attribute</span></span>|<span data-ttu-id="fc428-109">描述</span><span class="sxs-lookup"><span data-stu-id="fc428-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fc428-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="fc428-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="fc428-111">指定日期和時間剖析方法是否使用一組已調整的規則，來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="fc428-111">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="fc428-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="fc428-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="fc428-113">值</span><span class="sxs-lookup"><span data-stu-id="fc428-113">Value</span></span>|<span data-ttu-id="fc428-114">描述</span><span class="sxs-lookup"><span data-stu-id="fc428-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fc428-115">0</span><span class="sxs-lookup"><span data-stu-id="fc428-115">0</span></span>|<span data-ttu-id="fc428-116">日期和時間剖析方法不會使用已調整的規則，來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="fc428-116">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="fc428-117">1</span><span class="sxs-lookup"><span data-stu-id="fc428-117">1</span></span>|<span data-ttu-id="fc428-118">日期和時間剖析方法使用已調整的規則，來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。</span><span class="sxs-lookup"><span data-stu-id="fc428-118">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc428-119">子元素</span><span class="sxs-lookup"><span data-stu-id="fc428-119">Child Elements</span></span>  

 <span data-ttu-id="fc428-120">無。</span><span class="sxs-lookup"><span data-stu-id="fc428-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc428-121">父項目</span><span class="sxs-lookup"><span data-stu-id="fc428-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fc428-122">項目</span><span class="sxs-lookup"><span data-stu-id="fc428-122">Element</span></span>|<span data-ttu-id="fc428-123">描述</span><span class="sxs-lookup"><span data-stu-id="fc428-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fc428-124">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="fc428-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fc428-125">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="fc428-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc428-126">備註</span><span class="sxs-lookup"><span data-stu-id="fc428-126">Remarks</span></span>  

 <span data-ttu-id="fc428-127">專案 `<EnableAmPmParseAdjustment>` 會控制下列方法如何剖析包含數位日和月的日期字串，後面接著一小時和 AM/PM 指示項 (例如 "4/10 6 AM" ) ：</span><span class="sxs-lookup"><span data-stu-id="fc428-127">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="fc428-128">其他模式都不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="fc428-128">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="fc428-129">`<EnableAmPmParseAdjustment>`元素對於 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> 、 <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> 、 <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> 方法沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="fc428-129">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc428-130">在 .NET Core 和 .NET Native 中，依預設會啟用已調整的 AM/PM 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="fc428-130">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="fc428-131">如果未啟用剖析調整規則，則會將字串的第一個數位解釋為12小時制的小時，並忽略 AM/PM 指示項以外的字串其餘部分。</span><span class="sxs-lookup"><span data-stu-id="fc428-131">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="fc428-132">剖析方法所傳回的日期和時間，包含從日期字串中解壓縮之當日的目前日期和小時。</span><span class="sxs-lookup"><span data-stu-id="fc428-132">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="fc428-133">如果已啟用剖析調整規則，則剖析方法會將日期和月份解讀為屬於目前年份，並將時間轉譯為12小時制的小時。</span><span class="sxs-lookup"><span data-stu-id="fc428-133">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="fc428-134">下表說明 <xref:System.DateTime> 當 <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> 方法用來剖析 `<EnableAmPmParseAdjustment>` 元素的 `enabled` 屬性設定為 "0" 或 "1" 的字串 "" 4/10 6 AM "時，值中的差異。</span><span class="sxs-lookup"><span data-stu-id="fc428-134">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="fc428-135">它會假設今天的日期為2017年1月5日，並將日期顯示為使用指定文化特性的 "G" 格式字串來格式化。</span><span class="sxs-lookup"><span data-stu-id="fc428-135">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="fc428-136">文化特性名稱</span><span class="sxs-lookup"><span data-stu-id="fc428-136">Culture name</span></span>|<span data-ttu-id="fc428-137">enabled = "0"</span><span class="sxs-lookup"><span data-stu-id="fc428-137">enabled="0"</span></span>|<span data-ttu-id="fc428-138">enabled = "1"</span><span class="sxs-lookup"><span data-stu-id="fc428-138">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="fc428-139">en-US</span><span class="sxs-lookup"><span data-stu-id="fc428-139">en-US</span></span>|<span data-ttu-id="fc428-140">上午 1/5/2017 4:00:00</span><span class="sxs-lookup"><span data-stu-id="fc428-140">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="fc428-141">上午 4/10/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="fc428-141">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="fc428-142">en-GB</span><span class="sxs-lookup"><span data-stu-id="fc428-142">en-GB</span></span>|<span data-ttu-id="fc428-143">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="fc428-143">5/1/2017 6:00:00</span></span>|<span data-ttu-id="fc428-144">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="fc428-144">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc428-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc428-145">See also</span></span>

- [<span data-ttu-id="fc428-146">\<runtime> 元素</span><span class="sxs-lookup"><span data-stu-id="fc428-146">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="fc428-147">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="fc428-147">\<configuration> Element</span></span>](../configuration-element.md)
