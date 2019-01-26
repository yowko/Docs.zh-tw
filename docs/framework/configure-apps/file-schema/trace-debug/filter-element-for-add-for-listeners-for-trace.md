---
title: '&lt;篩選條件&gt;項目&lt;新增&gt;如&lt;接聽程式&gt;如&lt;追蹤&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b53c3e4cc2362a1f1dc0312d59aff403ca924b5e
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084181"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="0acea-102">&lt;篩選條件&gt;項目&lt;新增&gt;如&lt;接聽程式&gt;如&lt;追蹤&gt;</span><span class="sxs-lookup"><span data-stu-id="0acea-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="0acea-103">將篩選加入至中的接聽項`Listeners`追蹤的集合。</span><span class="sxs-lookup"><span data-stu-id="0acea-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="0acea-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0acea-104">\<configuration></span></span>  
<span data-ttu-id="0acea-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="0acea-105">\<system.diagnostics></span></span>  
<span data-ttu-id="0acea-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="0acea-106">\<trace></span></span>  
<span data-ttu-id="0acea-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="0acea-107">\<listeners></span></span>  
<span data-ttu-id="0acea-108">\<add></span><span class="sxs-lookup"><span data-stu-id="0acea-108">\<add></span></span>  
<span data-ttu-id="0acea-109">\<filter></span><span class="sxs-lookup"><span data-stu-id="0acea-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0acea-110">語法</span><span class="sxs-lookup"><span data-stu-id="0acea-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0acea-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0acea-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0acea-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0acea-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0acea-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0acea-113">Attributes</span></span>  
  
|<span data-ttu-id="0acea-114">屬性</span><span class="sxs-lookup"><span data-stu-id="0acea-114">Attribute</span></span>|<span data-ttu-id="0acea-115">描述</span><span class="sxs-lookup"><span data-stu-id="0acea-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="0acea-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0acea-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="0acea-117">指定的篩選器，應該繼承自類型<xref:System.Diagnostics.TraceFilter>類別。</span><span class="sxs-lookup"><span data-stu-id="0acea-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="0acea-118">您可以使用的命名空間限定名稱的型別，其對應至型別的<xref:System.Type.FullName%2A>屬性，或者您可以使用完整的類型名稱包括組件資訊，其對應至<xref:System.Type.AssemblyQualifiedName%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0acea-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="0acea-119">如需完整的型別名稱的資訊，請參閱[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="0acea-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="0acea-120">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="0acea-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0acea-121">指定的篩選條件類別傳遞至建構函式的字串。</span><span class="sxs-lookup"><span data-stu-id="0acea-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0acea-122">子元素</span><span class="sxs-lookup"><span data-stu-id="0acea-122">Child Elements</span></span>  
 <span data-ttu-id="0acea-123">無。</span><span class="sxs-lookup"><span data-stu-id="0acea-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0acea-124">父項目</span><span class="sxs-lookup"><span data-stu-id="0acea-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0acea-125">項目</span><span class="sxs-lookup"><span data-stu-id="0acea-125">Element</span></span>|<span data-ttu-id="0acea-126">描述</span><span class="sxs-lookup"><span data-stu-id="0acea-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0acea-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0acea-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0acea-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="0acea-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="0acea-129">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="0acea-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="0acea-130">包含用於收集、 儲存及路由傳送訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="0acea-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="0acea-131">接聽程式將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="0acea-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="0acea-132">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="0acea-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0acea-133">備註</span><span class="sxs-lookup"><span data-stu-id="0acea-133">Remarks</span></span>  
 <span data-ttu-id="0acea-134">`<filter>`項目必須包含在`<add>`中的追蹤接聽項，指定接聽程式類型的項目，不只是接聽程式的名稱定義[ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)。</span><span class="sxs-lookup"><span data-stu-id="0acea-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="0acea-135">如果接聽程式已定義在[ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)，必須在該項目中定義該接聽項的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="0acea-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="0acea-136">這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="0acea-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0acea-137">範例</span><span class="sxs-lookup"><span data-stu-id="0acea-137">Example</span></span>  
 <span data-ttu-id="0acea-138">下列範例示範如何使用`<filter>`項目加入至接聽程式的篩選器`console`中`Listeners`收集追蹤，並指定做為篩選事件層級`Error`。</span><span class="sxs-lookup"><span data-stu-id="0acea-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0acea-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0acea-139">See also</span></span>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="0acea-140">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0acea-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
