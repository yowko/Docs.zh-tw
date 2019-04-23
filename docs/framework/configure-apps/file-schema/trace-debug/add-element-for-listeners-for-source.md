---
title: <add> 項目<listeners>的 <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 4d2952e29b09fcf9f81624317e30caf301a61a51
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165456"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="79d41-102">\<新增 > 項目\<接聽程式 > 針對\<來源 ></span><span class="sxs-lookup"><span data-stu-id="79d41-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="79d41-103">將接聽項新增至追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="79d41-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="79d41-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="79d41-104">\<configuration></span></span>  
<span data-ttu-id="79d41-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="79d41-105">\<system.diagnostics></span></span>  
<span data-ttu-id="79d41-106">\<sources></span><span class="sxs-lookup"><span data-stu-id="79d41-106">\<sources></span></span>  
<span data-ttu-id="79d41-107">\<source></span><span class="sxs-lookup"><span data-stu-id="79d41-107">\<source></span></span>  
<span data-ttu-id="79d41-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="79d41-108">\<listeners></span></span>  
<span data-ttu-id="79d41-109">\<add></span><span class="sxs-lookup"><span data-stu-id="79d41-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79d41-110">語法</span><span class="sxs-lookup"><span data-stu-id="79d41-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79d41-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="79d41-111">Attributes and Elements</span></span>  
 <span data-ttu-id="79d41-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="79d41-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79d41-113">屬性</span><span class="sxs-lookup"><span data-stu-id="79d41-113">Attributes</span></span>  
  
|<span data-ttu-id="79d41-114">屬性</span><span class="sxs-lookup"><span data-stu-id="79d41-114">Attribute</span></span>|<span data-ttu-id="79d41-115">描述</span><span class="sxs-lookup"><span data-stu-id="79d41-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="79d41-116">所需的屬性，除非您在參考中的接聽項`sharedListeners`集合中的情況下，您只需要依名稱參考它 (請參閱 <<c2> [ 範例](#example))。</span><span class="sxs-lookup"><span data-stu-id="79d41-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="79d41-117">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="79d41-117">Specifies the type of the listener.</span></span> <span data-ttu-id="79d41-118">您必須使用符合在指定之需求的字串[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="79d41-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="79d41-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="79d41-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="79d41-120">指定的類別，建構函式傳遞的字串。</span><span class="sxs-lookup"><span data-stu-id="79d41-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="79d41-121">A<xref:System.Configuration.ConfigurationException>如果類別沒有可接受 string 建構函式會擲回。</span><span class="sxs-lookup"><span data-stu-id="79d41-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="79d41-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="79d41-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="79d41-123">指定接聽程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="79d41-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="79d41-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="79d41-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="79d41-125">指定<xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A>追蹤接聽程式的屬性值。</span><span class="sxs-lookup"><span data-stu-id="79d41-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="79d41-126">[自訂屬性]</span><span class="sxs-lookup"><span data-stu-id="79d41-126">[custom attributes]</span></span>|<span data-ttu-id="79d41-127">選擇性的屬性。</span><span class="sxs-lookup"><span data-stu-id="79d41-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="79d41-128">指定的值所識別的接聽程式的特定屬性<xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A>該接聽項的方法。</span><span class="sxs-lookup"><span data-stu-id="79d41-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="79d41-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 是唯一的額外屬性範例<xref:System.Diagnostics.DelimitedListTraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="79d41-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79d41-130">子元素</span><span class="sxs-lookup"><span data-stu-id="79d41-130">Child Elements</span></span>  
  
|<span data-ttu-id="79d41-131">項目</span><span class="sxs-lookup"><span data-stu-id="79d41-131">Element</span></span>|<span data-ttu-id="79d41-132">描述</span><span class="sxs-lookup"><span data-stu-id="79d41-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79d41-133">\<filter></span><span class="sxs-lookup"><span data-stu-id="79d41-133">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="79d41-134">將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="79d41-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79d41-135">父項目</span><span class="sxs-lookup"><span data-stu-id="79d41-135">Parent Elements</span></span>  
  
|<span data-ttu-id="79d41-136">項目</span><span class="sxs-lookup"><span data-stu-id="79d41-136">Element</span></span>|<span data-ttu-id="79d41-137">描述</span><span class="sxs-lookup"><span data-stu-id="79d41-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="79d41-138">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="79d41-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="79d41-139">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="79d41-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="79d41-140">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="79d41-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="79d41-141">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="79d41-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="79d41-142">指定用於收集、 儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="79d41-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79d41-143">備註</span><span class="sxs-lookup"><span data-stu-id="79d41-143">Remarks</span></span>  
 <span data-ttu-id="79d41-144">.NET Framework 隨附的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="79d41-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="79d41-145">如果您未指定`name`屬性的追蹤接聽項<xref:System.Diagnostics.TraceListener.Name%2A>追蹤接聽項的屬性會預設為空字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="79d41-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="79d41-146">如果您的應用程式有只有一個接聽程式，但沒有指定的名稱，可以將它加入，而您可以將它移除藉由指定名稱的空字串。</span><span class="sxs-lookup"><span data-stu-id="79d41-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="79d41-147">不過，如果您的應用程式有一個以上的接聽程式，您應該指定每個追蹤接聽程式，可讓您識別及管理個別的追蹤接聽項中的唯一名稱<xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>集合。</span><span class="sxs-lookup"><span data-stu-id="79d41-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79d41-148">加入一個以上的追蹤接聽程式相同的型別，而且具有相同名稱中只能有一個追蹤接聽程式的該類型的結果，並將命名要新增至`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="79d41-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="79d41-149">不過，您可以程式設計方式加入至多個相同的接聽程式`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="79d41-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="79d41-150">值`initializeData`屬性取決於您所建立的接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="79d41-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="79d41-151">並非所有的追蹤接聽程式會要求您指定`initializeData`。</span><span class="sxs-lookup"><span data-stu-id="79d41-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79d41-152">當您使用`initializeData`屬性，您可能會收到編譯器警告"未宣告 'initializeData' 屬性。 」</span><span class="sxs-lookup"><span data-stu-id="79d41-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="79d41-153">因為對抽象的基底類別會驗證組態設定，就會發生此警告<xref:System.Diagnostics.TraceListener>，其無法辨識`initializeData`屬性。</span><span class="sxs-lookup"><span data-stu-id="79d41-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="79d41-154">一般而言，您可以忽略此警告具有參數的建構函式的追蹤接聽程式實作。</span><span class="sxs-lookup"><span data-stu-id="79d41-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="79d41-155">下表顯示隨附於.NET Framework 追蹤接聽項，並描述的值及其`initializeData`屬性。</span><span class="sxs-lookup"><span data-stu-id="79d41-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="79d41-156">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="79d41-156">Trace listener class</span></span>|<span data-ttu-id="79d41-157">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="79d41-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="79d41-158">`useErrorStream`值<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="79d41-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="79d41-159">設定`initializeData`屬性設定為"`true`"來寫入追蹤和偵錯輸出至標準錯誤資料流中，將它設定為"`false`」 要寫入標準輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="79d41-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="79d41-160">檔案的名稱<xref:System.Diagnostics.DelimitedListTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="79d41-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="79d41-161">現有事件記錄檔來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="79d41-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="79d41-162">檔案的名稱，<xref:System.Diagnostics.EventSchemaTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="79d41-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="79d41-163">檔案的名稱，<xref:System.Diagnostics.TextWriterTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="79d41-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="79d41-164">檔案的名稱，<xref:System.Diagnostics.XmlWriterTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="79d41-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="79d41-165">組態檔</span><span class="sxs-lookup"><span data-stu-id="79d41-165">Configuration File</span></span>  
 <span data-ttu-id="79d41-166">這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="79d41-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79d41-167">範例</span><span class="sxs-lookup"><span data-stu-id="79d41-167">Example</span></span>  
 <span data-ttu-id="79d41-168">下列範例示範如何使用`<add>`加入接聽程式的項目`console`並`textListener`要`Listeners`追蹤來源的集合`TraceSourceApp`。</span><span class="sxs-lookup"><span data-stu-id="79d41-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="79d41-169">`textListener`接聽程式會將追蹤輸出寫入檔案 myListener.log。</span><span class="sxs-lookup"><span data-stu-id="79d41-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79d41-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79d41-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="79d41-171">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="79d41-171">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="79d41-172">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="79d41-172">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
