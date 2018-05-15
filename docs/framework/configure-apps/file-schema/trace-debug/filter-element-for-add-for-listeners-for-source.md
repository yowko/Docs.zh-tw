---
title: '&lt;篩選&gt;元素&lt;新增&gt;如&lt;接聽程式&gt;如&lt;來源&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 763d15a1391d8c9539d5fb92d4ad50132c17c065
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="2fe42-102">&lt;篩選&gt;元素&lt;新增&gt;如&lt;接聽程式&gt;如&lt;來源&gt;</span><span class="sxs-lookup"><span data-stu-id="2fe42-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="2fe42-103">將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="2fe42-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="2fe42-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2fe42-104">\<configuration></span></span>  
<span data-ttu-id="2fe42-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="2fe42-105">\<system.diagnostics></span></span>  
<span data-ttu-id="2fe42-106">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="2fe42-106">\<sources></span></span>  
<span data-ttu-id="2fe42-107">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="2fe42-107">\<source></span></span>  
<span data-ttu-id="2fe42-108">\<接聽項 ></span><span class="sxs-lookup"><span data-stu-id="2fe42-108">\<listeners></span></span>  
<span data-ttu-id="2fe42-109">\<add></span><span class="sxs-lookup"><span data-stu-id="2fe42-109">\<add></span></span>  
<span data-ttu-id="2fe42-110">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="2fe42-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fe42-111">語法</span><span class="sxs-lookup"><span data-stu-id="2fe42-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fe42-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2fe42-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2fe42-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2fe42-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fe42-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2fe42-114">Attributes</span></span>  
  
|<span data-ttu-id="2fe42-115">屬性</span><span class="sxs-lookup"><span data-stu-id="2fe42-115">Attribute</span></span>|<span data-ttu-id="2fe42-116">描述</span><span class="sxs-lookup"><span data-stu-id="2fe42-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="2fe42-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2fe42-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="2fe42-118">指定類型的篩選器，應該繼承自<xref:System.Diagnostics.TraceFilter>類別。</span><span class="sxs-lookup"><span data-stu-id="2fe42-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="2fe42-119">您可以使用的類型，對應於該類型的命名空間限定名稱<xref:System.Type.FullName%2A>屬性，或者您可以使用的完整限定的類型名稱，包括組件資訊，其對應至<xref:System.Type.AssemblyQualifiedName%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="2fe42-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="2fe42-120">如需完整限定的類型名稱的資訊，請參閱[指定限定的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="2fe42-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="2fe42-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="2fe42-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2fe42-122">指定的篩選條件類別傳遞至建構函式的字串。</span><span class="sxs-lookup"><span data-stu-id="2fe42-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fe42-123">子項目</span><span class="sxs-lookup"><span data-stu-id="2fe42-123">Child Elements</span></span>  
 <span data-ttu-id="2fe42-124">無。</span><span class="sxs-lookup"><span data-stu-id="2fe42-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fe42-125">父項目</span><span class="sxs-lookup"><span data-stu-id="2fe42-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2fe42-126">項目</span><span class="sxs-lookup"><span data-stu-id="2fe42-126">Element</span></span>|<span data-ttu-id="2fe42-127">描述</span><span class="sxs-lookup"><span data-stu-id="2fe42-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2fe42-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2fe42-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2fe42-129">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="2fe42-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="2fe42-130">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="2fe42-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="2fe42-131">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="2fe42-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="2fe42-132">包含收集、 儲存和路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="2fe42-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="2fe42-133">接聽程式將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="2fe42-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="2fe42-134">將接聽項新增至追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="2fe42-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fe42-135">備註</span><span class="sxs-lookup"><span data-stu-id="2fe42-135">Remarks</span></span>  
 <span data-ttu-id="2fe42-136">`<filter>`元素必須包含在`<add>`中的項目指定的接聽程式類型的追蹤來源接聽程式，不只接聽程式的名稱定義[ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)。</span><span class="sxs-lookup"><span data-stu-id="2fe42-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="2fe42-137">如果接聽程式已定義在[ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)，必須定義該接聽項的篩選條件，該元素中。</span><span class="sxs-lookup"><span data-stu-id="2fe42-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="2fe42-138">此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="2fe42-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fe42-139">範例</span><span class="sxs-lookup"><span data-stu-id="2fe42-139">Example</span></span>  
 <span data-ttu-id="2fe42-140">下列範例示範如何使用`<filter>`將篩選加入至接聽程式的項目`console`中`Listeners`追蹤來源的集合`myTraceSource`，指定做為篩選事件層級`Error`。</span><span class="sxs-lookup"><span data-stu-id="2fe42-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fe42-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fe42-141">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="2fe42-142">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2fe42-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
