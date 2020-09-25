---
title: <filter><add>的元素 <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 2b83fd10da506202427aaeee454411822ff1ae5b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201677"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="1dcd9-102">\<filter>\<add>的元素 \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="1dcd9-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>

<span data-ttu-id="1dcd9-103">將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="1dcd9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1dcd9-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dcd9-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1dcd9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1dcd9-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dcd9-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1dcd9-107">Attributes</span></span>  
  
|<span data-ttu-id="1dcd9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1dcd9-108">Attribute</span></span>|<span data-ttu-id="1dcd9-109">描述</span><span class="sxs-lookup"><span data-stu-id="1dcd9-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="1dcd9-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="1dcd9-111">指定篩選準則的型別，這應該繼承自 <xref:System.Diagnostics.TraceFilter> 類別。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="1dcd9-112">您可以使用類型的命名空間限定名稱（對應至類型的 <xref:System.Type.FullName%2A> 屬性），也可以使用完整的類型名稱，包括與屬性對應的元件資訊 <xref:System.Type.AssemblyQualifiedName%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="1dcd9-113">如需完整型別名稱的詳細資訊，請參閱 [指定完整的類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="1dcd9-114">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1dcd9-115">傳遞給指定之篩選類別之函式的字串。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1dcd9-116">子元素</span><span class="sxs-lookup"><span data-stu-id="1dcd9-116">Child Elements</span></span>  

 <span data-ttu-id="1dcd9-117">無。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1dcd9-118">父項目</span><span class="sxs-lookup"><span data-stu-id="1dcd9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1dcd9-119">項目</span><span class="sxs-lookup"><span data-stu-id="1dcd9-119">Element</span></span>|<span data-ttu-id="1dcd9-120">描述</span><span class="sxs-lookup"><span data-stu-id="1dcd9-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1dcd9-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1dcd9-122">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="1dcd9-123">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-123">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="1dcd9-124">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-124">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="1dcd9-125">包含收集、儲存和路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-125">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="1dcd9-126">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-126">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="1dcd9-127">將接聽項新增至追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-127">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dcd9-128">備註</span><span class="sxs-lookup"><span data-stu-id="1dcd9-128">Remarks</span></span>  

 <span data-ttu-id="1dcd9-129">專案 `<filter>` 必須包含在追蹤來源接聽程式的 `<add>` 元素中，以指定接聽程式的類型，而不只是在中定義之接聽程式的名稱 [\<sharedListeners>](sharedlisteners-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-129">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="1dcd9-130">如果接聽程式是在中定義 [\<sharedListeners>](sharedlisteners-element.md) ，則必須在該元素中定義該接聽程式的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-130">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="1dcd9-131">此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dcd9-132">範例</span><span class="sxs-lookup"><span data-stu-id="1dcd9-132">Example</span></span>  

 <span data-ttu-id="1dcd9-133">下列範例示範如何使用專案 `<filter>` ，將篩選準則加入至 `console` 追蹤來源集合中的接聽 `Listeners` 程式，並將 `myTraceSource` 篩選事件層級指定為 `Error` 。</span><span class="sxs-lookup"><span data-stu-id="1dcd9-133">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1dcd9-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dcd9-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="1dcd9-135">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1dcd9-135">Trace and Debug Settings Schema</span></span>](index.md)
