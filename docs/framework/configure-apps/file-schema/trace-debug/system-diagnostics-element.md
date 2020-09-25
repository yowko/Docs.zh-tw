---
title: <的 system.object> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: aff324ac9952c95c78d7ca15572651dba23b79b7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195164"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="cf6f2-102">\<system.diagnostics> 項目</span><span class="sxs-lookup"><span data-stu-id="cf6f2-102">\<system.diagnostics> Element</span></span>

<span data-ttu-id="cf6f2-103">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="cf6f2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="cf6f2-104">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf6f2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cf6f2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cf6f2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf6f2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="cf6f2-107">Attributes</span></span>  

 <span data-ttu-id="cf6f2-108">無。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf6f2-109">子元素</span><span class="sxs-lookup"><span data-stu-id="cf6f2-109">Child Elements</span></span>  
  
|<span data-ttu-id="cf6f2-110">項目</span><span class="sxs-lookup"><span data-stu-id="cf6f2-110">Element</span></span>|<span data-ttu-id="cf6f2-111">描述</span><span class="sxs-lookup"><span data-stu-id="cf6f2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|<span data-ttu-id="cf6f2-112">指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-112">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="cf6f2-113">指定效能計數器共用之全域記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-113">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="cf6f2-114">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-114">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="cf6f2-115">識別為共用接聽程式的接聽程式可以依名稱加入至來源或追蹤。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-115">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="cf6f2-116">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-116">Specifies trace sources that initiate tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="cf6f2-117">包含追蹤參數，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-117">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="cf6f2-118">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-118">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf6f2-119">父項目</span><span class="sxs-lookup"><span data-stu-id="cf6f2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cf6f2-120">項目</span><span class="sxs-lookup"><span data-stu-id="cf6f2-120">Element</span></span>|<span data-ttu-id="cf6f2-121">描述</span><span class="sxs-lookup"><span data-stu-id="cf6f2-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cf6f2-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cf6f2-123">範例</span><span class="sxs-lookup"><span data-stu-id="cf6f2-123">Example</span></span>  

 <span data-ttu-id="cf6f2-124">下列範例示範如何在專案內內嵌追蹤參數和追蹤接聽程式 **\<system.diagnostics>** 。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-124">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="cf6f2-125">`General`追蹤參數設定為 <xref:System.Diagnostics.TraceLevel> 層級。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-125">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="cf6f2-126">追蹤接聽程式會建立名為的檔案 `myListener` `MyListener.log` ，並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-126">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf6f2-127">在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-127">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="cf6f2-128">例如，您可以為指定， `true` <xref:System.Diagnostics.BooleanSwitch> 或使用代表列舉值的文字（例如） `Error` <xref:System.Diagnostics.TraceSwitch> 。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-128">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="cf6f2-129">`<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。</span><span class="sxs-lookup"><span data-stu-id="cf6f2-129">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf6f2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf6f2-130">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="cf6f2-131">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="cf6f2-131">Trace and Debug Settings Schema</span></span>](index.md)
