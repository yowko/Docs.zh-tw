---
title: '&lt;新增&gt;項目&lt;接聽程式&gt;如&lt;追蹤&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: 4edefcfdd56be56ccc0ccaf2bff118ba8266e226
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083635"
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="6c2de-102">&lt;新增&gt;項目&lt;接聽程式&gt;如&lt;追蹤&gt;</span><span class="sxs-lookup"><span data-stu-id="6c2de-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="6c2de-103">新增接聽程式，以**接聽程式**集合。</span><span class="sxs-lookup"><span data-stu-id="6c2de-103">Adds a listener to the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="6c2de-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6c2de-104">\<configuration></span></span>  
<span data-ttu-id="6c2de-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="6c2de-105">\<system.diagnostics></span></span>  
<span data-ttu-id="6c2de-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="6c2de-106">\<trace></span></span>  
<span data-ttu-id="6c2de-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="6c2de-107">\<listeners></span></span>  
<span data-ttu-id="6c2de-108">\<add></span><span class="sxs-lookup"><span data-stu-id="6c2de-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c2de-109">語法</span><span class="sxs-lookup"><span data-stu-id="6c2de-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c2de-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6c2de-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6c2de-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6c2de-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c2de-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6c2de-112">Attributes</span></span>  
  
|<span data-ttu-id="6c2de-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6c2de-113">Attribute</span></span>|<span data-ttu-id="6c2de-114">描述</span><span class="sxs-lookup"><span data-stu-id="6c2de-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c2de-115">**type**</span><span class="sxs-lookup"><span data-stu-id="6c2de-115">**type**</span></span>|<span data-ttu-id="6c2de-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6c2de-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6c2de-117">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="6c2de-117">Specifies the type of the listener.</span></span> <span data-ttu-id="6c2de-118">您必須使用符合在指定之需求的字串[指定完整的型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="6c2de-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="6c2de-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="6c2de-119">**initializeData**</span></span>|<span data-ttu-id="6c2de-120">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6c2de-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6c2de-121">指定的類別，建構函式傳遞的字串。</span><span class="sxs-lookup"><span data-stu-id="6c2de-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="6c2de-122">**name**</span><span class="sxs-lookup"><span data-stu-id="6c2de-122">**name**</span></span>|<span data-ttu-id="6c2de-123">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6c2de-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6c2de-124">指定接聽程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c2de-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c2de-125">子元素</span><span class="sxs-lookup"><span data-stu-id="6c2de-125">Child Elements</span></span>  
  
|<span data-ttu-id="6c2de-126">項目</span><span class="sxs-lookup"><span data-stu-id="6c2de-126">Element</span></span>|<span data-ttu-id="6c2de-127">描述</span><span class="sxs-lookup"><span data-stu-id="6c2de-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c2de-128">\<filter></span><span class="sxs-lookup"><span data-stu-id="6c2de-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="6c2de-129">將篩選加入至中的接聽項`Listeners`追蹤的集合。</span><span class="sxs-lookup"><span data-stu-id="6c2de-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c2de-130">父項目</span><span class="sxs-lookup"><span data-stu-id="6c2de-130">Parent Elements</span></span>  
  
|<span data-ttu-id="6c2de-131">項目</span><span class="sxs-lookup"><span data-stu-id="6c2de-131">Element</span></span>|<span data-ttu-id="6c2de-132">描述</span><span class="sxs-lookup"><span data-stu-id="6c2de-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6c2de-133">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6c2de-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="6c2de-134">指定的接聽程式會收集、 存放區，並將訊息路由。</span><span class="sxs-lookup"><span data-stu-id="6c2de-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="6c2de-135">接聽程式將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="6c2de-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6c2de-136">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="6c2de-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="6c2de-137">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="6c2de-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c2de-138">備註</span><span class="sxs-lookup"><span data-stu-id="6c2de-138">Remarks</span></span>  
 <span data-ttu-id="6c2de-139"><xref:System.Diagnostics.Debug>並<xref:System.Diagnostics.Trace>類別會共用相同**接聽程式**集合。</span><span class="sxs-lookup"><span data-stu-id="6c2de-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="6c2de-140">如果您加入接聽程式物件至集合中的其中一個這些類別時，另一個類別會使用相同接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6c2de-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="6c2de-141">接聽程式的類別衍生自<xref:System.Diagnostics.TraceListener>。</span><span class="sxs-lookup"><span data-stu-id="6c2de-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="6c2de-142">如果您未指定`name`屬性的追蹤接聽項<xref:System.Diagnostics.TraceListener.Name%2A>的追蹤接聽程式的預設值為空字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="6c2de-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="6c2de-143">如果您的應用程式有只有一個接聽程式，您可以加入不含指定名稱，並移除指定名稱的空字串。</span><span class="sxs-lookup"><span data-stu-id="6c2de-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="6c2de-144">不過，如果您的應用程式有一個以上的接聽程式，您應該指定唯一的名稱，每個追蹤接聽項，可讓您識別及管理內的個別的追蹤接聽項<xref:System.Diagnostics.Debug.Listeners%2A>和<xref:System.Diagnostics.Trace.Listeners%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="6c2de-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c2de-145">加入一個以上的追蹤接聽程式相同的型別，而且具有相同名稱中只能有一個追蹤接聽程式的該類型的結果，並將命名要新增至`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="6c2de-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="6c2de-146">不過，您可以程式設計方式加入至多個相同的接聽程式`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="6c2de-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="6c2de-147">值**initializeData**屬性取決於您所建立的接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="6c2de-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="6c2de-148">並非所有的追蹤接聽程式會要求您指定**initializeData**。</span><span class="sxs-lookup"><span data-stu-id="6c2de-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c2de-149">當您使用`initializeData`屬性，您可能會收到編譯器警告"未宣告 'initializeData' 屬性。 」</span><span class="sxs-lookup"><span data-stu-id="6c2de-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="6c2de-150">因為對抽象的基底類別會驗證組態設定，就會發生此警告<xref:System.Diagnostics.TraceListener>，其無法辨識`initializeData`屬性。</span><span class="sxs-lookup"><span data-stu-id="6c2de-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="6c2de-151">一般而言，您可以忽略此警告具有參數的建構函式的追蹤接聽程式實作。</span><span class="sxs-lookup"><span data-stu-id="6c2de-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="6c2de-152">下表顯示隨附於.NET Framework 追蹤接聽項，並說明的價值，他們**initializeData**屬性。</span><span class="sxs-lookup"><span data-stu-id="6c2de-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="6c2de-153">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="6c2de-153">Trace listener class</span></span>|<span data-ttu-id="6c2de-154">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="6c2de-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c2de-155">`useErrorStream`值<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="6c2de-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="6c2de-156">設定`initializeData`屬性設定為"`true`」 來撰寫追蹤和偵錯輸出至<xref:System.Console.Error%2A?displayProperty=nameWithType>;「`false`"寫入<xref:System.Console.Out%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6c2de-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c2de-157">檔案的名稱<xref:System.Diagnostics.DelimitedListTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="6c2de-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c2de-158">現有事件記錄檔來源的名稱的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c2de-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c2de-159">檔案的名稱，<xref:System.Diagnostics.EventSchemaTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="6c2de-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c2de-160">檔案的名稱，<xref:System.Diagnostics.TextWriterTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="6c2de-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6c2de-161">檔案的名稱，<xref:System.Diagnostics.XmlWriterTraceListener>寫入。</span><span class="sxs-lookup"><span data-stu-id="6c2de-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6c2de-162">範例</span><span class="sxs-lookup"><span data-stu-id="6c2de-162">Example</span></span>  
 <span data-ttu-id="6c2de-163">下列範例示範如何使用**\<新增 >** 加入接聽程式的項目`MyListener`並`MyEventListener`來**接聽程式**集合。</span><span class="sxs-lookup"><span data-stu-id="6c2de-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="6c2de-164">`MyListener` 建立一個稱為檔案`MyListener.log`並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="6c2de-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="6c2de-165">`MyEventListener` 建立事件記錄檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="6c2de-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c2de-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c2de-166">See also</span></span>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="6c2de-167">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6c2de-167">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="6c2de-168">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="6c2de-168">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
