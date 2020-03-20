---
title: <trace> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153369"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="94783-102">\<攔截器>\<元素進行跟蹤></span><span class="sxs-lookup"><span data-stu-id="94783-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="94783-103">指定收集、存儲和路由消息的攔截器。</span><span class="sxs-lookup"><span data-stu-id="94783-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="94783-104">攔截器將跟蹤輸出定向到適當的目標。</span><span class="sxs-lookup"><span data-stu-id="94783-104">Listeners direct the tracing output to an appropriate target.</span></span>  

<span data-ttu-id="94783-105">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="94783-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="94783-106">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="94783-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="94783-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="94783-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="94783-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<聽眾>**</span><span class="sxs-lookup"><span data-stu-id="94783-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>

## <a name="syntax"></a><span data-ttu-id="94783-109">語法</span><span class="sxs-lookup"><span data-stu-id="94783-109">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94783-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="94783-110">Attributes and Elements</span></span>  
 <span data-ttu-id="94783-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="94783-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94783-112">屬性</span><span class="sxs-lookup"><span data-stu-id="94783-112">Attributes</span></span>  
 <span data-ttu-id="94783-113">無。</span><span class="sxs-lookup"><span data-stu-id="94783-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="94783-114">子元素</span><span class="sxs-lookup"><span data-stu-id="94783-114">Child Elements</span></span>  
  
|<span data-ttu-id="94783-115">元素</span><span class="sxs-lookup"><span data-stu-id="94783-115">Element</span></span>|<span data-ttu-id="94783-116">描述</span><span class="sxs-lookup"><span data-stu-id="94783-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94783-117">\<添加></span><span class="sxs-lookup"><span data-stu-id="94783-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="94783-118">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="94783-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="94783-119">\<明確></span><span class="sxs-lookup"><span data-stu-id="94783-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="94783-120">清除追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="94783-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="94783-121">\<刪除></span><span class="sxs-lookup"><span data-stu-id="94783-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="94783-122">從`Listeners`集合中刪除攔截器。</span><span class="sxs-lookup"><span data-stu-id="94783-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94783-123">父項目</span><span class="sxs-lookup"><span data-stu-id="94783-123">Parent Elements</span></span>  
  
|<span data-ttu-id="94783-124">元素</span><span class="sxs-lookup"><span data-stu-id="94783-124">Element</span></span>|<span data-ttu-id="94783-125">描述</span><span class="sxs-lookup"><span data-stu-id="94783-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="94783-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="94783-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="94783-127">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="94783-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="94783-128">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="94783-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94783-129">備註</span><span class="sxs-lookup"><span data-stu-id="94783-129">Remarks</span></span>  
 <span data-ttu-id="94783-130">和 類共用相同的**攔截器**集合。 <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.Debug></span><span class="sxs-lookup"><span data-stu-id="94783-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="94783-131">如果向這些類之一的集合添加攔截器物件，則另一個類使用相同的攔截器。</span><span class="sxs-lookup"><span data-stu-id="94783-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="94783-132">.NET 框架附帶的攔截器類派生自<xref:System.Diagnostics.TraceListener>該類。</span><span class="sxs-lookup"><span data-stu-id="94783-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="94783-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="94783-133">Configuration File</span></span>  
 <span data-ttu-id="94783-134">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="94783-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94783-135">範例</span><span class="sxs-lookup"><span data-stu-id="94783-135">Example</span></span>  
 <span data-ttu-id="94783-136">下面的示例演示如何使用**\<攔截器>** 元素將攔截器`MyListener`和`MyEventListener`**攔截器集合添加到攔截器**集合。</span><span class="sxs-lookup"><span data-stu-id="94783-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="94783-137">`MyListener`創建一個稱為`MyListener.log`檔並將輸出寫入該檔。</span><span class="sxs-lookup"><span data-stu-id="94783-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="94783-138">`MyEventListener`在事件日誌中創建條目。</span><span class="sxs-lookup"><span data-stu-id="94783-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94783-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94783-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="94783-140">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="94783-140">Trace and Debug Settings Schema</span></span>](index.md)
