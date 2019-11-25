---
title: 適用于 <trace> 之 <listeners> <add> 的 <filter> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: cc970240ac07ad3ea72be50d1e9af452da638fa9
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088897"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="13a29-102">\<篩選 > 元素，以 \<為 \<追蹤 > 接聽程式新增 > \<</span><span class="sxs-lookup"><span data-stu-id="13a29-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="13a29-103">將篩選加入至追蹤之 `Listeners` 集合中的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="13a29-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

<span data-ttu-id="13a29-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="13a29-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="13a29-105">&nbsp;&nbsp;[ **\<系統診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="13a29-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="13a29-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<追蹤 >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="13a29-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="13a29-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<接聽程式[ **>** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="13a29-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="13a29-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="13a29-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>\
<span data-ttu-id="13a29-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<篩選 >**</span><span class="sxs-lookup"><span data-stu-id="13a29-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="13a29-110">語法</span><span class="sxs-lookup"><span data-stu-id="13a29-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13a29-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="13a29-111">Attributes and Elements</span></span>  
 <span data-ttu-id="13a29-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="13a29-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13a29-113">屬性</span><span class="sxs-lookup"><span data-stu-id="13a29-113">Attributes</span></span>  
  
|<span data-ttu-id="13a29-114">屬性</span><span class="sxs-lookup"><span data-stu-id="13a29-114">Attribute</span></span>|<span data-ttu-id="13a29-115">描述</span><span class="sxs-lookup"><span data-stu-id="13a29-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="13a29-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="13a29-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="13a29-117">指定篩選準則的類型，應該繼承自 <xref:System.Diagnostics.TraceFilter> 類別。</span><span class="sxs-lookup"><span data-stu-id="13a29-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="13a29-118">您可以使用類型的命名空間限定名稱，它會對應至類型的 <xref:System.Type.FullName%2A> 屬性，或者您可以使用包含元件資訊的完整類型名稱，這會對應至 <xref:System.Type.AssemblyQualifiedName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="13a29-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="13a29-119">如需完整型別名稱的詳細資訊，請參閱[指定完整的型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="13a29-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="13a29-120">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="13a29-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="13a29-121">傳遞給指定之篩選類別之函數的字串。</span><span class="sxs-lookup"><span data-stu-id="13a29-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13a29-122">子項目</span><span class="sxs-lookup"><span data-stu-id="13a29-122">Child Elements</span></span>  
 <span data-ttu-id="13a29-123">無。</span><span class="sxs-lookup"><span data-stu-id="13a29-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13a29-124">父項目</span><span class="sxs-lookup"><span data-stu-id="13a29-124">Parent Elements</span></span>  
  
|<span data-ttu-id="13a29-125">項目</span><span class="sxs-lookup"><span data-stu-id="13a29-125">Element</span></span>|<span data-ttu-id="13a29-126">描述</span><span class="sxs-lookup"><span data-stu-id="13a29-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="13a29-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="13a29-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="13a29-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="13a29-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="13a29-129">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="13a29-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="13a29-130">包含收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="13a29-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="13a29-131">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="13a29-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="13a29-132">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="13a29-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13a29-133">備註</span><span class="sxs-lookup"><span data-stu-id="13a29-133">Remarks</span></span>  
 <span data-ttu-id="13a29-134">`<filter>` 元素必須包含在指定接聽程式類型的追蹤接聽項 `<add>` 元素中，而不只是在[\<s >](sharedlisteners-element.md)中定義的接聽程式名稱。</span><span class="sxs-lookup"><span data-stu-id="13a29-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="13a29-135">如果接聽程式是在[\<s >](sharedlisteners-element.md)中定義，則必須在該元素中定義該接聽程式的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="13a29-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="13a29-136">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="13a29-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13a29-137">範例</span><span class="sxs-lookup"><span data-stu-id="13a29-137">Example</span></span>  
 <span data-ttu-id="13a29-138">下列範例示範如何使用 `<filter>` 專案，將篩選準則加入至追蹤的 `Listeners` 集合中的接聽程式 `console`，並將篩選事件層級指定為 [`Error`]。</span><span class="sxs-lookup"><span data-stu-id="13a29-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13a29-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="13a29-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="13a29-140">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="13a29-140">Trace and Debug Settings Schema</span></span>](index.md)
