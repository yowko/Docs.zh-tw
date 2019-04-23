---
title: < System.diagnostics > 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 026805ffb9b89aa55e84cf9a5c4afb8ed63cec09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142703"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="d1515-102">\<system.diagnostics > 項目</span><span class="sxs-lookup"><span data-stu-id="d1515-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="d1515-103">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="d1515-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="d1515-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d1515-104">\<configuration></span></span>  
<span data-ttu-id="d1515-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="d1515-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1515-106">語法</span><span class="sxs-lookup"><span data-stu-id="d1515-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1515-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d1515-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d1515-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d1515-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1515-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d1515-109">Attributes</span></span>  
 <span data-ttu-id="d1515-110">無。</span><span class="sxs-lookup"><span data-stu-id="d1515-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1515-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d1515-111">Child Elements</span></span>  
  
|<span data-ttu-id="d1515-112">項目</span><span class="sxs-lookup"><span data-stu-id="d1515-112">Element</span></span>|<span data-ttu-id="d1515-113">描述</span><span class="sxs-lookup"><span data-stu-id="d1515-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1515-114">\<assert></span><span class="sxs-lookup"><span data-stu-id="d1515-114">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="d1515-115">指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="d1515-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="d1515-116">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="d1515-116">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="d1515-117">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="d1515-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="d1515-118">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="d1515-118">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="d1515-119">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="d1515-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="d1515-120">識別為共用接聽項可以依名稱加入到來源或追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d1515-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="d1515-121">\<sources></span><span class="sxs-lookup"><span data-stu-id="d1515-121">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="d1515-122">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="d1515-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="d1515-123">\<switches></span><span class="sxs-lookup"><span data-stu-id="d1515-123">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="d1515-124">包含追蹤參數和其中設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="d1515-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="d1515-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="d1515-125">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="d1515-126">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="d1515-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1515-127">父項目</span><span class="sxs-lookup"><span data-stu-id="d1515-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d1515-128">項目</span><span class="sxs-lookup"><span data-stu-id="d1515-128">Element</span></span>|<span data-ttu-id="d1515-129">描述</span><span class="sxs-lookup"><span data-stu-id="d1515-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d1515-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d1515-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d1515-131">範例</span><span class="sxs-lookup"><span data-stu-id="d1515-131">Example</span></span>  
 <span data-ttu-id="d1515-132">下列範例示範如何內嵌追蹤參數和追蹤接聽程式內 **\<system.diagnostics >** 項目。</span><span class="sxs-lookup"><span data-stu-id="d1515-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="d1515-133">`General`若要設定追蹤參數<xref:System.Diagnostics.TraceLevel>層級。</span><span class="sxs-lookup"><span data-stu-id="d1515-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="d1515-134">追蹤接聽項`myListener`建立一個稱為檔案`MyListener.log`並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="d1515-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1515-135">在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。</span><span class="sxs-lookup"><span data-stu-id="d1515-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="d1515-136">比方說，您可以指定`true`for <xref:System.Diagnostics.BooleanSwitch> ，或使用的文字表示的列舉值，例如`Error`如<xref:System.Diagnostics.TraceSwitch>。</span><span class="sxs-lookup"><span data-stu-id="d1515-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="d1515-137">`<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。</span><span class="sxs-lookup"><span data-stu-id="d1515-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1515-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1515-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="d1515-139">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d1515-139">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
