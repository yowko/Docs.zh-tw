---
title: '&lt;EnableAmPmParseAdjustment&gt;項目'
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf56a2720ab407d05b8356280913445c15a17020
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611070"
---
# <a name="ltenableampmparseadjustmentgt-element"></a><span data-ttu-id="d0c2a-102">&lt;EnableAmPmParseAdjustment&gt;項目</span><span class="sxs-lookup"><span data-stu-id="d0c2a-102">&lt;EnableAmPmParseAdjustment&gt; Element</span></span>
<span data-ttu-id="d0c2a-103">決定日期和時間剖析方法使用一組調整過的規則來剖析日期字串，包含日期、 月份、 小時和 AM/PM 指示項。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="d0c2a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d0c2a-104">\<configuration></span></span>  
 <span data-ttu-id="d0c2a-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="d0c2a-105">\<runtime></span></span>  
<span data-ttu-id="d0c2a-106">\<EnableAmPmParseAdjustment ></span><span class="sxs-lookup"><span data-stu-id="d0c2a-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0c2a-107">語法</span><span class="sxs-lookup"><span data-stu-id="d0c2a-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0c2a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d0c2a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d0c2a-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0c2a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d0c2a-110">Attributes</span></span>  
  
|<span data-ttu-id="d0c2a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d0c2a-111">Attribute</span></span>|<span data-ttu-id="d0c2a-112">描述</span><span class="sxs-lookup"><span data-stu-id="d0c2a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d0c2a-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d0c2a-114">指定是否日期和時間剖析方法使用調整過的一組規則來剖析日期字串，包含日期、 月份、 小時和 AM/PM 指示項。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="d0c2a-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="d0c2a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d0c2a-116">值</span><span class="sxs-lookup"><span data-stu-id="d0c2a-116">Value</span></span>|<span data-ttu-id="d0c2a-117">描述</span><span class="sxs-lookup"><span data-stu-id="d0c2a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d0c2a-118">0</span><span class="sxs-lookup"><span data-stu-id="d0c2a-118">0</span></span>|<span data-ttu-id="d0c2a-119">日期和時間剖析方法不要使用調整過的規則來剖析日期字串，包含日期、 月份、 小時和 AM/PM 指示項。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="d0c2a-120">1</span><span class="sxs-lookup"><span data-stu-id="d0c2a-120">1</span></span>|<span data-ttu-id="d0c2a-121">日期和時間剖析方法使用調整過的規則來剖析日期字串，包含日期、 月份、 小時和 AM/PM 指示項。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0c2a-122">子元素</span><span class="sxs-lookup"><span data-stu-id="d0c2a-122">Child Elements</span></span>  
 <span data-ttu-id="d0c2a-123">無。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0c2a-124">父項目</span><span class="sxs-lookup"><span data-stu-id="d0c2a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d0c2a-125">項目</span><span class="sxs-lookup"><span data-stu-id="d0c2a-125">Element</span></span>|<span data-ttu-id="d0c2a-126">描述</span><span class="sxs-lookup"><span data-stu-id="d0c2a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d0c2a-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d0c2a-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0c2a-129">備註</span><span class="sxs-lookup"><span data-stu-id="d0c2a-129">Remarks</span></span>  
 <span data-ttu-id="d0c2a-130">`<EnableAmPmParseAdjustment>`元素可讓您控制下列方法如何剖析日期字串，其中包含數值的日期和月份，後面接著一小時的時間和 AM/PM 指示項，（例如"4/10 6 AM"):</span><span class="sxs-lookup"><span data-stu-id="d0c2a-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="d0c2a-131">會不影響任何其他的模式。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="d0c2a-132">`<EnableAmPmParseAdjustment>`項目並不會影響<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>， <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>， <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>，和<xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d0c2a-133">在.NET Core 和.NET Native，預設會啟用已調整的 AM/PM 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="d0c2a-134">如果未啟用剖析的調整規則，字串的第一個數字會解譯為 12 小時制時鐘的小時，除了 AM/PM 指示項的字串的其餘部分會被忽略。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="d0c2a-135">日期和時間剖析方法傳回包含目前的日期和日期字串中擷取當天的小時。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="d0c2a-136">如果啟用剖析的調整規則，則剖析方法解譯日期和月份為屬於目前的年份，並解譯為 12 小時制的小時的時間。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="d0c2a-137">下表說明中的差異<xref:System.DateTime>值時<xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType>方法來剖析字串""4/10 6 AM"與`<EnableAmPmParseAdjustment>`項目的`enabled`屬性設定為"0"或"1"。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="d0c2a-138">假設今天的日期為 2017 年 1 月 5 日，並且如同即會使用指定的文化特性"G"格式字串格式化顯示的日期。</span><span class="sxs-lookup"><span data-stu-id="d0c2a-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="d0c2a-139">文化特性名稱</span><span class="sxs-lookup"><span data-stu-id="d0c2a-139">Culture name</span></span>|<span data-ttu-id="d0c2a-140">已啟用 ="0"</span><span class="sxs-lookup"><span data-stu-id="d0c2a-140">enabled="0"</span></span>|<span data-ttu-id="d0c2a-141">已啟用 ="1"</span><span class="sxs-lookup"><span data-stu-id="d0c2a-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="d0c2a-142">en-US</span><span class="sxs-lookup"><span data-stu-id="d0c2a-142">en-US</span></span>|<span data-ttu-id="d0c2a-143">2017 年 1 月 5 日上午 4:00:00</span><span class="sxs-lookup"><span data-stu-id="d0c2a-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="d0c2a-144">2017 年 4 月 10 日上午 6:00:00</span><span class="sxs-lookup"><span data-stu-id="d0c2a-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="d0c2a-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="d0c2a-145">en-GB</span></span>|<span data-ttu-id="d0c2a-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="d0c2a-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="d0c2a-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="d0c2a-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0c2a-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0c2a-148">See Also</span></span>  
- [<span data-ttu-id="d0c2a-149">\<執行階段 > 項目</span><span class="sxs-lookup"><span data-stu-id="d0c2a-149">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
- [<span data-ttu-id="d0c2a-150">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="d0c2a-150">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
