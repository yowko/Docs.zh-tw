---
title: <add>的元素 <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: da5c0ccae08a32c324a1633b5a7ff7592efa6e2d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174039"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="a450b-102">\<add>的元素 \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="a450b-102">\<add> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="a450b-103">將接聽程式加入至接聽**程式集合。**</span><span class="sxs-lookup"><span data-stu-id="a450b-103">Adds a listener to the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="a450b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a450b-104">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a450b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a450b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a450b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a450b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a450b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a450b-107">Attributes</span></span>  
  
|<span data-ttu-id="a450b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a450b-108">Attribute</span></span>|<span data-ttu-id="a450b-109">描述</span><span class="sxs-lookup"><span data-stu-id="a450b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a450b-110">**type**</span><span class="sxs-lookup"><span data-stu-id="a450b-110">**type**</span></span>|<span data-ttu-id="a450b-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a450b-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="a450b-112">指定接聽程式的類型。</span><span class="sxs-lookup"><span data-stu-id="a450b-112">Specifies the type of the listener.</span></span> <span data-ttu-id="a450b-113">您必須使用符合指定 [完整限定型別名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。</span><span class="sxs-lookup"><span data-stu-id="a450b-113">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="a450b-114">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="a450b-114">**initializeData**</span></span>|<span data-ttu-id="a450b-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="a450b-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a450b-116">傳遞給指定類別之函式的字串。</span><span class="sxs-lookup"><span data-stu-id="a450b-116">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="a450b-117">**name**</span><span class="sxs-lookup"><span data-stu-id="a450b-117">**name**</span></span>|<span data-ttu-id="a450b-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="a450b-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a450b-119">指定接聽程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="a450b-119">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a450b-120">子元素</span><span class="sxs-lookup"><span data-stu-id="a450b-120">Child Elements</span></span>  
  
|<span data-ttu-id="a450b-121">項目</span><span class="sxs-lookup"><span data-stu-id="a450b-121">Element</span></span>|<span data-ttu-id="a450b-122">描述</span><span class="sxs-lookup"><span data-stu-id="a450b-122">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="a450b-123">將篩選加入至追蹤集合中的接聽 `Listeners` 程式。</span><span class="sxs-lookup"><span data-stu-id="a450b-123">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a450b-124">父項目</span><span class="sxs-lookup"><span data-stu-id="a450b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a450b-125">項目</span><span class="sxs-lookup"><span data-stu-id="a450b-125">Element</span></span>|<span data-ttu-id="a450b-126">描述</span><span class="sxs-lookup"><span data-stu-id="a450b-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a450b-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a450b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="a450b-128">指定收集、儲存和路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="a450b-128">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="a450b-129">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="a450b-129">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a450b-130">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="a450b-130">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="a450b-131">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="a450b-131">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a450b-132">備註</span><span class="sxs-lookup"><span data-stu-id="a450b-132">Remarks</span></span>  

 <span data-ttu-id="a450b-133"><xref:System.Diagnostics.Debug>和 <xref:System.Diagnostics.Trace> 類別共用相同的接聽**Listeners**程式集合。</span><span class="sxs-lookup"><span data-stu-id="a450b-133">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="a450b-134">如果您在其中一個類別中將接聽程式物件加入至集合，另一個類別會使用相同的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="a450b-134">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="a450b-135">接聽程式類別衍生自 <xref:System.Diagnostics.TraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="a450b-135">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="a450b-136">如果您未指定追蹤接聽 `name` 項的屬性，追蹤接聽程式的會 <xref:System.Diagnostics.TraceListener.Name%2A> 預設為空字串 ( "" ) 。</span><span class="sxs-lookup"><span data-stu-id="a450b-136">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="a450b-137">如果您的應用程式只有一個接聽程式，您可以在不指定名稱的情況下新增它，並指定名稱的空字串來移除它。</span><span class="sxs-lookup"><span data-stu-id="a450b-137">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="a450b-138">但是，如果您的應用程式有多個接聽程式，您應該為每個追蹤接聽程式指定唯一的名稱，讓您識別和管理和集合內的個別追蹤接聽程式 <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a450b-138">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a450b-139">加入一個以上相同類型且具有相同名稱的追蹤接聽程式，只會導致該型別和名稱的一個追蹤接聽項加入至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="a450b-139">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="a450b-140">不過，您可以透過程式設計方式將多個相同的接聽程式加入至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="a450b-140">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="a450b-141">[ **InitializeData** ] 屬性的值取決於您所建立的接聽程式類型。</span><span class="sxs-lookup"><span data-stu-id="a450b-141">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="a450b-142">並非所有的追蹤接聽項都需要您指定 **initializeData**。</span><span class="sxs-lookup"><span data-stu-id="a450b-142">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a450b-143">當您使用 `initializeData` 屬性時，您可能會收到編譯器警告「' initializeData ' 屬性未宣告」。</span><span class="sxs-lookup"><span data-stu-id="a450b-143">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="a450b-144">發生此警告的原因是，針對無法辨識屬性的抽象基類驗證設定設定 <xref:System.Diagnostics.TraceListener> `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="a450b-144">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="a450b-145">一般來說，如果追蹤接聽程式執行具有接受參數的函式，您可以忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="a450b-145">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="a450b-146">下表顯示 .NET Framework 隨附的追蹤接聽項，並描述其 **initializeData** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="a450b-146">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="a450b-147">追蹤接聽程式類別</span><span class="sxs-lookup"><span data-stu-id="a450b-147">Trace listener class</span></span>|<span data-ttu-id="a450b-148">initializeData 屬性值</span><span class="sxs-lookup"><span data-stu-id="a450b-148">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a450b-149">`useErrorStream`函數的值 <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a450b-149">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="a450b-150">將 `initializeData` 屬性設為 " `true` " 以將追蹤和調試輸出寫入至 <xref:System.Console.Error%2A?displayProperty=nameWithType> ;" `false` " 要寫入的 <xref:System.Console.Out%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="a450b-150">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a450b-151"><xref:System.Diagnostics.DelimitedListTraceListener> 寫入的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a450b-151">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a450b-152">現有事件記錄檔來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="a450b-152">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a450b-153">寫入的檔案名 <xref:System.Diagnostics.EventSchemaTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="a450b-153">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a450b-154">寫入的檔案名 <xref:System.Diagnostics.TextWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="a450b-154">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a450b-155">寫入的檔案名 <xref:System.Diagnostics.XmlWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="a450b-155">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a450b-156">範例</span><span class="sxs-lookup"><span data-stu-id="a450b-156">Example</span></span>  

 <span data-ttu-id="a450b-157">下列範例示範如何使用專案將接聽程式和接聽程式集合加入至接聽程式 **\<add>** `MyListener` `MyEventListener` 。 **Listeners**</span><span class="sxs-lookup"><span data-stu-id="a450b-157">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="a450b-158">`MyListener` 建立名為的檔案 `MyListener.log` ，並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="a450b-158">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="a450b-159">`MyEventListener` 在事件記錄檔中建立專案。</span><span class="sxs-lookup"><span data-stu-id="a450b-159">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a450b-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a450b-160">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="a450b-161">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a450b-161">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a450b-162">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="a450b-162">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
