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
ms.openlocfilehash: 617b42a0be2be272a78b33be997cce632d1c6dcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198921"
---
# <a name="trace-element"></a><span data-ttu-id="14bd2-102">\<trace> 項目</span><span class="sxs-lookup"><span data-stu-id="14bd2-102">\<trace> Element</span></span>

<span data-ttu-id="14bd2-103">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="14bd2-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="14bd2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="14bd2-104">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14bd2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="14bd2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="14bd2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="14bd2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14bd2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="14bd2-107">Attributes</span></span>  
  
|<span data-ttu-id="14bd2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="14bd2-108">Attribute</span></span>|<span data-ttu-id="14bd2-109">描述</span><span class="sxs-lookup"><span data-stu-id="14bd2-109">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="14bd2-110">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="14bd2-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="14bd2-111">指定追蹤接聽程式是否會在每次寫入作業之後自動排清輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="14bd2-111">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="14bd2-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="14bd2-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="14bd2-113">指定要縮排的空格數目。</span><span class="sxs-lookup"><span data-stu-id="14bd2-113">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="14bd2-114">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="14bd2-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="14bd2-115">指出是否應該使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="14bd2-115">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="14bd2-116">autoflush 屬性</span><span class="sxs-lookup"><span data-stu-id="14bd2-116">autoflush Attribute</span></span>  
  
|<span data-ttu-id="14bd2-117">值</span><span class="sxs-lookup"><span data-stu-id="14bd2-117">Value</span></span>|<span data-ttu-id="14bd2-118">描述</span><span class="sxs-lookup"><span data-stu-id="14bd2-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="14bd2-119">不會自動排清輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="14bd2-119">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="14bd2-120">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="14bd2-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="14bd2-121">自動排清輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="14bd2-121">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="14bd2-122">useGlobalLock 屬性</span><span class="sxs-lookup"><span data-stu-id="14bd2-122">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="14bd2-123">值</span><span class="sxs-lookup"><span data-stu-id="14bd2-123">Value</span></span>|<span data-ttu-id="14bd2-124">描述</span><span class="sxs-lookup"><span data-stu-id="14bd2-124">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="14bd2-125">如果接聽程式是安全線程，則不會使用全域鎖定;否則，會使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="14bd2-125">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="14bd2-126">不論接聽程式是否為安全線程，都會使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="14bd2-126">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="14bd2-127">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="14bd2-127">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14bd2-128">子元素</span><span class="sxs-lookup"><span data-stu-id="14bd2-128">Child Elements</span></span>  
  
|<span data-ttu-id="14bd2-129">項目</span><span class="sxs-lookup"><span data-stu-id="14bd2-129">Element</span></span>|<span data-ttu-id="14bd2-130">描述</span><span class="sxs-lookup"><span data-stu-id="14bd2-130">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="14bd2-131">指定收集、儲存和路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="14bd2-131">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14bd2-132">父項目</span><span class="sxs-lookup"><span data-stu-id="14bd2-132">Parent Elements</span></span>  
  
|<span data-ttu-id="14bd2-133">項目</span><span class="sxs-lookup"><span data-stu-id="14bd2-133">Element</span></span>|<span data-ttu-id="14bd2-134">描述</span><span class="sxs-lookup"><span data-stu-id="14bd2-134">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="14bd2-135">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="14bd2-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="14bd2-136">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="14bd2-136">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="14bd2-137">範例</span><span class="sxs-lookup"><span data-stu-id="14bd2-137">Example</span></span>  

 <span data-ttu-id="14bd2-138">下列範例示範如何使用專案將接聽程式 `<trace>` 加入 `MyListener` 至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="14bd2-138">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="14bd2-139">`MyListener` 建立名為的檔案 `MyListener.log` ，並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="14bd2-139">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="14bd2-140">`useGlobalLock`屬性設定為 `false` ，如果追蹤接聽程式是安全線程，就不會使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="14bd2-140">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="14bd2-141">`autoflush`屬性設定為 `true` ，無論是否呼叫方法，都會使追蹤接聽程式寫入檔案 <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="14bd2-141">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="14bd2-142">`indentsize`屬性設定為 0 (零) ，這會導致接聽程式在呼叫方法時縮排零空間 <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="14bd2-142">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="14bd2-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14bd2-143">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="14bd2-144">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="14bd2-144">Trace and Debug Settings Schema</span></span>](index.md)
