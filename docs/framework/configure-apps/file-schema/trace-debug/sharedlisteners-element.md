---
title: <sharedListeners> 項目
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
ms.openlocfilehash: 41cabcbce13409b0842cbbd625028b51d32d59d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926975"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="b778a-102">\<s > 元素</span><span class="sxs-lookup"><span data-stu-id="b778a-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="b778a-103">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="b778a-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="b778a-104">這些接聽程式預設不會接收任何追蹤, 而且在執行時間不可能取得這些接聽程式。</span><span class="sxs-lookup"><span data-stu-id="b778a-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="b778a-105">識別為共用接聽項的接聽程式可以依名稱新增至來源或追蹤。</span><span class="sxs-lookup"><span data-stu-id="b778a-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
 <span data-ttu-id="b778a-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b778a-106">\<configuration></span></span>  
<span data-ttu-id="b778a-107">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="b778a-107">\<system.diagnostics></span></span>  
<span data-ttu-id="b778a-108">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="b778a-108">\<sharedListeners></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b778a-109">語法</span><span class="sxs-lookup"><span data-stu-id="b778a-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b778a-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b778a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b778a-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b778a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b778a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b778a-112">Attributes</span></span>  
 <span data-ttu-id="b778a-113">無。</span><span class="sxs-lookup"><span data-stu-id="b778a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b778a-114">子元素</span><span class="sxs-lookup"><span data-stu-id="b778a-114">Child Elements</span></span>  
  
|<span data-ttu-id="b778a-115">項目</span><span class="sxs-lookup"><span data-stu-id="b778a-115">Element</span></span>|<span data-ttu-id="b778a-116">描述</span><span class="sxs-lookup"><span data-stu-id="b778a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b778a-117">\<add></span><span class="sxs-lookup"><span data-stu-id="b778a-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="b778a-118">將接聽項新增至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="b778a-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b778a-119">父項目</span><span class="sxs-lookup"><span data-stu-id="b778a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b778a-120">項目</span><span class="sxs-lookup"><span data-stu-id="b778a-120">Element</span></span>|<span data-ttu-id="b778a-121">說明</span><span class="sxs-lookup"><span data-stu-id="b778a-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="b778a-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="b778a-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b778a-123">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="b778a-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b778a-124">備註</span><span class="sxs-lookup"><span data-stu-id="b778a-124">Remarks</span></span>  
 <span data-ttu-id="b778a-125">將接聽程式加入至共用的接聽程式集合並不會使其成為作用中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="b778a-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="b778a-126">它仍然必須加入追蹤來源或追蹤中, 方法是將它新增至該`Listeners`追蹤元素的集合。</span><span class="sxs-lookup"><span data-stu-id="b778a-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="b778a-127">.NET Framework 中的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="b778a-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="b778a-128">此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="b778a-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b778a-129">範例</span><span class="sxs-lookup"><span data-stu-id="b778a-129">Example</span></span>  
 <span data-ttu-id="b778a-130">下列範例顯示如何`<sharedListeners>`使用專案, 將接聽程式<xref:System.Diagnostics.TraceSource>新增`console`至`Listeners`和<xref:System.Diagnostics.Trace>類別的集合。</span><span class="sxs-lookup"><span data-stu-id="b778a-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="b778a-131">主控台追蹤接聽程式會透過呼叫<xref:System.Diagnostics.TraceSource>或<xref:System.Diagnostics.Trace>, 將追蹤資訊寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="b778a-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="b778a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b778a-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="b778a-133">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b778a-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b778a-134">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="b778a-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
