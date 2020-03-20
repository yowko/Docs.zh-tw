---
title: <filter>用於<add><sharedListeners>
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
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153449"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="fe5a7-102">\<用於\<添加\<共用攔截器>>元素></span><span class="sxs-lookup"><span data-stu-id="fe5a7-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="fe5a7-103">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

<span data-ttu-id="fe5a7-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe5a7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fe5a7-105">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe5a7-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="fe5a7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<共用攔截器>**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe5a7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="fe5a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<添加>**](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="fe5a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>\
<span data-ttu-id="fe5a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<篩檢程式>**</span><span class="sxs-lookup"><span data-stu-id="fe5a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fe5a7-109">語法</span><span class="sxs-lookup"><span data-stu-id="fe5a7-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe5a7-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fe5a7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fe5a7-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe5a7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="fe5a7-112">Attributes</span></span>  
  
|<span data-ttu-id="fe5a7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fe5a7-113">Attribute</span></span>|<span data-ttu-id="fe5a7-114">描述</span><span class="sxs-lookup"><span data-stu-id="fe5a7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe5a7-115">**型別**</span><span class="sxs-lookup"><span data-stu-id="fe5a7-115">**type**</span></span>|<span data-ttu-id="fe5a7-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="fe5a7-117">指定篩選器的類型。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-117">Specifies the type of the filter.</span></span> <span data-ttu-id="fe5a7-118">只能使用類型的全名（<xref:System.Type.FullName%2A?displayProperty=nameWithType>以屬性的格式），也可以使用完全限定的類型名稱，包括程式集資訊（以<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>屬性的格式）。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="fe5a7-119">有關創建完全限定類型名稱的資訊，請參閱[指定完全限定類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="fe5a7-120">**初始化資料**</span><span class="sxs-lookup"><span data-stu-id="fe5a7-120">**initializeData**</span></span>|<span data-ttu-id="fe5a7-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fe5a7-122">字串傳遞給指定類的建構函式。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe5a7-123">子元素</span><span class="sxs-lookup"><span data-stu-id="fe5a7-123">Child Elements</span></span>  
 <span data-ttu-id="fe5a7-124">無。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe5a7-125">父項目</span><span class="sxs-lookup"><span data-stu-id="fe5a7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fe5a7-126">元素</span><span class="sxs-lookup"><span data-stu-id="fe5a7-126">Element</span></span>|<span data-ttu-id="fe5a7-127">描述</span><span class="sxs-lookup"><span data-stu-id="fe5a7-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fe5a7-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fe5a7-129">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="fe5a7-130">任何源或跟蹤元素都可以引用的攔截器集合。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="fe5a7-131">將攔截器添加到**共用攔截器**集合。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe5a7-132">備註</span><span class="sxs-lookup"><span data-stu-id="fe5a7-132">Remarks</span></span>  
 <span data-ttu-id="fe5a7-133">如果在`<add>``<sharedListeners>`元素的元素中定義了攔截器，則該攔截器的篩選器應在元素中定義，該`<filter>`元素是該元素的`<add>`子項目。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="fe5a7-134">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe5a7-135">範例</span><span class="sxs-lookup"><span data-stu-id="fe5a7-135">Example</span></span>  
 <span data-ttu-id="fe5a7-136">下面的示例演示如何使用 元素`<filter>`向`console``sharedListeners`集合中的跟蹤攔截器添加篩選器。</span><span class="sxs-lookup"><span data-stu-id="fe5a7-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe5a7-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe5a7-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="fe5a7-138">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="fe5a7-138">Trace and Debug Settings Schema</span></span>](index.md)
