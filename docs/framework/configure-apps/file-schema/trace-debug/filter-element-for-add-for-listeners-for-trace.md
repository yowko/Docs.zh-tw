---
title: <filter>用於<add> <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153462"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="f9dce-102">\<篩選器>元素，\<用於添加\<>跟蹤>的\<攔截器></span><span class="sxs-lookup"><span data-stu-id="f9dce-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="f9dce-103">將篩選器添加到跟蹤集合中的`Listeners`攔截器。</span><span class="sxs-lookup"><span data-stu-id="f9dce-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

<span data-ttu-id="f9dce-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f9dce-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f9dce-105">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="f9dce-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="f9dce-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="f9dce-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="f9dce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<聽眾>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="f9dce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="f9dce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<添加>**](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="f9dce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>\
<span data-ttu-id="f9dce-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<篩檢程式>**</span><span class="sxs-lookup"><span data-stu-id="f9dce-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f9dce-110">語法</span><span class="sxs-lookup"><span data-stu-id="f9dce-110">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9dce-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f9dce-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f9dce-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f9dce-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9dce-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f9dce-113">Attributes</span></span>  
  
|<span data-ttu-id="f9dce-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f9dce-114">Attribute</span></span>|<span data-ttu-id="f9dce-115">描述</span><span class="sxs-lookup"><span data-stu-id="f9dce-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="f9dce-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dce-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="f9dce-117">指定篩選器的類型，該篩選器應從<xref:System.Diagnostics.TraceFilter>類繼承。</span><span class="sxs-lookup"><span data-stu-id="f9dce-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="f9dce-118">可以使用類型的名稱空間限定名稱（對應于類型的屬性<xref:System.Type.FullName%2A>），也可以使用完全限定的類型名稱（包括對應于該屬性的<xref:System.Type.AssemblyQualifiedName%2A>程式集資訊）。</span><span class="sxs-lookup"><span data-stu-id="f9dce-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="f9dce-119">有關完全限定類型名稱的資訊，請參閱[指定完全限定類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="f9dce-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="f9dce-120">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f9dce-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f9dce-121">字串傳遞給指定篩選器類的建構函式。</span><span class="sxs-lookup"><span data-stu-id="f9dce-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9dce-122">子元素</span><span class="sxs-lookup"><span data-stu-id="f9dce-122">Child Elements</span></span>  
 <span data-ttu-id="f9dce-123">無。</span><span class="sxs-lookup"><span data-stu-id="f9dce-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9dce-124">父項目</span><span class="sxs-lookup"><span data-stu-id="f9dce-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f9dce-125">元素</span><span class="sxs-lookup"><span data-stu-id="f9dce-125">Element</span></span>|<span data-ttu-id="f9dce-126">描述</span><span class="sxs-lookup"><span data-stu-id="f9dce-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f9dce-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f9dce-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f9dce-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="f9dce-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="f9dce-129">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="f9dce-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="f9dce-130">包含收集、存儲和路由消息的攔截器。</span><span class="sxs-lookup"><span data-stu-id="f9dce-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="f9dce-131">攔截器將跟蹤輸出定向到適當的目標。</span><span class="sxs-lookup"><span data-stu-id="f9dce-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="f9dce-132">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="f9dce-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9dce-133">備註</span><span class="sxs-lookup"><span data-stu-id="f9dce-133">Remarks</span></span>  
 <span data-ttu-id="f9dce-134">元素`<filter>`必須包含在指定攔截器`<add>`類型的跟蹤攔截器的元素中，而不僅僅是[\<在共用攔截器>](sharedlisteners-element.md)中定義的攔截器的名稱。</span><span class="sxs-lookup"><span data-stu-id="f9dce-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="f9dce-135">如果在[\<共用攔截器>](sharedlisteners-element.md)中定義攔截器，則必須在該元素中定義該攔截器的篩選器。</span><span class="sxs-lookup"><span data-stu-id="f9dce-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="f9dce-136">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="f9dce-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9dce-137">範例</span><span class="sxs-lookup"><span data-stu-id="f9dce-137">Example</span></span>  
 <span data-ttu-id="f9dce-138">下面的示例演示如何使用`<filter>`元素向跟蹤集合中的`console``Listeners`攔截器添加篩選器，將篩選器事件級別指定為`Error`。</span><span class="sxs-lookup"><span data-stu-id="f9dce-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9dce-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9dce-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="f9dce-140">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="f9dce-140">Trace and Debug Settings Schema</span></span>](index.md)
