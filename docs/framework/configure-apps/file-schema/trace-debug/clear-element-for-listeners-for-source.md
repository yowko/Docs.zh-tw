---
title: '&lt;清除&gt;項目&lt;接聽程式&gt;如&lt;來源&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 362e1d7a4ac4c39309aa86561683df1d239f2ab1
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083858"
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="8cfb7-102">&lt;清除&gt;項目&lt;接聽程式&gt;如&lt;來源&gt;</span><span class="sxs-lookup"><span data-stu-id="8cfb7-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="8cfb7-103">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="8cfb7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8cfb7-104">\<configuration></span></span>  
<span data-ttu-id="8cfb7-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="8cfb7-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8cfb7-106">\<sources></span><span class="sxs-lookup"><span data-stu-id="8cfb7-106">\<sources></span></span>  
<span data-ttu-id="8cfb7-107">\<source></span><span class="sxs-lookup"><span data-stu-id="8cfb7-107">\<source></span></span>  
<span data-ttu-id="8cfb7-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="8cfb7-108">\<listeners></span></span>  
<span data-ttu-id="8cfb7-109">\<clear></span><span class="sxs-lookup"><span data-stu-id="8cfb7-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cfb7-110">語法</span><span class="sxs-lookup"><span data-stu-id="8cfb7-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cfb7-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8cfb7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8cfb7-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cfb7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8cfb7-113">Attributes</span></span>  
 <span data-ttu-id="8cfb7-114">無。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8cfb7-115">子元素</span><span class="sxs-lookup"><span data-stu-id="8cfb7-115">Child Elements</span></span>  
 <span data-ttu-id="8cfb7-116">無。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cfb7-117">父項目</span><span class="sxs-lookup"><span data-stu-id="8cfb7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8cfb7-118">項目</span><span class="sxs-lookup"><span data-stu-id="8cfb7-118">Element</span></span>|<span data-ttu-id="8cfb7-119">描述</span><span class="sxs-lookup"><span data-stu-id="8cfb7-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8cfb7-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8cfb7-121">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="8cfb7-122">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="8cfb7-123">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8cfb7-124">指定用於收集、 儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cfb7-125">備註</span><span class="sxs-lookup"><span data-stu-id="8cfb7-125">Remarks</span></span>  
 <span data-ttu-id="8cfb7-126">`<clear>`項目會移除所有的接聽程式，從`Listeners`集合的追蹤來源，包括<xref:System.Diagnostics.DefaultTraceListener>。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="8cfb7-127">您可以使用`<clear>`項目之前使用`<add>`確有沒有其他作用中接聽程式集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="8cfb7-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="8cfb7-128">Configuration File</span></span>  
 <span data-ttu-id="8cfb7-129">這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cfb7-130">範例</span><span class="sxs-lookup"><span data-stu-id="8cfb7-130">Example</span></span>  
 <span data-ttu-id="8cfb7-131">下列範例示範如何使用`<clear>`項目之前使用`<add>`加入接聽程式的項目`console`並`textListener`來`Listeners`追蹤來源的集合`TraceSourceApp`。</span><span class="sxs-lookup"><span data-stu-id="8cfb7-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="8cfb7-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cfb7-132">See also</span></span>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="8cfb7-133">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8cfb7-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="8cfb7-134">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="8cfb7-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
