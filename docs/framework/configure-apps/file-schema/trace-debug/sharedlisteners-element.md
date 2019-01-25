---
title: '&lt;sharedListeners&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3069022287d469704cc7adac40d02ef3c6997b56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563040"
---
# <a name="ltsharedlistenersgt-element"></a><span data-ttu-id="796d0-102">&lt;sharedListeners&gt;項目</span><span class="sxs-lookup"><span data-stu-id="796d0-102">&lt;sharedListeners&gt; Element</span></span>
<span data-ttu-id="796d0-103">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="796d0-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="796d0-104">根據預設，這些接聽程式沒有收到任何追蹤，則不可能在執行階段擷取這些接聽程式。</span><span class="sxs-lookup"><span data-stu-id="796d0-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="796d0-105">識別為共用接聽項可以依名稱加入到來源或追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="796d0-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
 <span data-ttu-id="796d0-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="796d0-106">\<configuration></span></span>  
<span data-ttu-id="796d0-107">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="796d0-107">\<system.diagnostics></span></span>  
<span data-ttu-id="796d0-108">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="796d0-108">\<sharedListeners></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796d0-109">語法</span><span class="sxs-lookup"><span data-stu-id="796d0-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="796d0-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="796d0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="796d0-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="796d0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="796d0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="796d0-112">Attributes</span></span>  
 <span data-ttu-id="796d0-113">無。</span><span class="sxs-lookup"><span data-stu-id="796d0-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="796d0-114">子元素</span><span class="sxs-lookup"><span data-stu-id="796d0-114">Child Elements</span></span>  
  
|<span data-ttu-id="796d0-115">項目</span><span class="sxs-lookup"><span data-stu-id="796d0-115">Element</span></span>|<span data-ttu-id="796d0-116">描述</span><span class="sxs-lookup"><span data-stu-id="796d0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="796d0-117">\<add></span><span class="sxs-lookup"><span data-stu-id="796d0-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="796d0-118">將接聽項新增至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="796d0-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="796d0-119">父項目</span><span class="sxs-lookup"><span data-stu-id="796d0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="796d0-120">項目</span><span class="sxs-lookup"><span data-stu-id="796d0-120">Element</span></span>|<span data-ttu-id="796d0-121">描述</span><span class="sxs-lookup"><span data-stu-id="796d0-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="796d0-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="796d0-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="796d0-123">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="796d0-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="796d0-124">備註</span><span class="sxs-lookup"><span data-stu-id="796d0-124">Remarks</span></span>  
 <span data-ttu-id="796d0-125">加入共用接聽項集合中的接聽程式不會進行它的作用中接聽程式。</span><span class="sxs-lookup"><span data-stu-id="796d0-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="796d0-126">它必須仍會加入至追蹤來源或追蹤將它加入至`Listeners`該追蹤項目的集合。</span><span class="sxs-lookup"><span data-stu-id="796d0-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="796d0-127">.NET Framework 中的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="796d0-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="796d0-128">這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="796d0-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="796d0-129">範例</span><span class="sxs-lookup"><span data-stu-id="796d0-129">Example</span></span>  
 <span data-ttu-id="796d0-130">下列範例示範如何使用`<sharedListeners>`加入接聽程式的項目`console`要`Listeners`兩個集合<xref:System.Diagnostics.TraceSource>和<xref:System.Diagnostics.Trace>類別。</span><span class="sxs-lookup"><span data-stu-id="796d0-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="796d0-131">主控台追蹤接聽項會將追蹤資訊寫入主控台中，透過呼叫其中一個<xref:System.Diagnostics.TraceSource>或<xref:System.Diagnostics.Trace>。</span><span class="sxs-lookup"><span data-stu-id="796d0-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a><span data-ttu-id="796d0-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="796d0-132">See also</span></span>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="796d0-133">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="796d0-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="796d0-134">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="796d0-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
