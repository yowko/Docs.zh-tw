---
title: <filter><add> For<listeners>之的元素<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0d25d0b955a94986147922914068c8a1cf2d96c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920525"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="87544-102">\<針對\<來源 > 的\<接聽項 > \<的 [新增 >] 篩選 > 元素</span><span class="sxs-lookup"><span data-stu-id="87544-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="87544-103">將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="87544-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="87544-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="87544-104">\<configuration></span></span>  
<span data-ttu-id="87544-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="87544-105">\<system.diagnostics></span></span>  
<span data-ttu-id="87544-106">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="87544-106">\<sources></span></span>  
<span data-ttu-id="87544-107">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="87544-107">\<source></span></span>  
<span data-ttu-id="87544-108">\<接聽程式 ></span><span class="sxs-lookup"><span data-stu-id="87544-108">\<listeners></span></span>  
<span data-ttu-id="87544-109">\<add></span><span class="sxs-lookup"><span data-stu-id="87544-109">\<add></span></span>  
<span data-ttu-id="87544-110">\<filter></span><span class="sxs-lookup"><span data-stu-id="87544-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87544-111">語法</span><span class="sxs-lookup"><span data-stu-id="87544-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87544-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87544-112">Attributes and Elements</span></span>  
 <span data-ttu-id="87544-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="87544-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87544-114">屬性</span><span class="sxs-lookup"><span data-stu-id="87544-114">Attributes</span></span>  
  
|<span data-ttu-id="87544-115">屬性</span><span class="sxs-lookup"><span data-stu-id="87544-115">Attribute</span></span>|<span data-ttu-id="87544-116">描述</span><span class="sxs-lookup"><span data-stu-id="87544-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="87544-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="87544-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="87544-118">指定篩選準則的類型, 這應該繼承自<xref:System.Diagnostics.TraceFilter>類別。</span><span class="sxs-lookup"><span data-stu-id="87544-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="87544-119">您可以使用類型的命名空間限定名稱, 它會對應至類型的<xref:System.Type.FullName%2A>屬性, 或者您可以使用包含元件資訊的完整類型名稱, 這會對應<xref:System.Type.AssemblyQualifiedName%2A>至屬性。</span><span class="sxs-lookup"><span data-stu-id="87544-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="87544-120">如需完整型別名稱的詳細資訊, 請參閱[指定完整的型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="87544-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="87544-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="87544-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="87544-122">傳遞給指定之篩選類別之函數的字串。</span><span class="sxs-lookup"><span data-stu-id="87544-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87544-123">子元素</span><span class="sxs-lookup"><span data-stu-id="87544-123">Child Elements</span></span>  
 <span data-ttu-id="87544-124">無。</span><span class="sxs-lookup"><span data-stu-id="87544-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87544-125">父項目</span><span class="sxs-lookup"><span data-stu-id="87544-125">Parent Elements</span></span>  
  
|<span data-ttu-id="87544-126">項目</span><span class="sxs-lookup"><span data-stu-id="87544-126">Element</span></span>|<span data-ttu-id="87544-127">說明</span><span class="sxs-lookup"><span data-stu-id="87544-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="87544-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="87544-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="87544-129">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="87544-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="87544-130">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="87544-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="87544-131">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="87544-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="87544-132">包含收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="87544-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="87544-133">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="87544-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="87544-134">將接聽項新增至追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="87544-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87544-135">備註</span><span class="sxs-lookup"><span data-stu-id="87544-135">Remarks</span></span>  
 <span data-ttu-id="87544-136">元素必須包含在指定接聽程式`<add>`類型的追蹤來源接聽程式元素中, 而不只是在[ \<s >](sharedlisteners-element.md)中定義的接聽項名稱。 `<filter>`</span><span class="sxs-lookup"><span data-stu-id="87544-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="87544-137">如果接聽程式是在[ \<s >](sharedlisteners-element.md)中定義, 則必須在該專案中定義該接聽程式的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="87544-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="87544-138">此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="87544-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87544-139">範例</span><span class="sxs-lookup"><span data-stu-id="87544-139">Example</span></span>  
 <span data-ttu-id="87544-140">下列範例示範如何`<filter>`使用專案, 將篩選準則加入至追蹤來源`myTraceSource`之`Listeners`集合`console`中的接聽程式, 並將篩選事件層級指定為`Error`。</span><span class="sxs-lookup"><span data-stu-id="87544-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="87544-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87544-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="87544-142">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="87544-142">Trace and Debug Settings Schema</span></span>](index.md)
