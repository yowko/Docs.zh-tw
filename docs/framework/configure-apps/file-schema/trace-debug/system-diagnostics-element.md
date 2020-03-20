---
title: <系統.診斷>元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153203"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="e0ff5-102">\<系統.診斷>元素</span><span class="sxs-lookup"><span data-stu-id="e0ff5-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="e0ff5-103">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="e0ff5-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="e0ff5-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e0ff5-105">&nbsp;&nbsp;**\<系統.診斷>**</span><span class="sxs-lookup"><span data-stu-id="e0ff5-105">&nbsp;&nbsp;**\<system.diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0ff5-106">語法</span><span class="sxs-lookup"><span data-stu-id="e0ff5-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0ff5-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e0ff5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e0ff5-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0ff5-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e0ff5-109">Attributes</span></span>  
 <span data-ttu-id="e0ff5-110">無。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e0ff5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e0ff5-111">Child Elements</span></span>  
  
|<span data-ttu-id="e0ff5-112">元素</span><span class="sxs-lookup"><span data-stu-id="e0ff5-112">Element</span></span>|<span data-ttu-id="e0ff5-113">描述</span><span class="sxs-lookup"><span data-stu-id="e0ff5-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0ff5-114">\<斷言></span><span class="sxs-lookup"><span data-stu-id="e0ff5-114">\<assert></span></span>](assert-element.md)|<span data-ttu-id="e0ff5-115">指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="e0ff5-116">\<效能計數器></span><span class="sxs-lookup"><span data-stu-id="e0ff5-116">\<performanceCounters></span></span>](performancecounters-element.md)|<span data-ttu-id="e0ff5-117">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="e0ff5-118">\<共用攔截器></span><span class="sxs-lookup"><span data-stu-id="e0ff5-118">\<sharedListeners></span></span>](sharedlisteners-element.md)|<span data-ttu-id="e0ff5-119">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="e0ff5-120">標識為共用攔截器的攔截器可以按名稱添加到源或跟蹤中。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="e0ff5-121">\<來源></span><span class="sxs-lookup"><span data-stu-id="e0ff5-121">\<sources></span></span>](sources-element.md)|<span data-ttu-id="e0ff5-122">指定啟動跟蹤消息的跟蹤源。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="e0ff5-123">\<開關></span><span class="sxs-lookup"><span data-stu-id="e0ff5-123">\<switches></span></span>](switches-element.md)|<span data-ttu-id="e0ff5-124">包含跟蹤開關和設置跟蹤開關的級別。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="e0ff5-125">\<跟蹤></span><span class="sxs-lookup"><span data-stu-id="e0ff5-125">\<trace></span></span>](trace-element.md)|<span data-ttu-id="e0ff5-126">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0ff5-127">父項目</span><span class="sxs-lookup"><span data-stu-id="e0ff5-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e0ff5-128">元素</span><span class="sxs-lookup"><span data-stu-id="e0ff5-128">Element</span></span>|<span data-ttu-id="e0ff5-129">描述</span><span class="sxs-lookup"><span data-stu-id="e0ff5-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e0ff5-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e0ff5-131">範例</span><span class="sxs-lookup"><span data-stu-id="e0ff5-131">Example</span></span>  
 <span data-ttu-id="e0ff5-132">下面的示例演示如何在**\<系統**中嵌入跟蹤開關和跟蹤攔截器>。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="e0ff5-133">跟蹤`General`開關設置為級別<xref:System.Diagnostics.TraceLevel>。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="e0ff5-134">跟蹤偵聽`myListener`器創建一個`MyListener.log`檔，並將輸出寫入該檔。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0ff5-135">在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="e0ff5-136">例如，`true`可以為 指定 或使用<xref:System.Diagnostics.BooleanSwitch>表示枚舉值（如 的 枚`Error`<xref:System.Diagnostics.TraceSwitch>舉值）的文本指定或使用 文本。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="e0ff5-137">`<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。</span><span class="sxs-lookup"><span data-stu-id="e0ff5-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0ff5-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0ff5-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="e0ff5-139">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="e0ff5-139">Trace and Debug Settings Schema</span></span>](index.md)
