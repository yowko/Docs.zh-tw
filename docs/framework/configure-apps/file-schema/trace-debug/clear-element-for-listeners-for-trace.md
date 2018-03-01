---
title: "&lt;清除&gt;元素&lt;接聽程式&gt;如&lt;追蹤&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: b2739cc5eaa6a1e43c06849e1b00f7ac8bd531e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="d6e97-102">&lt;清除&gt;元素&lt;接聽程式&gt;如&lt;追蹤&gt;</span><span class="sxs-lookup"><span data-stu-id="d6e97-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="d6e97-103">清除追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="d6e97-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="d6e97-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d6e97-104">\<configuration></span></span>  
<span data-ttu-id="d6e97-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d6e97-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d6e97-106">\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="d6e97-106">\<trace></span></span>  
<span data-ttu-id="d6e97-107">\<接聽項 ></span><span class="sxs-lookup"><span data-stu-id="d6e97-107">\<listeners></span></span>  
<span data-ttu-id="d6e97-108">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="d6e97-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e97-109">語法</span><span class="sxs-lookup"><span data-stu-id="d6e97-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6e97-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d6e97-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d6e97-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d6e97-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6e97-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d6e97-112">Attributes</span></span>  
 <span data-ttu-id="d6e97-113">無。</span><span class="sxs-lookup"><span data-stu-id="d6e97-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6e97-114">子元素</span><span class="sxs-lookup"><span data-stu-id="d6e97-114">Child Elements</span></span>  
 <span data-ttu-id="d6e97-115">無。</span><span class="sxs-lookup"><span data-stu-id="d6e97-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6e97-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d6e97-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d6e97-117">項目</span><span class="sxs-lookup"><span data-stu-id="d6e97-117">Element</span></span>|<span data-ttu-id="d6e97-118">描述</span><span class="sxs-lookup"><span data-stu-id="d6e97-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d6e97-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d6e97-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d6e97-120">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="d6e97-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="d6e97-121">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="d6e97-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="d6e97-122">包含收集、 儲存和路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d6e97-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="d6e97-123">接聽程式將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="d6e97-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6e97-124">備註</span><span class="sxs-lookup"><span data-stu-id="d6e97-124">Remarks</span></span>  
 <span data-ttu-id="d6e97-125">`<clear>`項目會移除所有的接聽程式從`Listeners`追蹤的集合。</span><span class="sxs-lookup"><span data-stu-id="d6e97-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="d6e97-126">您可以使用`<clear>`之前使用的項目`<add>`確定沒有其他作用中的接聽程式集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="d6e97-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="d6e97-127">您可以清除`Listeners`集合以程式設計方式呼叫<xref:System.Diagnostics.TraceListenerCollection.Clear%2A>方法<xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>屬性 (`System.Diagnostics.Trace.Listeners.Clear()`)。</span><span class="sxs-lookup"><span data-stu-id="d6e97-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="d6e97-128">此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="d6e97-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6e97-129">`<clear>`項目會移除<xref:System.Diagnostics.DefaultTraceListener>從`Listeners`集合中，變更的行為<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>，和<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="d6e97-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="d6e97-130">呼叫`Assert`或`Fail`方法通常會在顯示的訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="d6e97-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="d6e97-131">不過，訊息不會顯示方塊如果<xref:System.Diagnostics.DefaultTraceListener>不在`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="d6e97-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6e97-132">範例</span><span class="sxs-lookup"><span data-stu-id="d6e97-132">Example</span></span>  
 <span data-ttu-id="d6e97-133">下列範例示範如何使用`<clear>`之前使用的項目`<add>`加入接聽程式的項目`console`至`Listeners`追蹤的集合。</span><span class="sxs-lookup"><span data-stu-id="d6e97-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="d6e97-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="d6e97-134">See Also</span></span>  
 <xref:System.Diagnostics.Trace.Listeners%2A>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="d6e97-135">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d6e97-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="d6e97-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="d6e97-136">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)  
 [<span data-ttu-id="d6e97-137">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="d6e97-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
