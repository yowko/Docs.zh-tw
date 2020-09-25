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
ms.openlocfilehash: f0ede5f9dc19e9589afc888e7fcd01785bc1840c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174026"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="0f8c5-102">\<sharedListeners> 的 \<add> 項目</span><span class="sxs-lookup"><span data-stu-id="0f8c5-102">\<add> Element for \<sharedListeners></span></span>

<span data-ttu-id="0f8c5-103">將接聽項新增至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="0f8c5-104">`sharedListeners` 這是任何 [\<source>](source-element.md) 或可以參考之接聽項的集合 [\<trace>](trace-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="0f8c5-105">根據預設，集合中的接聽程式 `sharedListeners` 不會放置在 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="0f8c5-106">您必須依名稱將它們加入至 [\<source>](source-element.md) 或 [\<trace>](trace-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="0f8c5-107">您無法在執行時間于程式碼中取得集合中的接聽程式 `sharedListeners` 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="0f8c5-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="0f8c5-108">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f8c5-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0f8c5-109">Attributes and Elements</span></span>  

 <span data-ttu-id="0f8c5-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f8c5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0f8c5-111">Attributes</span></span>  
  
|<span data-ttu-id="0f8c5-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0f8c5-112">Attribute</span></span>|<span data-ttu-id="0f8c5-113">描述</span><span class="sxs-lookup"><span data-stu-id="0f8c5-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="0f8c5-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0f8c5-115">指定用來將共用接聽程式加入至集合之接聽程式的名稱 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-115">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="0f8c5-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="0f8c5-117">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-117">Specifies the type of the listener.</span></span> <span data-ttu-id="0f8c5-118">您必須使用符合指定 [完整限定型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="0f8c5-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0f8c5-120">傳遞給指定類別之函式的字串。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-120">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="0f8c5-121">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-121">Optional attribute.</span></span><br/><br/><span data-ttu-id="0f8c5-122">表示要寫入追蹤輸出之資料的一或多個列舉成員的字串表示 <xref:System.Diagnostics.TraceOptions> 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-122">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="0f8c5-123">多個專案會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-123">Multiple items are separated by commas.</span></span> <span data-ttu-id="0f8c5-124">預設值為 "None"。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-124">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0f8c5-125">子元素</span><span class="sxs-lookup"><span data-stu-id="0f8c5-125">Child Elements</span></span>  
  
|<span data-ttu-id="0f8c5-126">項目</span><span class="sxs-lookup"><span data-stu-id="0f8c5-126">Element</span></span>|<span data-ttu-id="0f8c5-127">描述</span><span class="sxs-lookup"><span data-stu-id="0f8c5-127">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="0f8c5-128">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-128">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f8c5-129">父項目</span><span class="sxs-lookup"><span data-stu-id="0f8c5-129">Parent Elements</span></span>  
  
|<span data-ttu-id="0f8c5-130">項目</span><span class="sxs-lookup"><span data-stu-id="0f8c5-130">Element</span></span>|<span data-ttu-id="0f8c5-131">描述</span><span class="sxs-lookup"><span data-stu-id="0f8c5-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0f8c5-132">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0f8c5-133">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="0f8c5-134">任何來源或追蹤元素可以參考的接聽項集合。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-134">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f8c5-135">備註</span><span class="sxs-lookup"><span data-stu-id="0f8c5-135">Remarks</span></span>  

 <span data-ttu-id="0f8c5-136">隨附于 .NET Framework 的接聽程式類別衍生自 <xref:System.Diagnostics.TraceListener> 類別。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-136">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="0f8c5-137">屬性的值 `name` 是用來將共用接聽程式加入至 `Listeners` 追蹤或追蹤來源的集合。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-137">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="0f8c5-138">屬性的值 `initializeData` 取決於您所建立的接聽程式類型。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-138">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="0f8c5-139">並非所有的追蹤接聽項都需要您指定 `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-139">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f8c5-140">當您使用 `initializeData` 屬性時，您可能會收到編譯器警告「' initializeData ' 屬性未宣告」。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-140">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="0f8c5-141">發生此警告的原因是，針對無法辨識屬性的抽象基類驗證設定設定 <xref:System.Diagnostics.TraceListener> `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-141">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="0f8c5-142">一般來說，如果追蹤接聽程式執行具有接受參數的函式，您可以忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-142">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="0f8c5-143">下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其屬性的值 `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-143">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="0f8c5-144">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="0f8c5-144">Trace listener class</span></span>|<span data-ttu-id="0f8c5-145">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="0f8c5-145">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="0f8c5-146">`useErrorStream`函數的值 <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-146">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="0f8c5-147">將 `initializeData` 屬性設為 " `true` "，以將追蹤和調試輸出寫入標準錯誤資料流程，將其設定為 `false` "" 以寫入至標準輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-147">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="0f8c5-148"><xref:System.Diagnostics.DelimitedListTraceListener> 寫入的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-148">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="0f8c5-149">現有事件記錄檔來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-149">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="0f8c5-150">寫入的檔案名 <xref:System.Diagnostics.EventSchemaTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-150">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="0f8c5-151">寫入的檔案名 <xref:System.Diagnostics.TextWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-151">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="0f8c5-152">寫入的檔案名 <xref:System.Diagnostics.XmlWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-152">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="0f8c5-153">組態檔</span><span class="sxs-lookup"><span data-stu-id="0f8c5-153">Configuration File</span></span>  

 <span data-ttu-id="0f8c5-154">此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-154">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f8c5-155">範例</span><span class="sxs-lookup"><span data-stu-id="0f8c5-155">Example</span></span>  

 <span data-ttu-id="0f8c5-156">下列範例示範如何使用專案 `<add>` 將加入 <xref:System.Diagnostics.TextWriterTraceListener> `textListener` 至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-156">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="0f8c5-157">`textListener` 會依名稱加入至 `Listeners` 追蹤來源的集合 `TraceSourceApp` 。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-157">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="0f8c5-158">接聽程式會將 `textListener` 追蹤輸出寫入 myListener 檔案。</span><span class="sxs-lookup"><span data-stu-id="0f8c5-158">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f8c5-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f8c5-159">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="0f8c5-160">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0f8c5-160">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0f8c5-161">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="0f8c5-161">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
