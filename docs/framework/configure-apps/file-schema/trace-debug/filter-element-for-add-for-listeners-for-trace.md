---
title: '&lt;篩選&gt;元素&lt;新增&gt;如&lt;接聽程式&gt;如&lt;追蹤&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 095212f73adb906d9d80db747c331c436c1cf846
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745774"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="4f641-102">&lt;篩選&gt;元素&lt;新增&gt;如&lt;接聽程式&gt;如&lt;追蹤&gt;</span><span class="sxs-lookup"><span data-stu-id="4f641-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="4f641-103">將篩選加入至接聽程式在`Listeners`追蹤的集合。</span><span class="sxs-lookup"><span data-stu-id="4f641-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="4f641-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4f641-104">\<configuration></span></span>  
<span data-ttu-id="4f641-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="4f641-105">\<system.diagnostics></span></span>  
<span data-ttu-id="4f641-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="4f641-106">\<trace></span></span>  
<span data-ttu-id="4f641-107">\<接聽項 ></span><span class="sxs-lookup"><span data-stu-id="4f641-107">\<listeners></span></span>  
<span data-ttu-id="4f641-108">\<add></span><span class="sxs-lookup"><span data-stu-id="4f641-108">\<add></span></span>  
<span data-ttu-id="4f641-109">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="4f641-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f641-110">語法</span><span class="sxs-lookup"><span data-stu-id="4f641-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f641-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4f641-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4f641-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4f641-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f641-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4f641-113">Attributes</span></span>  
  
|<span data-ttu-id="4f641-114">屬性</span><span class="sxs-lookup"><span data-stu-id="4f641-114">Attribute</span></span>|<span data-ttu-id="4f641-115">描述</span><span class="sxs-lookup"><span data-stu-id="4f641-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="4f641-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="4f641-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="4f641-117">指定類型的篩選器，應該繼承自<xref:System.Diagnostics.TraceFilter>類別。</span><span class="sxs-lookup"><span data-stu-id="4f641-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="4f641-118">您可以使用的類型，對應於該類型的命名空間限定名稱<xref:System.Type.FullName%2A>屬性，或者您可以使用的完整限定的類型名稱，包括組件資訊，其對應至<xref:System.Type.AssemblyQualifiedName%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4f641-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="4f641-119">如需完整限定的類型名稱的資訊，請參閱[指定限定的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="4f641-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="4f641-120">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="4f641-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4f641-121">指定的篩選條件類別傳遞至建構函式的字串。</span><span class="sxs-lookup"><span data-stu-id="4f641-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f641-122">子項目</span><span class="sxs-lookup"><span data-stu-id="4f641-122">Child Elements</span></span>  
 <span data-ttu-id="4f641-123">無。</span><span class="sxs-lookup"><span data-stu-id="4f641-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f641-124">父項目</span><span class="sxs-lookup"><span data-stu-id="4f641-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4f641-125">項目</span><span class="sxs-lookup"><span data-stu-id="4f641-125">Element</span></span>|<span data-ttu-id="4f641-126">描述</span><span class="sxs-lookup"><span data-stu-id="4f641-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4f641-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4f641-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4f641-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4f641-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="4f641-129">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="4f641-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4f641-130">包含收集、 儲存和路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="4f641-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="4f641-131">接聽程式將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="4f641-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="4f641-132">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="4f641-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f641-133">備註</span><span class="sxs-lookup"><span data-stu-id="4f641-133">Remarks</span></span>  
 <span data-ttu-id="4f641-134">`<filter>`元素必須包含在`<add>`中定義的追蹤接聽項，指定接聽程式類型的項目，不只接聽程式名稱[ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)。</span><span class="sxs-lookup"><span data-stu-id="4f641-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="4f641-135">如果接聽程式已定義在[ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)，必須定義該接聽項的篩選條件，該元素中。</span><span class="sxs-lookup"><span data-stu-id="4f641-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="4f641-136">此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="4f641-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f641-137">範例</span><span class="sxs-lookup"><span data-stu-id="4f641-137">Example</span></span>  
 <span data-ttu-id="4f641-138">下列範例示範如何使用`<filter>`將篩選加入至接聽程式的項目`console`中`Listeners`集合指定的篩選事件層級的追蹤`Error`。</span><span class="sxs-lookup"><span data-stu-id="4f641-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f641-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f641-139">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="4f641-140">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4f641-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
