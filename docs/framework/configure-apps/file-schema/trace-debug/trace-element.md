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
ms.openlocfilehash: fd90d271591a47849b3f70aea50cbe909b6fd613
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920403"
---
# <a name="trace-element"></a><span data-ttu-id="ad05b-102">\<追蹤 > 元素</span><span class="sxs-lookup"><span data-stu-id="ad05b-102">\<trace> Element</span></span>
<span data-ttu-id="ad05b-103">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="ad05b-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
 <span data-ttu-id="ad05b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ad05b-104">\<configuration></span></span>  
<span data-ttu-id="ad05b-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="ad05b-105">\<system.diagnostics></span></span>  
<span data-ttu-id="ad05b-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="ad05b-106">\<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad05b-107">語法</span><span class="sxs-lookup"><span data-stu-id="ad05b-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad05b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ad05b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ad05b-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ad05b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad05b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ad05b-110">Attributes</span></span>  
  
|<span data-ttu-id="ad05b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ad05b-111">Attribute</span></span>|<span data-ttu-id="ad05b-112">描述</span><span class="sxs-lookup"><span data-stu-id="ad05b-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="ad05b-113">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="ad05b-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ad05b-114">指定追蹤接聽程式是否會在每次寫入作業之後自動清除輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ad05b-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="ad05b-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="ad05b-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ad05b-116">指定要縮排的空格數目。</span><span class="sxs-lookup"><span data-stu-id="ad05b-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="ad05b-117">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="ad05b-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ad05b-118">指出是否應該使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="ad05b-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="ad05b-119">autoflush 屬性</span><span class="sxs-lookup"><span data-stu-id="ad05b-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="ad05b-120">值</span><span class="sxs-lookup"><span data-stu-id="ad05b-120">Value</span></span>|<span data-ttu-id="ad05b-121">描述</span><span class="sxs-lookup"><span data-stu-id="ad05b-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ad05b-122">不會自動排清輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ad05b-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="ad05b-123">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="ad05b-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ad05b-124">會自動排清輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ad05b-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="ad05b-125">useGlobalLock 屬性</span><span class="sxs-lookup"><span data-stu-id="ad05b-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="ad05b-126">值</span><span class="sxs-lookup"><span data-stu-id="ad05b-126">Value</span></span>|<span data-ttu-id="ad05b-127">描述</span><span class="sxs-lookup"><span data-stu-id="ad05b-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ad05b-128">如果接聽程式是安全線程, 則不會使用全域鎖定;否則, 會使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="ad05b-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="ad05b-129">不論接聽程式是否為安全線程, 都會使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="ad05b-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="ad05b-130">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="ad05b-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad05b-131">子元素</span><span class="sxs-lookup"><span data-stu-id="ad05b-131">Child Elements</span></span>  
  
|<span data-ttu-id="ad05b-132">項目</span><span class="sxs-lookup"><span data-stu-id="ad05b-132">Element</span></span>|<span data-ttu-id="ad05b-133">說明</span><span class="sxs-lookup"><span data-stu-id="ad05b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad05b-134">\<listeners></span><span class="sxs-lookup"><span data-stu-id="ad05b-134">\<listeners></span></span>](listeners-element-for-trace.md)|<span data-ttu-id="ad05b-135">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="ad05b-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad05b-136">父項目</span><span class="sxs-lookup"><span data-stu-id="ad05b-136">Parent Elements</span></span>  
  
|<span data-ttu-id="ad05b-137">項目</span><span class="sxs-lookup"><span data-stu-id="ad05b-137">Element</span></span>|<span data-ttu-id="ad05b-138">描述</span><span class="sxs-lookup"><span data-stu-id="ad05b-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ad05b-139">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ad05b-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ad05b-140">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="ad05b-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ad05b-141">範例</span><span class="sxs-lookup"><span data-stu-id="ad05b-141">Example</span></span>  
 <span data-ttu-id="ad05b-142">下列範例顯示如何使用`<trace>`專案, 將接聽程式加入`MyListener`至`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="ad05b-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="ad05b-143">`MyListener`建立名`MyListener.log`為的檔案, 並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="ad05b-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="ad05b-144">屬性會設定為`false`, 如果追蹤接聽程式是安全線程, 則不會使用全域鎖定。 `useGlobalLock`</span><span class="sxs-lookup"><span data-stu-id="ad05b-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="ad05b-145">屬性會設定為`true`, 這會使追蹤接聽程式寫入檔案, 而不論是否<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>呼叫方法。 `autoflush`</span><span class="sxs-lookup"><span data-stu-id="ad05b-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="ad05b-146">屬性會設定為 0 (零), 這會導致接聽程式在呼叫<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>方法時縮排零空間。 `indentsize`</span><span class="sxs-lookup"><span data-stu-id="ad05b-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad05b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad05b-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="ad05b-148">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ad05b-148">Trace and Debug Settings Schema</span></span>](index.md)
