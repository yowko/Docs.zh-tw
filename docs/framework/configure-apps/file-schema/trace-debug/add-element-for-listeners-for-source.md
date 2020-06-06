---
title: <add><listeners>For 的元素<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153681"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="f7bdd-102">\<add>\<listeners>For 的元素\<source></span><span class="sxs-lookup"><span data-stu-id="f7bdd-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="f7bdd-103">將接聽項新增至追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="f7bdd-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7bdd-104">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7bdd-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f7bdd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f7bdd-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7bdd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f7bdd-107">Attributes</span></span>  
  
|<span data-ttu-id="f7bdd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f7bdd-108">Attribute</span></span>|<span data-ttu-id="f7bdd-109">描述</span><span class="sxs-lookup"><span data-stu-id="f7bdd-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="f7bdd-110">必要屬性，除非您要參考集合中的接聽 `sharedListeners` 程式，在此情況下，您只需要依名稱參考它（請參閱[範例](#example)）。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-110">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="f7bdd-111">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-111">Specifies the type of the listener.</span></span> <span data-ttu-id="f7bdd-112">您必須使用符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-112">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="f7bdd-113">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f7bdd-114">傳遞至指定類別之函數的字串。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-114">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="f7bdd-115"><xref:System.Configuration.ConfigurationException>如果類別沒有接受字串的函式，則會擲回。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-115">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="f7bdd-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f7bdd-117">指定接聽程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-117">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="f7bdd-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f7bdd-119">指定 <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> 追蹤接聽程式的屬性值。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-119">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="f7bdd-120">[自訂屬性]</span><span class="sxs-lookup"><span data-stu-id="f7bdd-120">[custom attributes]</span></span>|<span data-ttu-id="f7bdd-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-121">Optional attributes.</span></span><br /><br /> <span data-ttu-id="f7bdd-122">指定接聽程式的方法所識別之接聽程式特有屬性的值 <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-122">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="f7bdd-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>是類別獨有的額外屬性範例 <xref:System.Diagnostics.DelimitedListTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7bdd-124">子元素</span><span class="sxs-lookup"><span data-stu-id="f7bdd-124">Child Elements</span></span>  
  
|<span data-ttu-id="f7bdd-125">元素</span><span class="sxs-lookup"><span data-stu-id="f7bdd-125">Element</span></span>|<span data-ttu-id="f7bdd-126">描述</span><span class="sxs-lookup"><span data-stu-id="f7bdd-126">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="f7bdd-127">將篩選新增至追蹤來源之 `Listeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-127">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7bdd-128">父項目</span><span class="sxs-lookup"><span data-stu-id="f7bdd-128">Parent Elements</span></span>  
  
|<span data-ttu-id="f7bdd-129">元素</span><span class="sxs-lookup"><span data-stu-id="f7bdd-129">Element</span></span>|<span data-ttu-id="f7bdd-130">描述</span><span class="sxs-lookup"><span data-stu-id="f7bdd-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f7bdd-131">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f7bdd-132">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-132">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="f7bdd-133">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-133">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="f7bdd-134">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-134">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="f7bdd-135">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-135">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7bdd-136">備註</span><span class="sxs-lookup"><span data-stu-id="f7bdd-136">Remarks</span></span>  
 <span data-ttu-id="f7bdd-137">隨附于 .NET Framework 的接聽程式類別衍生自 <xref:System.Diagnostics.TraceListener> 類別。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="f7bdd-138">如果您未指定追蹤接聽 `name` 項的屬性，則追蹤接聽 <xref:System.Diagnostics.TraceListener.Name%2A> 項的屬性會預設為空字串（""）。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-138">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="f7bdd-139">如果您的應用程式只有一個接聽程式，您可以在不指定名稱的情況下新增它，而且可以藉由指定名稱的空字串來移除它。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-139">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="f7bdd-140">不過，如果您的應用程式有多個接聽程式，您應該為每個追蹤接聽項指定唯一的名稱，讓您識別和管理集合中的個別追蹤接聽項 <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-140">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7bdd-141">加入多個相同類型且具有相同名稱的追蹤接聽程式，只會導致該類型和名稱的一個追蹤接聽項加入至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-141">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="f7bdd-142">不過，您可以透過程式設計的方式，將多個相同的接聽程式加入至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-142">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="f7bdd-143">屬性的值 `initializeData` 取決於您所建立的接聽程式類型。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="f7bdd-144">並非所有的追蹤接聽程式都需要您指定 `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7bdd-145">當您使用 `initializeData` 屬性時，您可能會收到編譯器警告：「' initializeData ' 屬性未宣告」。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="f7bdd-146">之所以會發生這個警告，是因為系統會針對抽象基類驗證設定值，而該類別 <xref:System.Diagnostics.TraceListener> 無法辨識 `initializeData` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="f7bdd-147">一般來說，您可以忽略具有接受參數之函式的追蹤接聽程式執行的這個警告。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="f7bdd-148">下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其屬性的值 `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="f7bdd-149">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="f7bdd-149">Trace listener class</span></span>|<span data-ttu-id="f7bdd-150">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="f7bdd-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f7bdd-151">此函式的 `useErrorStream` 值 <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="f7bdd-152">將 `initializeData` 屬性設定為 " `true` "，以將追蹤和調試輸出寫入標準錯誤資料流程; 將其設定為 " `false` " 以寫入標準輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f7bdd-153"><xref:System.Diagnostics.DelimitedListTraceListener> 寫入的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f7bdd-154">現有事件記錄檔來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f7bdd-155">寫入的檔案名 <xref:System.Diagnostics.EventSchemaTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f7bdd-156">寫入的檔案名 <xref:System.Diagnostics.TextWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f7bdd-157">寫入的檔案名 <xref:System.Diagnostics.XmlWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="f7bdd-158">組態檔</span><span class="sxs-lookup"><span data-stu-id="f7bdd-158">Configuration File</span></span>  
 <span data-ttu-id="f7bdd-159">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7bdd-160">範例</span><span class="sxs-lookup"><span data-stu-id="f7bdd-160">Example</span></span>  
 <span data-ttu-id="f7bdd-161">下列範例顯示如何使用專案， `<add>` 將接聽 `console` 程式和加入 `textListener` 至 `Listeners` 追蹤來源的集合 `TraceSourceApp` 。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-161">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="f7bdd-162">接聽程式會將 `textListener` 追蹤輸出寫入至 myListener 檔案。</span><span class="sxs-lookup"><span data-stu-id="f7bdd-162">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f7bdd-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7bdd-163">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="f7bdd-164">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f7bdd-164">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f7bdd-165">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="f7bdd-165">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
