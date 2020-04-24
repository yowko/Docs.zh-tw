---
title: <sharedListeners> 的 <add> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153603"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="67dda-102">\<新增 s> 的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="67dda-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="67dda-103">將接聽項新增至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="67dda-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="67dda-104">`sharedListeners`這是任何[ \<來源>](source-element.md)或[ \<追蹤>](trace-element.md)可以參考的接聽項集合。</span><span class="sxs-lookup"><span data-stu-id="67dda-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="67dda-105">根據預設，集合中的`sharedListeners`接聽項不會放置在`Listeners`集合中。</span><span class="sxs-lookup"><span data-stu-id="67dda-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="67dda-106">它們必須依名稱加入至[ \<來源>](source-element.md)或[ \<追蹤>](trace-element.md)。</span><span class="sxs-lookup"><span data-stu-id="67dda-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="67dda-107">您無法在執行時間的程式碼中取得`sharedListeners`集合中的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="67dda-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

<span data-ttu-id="67dda-108">[**\<設定>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="67dda-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="67dda-109">&nbsp;&nbsp;[**\<系統診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="67dda-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="67dda-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<s>**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="67dda-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="67dda-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<新增>**</span><span class="sxs-lookup"><span data-stu-id="67dda-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="67dda-112">語法</span><span class="sxs-lookup"><span data-stu-id="67dda-112">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67dda-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="67dda-113">Attributes and Elements</span></span>  
 <span data-ttu-id="67dda-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="67dda-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67dda-115">屬性</span><span class="sxs-lookup"><span data-stu-id="67dda-115">Attributes</span></span>  
  
|<span data-ttu-id="67dda-116">屬性</span><span class="sxs-lookup"><span data-stu-id="67dda-116">Attribute</span></span>|<span data-ttu-id="67dda-117">說明</span><span class="sxs-lookup"><span data-stu-id="67dda-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="67dda-118">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="67dda-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="67dda-119">指定用來將共用接聽項加入至`Listeners`集合的接聽程式名稱。</span><span class="sxs-lookup"><span data-stu-id="67dda-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="67dda-120">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="67dda-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="67dda-121">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="67dda-121">Specifies the type of the listener.</span></span> <span data-ttu-id="67dda-122">您必須使用符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。</span><span class="sxs-lookup"><span data-stu-id="67dda-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="67dda-123">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="67dda-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="67dda-124">傳遞至指定類別之函數的字串。</span><span class="sxs-lookup"><span data-stu-id="67dda-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="67dda-125">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="67dda-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="67dda-126">一或多個<xref:System.Diagnostics.TraceOptions>列舉成員的字串表示，表示要寫入追蹤輸出的資料。</span><span class="sxs-lookup"><span data-stu-id="67dda-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="67dda-127">以逗號分隔多個專案。</span><span class="sxs-lookup"><span data-stu-id="67dda-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="67dda-128">預設值為 "None"。</span><span class="sxs-lookup"><span data-stu-id="67dda-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="67dda-129">子元素</span><span class="sxs-lookup"><span data-stu-id="67dda-129">Child Elements</span></span>  
  
|<span data-ttu-id="67dda-130">元素</span><span class="sxs-lookup"><span data-stu-id="67dda-130">Element</span></span>|<span data-ttu-id="67dda-131">描述</span><span class="sxs-lookup"><span data-stu-id="67dda-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67dda-132">\<篩選></span><span class="sxs-lookup"><span data-stu-id="67dda-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="67dda-133">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="67dda-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67dda-134">父項目</span><span class="sxs-lookup"><span data-stu-id="67dda-134">Parent Elements</span></span>  
  
|<span data-ttu-id="67dda-135">元素</span><span class="sxs-lookup"><span data-stu-id="67dda-135">Element</span></span>|<span data-ttu-id="67dda-136">描述</span><span class="sxs-lookup"><span data-stu-id="67dda-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="67dda-137">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="67dda-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="67dda-138">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="67dda-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="67dda-139">任何來源或追蹤元素可以參考的接聽程式集合。</span><span class="sxs-lookup"><span data-stu-id="67dda-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67dda-140">備註</span><span class="sxs-lookup"><span data-stu-id="67dda-140">Remarks</span></span>  
 <span data-ttu-id="67dda-141">隨附于 .NET Framework 的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="67dda-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="67dda-142">`name`屬性的值是用來將共用接聽程式加入至追蹤或`Listeners`追蹤來源的集合。</span><span class="sxs-lookup"><span data-stu-id="67dda-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="67dda-143">`initializeData`屬性的值取決於您所建立的接聽程式類型。</span><span class="sxs-lookup"><span data-stu-id="67dda-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="67dda-144">並非所有的追蹤接聽程式都需要`initializeData`您指定。</span><span class="sxs-lookup"><span data-stu-id="67dda-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67dda-145">當您使用`initializeData`屬性時，您可能會收到編譯器警告：「' initializeData ' 屬性未宣告」。</span><span class="sxs-lookup"><span data-stu-id="67dda-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="67dda-146">之所以會發生這個警告，是因為系統會針對抽象基類驗證<xref:System.Diagnostics.TraceListener>設定值，而該類別`initializeData`無法辨識屬性。</span><span class="sxs-lookup"><span data-stu-id="67dda-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="67dda-147">一般來說，您可以忽略具有接受參數之函式的追蹤接聽程式執行的這個警告。</span><span class="sxs-lookup"><span data-stu-id="67dda-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="67dda-148">下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其`initializeData`屬性的值。</span><span class="sxs-lookup"><span data-stu-id="67dda-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="67dda-149">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="67dda-149">Trace listener class</span></span>|<span data-ttu-id="67dda-150">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="67dda-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="67dda-151">此`useErrorStream` <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>函式的值。</span><span class="sxs-lookup"><span data-stu-id="67dda-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="67dda-152">將`initializeData`屬性設定為 "`true`"，以將追蹤和調試輸出寫入標準錯誤資料流程;將它設定為`false`"" 以寫入標準輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="67dda-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="67dda-153"><xref:System.Diagnostics.DelimitedListTraceListener> 寫入的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="67dda-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="67dda-154">現有事件記錄檔來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="67dda-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="67dda-155">寫入的<xref:System.Diagnostics.EventSchemaTraceListener>檔案名。</span><span class="sxs-lookup"><span data-stu-id="67dda-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="67dda-156">寫入的<xref:System.Diagnostics.TextWriterTraceListener>檔案名。</span><span class="sxs-lookup"><span data-stu-id="67dda-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="67dda-157">寫入的<xref:System.Diagnostics.XmlWriterTraceListener>檔案名。</span><span class="sxs-lookup"><span data-stu-id="67dda-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="67dda-158">組態檔</span><span class="sxs-lookup"><span data-stu-id="67dda-158">Configuration File</span></span>  
 <span data-ttu-id="67dda-159">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="67dda-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67dda-160">範例</span><span class="sxs-lookup"><span data-stu-id="67dda-160">Example</span></span>  
 <span data-ttu-id="67dda-161">`<add>`下列範例顯示如何使用專案將加入<xref:System.Diagnostics.TextWriterTraceListener> `textListener`至`sharedListeners`集合。</span><span class="sxs-lookup"><span data-stu-id="67dda-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="67dda-162">`textListener`會依名稱加入至追蹤`Listeners`來源`TraceSourceApp`的集合。</span><span class="sxs-lookup"><span data-stu-id="67dda-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="67dda-163">`textListener`接聽程式會將追蹤輸出寫入至 myListener 檔案。</span><span class="sxs-lookup"><span data-stu-id="67dda-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67dda-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67dda-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="67dda-165">追蹤和 Debug 設定架構</span><span class="sxs-lookup"><span data-stu-id="67dda-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="67dda-166">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="67dda-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
