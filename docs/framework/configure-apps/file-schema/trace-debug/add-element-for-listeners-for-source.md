---
title: 適用于 <source> <listeners> 的 <add> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 0818d7ec248b210f215759069b9f69a3e29637f5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699408"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="3a9b7-102">\<source 的 \<listeners > 的 @no__t 0add > 元素 ></span><span class="sxs-lookup"><span data-stu-id="3a9b7-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="3a9b7-103">將接聽項新增至追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="3a9b7-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="3a9b7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="3a9b7-105">&nbsp; @ no__t-1[ **\<system. 診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a9b7-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="3a9b7-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a9b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="3a9b7-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a9b7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="3a9b7-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="3a9b7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="3a9b7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="3a9b7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a9b7-110">語法</span><span class="sxs-lookup"><span data-stu-id="3a9b7-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a9b7-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3a9b7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3a9b7-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a9b7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3a9b7-113">Attributes</span></span>  
  
|<span data-ttu-id="3a9b7-114">屬性</span><span class="sxs-lookup"><span data-stu-id="3a9b7-114">Attribute</span></span>|<span data-ttu-id="3a9b7-115">描述</span><span class="sxs-lookup"><span data-stu-id="3a9b7-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="3a9b7-116">必要的屬性，除非您要參考 `sharedListeners` 集合中的接聽程式，在此情況下，您只需要依名稱參考（請參閱[範例](#example)）。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="3a9b7-117">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-117">Specifies the type of the listener.</span></span> <span data-ttu-id="3a9b7-118">您必須使用符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="3a9b7-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3a9b7-120">傳遞至指定類別之函數的字串。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="3a9b7-121">如果類別沒有接受字串的函式，則會擲回 <xref:System.Configuration.ConfigurationException>。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="3a9b7-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3a9b7-123">指定接聽程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="3a9b7-124">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3a9b7-125">指定追蹤接聽程式的 <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="3a9b7-126">[自訂屬性]</span><span class="sxs-lookup"><span data-stu-id="3a9b7-126">[custom attributes]</span></span>|<span data-ttu-id="3a9b7-127">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="3a9b7-128">指定接聽程式的 <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> 方法所識別之接聽程式特有屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="3a9b7-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 是 @no__t 1 類別獨有的額外屬性範例。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a9b7-130">子元素</span><span class="sxs-lookup"><span data-stu-id="3a9b7-130">Child Elements</span></span>  
  
|<span data-ttu-id="3a9b7-131">元素</span><span class="sxs-lookup"><span data-stu-id="3a9b7-131">Element</span></span>|<span data-ttu-id="3a9b7-132">描述</span><span class="sxs-lookup"><span data-stu-id="3a9b7-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a9b7-133">\<filter></span><span class="sxs-lookup"><span data-stu-id="3a9b7-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="3a9b7-134">將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a9b7-135">父項目</span><span class="sxs-lookup"><span data-stu-id="3a9b7-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3a9b7-136">項目</span><span class="sxs-lookup"><span data-stu-id="3a9b7-136">Element</span></span>|<span data-ttu-id="3a9b7-137">描述</span><span class="sxs-lookup"><span data-stu-id="3a9b7-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3a9b7-138">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3a9b7-139">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="3a9b7-140">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="3a9b7-141">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="3a9b7-142">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a9b7-143">備註</span><span class="sxs-lookup"><span data-stu-id="3a9b7-143">Remarks</span></span>  
 <span data-ttu-id="3a9b7-144">隨附于 .NET Framework 的接聽程式類別衍生自 <xref:System.Diagnostics.TraceListener> 類別。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="3a9b7-145">如果您未指定追蹤接聽項的 `name` 屬性，追蹤接聽項的 <xref:System.Diagnostics.TraceListener.Name%2A> 屬性會預設為空字串（""）。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="3a9b7-146">如果您的應用程式只有一個接聽程式，您可以在不指定名稱的情況下新增它，而且可以藉由指定名稱的空字串來移除它。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="3a9b7-147">不過，如果您的應用程式有多個接聽程式，您應該為每個追蹤接聽項指定唯一的名稱，讓您識別和管理 <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> 集合中的個別追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a9b7-148">加入多個相同類型且具有相同名稱的追蹤接聽程式，只會使該類型和名稱的一個追蹤接聽程式新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="3a9b7-149">不過，您可以透過程式設計的方式，將多個相同的接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="3a9b7-150">@No__t-0 屬性的值取決於您所建立的接聽程式類型。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="3a9b7-151">並非所有的追蹤接聽程式都需要您指定 `initializeData`。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a9b7-152">當您使用 `initializeData` 屬性時，您可能會收到編譯器警告：「' initializeData ' 屬性未宣告」。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="3a9b7-153">之所以會發生這個警告，是因為根據抽象基類驗證設定值 <xref:System.Diagnostics.TraceListener>，這不會辨識 `initializeData` 屬性。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="3a9b7-154">一般來說，您可以忽略具有接受參數之函式的追蹤接聽程式執行的這個警告。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="3a9b7-155">下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其 `initializeData` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="3a9b7-156">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="3a9b7-156">Trace listener class</span></span>|<span data-ttu-id="3a9b7-157">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="3a9b7-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3a9b7-158">@No__t-1 的函式的 `useErrorStream` 值。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="3a9b7-159">將 `initializeData` 屬性設定為 "`true`"，以將追蹤和調試輸出寫入標準錯誤資料流程;將它設定為 "`false`" 以寫入標準輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3a9b7-160">@No__t 0 寫入的檔案名。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3a9b7-161">現有事件記錄檔來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3a9b7-162">@No__t-0 寫入的檔案名。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3a9b7-163">@No__t-0 寫入的檔案名。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3a9b7-164">@No__t-0 寫入的檔案名。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="3a9b7-165">組態檔</span><span class="sxs-lookup"><span data-stu-id="3a9b7-165">Configuration File</span></span>  
 <span data-ttu-id="3a9b7-166">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a9b7-167">範例</span><span class="sxs-lookup"><span data-stu-id="3a9b7-167">Example</span></span>  
 <span data-ttu-id="3a9b7-168">下列範例顯示如何使用 `<add>` 元素，將接聽程式 `console` 和 `textListener` 加入追蹤來源 `TraceSourceApp` 的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="3a9b7-169">@No__t-0 接聽程式會將追蹤輸出寫入至 myListener 檔案。</span><span class="sxs-lookup"><span data-stu-id="3a9b7-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a9b7-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a9b7-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="3a9b7-171">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3a9b7-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3a9b7-172">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="3a9b7-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
