---
title: <trace> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153162"
---
# <a name="trace-element"></a><span data-ttu-id="8fc2e-102">\<跟蹤>元素</span><span class="sxs-lookup"><span data-stu-id="8fc2e-102">\<trace> Element</span></span>
<span data-ttu-id="8fc2e-103">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[<span data-ttu-id="8fc2e-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="8fc2e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8fc2e-105">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="8fc2e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="8fc2e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<跟蹤>**</span><span class="sxs-lookup"><span data-stu-id="8fc2e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc2e-107">語法</span><span class="sxs-lookup"><span data-stu-id="8fc2e-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fc2e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8fc2e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8fc2e-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fc2e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8fc2e-110">Attributes</span></span>  
  
|<span data-ttu-id="8fc2e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8fc2e-111">Attribute</span></span>|<span data-ttu-id="8fc2e-112">描述</span><span class="sxs-lookup"><span data-stu-id="8fc2e-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="8fc2e-113">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8fc2e-114">指定跟蹤攔截器在每個寫入操作後是否自動刷新輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="8fc2e-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8fc2e-116">指定縮進空格數。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="8fc2e-117">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8fc2e-118">指示是否應使用全域鎖。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="8fc2e-119">自動刷新屬性</span><span class="sxs-lookup"><span data-stu-id="8fc2e-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="8fc2e-120">值</span><span class="sxs-lookup"><span data-stu-id="8fc2e-120">Value</span></span>|<span data-ttu-id="8fc2e-121">描述</span><span class="sxs-lookup"><span data-stu-id="8fc2e-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8fc2e-122">不會自動刷新輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="8fc2e-123">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="8fc2e-124">自動刷新輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="8fc2e-125">使用全域鎖定屬性</span><span class="sxs-lookup"><span data-stu-id="8fc2e-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="8fc2e-126">值</span><span class="sxs-lookup"><span data-stu-id="8fc2e-126">Value</span></span>|<span data-ttu-id="8fc2e-127">描述</span><span class="sxs-lookup"><span data-stu-id="8fc2e-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8fc2e-128">如果攔截器是執行緒安全的，則不使用全域鎖;否則，使用全域鎖。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="8fc2e-129">無論攔截器是否安全，都使用全域鎖。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="8fc2e-130">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fc2e-131">子元素</span><span class="sxs-lookup"><span data-stu-id="8fc2e-131">Child Elements</span></span>  
  
|<span data-ttu-id="8fc2e-132">元素</span><span class="sxs-lookup"><span data-stu-id="8fc2e-132">Element</span></span>|<span data-ttu-id="8fc2e-133">描述</span><span class="sxs-lookup"><span data-stu-id="8fc2e-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fc2e-134">\<聽眾></span><span class="sxs-lookup"><span data-stu-id="8fc2e-134">\<listeners></span></span>](listeners-element-for-trace.md)|<span data-ttu-id="8fc2e-135">指定收集、存儲和路由消息的攔截器。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8fc2e-136">父項目</span><span class="sxs-lookup"><span data-stu-id="8fc2e-136">Parent Elements</span></span>  
  
|<span data-ttu-id="8fc2e-137">元素</span><span class="sxs-lookup"><span data-stu-id="8fc2e-137">Element</span></span>|<span data-ttu-id="8fc2e-138">描述</span><span class="sxs-lookup"><span data-stu-id="8fc2e-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8fc2e-139">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8fc2e-140">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8fc2e-141">範例</span><span class="sxs-lookup"><span data-stu-id="8fc2e-141">Example</span></span>  
 <span data-ttu-id="8fc2e-142">下面的示例演示如何使用 元素`<trace>`將攔截器`MyListener`添加到`Listeners`集合中。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="8fc2e-143">`MyListener`創建命名`MyListener.log`的檔並將輸出寫入該檔。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="8fc2e-144">屬性`useGlobalLock`設置為`false`，這將導致在跟蹤攔截器是執行緒安全的時不使用全域鎖。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="8fc2e-145">屬性`autoflush`設置為`true`，這將導致跟蹤攔截器寫入檔，而不考慮是否調用<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>該方法。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="8fc2e-146">屬性`indentsize`設置為 0（零），這將導致調用<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>方法時攔截器縮進零空格。</span><span class="sxs-lookup"><span data-stu-id="8fc2e-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fc2e-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fc2e-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="8fc2e-148">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="8fc2e-148">Trace and Debug Settings Schema</span></span>](index.md)
