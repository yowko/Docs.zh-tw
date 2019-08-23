---
title: <filter><add> For<listeners>之的元素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: afde5381a7dd7dfe6a1a9d238a2029511bd9bae2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927140"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="397f2-102">\<針對\<追蹤 > 的\<[加入 > \<>] 篩選準則 > 元素</span><span class="sxs-lookup"><span data-stu-id="397f2-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="397f2-103">將篩選加入至追蹤之`Listeners`集合中的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="397f2-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="397f2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="397f2-104">\<configuration></span></span>  
<span data-ttu-id="397f2-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="397f2-105">\<system.diagnostics></span></span>  
<span data-ttu-id="397f2-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="397f2-106">\<trace></span></span>  
<span data-ttu-id="397f2-107">\<接聽程式 ></span><span class="sxs-lookup"><span data-stu-id="397f2-107">\<listeners></span></span>  
<span data-ttu-id="397f2-108">\<add></span><span class="sxs-lookup"><span data-stu-id="397f2-108">\<add></span></span>  
<span data-ttu-id="397f2-109">\<filter></span><span class="sxs-lookup"><span data-stu-id="397f2-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="397f2-110">語法</span><span class="sxs-lookup"><span data-stu-id="397f2-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="397f2-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="397f2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="397f2-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="397f2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="397f2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="397f2-113">Attributes</span></span>  
  
|<span data-ttu-id="397f2-114">屬性</span><span class="sxs-lookup"><span data-stu-id="397f2-114">Attribute</span></span>|<span data-ttu-id="397f2-115">描述</span><span class="sxs-lookup"><span data-stu-id="397f2-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="397f2-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="397f2-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="397f2-117">指定篩選準則的類型, 這應該繼承自<xref:System.Diagnostics.TraceFilter>類別。</span><span class="sxs-lookup"><span data-stu-id="397f2-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="397f2-118">您可以使用類型的命名空間限定名稱, 它會對應至類型的<xref:System.Type.FullName%2A>屬性, 或者您可以使用包含元件資訊的完整類型名稱, 這會對應<xref:System.Type.AssemblyQualifiedName%2A>至屬性。</span><span class="sxs-lookup"><span data-stu-id="397f2-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="397f2-119">如需完整型別名稱的詳細資訊, 請參閱[指定完整的型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="397f2-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="397f2-120">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="397f2-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="397f2-121">傳遞給指定之篩選類別之函數的字串。</span><span class="sxs-lookup"><span data-stu-id="397f2-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="397f2-122">子元素</span><span class="sxs-lookup"><span data-stu-id="397f2-122">Child Elements</span></span>  
 <span data-ttu-id="397f2-123">無。</span><span class="sxs-lookup"><span data-stu-id="397f2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="397f2-124">父項目</span><span class="sxs-lookup"><span data-stu-id="397f2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="397f2-125">項目</span><span class="sxs-lookup"><span data-stu-id="397f2-125">Element</span></span>|<span data-ttu-id="397f2-126">說明</span><span class="sxs-lookup"><span data-stu-id="397f2-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="397f2-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="397f2-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="397f2-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="397f2-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="397f2-129">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="397f2-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="397f2-130">包含收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="397f2-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="397f2-131">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="397f2-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="397f2-132">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="397f2-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="397f2-133">備註</span><span class="sxs-lookup"><span data-stu-id="397f2-133">Remarks</span></span>  
 <span data-ttu-id="397f2-134">元素必須包含在指定接聽程式`<add>`類型的追蹤接聽項的專案中, 而不只是在[ \<s >](sharedlisteners-element.md)中定義的接聽程式名稱。 `<filter>`</span><span class="sxs-lookup"><span data-stu-id="397f2-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="397f2-135">如果接聽程式是在[ \<s >](sharedlisteners-element.md)中定義, 則必須在該專案中定義該接聽程式的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="397f2-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="397f2-136">此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="397f2-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="397f2-137">範例</span><span class="sxs-lookup"><span data-stu-id="397f2-137">Example</span></span>  
 <span data-ttu-id="397f2-138">下列範例示範如何`<filter>`使用專案, 將篩選準則加入至`console` `Listeners`集合中的接聽程式, 並將篩選事件層級指定為`Error`。</span><span class="sxs-lookup"><span data-stu-id="397f2-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="397f2-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="397f2-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="397f2-140">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="397f2-140">Trace and Debug Settings Schema</span></span>](index.md)
