---
title: '&lt;清除&gt;元素&lt;接聽程式&gt;如&lt;來源&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8c6ef51dae36e94fa4a4fdc5ad8983380e78bde3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746848"
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="cecef-102">&lt;清除&gt;元素&lt;接聽程式&gt;如&lt;來源&gt;</span><span class="sxs-lookup"><span data-stu-id="cecef-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="cecef-103">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="cecef-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="cecef-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="cecef-104">\<configuration></span></span>  
<span data-ttu-id="cecef-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="cecef-105">\<system.diagnostics></span></span>  
<span data-ttu-id="cecef-106">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="cecef-106">\<sources></span></span>  
<span data-ttu-id="cecef-107">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="cecef-107">\<source></span></span>  
<span data-ttu-id="cecef-108">\<接聽項 ></span><span class="sxs-lookup"><span data-stu-id="cecef-108">\<listeners></span></span>  
<span data-ttu-id="cecef-109">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="cecef-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cecef-110">語法</span><span class="sxs-lookup"><span data-stu-id="cecef-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cecef-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cecef-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cecef-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cecef-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cecef-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cecef-113">Attributes</span></span>  
 <span data-ttu-id="cecef-114">無。</span><span class="sxs-lookup"><span data-stu-id="cecef-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cecef-115">子項目</span><span class="sxs-lookup"><span data-stu-id="cecef-115">Child Elements</span></span>  
 <span data-ttu-id="cecef-116">無。</span><span class="sxs-lookup"><span data-stu-id="cecef-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cecef-117">父項目</span><span class="sxs-lookup"><span data-stu-id="cecef-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cecef-118">項目</span><span class="sxs-lookup"><span data-stu-id="cecef-118">Element</span></span>|<span data-ttu-id="cecef-119">描述</span><span class="sxs-lookup"><span data-stu-id="cecef-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cecef-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="cecef-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cecef-121">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="cecef-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="cecef-122">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="cecef-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="cecef-123">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="cecef-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="cecef-124">指定接聽程式以收集、 儲存和路由傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="cecef-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cecef-125">備註</span><span class="sxs-lookup"><span data-stu-id="cecef-125">Remarks</span></span>  
 <span data-ttu-id="cecef-126">`<clear>`項目會移除所有的接聽程式從`Listeners`集合的追蹤來源，包括<xref:System.Diagnostics.DefaultTraceListener>。</span><span class="sxs-lookup"><span data-stu-id="cecef-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="cecef-127">您可以使用`<clear>`之前使用的項目`<add>`確定沒有其他作用中的接聽程式集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="cecef-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="cecef-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="cecef-128">Configuration File</span></span>  
 <span data-ttu-id="cecef-129">此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="cecef-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cecef-130">範例</span><span class="sxs-lookup"><span data-stu-id="cecef-130">Example</span></span>  
 <span data-ttu-id="cecef-131">下列範例示範如何使用`<clear>`之前使用的項目`<add>`項目將接聽項`console`和`textListener`至`Listeners`追蹤來源的集合`TraceSourceApp`。</span><span class="sxs-lookup"><span data-stu-id="cecef-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cecef-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cecef-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="cecef-133">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="cecef-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="cecef-134">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="cecef-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
