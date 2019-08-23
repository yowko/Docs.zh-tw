---
title: <filter><add> For 的元素<sharedListeners>
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
ms.openlocfilehash: 571a3add232f3e4f9747040dc104b85e8cc3085e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920515"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="bcb57-102">\<針對\<s > 的\<[新增 >] 篩選 > 元素</span><span class="sxs-lookup"><span data-stu-id="bcb57-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="bcb57-103">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="bcb57-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="bcb57-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="bcb57-104">\<configuration></span></span>  
<span data-ttu-id="bcb57-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="bcb57-105">\<system.diagnostics></span></span>  
<span data-ttu-id="bcb57-106">\<s > 元素</span><span class="sxs-lookup"><span data-stu-id="bcb57-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="bcb57-107">\<add></span><span class="sxs-lookup"><span data-stu-id="bcb57-107">\<add></span></span>  
<span data-ttu-id="bcb57-108">\<filter></span><span class="sxs-lookup"><span data-stu-id="bcb57-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb57-109">語法</span><span class="sxs-lookup"><span data-stu-id="bcb57-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcb57-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bcb57-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bcb57-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bcb57-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcb57-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bcb57-112">Attributes</span></span>  
  
|<span data-ttu-id="bcb57-113">屬性</span><span class="sxs-lookup"><span data-stu-id="bcb57-113">Attribute</span></span>|<span data-ttu-id="bcb57-114">描述</span><span class="sxs-lookup"><span data-stu-id="bcb57-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bcb57-115">**type**</span><span class="sxs-lookup"><span data-stu-id="bcb57-115">**type**</span></span>|<span data-ttu-id="bcb57-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="bcb57-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="bcb57-117">指定篩選準則的類型。</span><span class="sxs-lookup"><span data-stu-id="bcb57-117">Specifies the type of the filter.</span></span> <span data-ttu-id="bcb57-118">您只能使用類型的完整名稱 (以<xref:System.Type.FullName%2A?displayProperty=nameWithType>屬性的格式), 也可以使用包含元件資訊的完整類型名稱 (以<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>屬性的格式)。</span><span class="sxs-lookup"><span data-stu-id="bcb57-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="bcb57-119">如需建立完整型別名稱的相關資訊, 請參閱[指定完整的型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="bcb57-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="bcb57-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="bcb57-120">**initializeData**</span></span>|<span data-ttu-id="bcb57-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="bcb57-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="bcb57-122">傳遞至指定類別之函數的字串。</span><span class="sxs-lookup"><span data-stu-id="bcb57-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bcb57-123">子元素</span><span class="sxs-lookup"><span data-stu-id="bcb57-123">Child Elements</span></span>  
 <span data-ttu-id="bcb57-124">無。</span><span class="sxs-lookup"><span data-stu-id="bcb57-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bcb57-125">父項目</span><span class="sxs-lookup"><span data-stu-id="bcb57-125">Parent Elements</span></span>  
  
|<span data-ttu-id="bcb57-126">項目</span><span class="sxs-lookup"><span data-stu-id="bcb57-126">Element</span></span>|<span data-ttu-id="bcb57-127">描述</span><span class="sxs-lookup"><span data-stu-id="bcb57-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bcb57-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bcb57-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bcb57-129">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="bcb57-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="bcb57-130">任何來源或追蹤元素可以參考的接聽程式集合。</span><span class="sxs-lookup"><span data-stu-id="bcb57-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="bcb57-131">將接聽程式加入至**s**集合。</span><span class="sxs-lookup"><span data-stu-id="bcb57-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcb57-132">備註</span><span class="sxs-lookup"><span data-stu-id="bcb57-132">Remarks</span></span>  
 <span data-ttu-id="bcb57-133">如果`<add>`在專案`<sharedListeners>`的專案中定義了接聽程式, 則該接聽程式的篩選器`<filter>`應該定義于專案子`<add>`系的專案中。</span><span class="sxs-lookup"><span data-stu-id="bcb57-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="bcb57-134">此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="bcb57-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcb57-135">範例</span><span class="sxs-lookup"><span data-stu-id="bcb57-135">Example</span></span>  
 <span data-ttu-id="bcb57-136">下列範例顯示如何使用`<filter>`專案, 將篩選加入`sharedListeners`集合`console`中的追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="bcb57-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bcb57-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcb57-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="bcb57-138">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bcb57-138">Trace and Debug Settings Schema</span></span>](index.md)
