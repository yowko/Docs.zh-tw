---
title: "&lt;新增&gt;元素&lt;sharedListeners&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 490e58d4514667c5ec781dd76644012b0c97509d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a><span data-ttu-id="5085f-102">&lt;新增&gt;元素&lt;sharedListeners&gt;</span><span class="sxs-lookup"><span data-stu-id="5085f-102">&lt;add&gt; Element for &lt;sharedListeners&gt;</span></span>
<span data-ttu-id="5085f-103">將接聽項新增至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="5085f-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="5085f-104">`sharedListeners`是的接聽程式集合的任何[\<來源 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或[\<追蹤 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)可以參考。</span><span class="sxs-lookup"><span data-stu-id="5085f-104">`sharedListeners` is a collection of listeners that any [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) can reference.</span></span>  <span data-ttu-id="5085f-105">根據預設中的接聽程式`sharedListeners`集合未放置在`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="5085f-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="5085f-106">必須將它們加入使用名稱來[\<來源 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或[\<追蹤 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)。</span><span class="sxs-lookup"><span data-stu-id="5085f-106">They must be added by name to the [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span></span> <span data-ttu-id="5085f-107">不可能取得接聽程式`sharedListeners`在執行階段程式碼中的集合。</span><span class="sxs-lookup"><span data-stu-id="5085f-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="5085f-108">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5085f-108">\<configuration></span></span>  
<span data-ttu-id="5085f-109">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="5085f-109">\<system.diagnostics></span></span>  
<span data-ttu-id="5085f-110">\<sharedListeners > 項目</span><span class="sxs-lookup"><span data-stu-id="5085f-110">\<sharedListeners> Element</span></span>  
<span data-ttu-id="5085f-111">\<add></span><span class="sxs-lookup"><span data-stu-id="5085f-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5085f-112">語法</span><span class="sxs-lookup"><span data-stu-id="5085f-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5085f-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5085f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5085f-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5085f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5085f-115">屬性</span><span class="sxs-lookup"><span data-stu-id="5085f-115">Attributes</span></span>  
  
|<span data-ttu-id="5085f-116">屬性</span><span class="sxs-lookup"><span data-stu-id="5085f-116">Attribute</span></span>|<span data-ttu-id="5085f-117">描述</span><span class="sxs-lookup"><span data-stu-id="5085f-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="5085f-118">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5085f-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="5085f-119">指定用來將共用的接聽程式加入接聽程式名稱`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="5085f-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="5085f-120">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5085f-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="5085f-121">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="5085f-121">Specifies the type of the listener.</span></span> <span data-ttu-id="5085f-122">您必須使用符合在指定之需求的字串[指定限定的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="5085f-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="5085f-123">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="5085f-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5085f-124">指定的類別傳遞至建構函式的字串。</span><span class="sxs-lookup"><span data-stu-id="5085f-124">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5085f-125">子元素</span><span class="sxs-lookup"><span data-stu-id="5085f-125">Child Elements</span></span>  
  
|<span data-ttu-id="5085f-126">項目</span><span class="sxs-lookup"><span data-stu-id="5085f-126">Element</span></span>|<span data-ttu-id="5085f-127">描述</span><span class="sxs-lookup"><span data-stu-id="5085f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5085f-128">\<filter></span><span class="sxs-lookup"><span data-stu-id="5085f-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="5085f-129">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="5085f-129">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5085f-130">父項目</span><span class="sxs-lookup"><span data-stu-id="5085f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="5085f-131">項目</span><span class="sxs-lookup"><span data-stu-id="5085f-131">Element</span></span>|<span data-ttu-id="5085f-132">描述</span><span class="sxs-lookup"><span data-stu-id="5085f-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5085f-133">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5085f-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5085f-134">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="5085f-134">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="5085f-135">接聽程式可以參考任何來源或追蹤項目集合。</span><span class="sxs-lookup"><span data-stu-id="5085f-135">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5085f-136">備註</span><span class="sxs-lookup"><span data-stu-id="5085f-136">Remarks</span></span>  
 <span data-ttu-id="5085f-137">.NET Framework 所隨附的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="5085f-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="5085f-138">值`name`屬性用來將共用的接聽程式加入`Listeners`追蹤或追蹤來源的集合。</span><span class="sxs-lookup"><span data-stu-id="5085f-138">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="5085f-139">值`initializeData`屬性取決於您所建立的接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="5085f-139">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="5085f-140">並非所有的追蹤接聽程式會要求您指定`initializeData`。</span><span class="sxs-lookup"><span data-stu-id="5085f-140">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5085f-141">當您使用`initializeData`屬性，可能會遇到的編譯器警告"未宣告 'initializeData' 屬性。 」</span><span class="sxs-lookup"><span data-stu-id="5085f-141">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="5085f-142">發生這個警告是因為組態設定會根據抽象基底類別來驗證<xref:System.Diagnostics.TraceListener>，其無法辨識`initializeData`屬性。</span><span class="sxs-lookup"><span data-stu-id="5085f-142">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="5085f-143">一般而言，您可以忽略此警告具有參數的建構函式的追蹤接聽程式實作。</span><span class="sxs-lookup"><span data-stu-id="5085f-143">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="5085f-144">下表顯示隨附於.NET Framework 追蹤接聽項，並描述的值及其`initializeData`屬性。</span><span class="sxs-lookup"><span data-stu-id="5085f-144">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="5085f-145">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="5085f-145">Trace listener class</span></span>|<span data-ttu-id="5085f-146">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="5085f-146">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="5085f-147">`useErrorStream`值<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="5085f-147">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="5085f-148">設定`initializeData`屬性設定為"`true`"來寫入追蹤和偵錯輸出到標準錯誤資料流中，將它設定為"`false`"寫入標準輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="5085f-148">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="5085f-149">檔案的名稱<xref:System.Diagnostics.DelimitedListTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="5085f-149">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="5085f-150">現有的事件記錄檔來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="5085f-150">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="5085f-151">檔案的名稱，<xref:System.Diagnostics.EventSchemaTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="5085f-151">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="5085f-152">檔案的名稱，<xref:System.Diagnostics.TextWriterTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="5085f-152">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="5085f-153">檔案的名稱，<xref:System.Diagnostics.XmlWriterTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="5085f-153">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="5085f-154">組態檔</span><span class="sxs-lookup"><span data-stu-id="5085f-154">Configuration File</span></span>  
 <span data-ttu-id="5085f-155">此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="5085f-155">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5085f-156">範例</span><span class="sxs-lookup"><span data-stu-id="5085f-156">Example</span></span>  
 <span data-ttu-id="5085f-157">下列範例示範如何使用`<add>`項目加入<xref:System.Diagnostics.TextWriterTraceListener>`textListener`至`sharedListeners`集合。</span><span class="sxs-lookup"><span data-stu-id="5085f-157">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="5085f-158">`textListener`使用名稱來加入`Listeners`追蹤來源的集合`TraceSourceApp`。</span><span class="sxs-lookup"><span data-stu-id="5085f-158">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="5085f-159">`textListener`接聽程式會將追蹤輸出寫入檔案 myListener.log。</span><span class="sxs-lookup"><span data-stu-id="5085f-159">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="5085f-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="5085f-160">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="5085f-161">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5085f-161">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="5085f-162">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="5085f-162">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
