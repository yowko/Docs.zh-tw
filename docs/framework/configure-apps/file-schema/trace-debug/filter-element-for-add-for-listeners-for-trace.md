---
title: <filter>For 之 <add> 的元素 <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153462"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="32732-102">\<filter>For 之 \<add> 的元素 \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="32732-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="32732-103">將篩選加入至追蹤之集合中的接聽 `Listeners` 程式。</span><span class="sxs-lookup"><span data-stu-id="32732-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="32732-104">語法</span><span class="sxs-lookup"><span data-stu-id="32732-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32732-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="32732-105">Attributes and Elements</span></span>  
 <span data-ttu-id="32732-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="32732-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32732-107">屬性</span><span class="sxs-lookup"><span data-stu-id="32732-107">Attributes</span></span>  
  
|<span data-ttu-id="32732-108">屬性</span><span class="sxs-lookup"><span data-stu-id="32732-108">Attribute</span></span>|<span data-ttu-id="32732-109">描述</span><span class="sxs-lookup"><span data-stu-id="32732-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="32732-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="32732-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="32732-111">指定篩選準則的類型，這應該繼承自 <xref:System.Diagnostics.TraceFilter> 類別。</span><span class="sxs-lookup"><span data-stu-id="32732-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="32732-112">您可以使用類型的命名空間限定名稱，它會對應至類型的 <xref:System.Type.FullName%2A> 屬性，或者您可以使用包含元件資訊的完整類型名稱，這會對應至 <xref:System.Type.AssemblyQualifiedName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="32732-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="32732-113">如需完整型別名稱的詳細資訊，請參閱[指定完整的型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="32732-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="32732-114">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="32732-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="32732-115">傳遞給指定之篩選類別之函數的字串。</span><span class="sxs-lookup"><span data-stu-id="32732-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32732-116">子元素</span><span class="sxs-lookup"><span data-stu-id="32732-116">Child Elements</span></span>  
 <span data-ttu-id="32732-117">無。</span><span class="sxs-lookup"><span data-stu-id="32732-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32732-118">父項目</span><span class="sxs-lookup"><span data-stu-id="32732-118">Parent Elements</span></span>  
  
|<span data-ttu-id="32732-119">元素</span><span class="sxs-lookup"><span data-stu-id="32732-119">Element</span></span>|<span data-ttu-id="32732-120">描述</span><span class="sxs-lookup"><span data-stu-id="32732-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="32732-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="32732-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="32732-122">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="32732-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="32732-123">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="32732-123">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="32732-124">包含收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="32732-124">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="32732-125">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="32732-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="32732-126">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="32732-126">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32732-127">備註</span><span class="sxs-lookup"><span data-stu-id="32732-127">Remarks</span></span>  
 <span data-ttu-id="32732-128">`<filter>`元素必須包含在指定接聽程式類型的追蹤接聽項的 `<add>` 元素中，而不只是定義于中的接聽程式名稱 [\<sharedListeners>](sharedlisteners-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="32732-128">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="32732-129">如果接聽程式是在中定義 [\<sharedListeners>](sharedlisteners-element.md) ，則必須在該元素中定義該接聽程式的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="32732-129">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="32732-130">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="32732-130">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32732-131">範例</span><span class="sxs-lookup"><span data-stu-id="32732-131">Example</span></span>  
 <span data-ttu-id="32732-132">下列範例示範如何使用專案 `<filter>` ，將篩選準則加入至集合中的接聽 `console` `Listeners` 程式，並將篩選事件層級指定為 `Error` 。</span><span class="sxs-lookup"><span data-stu-id="32732-132">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32732-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32732-133">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="32732-134">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="32732-134">Trace and Debug Settings Schema</span></span>](index.md)
