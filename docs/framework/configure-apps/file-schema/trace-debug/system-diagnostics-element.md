---
title: < diagnostics > 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699200"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="8446a-102">\<system. 診斷 > 元素</span><span class="sxs-lookup"><span data-stu-id="8446a-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="8446a-103">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="8446a-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="8446a-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="8446a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8446a-105">&nbsp; @ no__t-1 **\<system. 診斷 >**</span><span class="sxs-lookup"><span data-stu-id="8446a-105">&nbsp;&nbsp;**\<system.diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8446a-106">語法</span><span class="sxs-lookup"><span data-stu-id="8446a-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8446a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8446a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8446a-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8446a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8446a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8446a-109">Attributes</span></span>  
 <span data-ttu-id="8446a-110">無。</span><span class="sxs-lookup"><span data-stu-id="8446a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8446a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8446a-111">Child Elements</span></span>  
  
|<span data-ttu-id="8446a-112">元素</span><span class="sxs-lookup"><span data-stu-id="8446a-112">Element</span></span>|<span data-ttu-id="8446a-113">描述</span><span class="sxs-lookup"><span data-stu-id="8446a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8446a-114">\<assert></span><span class="sxs-lookup"><span data-stu-id="8446a-114">\<assert></span></span>](assert-element.md)|<span data-ttu-id="8446a-115">指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="8446a-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="8446a-116">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="8446a-116">\<performanceCounters></span></span>](performancecounters-element.md)|<span data-ttu-id="8446a-117">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="8446a-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="8446a-118">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="8446a-118">\<sharedListeners></span></span>](sharedlisteners-element.md)|<span data-ttu-id="8446a-119">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="8446a-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="8446a-120">識別為共用接聽項的接聽程式可以依名稱新增至來源或追蹤。</span><span class="sxs-lookup"><span data-stu-id="8446a-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="8446a-121">\<sources></span><span class="sxs-lookup"><span data-stu-id="8446a-121">\<sources></span></span>](sources-element.md)|<span data-ttu-id="8446a-122">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="8446a-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="8446a-123">\<switches></span><span class="sxs-lookup"><span data-stu-id="8446a-123">\<switches></span></span>](switches-element.md)|<span data-ttu-id="8446a-124">包含追蹤參數和設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="8446a-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="8446a-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="8446a-125">\<trace></span></span>](trace-element.md)|<span data-ttu-id="8446a-126">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="8446a-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8446a-127">父項目</span><span class="sxs-lookup"><span data-stu-id="8446a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="8446a-128">項目</span><span class="sxs-lookup"><span data-stu-id="8446a-128">Element</span></span>|<span data-ttu-id="8446a-129">描述</span><span class="sxs-lookup"><span data-stu-id="8446a-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8446a-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8446a-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8446a-131">範例</span><span class="sxs-lookup"><span data-stu-id="8446a-131">Example</span></span>  
 <span data-ttu-id="8446a-132">下列範例示範如何將追蹤參數和追蹤接聽程式內嵌在 **\<system >** 元素內。</span><span class="sxs-lookup"><span data-stu-id="8446a-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="8446a-133">@No__t-0 追蹤參數設定為 <xref:System.Diagnostics.TraceLevel> 層級。</span><span class="sxs-lookup"><span data-stu-id="8446a-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="8446a-134">追蹤接聽程式 `myListener` 會建立名為 `MyListener.log` 的檔案，並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="8446a-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8446a-135">在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。</span><span class="sxs-lookup"><span data-stu-id="8446a-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="8446a-136">例如，您可以為 <xref:System.Diagnostics.BooleanSwitch> 指定 `true`，或使用代表列舉值的文字，例如 <xref:System.Diagnostics.TraceSwitch> 的 `Error`。</span><span class="sxs-lookup"><span data-stu-id="8446a-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="8446a-137">`<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。</span><span class="sxs-lookup"><span data-stu-id="8446a-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8446a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8446a-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="8446a-139">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8446a-139">Trace and Debug Settings Schema</span></span>](index.md)
