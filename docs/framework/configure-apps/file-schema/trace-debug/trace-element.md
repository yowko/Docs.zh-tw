---
title: '&lt;追蹤&gt;項目'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 55a7eb431432b67b3252853d14bf93be304ee883
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47233089"
---
# <a name="lttracegt-element"></a><span data-ttu-id="2b5b8-102">&lt;追蹤&gt;項目</span><span class="sxs-lookup"><span data-stu-id="2b5b8-102">&lt;trace&gt; Element</span></span>
<span data-ttu-id="2b5b8-103">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
 <span data-ttu-id="2b5b8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2b5b8-104">\<configuration></span></span>  
<span data-ttu-id="2b5b8-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="2b5b8-105">\<system.diagnostics></span></span>  
<span data-ttu-id="2b5b8-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="2b5b8-106">\<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b5b8-107">語法</span><span class="sxs-lookup"><span data-stu-id="2b5b8-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b5b8-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2b5b8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2b5b8-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b5b8-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2b5b8-110">Attributes</span></span>  
  
|<span data-ttu-id="2b5b8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2b5b8-111">Attribute</span></span>|<span data-ttu-id="2b5b8-112">描述</span><span class="sxs-lookup"><span data-stu-id="2b5b8-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="2b5b8-113">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2b5b8-114">指定的追蹤接聽程式是否會自動清除之後每次寫入作業的輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="2b5b8-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2b5b8-116">指定要縮排空格的數目。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="2b5b8-117">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2b5b8-118">指出是否應該使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="2b5b8-119">autoflush 屬性</span><span class="sxs-lookup"><span data-stu-id="2b5b8-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="2b5b8-120">值</span><span class="sxs-lookup"><span data-stu-id="2b5b8-120">Value</span></span>|<span data-ttu-id="2b5b8-121">描述</span><span class="sxs-lookup"><span data-stu-id="2b5b8-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2b5b8-122">不會自動清除輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="2b5b8-123">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="2b5b8-124">會自動排清輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="2b5b8-125">useGlobalLock 屬性</span><span class="sxs-lookup"><span data-stu-id="2b5b8-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="2b5b8-126">值</span><span class="sxs-lookup"><span data-stu-id="2b5b8-126">Value</span></span>|<span data-ttu-id="2b5b8-127">描述</span><span class="sxs-lookup"><span data-stu-id="2b5b8-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2b5b8-128">如果接聽程式是具備執行緒安全; 不會使用全域鎖定否則，會使用全域鎖定。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="2b5b8-129">使用全域鎖定，而不論接聽程式是否具備執行緒安全。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="2b5b8-130">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b5b8-131">子元素</span><span class="sxs-lookup"><span data-stu-id="2b5b8-131">Child Elements</span></span>  
  
|<span data-ttu-id="2b5b8-132">項目</span><span class="sxs-lookup"><span data-stu-id="2b5b8-132">Element</span></span>|<span data-ttu-id="2b5b8-133">描述</span><span class="sxs-lookup"><span data-stu-id="2b5b8-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b5b8-134">\<listeners></span><span class="sxs-lookup"><span data-stu-id="2b5b8-134">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="2b5b8-135">指定的接聽程式會收集、 存放區，並將訊息路由。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b5b8-136">父項目</span><span class="sxs-lookup"><span data-stu-id="2b5b8-136">Parent Elements</span></span>  
  
|<span data-ttu-id="2b5b8-137">項目</span><span class="sxs-lookup"><span data-stu-id="2b5b8-137">Element</span></span>|<span data-ttu-id="2b5b8-138">描述</span><span class="sxs-lookup"><span data-stu-id="2b5b8-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2b5b8-139">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2b5b8-140">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2b5b8-141">範例</span><span class="sxs-lookup"><span data-stu-id="2b5b8-141">Example</span></span>  
 <span data-ttu-id="2b5b8-142">下列範例示範如何使用`<trace>`加入接聽程式的項目`MyListener`到`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="2b5b8-143">`MyListener` 建立檔案，稱為`MyListener.log`並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="2b5b8-144">`useGlobalLock`屬性設為`false`，因而導致全域鎖定不會使用追蹤接聽程式是否具備執行緒安全。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="2b5b8-145">`autoflush`屬性設定為`true`，這會讓追蹤接聽項寫入至檔案，無論<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="2b5b8-146">`indentsize`屬性設為 0 （零），這會導致要為零的縮排的接聽程式時<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="2b5b8-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b5b8-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b5b8-147">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [<span data-ttu-id="2b5b8-148">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2b5b8-148">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
