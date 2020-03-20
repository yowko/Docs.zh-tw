---
title: <clear>用於<listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 7f9ddd93d27c3619119702c82c9e8752dab1af7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153577"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="1f291-102">\<為\<攔截器>\<源>清除>元素</span><span class="sxs-lookup"><span data-stu-id="1f291-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="1f291-103">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="1f291-103">Clears the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="1f291-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f291-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1f291-105">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f291-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="1f291-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<來源>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f291-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="1f291-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<源>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f291-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="1f291-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<聽眾>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="1f291-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="1f291-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<明確>**</span><span class="sxs-lookup"><span data-stu-id="1f291-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1f291-110">語法</span><span class="sxs-lookup"><span data-stu-id="1f291-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f291-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1f291-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1f291-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1f291-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f291-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1f291-113">Attributes</span></span>  
 <span data-ttu-id="1f291-114">無。</span><span class="sxs-lookup"><span data-stu-id="1f291-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1f291-115">子元素</span><span class="sxs-lookup"><span data-stu-id="1f291-115">Child Elements</span></span>  
 <span data-ttu-id="1f291-116">無。</span><span class="sxs-lookup"><span data-stu-id="1f291-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f291-117">父項目</span><span class="sxs-lookup"><span data-stu-id="1f291-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1f291-118">元素</span><span class="sxs-lookup"><span data-stu-id="1f291-118">Element</span></span>|<span data-ttu-id="1f291-119">描述</span><span class="sxs-lookup"><span data-stu-id="1f291-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1f291-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1f291-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1f291-121">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="1f291-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="1f291-122">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="1f291-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="1f291-123">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="1f291-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="1f291-124">指定收集、存儲和路由消息的攔截器。</span><span class="sxs-lookup"><span data-stu-id="1f291-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f291-125">備註</span><span class="sxs-lookup"><span data-stu-id="1f291-125">Remarks</span></span>  
 <span data-ttu-id="1f291-126">該`<clear>`元素從跟蹤源（包括`Listeners`）<xref:System.Diagnostics.DefaultTraceListener>的集合中刪除所有攔截器。</span><span class="sxs-lookup"><span data-stu-id="1f291-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="1f291-127">在使用 元素`<clear>`之前，`<add>`可以使用 該元素來確定集合中沒有其他活動攔截器。</span><span class="sxs-lookup"><span data-stu-id="1f291-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="1f291-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="1f291-128">Configuration File</span></span>  
 <span data-ttu-id="1f291-129">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="1f291-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f291-130">範例</span><span class="sxs-lookup"><span data-stu-id="1f291-130">Example</span></span>  
 <span data-ttu-id="1f291-131">下面的示例演示如何`<clear>`在使用`<add>`元素將攔截器`console`和`textListener`跟蹤源`Listeners``TraceSourceApp`的集合之前使用元素。</span><span class="sxs-lookup"><span data-stu-id="1f291-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="1f291-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f291-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="1f291-133">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="1f291-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1f291-134">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="1f291-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
