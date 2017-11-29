---
title: "&lt;EnableAmPmParseAdjustment&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 44bd6297142b6f29d93e9a3bebdb89d32d4bf46a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltenableampmparseadjustmentgt-element"></a><span data-ttu-id="025b5-102">&lt;EnableAmPmParseAdjustment&gt;項目</span><span class="sxs-lookup"><span data-stu-id="025b5-102">&lt;EnableAmPmParseAdjustment&gt; Element</span></span>
<span data-ttu-id="025b5-103">決定是否日期和時間剖析方法使用調整過的一組規則剖析日期字串，包含日、 月、 小時和 AM/PM 指示項。</span><span class="sxs-lookup"><span data-stu-id="025b5-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="025b5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="025b5-104">\<configuration></span></span>  
 <span data-ttu-id="025b5-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="025b5-105">\<runtime></span></span>  
<span data-ttu-id="025b5-106">\<EnableAmPmParseAdjustment ></span><span class="sxs-lookup"><span data-stu-id="025b5-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="025b5-107">語法</span><span class="sxs-lookup"><span data-stu-id="025b5-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="025b5-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="025b5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="025b5-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="025b5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="025b5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="025b5-110">Attributes</span></span>  
  
|<span data-ttu-id="025b5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="025b5-111">Attribute</span></span>|<span data-ttu-id="025b5-112">描述</span><span class="sxs-lookup"><span data-stu-id="025b5-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="025b5-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="025b5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="025b5-114">指定是否日期和時間剖析方法使用調整過的一組規則剖析日期字串，包含只日、 月、 小時和 AM/PM 指示項。</span><span class="sxs-lookup"><span data-stu-id="025b5-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="025b5-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="025b5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="025b5-116">值</span><span class="sxs-lookup"><span data-stu-id="025b5-116">Value</span></span>|<span data-ttu-id="025b5-117">描述</span><span class="sxs-lookup"><span data-stu-id="025b5-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="025b5-118">0</span><span class="sxs-lookup"><span data-stu-id="025b5-118">0</span></span>|<span data-ttu-id="025b5-119">日期和時間剖析方法請勿用於調整的規則剖析日期字串，包含只日、 月、 小時和 AM/PM 指示項。</span><span class="sxs-lookup"><span data-stu-id="025b5-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="025b5-120">1</span><span class="sxs-lookup"><span data-stu-id="025b5-120">1</span></span>|<span data-ttu-id="025b5-121">日期和時間剖析方法可用於調整的規則剖析日期字串，包含只日、 月、 小時和 AM/PM 指示項。</span><span class="sxs-lookup"><span data-stu-id="025b5-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="025b5-122">子元素</span><span class="sxs-lookup"><span data-stu-id="025b5-122">Child Elements</span></span>  
 <span data-ttu-id="025b5-123">無。</span><span class="sxs-lookup"><span data-stu-id="025b5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="025b5-124">父項目</span><span class="sxs-lookup"><span data-stu-id="025b5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="025b5-125">項目</span><span class="sxs-lookup"><span data-stu-id="025b5-125">Element</span></span>|<span data-ttu-id="025b5-126">描述</span><span class="sxs-lookup"><span data-stu-id="025b5-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="025b5-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="025b5-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="025b5-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="025b5-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="025b5-129">備註</span><span class="sxs-lookup"><span data-stu-id="025b5-129">Remarks</span></span>  
 <span data-ttu-id="025b5-130">`<EnableAmPmParseAdjustment>`項目會控制下列方法如何剖析日期字串，包含數值的日期和月份，後面接著一小時和 AM/PM 指示項，（例如"4/10 6 AM"):</span><span class="sxs-lookup"><span data-stu-id="025b5-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="025b5-131">會不影響任何其他的模式。</span><span class="sxs-lookup"><span data-stu-id="025b5-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="025b5-132">`<EnableAmPmParseAdjustment>`項目沒有任何作用<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>， <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>， <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>，和<xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="025b5-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="025b5-133">在.NET Core 和.NET 原生，預設會啟用已調整的 AM/PM 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="025b5-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="025b5-134">剖析的調整規則未啟用，如果第一個數字的字串會解譯為 12 小時制的小時，除了 AM/PM 指示項的字串的其餘部分會被忽略。</span><span class="sxs-lookup"><span data-stu-id="025b5-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="025b5-135">日期和時間剖析方法傳回包含目前的日期和從日期字串擷取當天的小時。</span><span class="sxs-lookup"><span data-stu-id="025b5-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="025b5-136">如果剖析的調整規則已啟用，剖析方法解譯的日期和月份為屬於目前的年份，並解譯在 12 小時制的小時與時間。</span><span class="sxs-lookup"><span data-stu-id="025b5-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="025b5-137">下表說明中的差異<xref:System.DateTime>值時<xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType>方法用來剖析字串""4/10 6 AM"與`<EnableAmPmParseAdjustment>`項目的`enabled`屬性設定為"0"或"1"。</span><span class="sxs-lookup"><span data-stu-id="025b5-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="025b5-138">假設今天的日期是 2017 年 1 月 5，並且如同它使用指定的文化特性"G"格式字串來格式化顯示的日期。</span><span class="sxs-lookup"><span data-stu-id="025b5-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="025b5-139">文化特性名稱</span><span class="sxs-lookup"><span data-stu-id="025b5-139">Culture name</span></span>|<span data-ttu-id="025b5-140">已啟用 ="0"</span><span class="sxs-lookup"><span data-stu-id="025b5-140">enabled="0"</span></span>|<span data-ttu-id="025b5-141">已啟用 ="1"</span><span class="sxs-lookup"><span data-stu-id="025b5-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="025b5-142">zh-TW</span><span class="sxs-lookup"><span data-stu-id="025b5-142">en-US</span></span>|<span data-ttu-id="025b5-143">2017 年 1/5/4:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="025b5-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="025b5-144">2017 年 4/10/6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="025b5-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="025b5-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="025b5-145">en-GB</span></span>|<span data-ttu-id="025b5-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="025b5-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="025b5-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="025b5-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="025b5-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="025b5-148">See Also</span></span>  
 [<span data-ttu-id="025b5-149">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="025b5-149">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [<span data-ttu-id="025b5-150">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="025b5-150">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
