---
title: '&lt;接聽程式&gt;元素&lt;來源&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a711b8d6bfd5b6d73d3240cb84810841bdc5a2b6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a><span data-ttu-id="13cd1-102">&lt;接聽程式&gt;元素&lt;來源&gt;</span><span class="sxs-lookup"><span data-stu-id="13cd1-102">&lt;listeners&gt; Element for &lt;source&gt;</span></span>
<span data-ttu-id="13cd1-103">加入或移除接聽程式在<xref:System.Diagnostics.TraceSource.Listeners%2A>集合<xref:System.Diagnostics.TraceSource>。</span><span class="sxs-lookup"><span data-stu-id="13cd1-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="13cd1-104">接聽程式追蹤將輸出導向至適當的目標，例如記錄檔、 視窗或文字檔。</span><span class="sxs-lookup"><span data-stu-id="13cd1-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="13cd1-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="13cd1-105">\<configuration></span></span>  
<span data-ttu-id="13cd1-106">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="13cd1-106">\<system.diagnostics></span></span>  
<span data-ttu-id="13cd1-107">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="13cd1-107">\<sources></span></span>  
<span data-ttu-id="13cd1-108">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="13cd1-108">\<source></span></span>  
<span data-ttu-id="13cd1-109">\<接聽程式 > 項目</span><span class="sxs-lookup"><span data-stu-id="13cd1-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13cd1-110">語法</span><span class="sxs-lookup"><span data-stu-id="13cd1-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13cd1-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="13cd1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="13cd1-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="13cd1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13cd1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="13cd1-113">Attributes</span></span>  
 <span data-ttu-id="13cd1-114">無。</span><span class="sxs-lookup"><span data-stu-id="13cd1-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="13cd1-115">子項目</span><span class="sxs-lookup"><span data-stu-id="13cd1-115">Child Elements</span></span>  
  
|<span data-ttu-id="13cd1-116">項目</span><span class="sxs-lookup"><span data-stu-id="13cd1-116">Element</span></span>|<span data-ttu-id="13cd1-117">描述</span><span class="sxs-lookup"><span data-stu-id="13cd1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13cd1-118">\<add></span><span class="sxs-lookup"><span data-stu-id="13cd1-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="13cd1-119">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="13cd1-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="13cd1-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="13cd1-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="13cd1-121">移除的接聽程式從`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="13cd1-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="13cd1-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="13cd1-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="13cd1-123">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="13cd1-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13cd1-124">父項目</span><span class="sxs-lookup"><span data-stu-id="13cd1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="13cd1-125">項目</span><span class="sxs-lookup"><span data-stu-id="13cd1-125">Element</span></span>|<span data-ttu-id="13cd1-126">描述</span><span class="sxs-lookup"><span data-stu-id="13cd1-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="13cd1-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="13cd1-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="13cd1-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="13cd1-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="13cd1-129">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="13cd1-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="13cd1-130">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="13cd1-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13cd1-131">備註</span><span class="sxs-lookup"><span data-stu-id="13cd1-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="13cd1-132">組態檔</span><span class="sxs-lookup"><span data-stu-id="13cd1-132">Configuration File</span></span>  
 <span data-ttu-id="13cd1-133">此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="13cd1-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13cd1-134">範例</span><span class="sxs-lookup"><span data-stu-id="13cd1-134">Example</span></span>  
 <span data-ttu-id="13cd1-135">下列範例示範如何使用`<listeners>`將主控台追蹤接聽程式，加入的項目`mySource`來源，並移除預設的追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="13cd1-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13cd1-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13cd1-136">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="13cd1-137">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="13cd1-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="13cd1-138">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="13cd1-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
