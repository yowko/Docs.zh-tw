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
ms.openlocfilehash: 02fd794eb7b7b7f46f7f7bc4e43036cb4a4758ed
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699175"
---
# <a name="trace-element"></a><span data-ttu-id="c41ea-102">@no__t 0trace > 元素</span><span class="sxs-lookup"><span data-stu-id="c41ea-102">\<trace> Element</span></span>
<span data-ttu-id="c41ea-103">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="c41ea-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[<span data-ttu-id="c41ea-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="c41ea-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c41ea-105">&nbsp; @ no__t-1[ **\<system. 診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="c41ea-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="c41ea-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<trace >**</span><span class="sxs-lookup"><span data-stu-id="c41ea-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c41ea-107">語法</span><span class="sxs-lookup"><span data-stu-id="c41ea-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c41ea-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c41ea-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c41ea-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c41ea-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c41ea-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c41ea-110">Attributes</span></span>  
  
|<span data-ttu-id="c41ea-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c41ea-111">Attribute</span></span>|<span data-ttu-id="c41ea-112">描述</span><span class="sxs-lookup"><span data-stu-id="c41ea-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="c41ea-113">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="c41ea-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c41ea-114">指定追蹤接聽程式是否會在每次寫入作業之後自動清除輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c41ea-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="c41ea-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="c41ea-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c41ea-116">指定要縮排的空格數目。</span><span class="sxs-lookup"><span data-stu-id="c41ea-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="c41ea-117">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="c41ea-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c41ea-118">指出是否應該使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="c41ea-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="c41ea-119">autoflush 屬性</span><span class="sxs-lookup"><span data-stu-id="c41ea-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="c41ea-120">值</span><span class="sxs-lookup"><span data-stu-id="c41ea-120">Value</span></span>|<span data-ttu-id="c41ea-121">描述</span><span class="sxs-lookup"><span data-stu-id="c41ea-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c41ea-122">不會自動排清輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c41ea-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="c41ea-123">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="c41ea-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="c41ea-124">會自動排清輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c41ea-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="c41ea-125">useGlobalLock 屬性</span><span class="sxs-lookup"><span data-stu-id="c41ea-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="c41ea-126">值</span><span class="sxs-lookup"><span data-stu-id="c41ea-126">Value</span></span>|<span data-ttu-id="c41ea-127">描述</span><span class="sxs-lookup"><span data-stu-id="c41ea-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c41ea-128">如果接聽程式是安全線程，則不會使用全域鎖定;否則，會使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="c41ea-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="c41ea-129">不論接聽程式是否為安全線程，都會使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="c41ea-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="c41ea-130">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="c41ea-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c41ea-131">子元素</span><span class="sxs-lookup"><span data-stu-id="c41ea-131">Child Elements</span></span>  
  
|<span data-ttu-id="c41ea-132">元素</span><span class="sxs-lookup"><span data-stu-id="c41ea-132">Element</span></span>|<span data-ttu-id="c41ea-133">描述</span><span class="sxs-lookup"><span data-stu-id="c41ea-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c41ea-134">\<listeners></span><span class="sxs-lookup"><span data-stu-id="c41ea-134">\<listeners></span></span>](listeners-element-for-trace.md)|<span data-ttu-id="c41ea-135">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="c41ea-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c41ea-136">父項目</span><span class="sxs-lookup"><span data-stu-id="c41ea-136">Parent Elements</span></span>  
  
|<span data-ttu-id="c41ea-137">項目</span><span class="sxs-lookup"><span data-stu-id="c41ea-137">Element</span></span>|<span data-ttu-id="c41ea-138">描述</span><span class="sxs-lookup"><span data-stu-id="c41ea-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c41ea-139">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c41ea-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c41ea-140">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="c41ea-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c41ea-141">範例</span><span class="sxs-lookup"><span data-stu-id="c41ea-141">Example</span></span>  
 <span data-ttu-id="c41ea-142">下列範例示範如何使用 `<trace>` 元素，將接聽程式 `MyListener` 新增至 @no__t 2 集合。</span><span class="sxs-lookup"><span data-stu-id="c41ea-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="c41ea-143">`MyListener` 會建立名為 `MyListener.log` 的檔案，並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="c41ea-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="c41ea-144">@No__t-0 屬性會設定為 `false`，如果追蹤接聽程式是安全線程，則不會使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="c41ea-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="c41ea-145">@No__t-0 屬性會設定為 `true`，這會使追蹤接聽程式寫入檔案，不論是否呼叫 @no__t 2 方法。</span><span class="sxs-lookup"><span data-stu-id="c41ea-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="c41ea-146">@No__t-0 屬性設為0（零），這會在呼叫 <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> 方法時，讓接聽程式縮排零空間。</span><span class="sxs-lookup"><span data-stu-id="c41ea-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c41ea-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c41ea-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="c41ea-148">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c41ea-148">Trace and Debug Settings Schema</span></span>](index.md)
