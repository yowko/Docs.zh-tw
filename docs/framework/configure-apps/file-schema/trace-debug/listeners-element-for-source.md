---
title: <source> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 853bc94978218fd4d426e6070b3a36e20435cd6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920498"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="6bd57-102">\<來源 > 的\<接聽項 > 元素</span><span class="sxs-lookup"><span data-stu-id="6bd57-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="6bd57-103">在的<xref:System.Diagnostics.TraceSource.Listeners%2A>集合中加入或移除接聽<xref:System.Diagnostics.TraceSource>程式。</span><span class="sxs-lookup"><span data-stu-id="6bd57-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="6bd57-104">接聽程式會將追蹤輸出導向至適當的目標, 例如記錄檔、視窗或文字檔。</span><span class="sxs-lookup"><span data-stu-id="6bd57-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="6bd57-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6bd57-105">\<configuration></span></span>  
<span data-ttu-id="6bd57-106">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="6bd57-106">\<system.diagnostics></span></span>  
<span data-ttu-id="6bd57-107">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="6bd57-107">\<sources></span></span>  
<span data-ttu-id="6bd57-108">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="6bd57-108">\<source></span></span>  
<span data-ttu-id="6bd57-109">\<> 元素的接聽程式</span><span class="sxs-lookup"><span data-stu-id="6bd57-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bd57-110">語法</span><span class="sxs-lookup"><span data-stu-id="6bd57-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bd57-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6bd57-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6bd57-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6bd57-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bd57-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6bd57-113">Attributes</span></span>  
 <span data-ttu-id="6bd57-114">無。</span><span class="sxs-lookup"><span data-stu-id="6bd57-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6bd57-115">子元素</span><span class="sxs-lookup"><span data-stu-id="6bd57-115">Child Elements</span></span>  
  
|<span data-ttu-id="6bd57-116">項目</span><span class="sxs-lookup"><span data-stu-id="6bd57-116">Element</span></span>|<span data-ttu-id="6bd57-117">說明</span><span class="sxs-lookup"><span data-stu-id="6bd57-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6bd57-118">\<add></span><span class="sxs-lookup"><span data-stu-id="6bd57-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="6bd57-119">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="6bd57-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="6bd57-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="6bd57-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="6bd57-121">從`Listeners`集合中移除接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6bd57-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="6bd57-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="6bd57-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="6bd57-123">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="6bd57-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6bd57-124">父項目</span><span class="sxs-lookup"><span data-stu-id="6bd57-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6bd57-125">項目</span><span class="sxs-lookup"><span data-stu-id="6bd57-125">Element</span></span>|<span data-ttu-id="6bd57-126">說明</span><span class="sxs-lookup"><span data-stu-id="6bd57-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6bd57-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6bd57-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6bd57-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="6bd57-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="6bd57-129">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="6bd57-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="6bd57-130">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="6bd57-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bd57-131">備註</span><span class="sxs-lookup"><span data-stu-id="6bd57-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6bd57-132">組態檔</span><span class="sxs-lookup"><span data-stu-id="6bd57-132">Configuration File</span></span>  
 <span data-ttu-id="6bd57-133">此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="6bd57-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bd57-134">範例</span><span class="sxs-lookup"><span data-stu-id="6bd57-134">Example</span></span>  
 <span data-ttu-id="6bd57-135">下列範例顯示如何使用`<listeners>`專案, 將主控台追蹤接聽程式加入`mySource`至來源, 並移除預設的追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6bd57-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6bd57-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bd57-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="6bd57-137">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6bd57-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6bd57-138">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="6bd57-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
