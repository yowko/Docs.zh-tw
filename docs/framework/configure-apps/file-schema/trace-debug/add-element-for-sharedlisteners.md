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
ms.openlocfilehash: e7934ed5e71005cfd28271298ff6ce1eb8829a0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701368"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="1dd4c-102">\<新增 > 項目\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="1dd4c-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="1dd4c-103">將接聽項新增至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="1dd4c-104">`sharedListeners` 是的接聽程式集合的任何[\<來源 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或是[\<追蹤 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)可以參考。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-104">`sharedListeners` is a collection of listeners that any [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) can reference.</span></span>  <span data-ttu-id="1dd4c-105">根據預設，在 接聽程式`sharedListeners`集合不會放在`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="1dd4c-106">它們必須依名稱加入[\<來源 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或是[\<追蹤 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-106">They must be added by name to the [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span></span> <span data-ttu-id="1dd4c-107">不可能取得接聽程式`sharedListeners`在執行階段程式碼中的集合。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="1dd4c-108">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1dd4c-108">\<configuration></span></span>  
<span data-ttu-id="1dd4c-109">&nbsp;&nbsp;\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="1dd4c-109">&nbsp;&nbsp;\<system.diagnostics></span></span>  
<span data-ttu-id="1dd4c-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners > 項目</span><span class="sxs-lookup"><span data-stu-id="1dd4c-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners> Element</span></span>  
<span data-ttu-id="1dd4c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span><span class="sxs-lookup"><span data-stu-id="1dd4c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd4c-112">語法</span><span class="sxs-lookup"><span data-stu-id="1dd4c-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dd4c-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1dd4c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1dd4c-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dd4c-115">屬性</span><span class="sxs-lookup"><span data-stu-id="1dd4c-115">Attributes</span></span>  
  
|<span data-ttu-id="1dd4c-116">屬性</span><span class="sxs-lookup"><span data-stu-id="1dd4c-116">Attribute</span></span>|<span data-ttu-id="1dd4c-117">描述</span><span class="sxs-lookup"><span data-stu-id="1dd4c-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="1dd4c-118">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="1dd4c-119">指定用來新增共用的接聽程式接聽程式名稱`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="1dd4c-120">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="1dd4c-121">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-121">Specifies the type of the listener.</span></span> <span data-ttu-id="1dd4c-122">您必須使用符合在指定之需求的字串[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="1dd4c-123">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1dd4c-124">指定的類別，建構函式傳遞的字串。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="1dd4c-125">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="1dd4c-126">一或多個的字串表示<xref:System.Diagnostics.TraceOptions>列舉成員，表示要寫入至追蹤輸出的資料。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="1dd4c-127">以逗號分隔多個項目。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="1dd4c-128">預設值為"None"。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1dd4c-129">子元素</span><span class="sxs-lookup"><span data-stu-id="1dd4c-129">Child Elements</span></span>  
  
|<span data-ttu-id="1dd4c-130">項目</span><span class="sxs-lookup"><span data-stu-id="1dd4c-130">Element</span></span>|<span data-ttu-id="1dd4c-131">描述</span><span class="sxs-lookup"><span data-stu-id="1dd4c-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1dd4c-132">\<filter></span><span class="sxs-lookup"><span data-stu-id="1dd4c-132">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="1dd4c-133">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1dd4c-134">父項目</span><span class="sxs-lookup"><span data-stu-id="1dd4c-134">Parent Elements</span></span>  
  
|<span data-ttu-id="1dd4c-135">項目</span><span class="sxs-lookup"><span data-stu-id="1dd4c-135">Element</span></span>|<span data-ttu-id="1dd4c-136">描述</span><span class="sxs-lookup"><span data-stu-id="1dd4c-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1dd4c-137">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1dd4c-138">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="1dd4c-139">任何來源或追蹤項目可以參考的接聽程式的集合。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dd4c-140">備註</span><span class="sxs-lookup"><span data-stu-id="1dd4c-140">Remarks</span></span>  
 <span data-ttu-id="1dd4c-141">.NET Framework 隨附的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="1dd4c-142">值`name`屬性用來新增共用的接聽程式`Listeners`追蹤或追蹤來源的集合。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="1dd4c-143">值`initializeData`屬性取決於您所建立的接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="1dd4c-144">並非所有的追蹤接聽程式會要求您指定`initializeData`。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1dd4c-145">當您使用`initializeData`屬性，您可能會收到編譯器警告"未宣告 'initializeData' 屬性。 」</span><span class="sxs-lookup"><span data-stu-id="1dd4c-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="1dd4c-146">因為對抽象的基底類別會驗證組態設定，就會發生此警告<xref:System.Diagnostics.TraceListener>，其無法辨識`initializeData`屬性。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="1dd4c-147">一般而言，您可以忽略此警告具有參數的建構函式的追蹤接聽程式實作。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="1dd4c-148">下表顯示隨附於.NET Framework 追蹤接聽項，並描述的值及其`initializeData`屬性。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="1dd4c-149">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="1dd4c-149">Trace listener class</span></span>|<span data-ttu-id="1dd4c-150">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="1dd4c-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="1dd4c-151">`useErrorStream`值<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="1dd4c-152">設定`initializeData`屬性設定為"`true`"來寫入追蹤和偵錯輸出至標準錯誤資料流中，將它設定為"`false`」 要寫入標準輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="1dd4c-153">檔案的名稱<xref:System.Diagnostics.DelimitedListTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1dd4c-154">現有事件記錄檔來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1dd4c-155">檔案的名稱，<xref:System.Diagnostics.EventSchemaTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="1dd4c-156">檔案的名稱，<xref:System.Diagnostics.TextWriterTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="1dd4c-157">檔案的名稱，<xref:System.Diagnostics.XmlWriterTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="1dd4c-158">組態檔</span><span class="sxs-lookup"><span data-stu-id="1dd4c-158">Configuration File</span></span>  
 <span data-ttu-id="1dd4c-159">這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dd4c-160">範例</span><span class="sxs-lookup"><span data-stu-id="1dd4c-160">Example</span></span>  
 <span data-ttu-id="1dd4c-161">下列範例示範如何使用`<add>`要加入項目<xref:System.Diagnostics.TextWriterTraceListener>`textListener`到`sharedListeners`集合。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="1dd4c-162">`textListener` 依名稱加入`Listeners`追蹤來源的集合`TraceSourceApp`。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="1dd4c-163">`textListener`接聽程式會將追蹤輸出寫入檔案 myListener.log。</span><span class="sxs-lookup"><span data-stu-id="1dd4c-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1dd4c-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dd4c-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="1dd4c-165">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1dd4c-165">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="1dd4c-166">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="1dd4c-166">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
