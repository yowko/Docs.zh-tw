---
title: 適用于 <sharedListeners> <add> 的 <filter> 元素
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
ms.openlocfilehash: 4e92f80e9f6069b5fa70501e13a55d5a6fe95e7a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697317"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="89b2a-102">\<sharedListeners 的 \<add > 的 @no__t 0filter > 元素 ></span><span class="sxs-lookup"><span data-stu-id="89b2a-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="89b2a-103">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="89b2a-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
[<span data-ttu-id="89b2a-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="89b2a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="89b2a-105">&nbsp; @ no__t-1[ **\<system. 診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="89b2a-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="89b2a-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sharedListeners >** ](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="89b2a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>  
<span data-ttu-id="89b2a-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<add >** ](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="89b2a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>  
<span data-ttu-id="89b2a-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<filter >**</span><span class="sxs-lookup"><span data-stu-id="89b2a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89b2a-109">語法</span><span class="sxs-lookup"><span data-stu-id="89b2a-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89b2a-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="89b2a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="89b2a-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="89b2a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89b2a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="89b2a-112">Attributes</span></span>  
  
|<span data-ttu-id="89b2a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="89b2a-113">Attribute</span></span>|<span data-ttu-id="89b2a-114">描述</span><span class="sxs-lookup"><span data-stu-id="89b2a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89b2a-115">**type**</span><span class="sxs-lookup"><span data-stu-id="89b2a-115">**type**</span></span>|<span data-ttu-id="89b2a-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="89b2a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="89b2a-117">指定篩選準則的類型。</span><span class="sxs-lookup"><span data-stu-id="89b2a-117">Specifies the type of the filter.</span></span> <span data-ttu-id="89b2a-118">您只能使用類型的完整名稱（格式為 <xref:System.Type.FullName%2A?displayProperty=nameWithType> 屬性），也可以使用包含元件資訊的完整型別名稱（格式為 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> 屬性）。</span><span class="sxs-lookup"><span data-stu-id="89b2a-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="89b2a-119">如需建立完整型別名稱的相關資訊，請參閱[指定完整的型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="89b2a-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="89b2a-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="89b2a-120">**initializeData**</span></span>|<span data-ttu-id="89b2a-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="89b2a-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="89b2a-122">傳遞至指定類別之函數的字串。</span><span class="sxs-lookup"><span data-stu-id="89b2a-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89b2a-123">子元素</span><span class="sxs-lookup"><span data-stu-id="89b2a-123">Child Elements</span></span>  
 <span data-ttu-id="89b2a-124">無。</span><span class="sxs-lookup"><span data-stu-id="89b2a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89b2a-125">父項目</span><span class="sxs-lookup"><span data-stu-id="89b2a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="89b2a-126">項目</span><span class="sxs-lookup"><span data-stu-id="89b2a-126">Element</span></span>|<span data-ttu-id="89b2a-127">描述</span><span class="sxs-lookup"><span data-stu-id="89b2a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="89b2a-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="89b2a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="89b2a-129">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="89b2a-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="89b2a-130">任何來源或追蹤元素可以參考的接聽程式集合。</span><span class="sxs-lookup"><span data-stu-id="89b2a-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="89b2a-131">將接聽程式加入至**s**集合。</span><span class="sxs-lookup"><span data-stu-id="89b2a-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89b2a-132">備註</span><span class="sxs-lookup"><span data-stu-id="89b2a-132">Remarks</span></span>  
 <span data-ttu-id="89b2a-133">如果接聽程式是在 `<sharedListeners>` 元素的 `<add>` 元素中定義，則該接聽程式的篩選器應該定義于屬於 `<add>` 元素子系的 @no__t 2 元素中。</span><span class="sxs-lookup"><span data-stu-id="89b2a-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="89b2a-134">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="89b2a-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89b2a-135">範例</span><span class="sxs-lookup"><span data-stu-id="89b2a-135">Example</span></span>  
 <span data-ttu-id="89b2a-136">下列範例示範如何使用 `<filter>` 元素，將篩選準則加入至 @no__t 2 集合中的追蹤接聽項 `console`。</span><span class="sxs-lookup"><span data-stu-id="89b2a-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89b2a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89b2a-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="89b2a-138">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="89b2a-138">Trace and Debug Settings Schema</span></span>](index.md)
