---
title: 適用于 <listeners> 的 <clear> 元素 <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 4567f236397435e89371ca4c80730ff964fddd21
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088925"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="b1ed5-102">\<清除 \<來源的 \<接聽程式 > 元素 > ></span><span class="sxs-lookup"><span data-stu-id="b1ed5-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="b1ed5-103">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-103">Clears the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="b1ed5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1ed5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1ed5-105">&nbsp;&nbsp;[ **\<系統診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1ed5-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="b1ed5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<來源**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1ed5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="b1ed5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**來源 >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1ed5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="b1ed5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](listeners-element-for-source.md)接聽程式 ></span><span class="sxs-lookup"><span data-stu-id="b1ed5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="b1ed5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="b1ed5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b1ed5-110">語法</span><span class="sxs-lookup"><span data-stu-id="b1ed5-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1ed5-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b1ed5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b1ed5-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1ed5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b1ed5-113">Attributes</span></span>  
 <span data-ttu-id="b1ed5-114">無。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1ed5-115">子項目</span><span class="sxs-lookup"><span data-stu-id="b1ed5-115">Child Elements</span></span>  
 <span data-ttu-id="b1ed5-116">無。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1ed5-117">父項目</span><span class="sxs-lookup"><span data-stu-id="b1ed5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b1ed5-118">項目</span><span class="sxs-lookup"><span data-stu-id="b1ed5-118">Element</span></span>|<span data-ttu-id="b1ed5-119">描述</span><span class="sxs-lookup"><span data-stu-id="b1ed5-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b1ed5-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b1ed5-121">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="b1ed5-122">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="b1ed5-123">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="b1ed5-124">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1ed5-125">備註</span><span class="sxs-lookup"><span data-stu-id="b1ed5-125">Remarks</span></span>  
 <span data-ttu-id="b1ed5-126">`<clear>` 元素會從追蹤來源的 `Listeners` 集合中移除所有接聽程式，包括 <xref:System.Diagnostics.DefaultTraceListener>。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="b1ed5-127">您可以使用 `<clear>` 專案，然後再使用 `<add>` 元素，以確保集合中沒有其他作用中的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b1ed5-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="b1ed5-128">Configuration File</span></span>  
 <span data-ttu-id="b1ed5-129">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1ed5-130">範例</span><span class="sxs-lookup"><span data-stu-id="b1ed5-130">Example</span></span>  
 <span data-ttu-id="b1ed5-131">下列範例示範如何使用 `<clear>` 專案，然後使用 `<add>` 元素，將接聽程式 `console` 和 `textListener` 加入至追蹤來源 `Listeners` 的 `TraceSourceApp`集合。</span><span class="sxs-lookup"><span data-stu-id="b1ed5-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="b1ed5-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1ed5-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="b1ed5-133">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b1ed5-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b1ed5-134">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="b1ed5-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
