---
title: <filter> 項目<add>的 <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 2bef729f179b41509d3c0381b26e38e364dbf86b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120740"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="e44b2-102">\<篩選條件 > 項目\<新增 > 針對\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="e44b2-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="e44b2-103">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="e44b2-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="e44b2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e44b2-104">\<configuration></span></span>  
<span data-ttu-id="e44b2-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="e44b2-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e44b2-106">\<sharedListeners > 項目</span><span class="sxs-lookup"><span data-stu-id="e44b2-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="e44b2-107">\<add></span><span class="sxs-lookup"><span data-stu-id="e44b2-107">\<add></span></span>  
<span data-ttu-id="e44b2-108">\<filter></span><span class="sxs-lookup"><span data-stu-id="e44b2-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e44b2-109">語法</span><span class="sxs-lookup"><span data-stu-id="e44b2-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e44b2-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e44b2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e44b2-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e44b2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e44b2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e44b2-112">Attributes</span></span>  
  
|<span data-ttu-id="e44b2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e44b2-113">Attribute</span></span>|<span data-ttu-id="e44b2-114">描述</span><span class="sxs-lookup"><span data-stu-id="e44b2-114">Description</span></span>|  
|---------------|-----------------|  
|**<span data-ttu-id="e44b2-115">類型</span><span class="sxs-lookup"><span data-stu-id="e44b2-115">type</span></span>**|<span data-ttu-id="e44b2-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e44b2-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e44b2-117">指定的篩選器類型。</span><span class="sxs-lookup"><span data-stu-id="e44b2-117">Specifies the type of the filter.</span></span> <span data-ttu-id="e44b2-118">您可以使用類型的完整名稱 (格式為<xref:System.Type.FullName%2A?displayProperty=nameWithType>屬性)，或者您可以使用完整的類型名稱包括組件資訊 (格式為<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>屬性)。</span><span class="sxs-lookup"><span data-stu-id="e44b2-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="e44b2-119">如需建立完整限定的類型名稱的資訊，請參閱[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="e44b2-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|**<span data-ttu-id="e44b2-120">initializeData</span><span class="sxs-lookup"><span data-stu-id="e44b2-120">initializeData</span></span>**|<span data-ttu-id="e44b2-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="e44b2-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e44b2-122">指定的類別，建構函式傳遞的字串。</span><span class="sxs-lookup"><span data-stu-id="e44b2-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e44b2-123">子元素</span><span class="sxs-lookup"><span data-stu-id="e44b2-123">Child Elements</span></span>  
 <span data-ttu-id="e44b2-124">無。</span><span class="sxs-lookup"><span data-stu-id="e44b2-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e44b2-125">父項目</span><span class="sxs-lookup"><span data-stu-id="e44b2-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e44b2-126">項目</span><span class="sxs-lookup"><span data-stu-id="e44b2-126">Element</span></span>|<span data-ttu-id="e44b2-127">描述</span><span class="sxs-lookup"><span data-stu-id="e44b2-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e44b2-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e44b2-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e44b2-129">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="e44b2-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="e44b2-130">任何來源或追蹤項目可以參考的接聽程式的集合。</span><span class="sxs-lookup"><span data-stu-id="e44b2-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="e44b2-131">新增接聽程式，以**sharedListeners**集合。</span><span class="sxs-lookup"><span data-stu-id="e44b2-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e44b2-132">備註</span><span class="sxs-lookup"><span data-stu-id="e44b2-132">Remarks</span></span>  
 <span data-ttu-id="e44b2-133">如果接聽程式已定義在`<add>`項目`<sharedListeners>`項目，應在定義該接聽項的篩選條件`<filter>`子系的項目`<add>`項目。</span><span class="sxs-lookup"><span data-stu-id="e44b2-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="e44b2-134">這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="e44b2-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e44b2-135">範例</span><span class="sxs-lookup"><span data-stu-id="e44b2-135">Example</span></span>  
 <span data-ttu-id="e44b2-136">下列範例示範如何使用`<filter>`新增至追蹤接聽項的篩選條件的項目`console`在`sharedListeners`集合。</span><span class="sxs-lookup"><span data-stu-id="e44b2-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e44b2-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e44b2-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="e44b2-138">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e44b2-138">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
