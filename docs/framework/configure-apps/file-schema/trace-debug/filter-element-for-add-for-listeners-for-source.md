---
title: <filter>用於<add> <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153512"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="d660d-102">\<篩選器>元素，\<用於為\<\<源>>的攔截器添加></span><span class="sxs-lookup"><span data-stu-id="d660d-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="d660d-103">將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="d660d-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="d660d-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d660d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d660d-105">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="d660d-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="d660d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<來源>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="d660d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="d660d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<源>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="d660d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="d660d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<聽眾>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="d660d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="d660d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<添加>**](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="d660d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>\
<span data-ttu-id="d660d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<篩檢程式>**</span><span class="sxs-lookup"><span data-stu-id="d660d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d660d-111">語法</span><span class="sxs-lookup"><span data-stu-id="d660d-111">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d660d-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d660d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d660d-113">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d660d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d660d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d660d-114">Attributes</span></span>  
  
|<span data-ttu-id="d660d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="d660d-115">Attribute</span></span>|<span data-ttu-id="d660d-116">描述</span><span class="sxs-lookup"><span data-stu-id="d660d-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="d660d-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d660d-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="d660d-118">指定篩選器的類型，該篩選器應從<xref:System.Diagnostics.TraceFilter>類繼承。</span><span class="sxs-lookup"><span data-stu-id="d660d-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="d660d-119">可以使用類型的名稱空間限定名稱（對應于類型的屬性<xref:System.Type.FullName%2A>），也可以使用完全限定的類型名稱（包括對應于該屬性的<xref:System.Type.AssemblyQualifiedName%2A>程式集資訊）。</span><span class="sxs-lookup"><span data-stu-id="d660d-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="d660d-120">有關完全限定類型名稱的資訊，請參閱[指定完全限定類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="d660d-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="d660d-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d660d-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d660d-122">字串傳遞給指定篩選器類的建構函式。</span><span class="sxs-lookup"><span data-stu-id="d660d-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d660d-123">子元素</span><span class="sxs-lookup"><span data-stu-id="d660d-123">Child Elements</span></span>  
 <span data-ttu-id="d660d-124">無。</span><span class="sxs-lookup"><span data-stu-id="d660d-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d660d-125">父項目</span><span class="sxs-lookup"><span data-stu-id="d660d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d660d-126">元素</span><span class="sxs-lookup"><span data-stu-id="d660d-126">Element</span></span>|<span data-ttu-id="d660d-127">描述</span><span class="sxs-lookup"><span data-stu-id="d660d-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d660d-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d660d-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d660d-129">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="d660d-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="d660d-130">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="d660d-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="d660d-131">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="d660d-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="d660d-132">包含收集、存儲和路由消息的攔截器。</span><span class="sxs-lookup"><span data-stu-id="d660d-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="d660d-133">攔截器將跟蹤輸出定向到適當的目標。</span><span class="sxs-lookup"><span data-stu-id="d660d-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="d660d-134">將接聽項新增至追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="d660d-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d660d-135">備註</span><span class="sxs-lookup"><span data-stu-id="d660d-135">Remarks</span></span>  
 <span data-ttu-id="d660d-136">元素`<filter>`必須包含在指定攔截器`<add>`類型的跟蹤源攔截器的元素中，而不僅僅是[\<在共用攔截器>](sharedlisteners-element.md)中定義的攔截器的名稱。</span><span class="sxs-lookup"><span data-stu-id="d660d-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="d660d-137">如果在[\<共用攔截器>](sharedlisteners-element.md)中定義攔截器，則必須在該元素中定義該攔截器的篩選器。</span><span class="sxs-lookup"><span data-stu-id="d660d-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="d660d-138">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="d660d-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d660d-139">範例</span><span class="sxs-lookup"><span data-stu-id="d660d-139">Example</span></span>  
 <span data-ttu-id="d660d-140">下面的示例演示如何`<filter>`使用 元素向跟蹤源`console``Listeners``myTraceSource`集合中的攔截器添加篩選器，將篩選器事件級別指定為`Error`。</span><span class="sxs-lookup"><span data-stu-id="d660d-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d660d-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d660d-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="d660d-142">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="d660d-142">Trace and Debug Settings Schema</span></span>](index.md)
