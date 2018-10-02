---
title: '&lt;接聽程式&gt;項目&lt;來源&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 86b85779f4eff72e8ab910a5ccd32fd369270509
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027811"
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a><span data-ttu-id="0afb8-102">&lt;接聽程式&gt;項目&lt;來源&gt;</span><span class="sxs-lookup"><span data-stu-id="0afb8-102">&lt;listeners&gt; Element for &lt;source&gt;</span></span>
<span data-ttu-id="0afb8-103">新增或移除接聽程式中的<xref:System.Diagnostics.TraceSource.Listeners%2A>集合<xref:System.Diagnostics.TraceSource>。</span><span class="sxs-lookup"><span data-stu-id="0afb8-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="0afb8-104">接聽程式會將適當的目標，例如記錄檔、 視窗或文字檔追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="0afb8-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="0afb8-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0afb8-105">\<configuration></span></span>  
<span data-ttu-id="0afb8-106">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="0afb8-106">\<system.diagnostics></span></span>  
<span data-ttu-id="0afb8-107">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="0afb8-107">\<sources></span></span>  
<span data-ttu-id="0afb8-108">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="0afb8-108">\<source></span></span>  
<span data-ttu-id="0afb8-109">\<接聽程式 > 項目</span><span class="sxs-lookup"><span data-stu-id="0afb8-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0afb8-110">語法</span><span class="sxs-lookup"><span data-stu-id="0afb8-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0afb8-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0afb8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0afb8-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0afb8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0afb8-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0afb8-113">Attributes</span></span>  
 <span data-ttu-id="0afb8-114">無。</span><span class="sxs-lookup"><span data-stu-id="0afb8-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0afb8-115">子元素</span><span class="sxs-lookup"><span data-stu-id="0afb8-115">Child Elements</span></span>  
  
|<span data-ttu-id="0afb8-116">項目</span><span class="sxs-lookup"><span data-stu-id="0afb8-116">Element</span></span>|<span data-ttu-id="0afb8-117">描述</span><span class="sxs-lookup"><span data-stu-id="0afb8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0afb8-118">\<add></span><span class="sxs-lookup"><span data-stu-id="0afb8-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="0afb8-119">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="0afb8-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="0afb8-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="0afb8-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="0afb8-121">移除接聽程式從`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="0afb8-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="0afb8-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="0afb8-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="0afb8-123">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="0afb8-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0afb8-124">父項目</span><span class="sxs-lookup"><span data-stu-id="0afb8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0afb8-125">項目</span><span class="sxs-lookup"><span data-stu-id="0afb8-125">Element</span></span>|<span data-ttu-id="0afb8-126">描述</span><span class="sxs-lookup"><span data-stu-id="0afb8-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0afb8-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0afb8-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0afb8-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="0afb8-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="0afb8-129">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="0afb8-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="0afb8-130">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="0afb8-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0afb8-131">備註</span><span class="sxs-lookup"><span data-stu-id="0afb8-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0afb8-132">組態檔</span><span class="sxs-lookup"><span data-stu-id="0afb8-132">Configuration File</span></span>  
 <span data-ttu-id="0afb8-133">這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="0afb8-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0afb8-134">範例</span><span class="sxs-lookup"><span data-stu-id="0afb8-134">Example</span></span>  
 <span data-ttu-id="0afb8-135">下列範例示範如何使用`<listeners>`要加入的主控台追蹤接聽程式項目`mySource`來源，以及移除預設的追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="0afb8-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0afb8-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0afb8-136">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="0afb8-137">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0afb8-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="0afb8-138">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="0afb8-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
