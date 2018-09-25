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
ms.openlocfilehash: 35fe167beb53c27aa511e08507415a26b1749ca2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156974"
---
# <a name="ltsystemdiagnosticsgt-element"></a><span data-ttu-id="0d2e7-102">&lt;system.diagnostics&gt;項目</span><span class="sxs-lookup"><span data-stu-id="0d2e7-102">&lt;system.diagnostics&gt; Element</span></span>
<span data-ttu-id="0d2e7-103">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="0d2e7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0d2e7-104">\<configuration></span></span>  
<span data-ttu-id="0d2e7-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="0d2e7-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d2e7-106">語法</span><span class="sxs-lookup"><span data-stu-id="0d2e7-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d2e7-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0d2e7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0d2e7-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d2e7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0d2e7-109">Attributes</span></span>  
 <span data-ttu-id="0d2e7-110">無。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0d2e7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0d2e7-111">Child Elements</span></span>  
  
|<span data-ttu-id="0d2e7-112">項目</span><span class="sxs-lookup"><span data-stu-id="0d2e7-112">Element</span></span>|<span data-ttu-id="0d2e7-113">描述</span><span class="sxs-lookup"><span data-stu-id="0d2e7-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d2e7-114">\<assert></span><span class="sxs-lookup"><span data-stu-id="0d2e7-114">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="0d2e7-115">指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="0d2e7-116">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="0d2e7-116">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="0d2e7-117">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="0d2e7-118">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="0d2e7-118">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="0d2e7-119">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="0d2e7-120">識別為共用接聽項可以依名稱加入到來源或追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="0d2e7-121">\<sources></span><span class="sxs-lookup"><span data-stu-id="0d2e7-121">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="0d2e7-122">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="0d2e7-123">\<switches></span><span class="sxs-lookup"><span data-stu-id="0d2e7-123">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="0d2e7-124">包含追蹤參數和其中設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="0d2e7-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="0d2e7-125">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="0d2e7-126">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d2e7-127">父項目</span><span class="sxs-lookup"><span data-stu-id="0d2e7-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0d2e7-128">項目</span><span class="sxs-lookup"><span data-stu-id="0d2e7-128">Element</span></span>|<span data-ttu-id="0d2e7-129">描述</span><span class="sxs-lookup"><span data-stu-id="0d2e7-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0d2e7-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0d2e7-131">範例</span><span class="sxs-lookup"><span data-stu-id="0d2e7-131">Example</span></span>  
 <span data-ttu-id="0d2e7-132">下列範例示範如何內嵌追蹤參數和追蹤接聽程式內 **\<system.diagnostics >** 項目。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="0d2e7-133">`General`若要設定追蹤參數<xref:System.Diagnostics.TraceLevel>層級。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="0d2e7-134">追蹤接聽項`myListener`建立一個稱為檔案`MyListener.log`並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d2e7-135">在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="0d2e7-136">比方說，您可以指定`true`for <xref:System.Diagnostics.BooleanSwitch> ，或使用的文字表示的列舉值，例如`Error`如<xref:System.Diagnostics.TraceSwitch>。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="0d2e7-137">`<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。</span><span class="sxs-lookup"><span data-stu-id="0d2e7-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d2e7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d2e7-138">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="0d2e7-139">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0d2e7-139">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
