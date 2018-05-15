---
title: '&lt;system.diagnostics&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 090c296ba84043445364b350c8b74587c35b5940
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemdiagnosticsgt-element"></a><span data-ttu-id="8d297-102">&lt;system.diagnostics&gt;項目</span><span class="sxs-lookup"><span data-stu-id="8d297-102">&lt;system.diagnostics&gt; Element</span></span>
<span data-ttu-id="8d297-103">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="8d297-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="8d297-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8d297-104">\<configuration></span></span>  
<span data-ttu-id="8d297-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="8d297-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d297-106">語法</span><span class="sxs-lookup"><span data-stu-id="8d297-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d297-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8d297-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8d297-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8d297-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d297-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8d297-109">Attributes</span></span>  
 <span data-ttu-id="8d297-110">無。</span><span class="sxs-lookup"><span data-stu-id="8d297-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d297-111">子項目</span><span class="sxs-lookup"><span data-stu-id="8d297-111">Child Elements</span></span>  
  
|<span data-ttu-id="8d297-112">項目</span><span class="sxs-lookup"><span data-stu-id="8d297-112">Element</span></span>|<span data-ttu-id="8d297-113">描述</span><span class="sxs-lookup"><span data-stu-id="8d297-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d297-114">\<assert></span><span class="sxs-lookup"><span data-stu-id="8d297-114">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="8d297-115">指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d297-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="8d297-116">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="8d297-116">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="8d297-117">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="8d297-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="8d297-118">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="8d297-118">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="8d297-119">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="8d297-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="8d297-120">識別為共用接聽項可以依名稱加入至來源或追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="8d297-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="8d297-121">\<sources></span><span class="sxs-lookup"><span data-stu-id="8d297-121">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="8d297-122">指定初始化追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="8d297-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="8d297-123">\<switches></span><span class="sxs-lookup"><span data-stu-id="8d297-123">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="8d297-124">包含追蹤參數和追蹤參數會設定其中的層級。</span><span class="sxs-lookup"><span data-stu-id="8d297-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="8d297-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="8d297-125">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="8d297-126">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="8d297-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d297-127">父項目</span><span class="sxs-lookup"><span data-stu-id="8d297-127">Parent Elements</span></span>  
  
|<span data-ttu-id="8d297-128">項目</span><span class="sxs-lookup"><span data-stu-id="8d297-128">Element</span></span>|<span data-ttu-id="8d297-129">描述</span><span class="sxs-lookup"><span data-stu-id="8d297-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8d297-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8d297-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8d297-131">範例</span><span class="sxs-lookup"><span data-stu-id="8d297-131">Example</span></span>  
 <span data-ttu-id="8d297-132">下列範例示範如何內嵌追蹤參數和追蹤接聽程式 **\<system.diagnostics >** 項目。</span><span class="sxs-lookup"><span data-stu-id="8d297-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="8d297-133">`General`追蹤參數設為<xref:System.Diagnostics.TraceLevel>層級。</span><span class="sxs-lookup"><span data-stu-id="8d297-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="8d297-134">追蹤接聽項`myListener`會建立名為的檔案`MyListener.log`並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="8d297-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d297-135">在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。</span><span class="sxs-lookup"><span data-stu-id="8d297-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="8d297-136">例如，您可以指定`true`如<xref:System.Diagnostics.BooleanSwitch>或使用這類代表列舉值的文字`Error`如<xref:System.Diagnostics.TraceSwitch>。</span><span class="sxs-lookup"><span data-stu-id="8d297-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="8d297-137">`<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。</span><span class="sxs-lookup"><span data-stu-id="8d297-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d297-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d297-138">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="8d297-139">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8d297-139">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
