---
title: "&lt;新增&gt;元素&lt;接聽程式&gt;如&lt;來源&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 86177010d8ed70302b51ec9c416a3295009e7394
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="b0abc-102">&lt;新增&gt;元素&lt;接聽程式&gt;如&lt;來源&gt;</span><span class="sxs-lookup"><span data-stu-id="b0abc-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="b0abc-103">將接聽項新增至追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="b0abc-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="b0abc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b0abc-104">\<configuration></span></span>  
<span data-ttu-id="b0abc-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="b0abc-105">\<system.diagnostics></span></span>  
<span data-ttu-id="b0abc-106">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="b0abc-106">\<sources></span></span>  
<span data-ttu-id="b0abc-107">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="b0abc-107">\<source></span></span>  
<span data-ttu-id="b0abc-108">\<接聽項 ></span><span class="sxs-lookup"><span data-stu-id="b0abc-108">\<listeners></span></span>  
<span data-ttu-id="b0abc-109">\<add></span><span class="sxs-lookup"><span data-stu-id="b0abc-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0abc-110">語法</span><span class="sxs-lookup"><span data-stu-id="b0abc-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0abc-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b0abc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b0abc-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b0abc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0abc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b0abc-113">Attributes</span></span>  
  
|<span data-ttu-id="b0abc-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b0abc-114">Attribute</span></span>|<span data-ttu-id="b0abc-115">描述</span><span class="sxs-lookup"><span data-stu-id="b0abc-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="b0abc-116">必要屬性，除非您正在參考中的接聽程式`sharedListeners`集合中的情況下，您只需要依名稱參考它 (請參閱[範例](#example))。</span><span class="sxs-lookup"><span data-stu-id="b0abc-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="b0abc-117">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="b0abc-117">Specifies the type of the listener.</span></span> <span data-ttu-id="b0abc-118">您必須使用符合在指定之需求的字串[指定限定的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="b0abc-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="b0abc-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="b0abc-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b0abc-120">指定的類別傳遞至建構函式的字串。</span><span class="sxs-lookup"><span data-stu-id="b0abc-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="b0abc-121">A<xref:System.Configuration.ConfigurationException>如果類別沒有可接受 string 建構函式會擲回。</span><span class="sxs-lookup"><span data-stu-id="b0abc-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="b0abc-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="b0abc-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b0abc-123">指定的接聽程式名稱。</span><span class="sxs-lookup"><span data-stu-id="b0abc-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="b0abc-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="b0abc-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b0abc-125">指定<xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A>追蹤接聽程式的屬性值。</span><span class="sxs-lookup"><span data-stu-id="b0abc-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="b0abc-126">[自訂屬性]</span><span class="sxs-lookup"><span data-stu-id="b0abc-126">[custom attributes]</span></span>|<span data-ttu-id="b0abc-127">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="b0abc-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="b0abc-128">指定的值所識別的接聽程式的特定屬性<xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A>該接聽項的方法。</span><span class="sxs-lookup"><span data-stu-id="b0abc-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="b0abc-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>是唯一的額外屬性範例<xref:System.Diagnostics.DelimitedListTraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="b0abc-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0abc-130">子元素</span><span class="sxs-lookup"><span data-stu-id="b0abc-130">Child Elements</span></span>  
  
|<span data-ttu-id="b0abc-131">項目</span><span class="sxs-lookup"><span data-stu-id="b0abc-131">Element</span></span>|<span data-ttu-id="b0abc-132">描述</span><span class="sxs-lookup"><span data-stu-id="b0abc-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0abc-133">\<filter></span><span class="sxs-lookup"><span data-stu-id="b0abc-133">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="b0abc-134">將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="b0abc-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0abc-135">父項目</span><span class="sxs-lookup"><span data-stu-id="b0abc-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b0abc-136">項目</span><span class="sxs-lookup"><span data-stu-id="b0abc-136">Element</span></span>|<span data-ttu-id="b0abc-137">描述</span><span class="sxs-lookup"><span data-stu-id="b0abc-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b0abc-138">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="b0abc-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b0abc-139">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="b0abc-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="b0abc-140">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b0abc-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="b0abc-141">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b0abc-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="b0abc-142">指定接聽程式以收集、 儲存和路由傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="b0abc-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0abc-143">備註</span><span class="sxs-lookup"><span data-stu-id="b0abc-143">Remarks</span></span>  
 <span data-ttu-id="b0abc-144">.NET Framework 所隨附的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="b0abc-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="b0abc-145">如果您未指定`name`屬性的追蹤接聽項，<xref:System.Diagnostics.TraceListener.Name%2A>追蹤接聽項的屬性會預設為空字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="b0abc-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="b0abc-146">如果您的應用程式只能有一個接聽程式，而不指定名稱，可以將它加入，您可以藉由指定名稱為空字串中移除。</span><span class="sxs-lookup"><span data-stu-id="b0abc-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="b0abc-147">不過，如果您的應用程式有多個接聽程式，您應該指定每個追蹤接聽程式，可讓您識別及管理中的個別追蹤接聽項的唯一名稱<xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>集合。</span><span class="sxs-lookup"><span data-stu-id="b0abc-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0abc-148">加入一個以上的追蹤接聽程式相同的型別且具有相同名稱只能有一個追蹤接聽項中的該類型的結果和名稱新增至`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="b0abc-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="b0abc-149">不過，您可以程式設計方式加入至多個相同的接聽程式`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="b0abc-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="b0abc-150">值`initializeData`屬性取決於您所建立的接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="b0abc-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="b0abc-151">並非所有的追蹤接聽程式會要求您指定`initializeData`。</span><span class="sxs-lookup"><span data-stu-id="b0abc-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0abc-152">當您使用`initializeData`屬性，可能會遇到的編譯器警告"未宣告 'initializeData' 屬性。 」</span><span class="sxs-lookup"><span data-stu-id="b0abc-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="b0abc-153">發生這個警告是因為組態設定會根據抽象基底類別來驗證<xref:System.Diagnostics.TraceListener>，其無法辨識`initializeData`屬性。</span><span class="sxs-lookup"><span data-stu-id="b0abc-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="b0abc-154">一般而言，您可以忽略此警告具有參數的建構函式的追蹤接聽程式實作。</span><span class="sxs-lookup"><span data-stu-id="b0abc-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="b0abc-155">下表顯示隨附於.NET Framework 追蹤接聽項，並描述的值及其`initializeData`屬性。</span><span class="sxs-lookup"><span data-stu-id="b0abc-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="b0abc-156">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="b0abc-156">Trace listener class</span></span>|<span data-ttu-id="b0abc-157">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="b0abc-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b0abc-158">`useErrorStream`值<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="b0abc-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="b0abc-159">設定`initializeData`屬性設定為"`true`"來寫入追蹤和偵錯輸出到標準錯誤資料流中，將它設定為"`false`"寫入標準輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="b0abc-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b0abc-160">檔案的名稱<xref:System.Diagnostics.DelimitedListTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="b0abc-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b0abc-161">現有的事件記錄檔來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0abc-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b0abc-162">檔案的名稱，<xref:System.Diagnostics.EventSchemaTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="b0abc-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b0abc-163">檔案的名稱，<xref:System.Diagnostics.TextWriterTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="b0abc-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b0abc-164">檔案的名稱，<xref:System.Diagnostics.XmlWriterTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="b0abc-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="b0abc-165">組態檔</span><span class="sxs-lookup"><span data-stu-id="b0abc-165">Configuration File</span></span>  
 <span data-ttu-id="b0abc-166">此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="b0abc-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0abc-167">範例</span><span class="sxs-lookup"><span data-stu-id="b0abc-167">Example</span></span>  
 <span data-ttu-id="b0abc-168">下列範例示範如何使用`<add>`項目將接聽項`console`和`textListener`至`Listeners`追蹤來源的集合`TraceSourceApp`。</span><span class="sxs-lookup"><span data-stu-id="b0abc-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="b0abc-169">`textListener`接聽程式會將追蹤輸出寫入檔案 myListener.log。</span><span class="sxs-lookup"><span data-stu-id="b0abc-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0abc-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0abc-170">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="b0abc-171">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b0abc-171">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="b0abc-172">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="b0abc-172">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
