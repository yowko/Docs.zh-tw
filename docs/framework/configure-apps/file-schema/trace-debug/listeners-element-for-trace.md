---
title: '&lt;接聽程式&gt;元素&lt;追蹤&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2f0d795d6a8789772ff3fd46648fbc0d683c66e5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltlistenersgt-element-for-lttracegt"></a><span data-ttu-id="17605-102">&lt;接聽程式&gt;元素&lt;追蹤&gt;</span><span class="sxs-lookup"><span data-stu-id="17605-102">&lt;listeners&gt; Element for &lt;trace&gt;</span></span>
<span data-ttu-id="17605-103">指定的接聽程式會收集，存放區，並將訊息路由。</span><span class="sxs-lookup"><span data-stu-id="17605-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="17605-104">接聽程式將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="17605-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="17605-105">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="17605-105">\<configuration> Element</span></span>  
<span data-ttu-id="17605-106">\<system.diagnostics > 項目</span><span class="sxs-lookup"><span data-stu-id="17605-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="17605-107">\<追蹤 > 項目</span><span class="sxs-lookup"><span data-stu-id="17605-107">\<trace> Element</span></span>  
<span data-ttu-id="17605-108">\<接聽程式 > 項目\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="17605-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17605-109">語法</span><span class="sxs-lookup"><span data-stu-id="17605-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17605-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="17605-110">Attributes and Elements</span></span>  
 <span data-ttu-id="17605-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="17605-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17605-112">屬性</span><span class="sxs-lookup"><span data-stu-id="17605-112">Attributes</span></span>  
 <span data-ttu-id="17605-113">無。</span><span class="sxs-lookup"><span data-stu-id="17605-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="17605-114">子項目</span><span class="sxs-lookup"><span data-stu-id="17605-114">Child Elements</span></span>  
  
|<span data-ttu-id="17605-115">項目</span><span class="sxs-lookup"><span data-stu-id="17605-115">Element</span></span>|<span data-ttu-id="17605-116">描述</span><span class="sxs-lookup"><span data-stu-id="17605-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17605-117">\<add></span><span class="sxs-lookup"><span data-stu-id="17605-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="17605-118">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="17605-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="17605-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="17605-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="17605-120">清除追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="17605-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="17605-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="17605-121">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="17605-122">移除的接聽程式從`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="17605-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17605-123">父項目</span><span class="sxs-lookup"><span data-stu-id="17605-123">Parent Elements</span></span>  
  
|<span data-ttu-id="17605-124">項目</span><span class="sxs-lookup"><span data-stu-id="17605-124">Element</span></span>|<span data-ttu-id="17605-125">描述</span><span class="sxs-lookup"><span data-stu-id="17605-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="17605-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="17605-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="17605-127">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="17605-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="17605-128">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="17605-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17605-129">備註</span><span class="sxs-lookup"><span data-stu-id="17605-129">Remarks</span></span>  
 <span data-ttu-id="17605-130"><xref:System.Diagnostics.Debug>和<xref:System.Diagnostics.Trace>類別共用相同**接聽程式**集合。</span><span class="sxs-lookup"><span data-stu-id="17605-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="17605-131">如果您將接聽程式物件加入至集合中的其中一個這些類別，另一個類別會使用相同的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="17605-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="17605-132">.NET Framework 所隨附的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="17605-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="17605-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="17605-133">Configuration File</span></span>  
 <span data-ttu-id="17605-134">此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="17605-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17605-135">範例</span><span class="sxs-lookup"><span data-stu-id="17605-135">Example</span></span>  
 <span data-ttu-id="17605-136">下列範例示範如何使用**\<接聽程式 >** 項目將接聽項`MyListener`和`MyEventListener`至**接聽程式**集合。</span><span class="sxs-lookup"><span data-stu-id="17605-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="17605-137">`MyListener` 建立名為的檔案`MyListener.log`並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="17605-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="17605-138">`MyEventListener` 事件記錄檔中建立項目。</span><span class="sxs-lookup"><span data-stu-id="17605-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17605-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17605-139">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="17605-140">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="17605-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
