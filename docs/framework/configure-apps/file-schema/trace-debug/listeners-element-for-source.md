---
title: <source> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153408"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="10986-102">\<源>的偵\<聽器>元素</span><span class="sxs-lookup"><span data-stu-id="10986-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="10986-103">添加或刪除 集合中的<xref:System.Diagnostics.TraceSource.Listeners%2A>攔截器。 <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="10986-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="10986-104">攔截器將跟蹤輸出定向到適當的目標，如日誌、視窗或文字檔。</span><span class="sxs-lookup"><span data-stu-id="10986-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[<span data-ttu-id="10986-105">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="10986-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="10986-106">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="10986-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="10986-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<來源>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="10986-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="10986-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<源>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="10986-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="10986-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<聽眾>**</span><span class="sxs-lookup"><span data-stu-id="10986-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10986-110">語法</span><span class="sxs-lookup"><span data-stu-id="10986-110">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10986-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="10986-111">Attributes and Elements</span></span>  
 <span data-ttu-id="10986-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="10986-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10986-113">屬性</span><span class="sxs-lookup"><span data-stu-id="10986-113">Attributes</span></span>  
 <span data-ttu-id="10986-114">無。</span><span class="sxs-lookup"><span data-stu-id="10986-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10986-115">子元素</span><span class="sxs-lookup"><span data-stu-id="10986-115">Child Elements</span></span>  
  
|<span data-ttu-id="10986-116">元素</span><span class="sxs-lookup"><span data-stu-id="10986-116">Element</span></span>|<span data-ttu-id="10986-117">描述</span><span class="sxs-lookup"><span data-stu-id="10986-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10986-118">\<添加></span><span class="sxs-lookup"><span data-stu-id="10986-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="10986-119">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="10986-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="10986-120">\<刪除></span><span class="sxs-lookup"><span data-stu-id="10986-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="10986-121">從`Listeners`集合中刪除攔截器。</span><span class="sxs-lookup"><span data-stu-id="10986-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="10986-122">\<明確></span><span class="sxs-lookup"><span data-stu-id="10986-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="10986-123">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="10986-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10986-124">父項目</span><span class="sxs-lookup"><span data-stu-id="10986-124">Parent Elements</span></span>  
  
|<span data-ttu-id="10986-125">元素</span><span class="sxs-lookup"><span data-stu-id="10986-125">Element</span></span>|<span data-ttu-id="10986-126">描述</span><span class="sxs-lookup"><span data-stu-id="10986-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="10986-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="10986-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="10986-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="10986-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="10986-129">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="10986-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="10986-130">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="10986-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10986-131">備註</span><span class="sxs-lookup"><span data-stu-id="10986-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="10986-132">組態檔</span><span class="sxs-lookup"><span data-stu-id="10986-132">Configuration File</span></span>  
 <span data-ttu-id="10986-133">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="10986-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10986-134">範例</span><span class="sxs-lookup"><span data-stu-id="10986-134">Example</span></span>  
 <span data-ttu-id="10986-135">下面的示例演示如何使用 元素`<listeners>`向`mySource`源添加主控台跟蹤攔截器並刪除預設跟蹤攔截器。</span><span class="sxs-lookup"><span data-stu-id="10986-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="10986-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10986-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="10986-137">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="10986-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="10986-138">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="10986-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
