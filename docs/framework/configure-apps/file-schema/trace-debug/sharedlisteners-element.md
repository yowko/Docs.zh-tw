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
ms.openlocfilehash: b419ecf451b79808e545525c7b8761175f390200
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699295"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="3b6df-102">@no__t 0sharedListeners > 元素</span><span class="sxs-lookup"><span data-stu-id="3b6df-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="3b6df-103">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="3b6df-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="3b6df-104">這些接聽程式預設不會接收任何追蹤，而且在執行時間不可能取得這些接聽程式。</span><span class="sxs-lookup"><span data-stu-id="3b6df-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="3b6df-105">識別為共用接聽項的接聽程式可以依名稱新增至來源或追蹤。</span><span class="sxs-lookup"><span data-stu-id="3b6df-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="3b6df-106"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="3b6df-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="3b6df-107">&nbsp; @ no__t-1[ **\<system. 診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b6df-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="3b6df-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<sharedListeners >**</span><span class="sxs-lookup"><span data-stu-id="3b6df-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b6df-109">語法</span><span class="sxs-lookup"><span data-stu-id="3b6df-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b6df-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3b6df-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3b6df-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3b6df-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b6df-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3b6df-112">Attributes</span></span>  
 <span data-ttu-id="3b6df-113">無。</span><span class="sxs-lookup"><span data-stu-id="3b6df-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3b6df-114">子元素</span><span class="sxs-lookup"><span data-stu-id="3b6df-114">Child Elements</span></span>  
  
|<span data-ttu-id="3b6df-115">元素</span><span class="sxs-lookup"><span data-stu-id="3b6df-115">Element</span></span>|<span data-ttu-id="3b6df-116">描述</span><span class="sxs-lookup"><span data-stu-id="3b6df-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b6df-117">\<add></span><span class="sxs-lookup"><span data-stu-id="3b6df-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="3b6df-118">將接聽項新增至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="3b6df-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b6df-119">父項目</span><span class="sxs-lookup"><span data-stu-id="3b6df-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3b6df-120">項目</span><span class="sxs-lookup"><span data-stu-id="3b6df-120">Element</span></span>|<span data-ttu-id="3b6df-121">描述</span><span class="sxs-lookup"><span data-stu-id="3b6df-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="3b6df-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3b6df-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3b6df-123">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="3b6df-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b6df-124">備註</span><span class="sxs-lookup"><span data-stu-id="3b6df-124">Remarks</span></span>  
 <span data-ttu-id="3b6df-125">將接聽程式加入至共用的接聽程式集合並不會使其成為作用中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="3b6df-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="3b6df-126">它仍然必須加入追蹤來源或追蹤中，方法是將它新增至該追蹤專案的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="3b6df-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="3b6df-127">.NET Framework 中的接聽程式類別衍生自 <xref:System.Diagnostics.TraceListener> 類別。</span><span class="sxs-lookup"><span data-stu-id="3b6df-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="3b6df-128">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="3b6df-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b6df-129">範例</span><span class="sxs-lookup"><span data-stu-id="3b6df-129">Example</span></span>  
 <span data-ttu-id="3b6df-130">下列範例顯示如何使用 `<sharedListeners>` 元素，將接聽程式 `console` 新增至 <xref:System.Diagnostics.TraceSource> 和 @no__t 4 類別的 @no__t 2 集合。</span><span class="sxs-lookup"><span data-stu-id="3b6df-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="3b6df-131">主控台追蹤接聽程式會透過對 <xref:System.Diagnostics.TraceSource> 或 <xref:System.Diagnostics.Trace> 的呼叫，將追蹤資訊寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="3b6df-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b6df-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b6df-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="3b6df-133">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3b6df-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3b6df-134">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="3b6df-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
