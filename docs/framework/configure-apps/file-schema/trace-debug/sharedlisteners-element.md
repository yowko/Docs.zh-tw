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
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153317"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="70391-102">\<共用攔截器>元素</span><span class="sxs-lookup"><span data-stu-id="70391-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="70391-103">包含任何來源或追蹤項目可參考的接聽項。</span><span class="sxs-lookup"><span data-stu-id="70391-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="70391-104">預設情況下，這些攔截器不會接收任何跟蹤，並且無法在運行時檢索這些攔截器。</span><span class="sxs-lookup"><span data-stu-id="70391-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="70391-105">標識為共用攔截器的攔截器可以按名稱添加到源或跟蹤中。</span><span class="sxs-lookup"><span data-stu-id="70391-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="70391-106">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="70391-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="70391-107">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="70391-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="70391-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<共用攔截器>**</span><span class="sxs-lookup"><span data-stu-id="70391-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70391-109">語法</span><span class="sxs-lookup"><span data-stu-id="70391-109">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70391-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="70391-110">Attributes and Elements</span></span>  
 <span data-ttu-id="70391-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="70391-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70391-112">屬性</span><span class="sxs-lookup"><span data-stu-id="70391-112">Attributes</span></span>  
 <span data-ttu-id="70391-113">無。</span><span class="sxs-lookup"><span data-stu-id="70391-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70391-114">子元素</span><span class="sxs-lookup"><span data-stu-id="70391-114">Child Elements</span></span>  
  
|<span data-ttu-id="70391-115">元素</span><span class="sxs-lookup"><span data-stu-id="70391-115">Element</span></span>|<span data-ttu-id="70391-116">描述</span><span class="sxs-lookup"><span data-stu-id="70391-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70391-117">\<添加></span><span class="sxs-lookup"><span data-stu-id="70391-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="70391-118">將接聽項新增至 `sharedListeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="70391-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70391-119">父項目</span><span class="sxs-lookup"><span data-stu-id="70391-119">Parent Elements</span></span>  
  
|<span data-ttu-id="70391-120">元素</span><span class="sxs-lookup"><span data-stu-id="70391-120">Element</span></span>|<span data-ttu-id="70391-121">描述</span><span class="sxs-lookup"><span data-stu-id="70391-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="70391-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="70391-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="70391-123">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="70391-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70391-124">備註</span><span class="sxs-lookup"><span data-stu-id="70391-124">Remarks</span></span>  
 <span data-ttu-id="70391-125">將攔截器添加到共用攔截器集合不會使其成為活動攔截器。</span><span class="sxs-lookup"><span data-stu-id="70391-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="70391-126">仍必須通過將其添加到該跟蹤元素`Listeners`的集合並將其添加到跟蹤源或跟蹤中。</span><span class="sxs-lookup"><span data-stu-id="70391-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="70391-127">.NET 框架中的攔截器類派生自<xref:System.Diagnostics.TraceListener>類。</span><span class="sxs-lookup"><span data-stu-id="70391-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="70391-128">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="70391-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70391-129">範例</span><span class="sxs-lookup"><span data-stu-id="70391-129">Example</span></span>  
 <span data-ttu-id="70391-130">下面的示例演示如何使用`<sharedListeners>`元素將攔截器`console`添加到 和`Listeners`<xref:System.Diagnostics.TraceSource><xref:System.Diagnostics.Trace>類的集合。</span><span class="sxs-lookup"><span data-stu-id="70391-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="70391-131">主控台跟蹤攔截器通過調用<xref:System.Diagnostics.TraceSource>或<xref:System.Diagnostics.Trace>向 向 主控台寫入跟蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="70391-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70391-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70391-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="70391-133">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="70391-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="70391-134">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="70391-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
