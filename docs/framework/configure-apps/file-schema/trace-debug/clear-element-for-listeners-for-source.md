---
title: <clear>的元素 <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: d3e76496c82b508feabf8a46cf7bce7e3d54e8cf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149279"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="8b3c8-102">\<clear>的元素 \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="8b3c8-102">\<clear> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="8b3c8-103">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-103">Clears the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="8b3c8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8b3c8-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b3c8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8b3c8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8b3c8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b3c8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8b3c8-107">Attributes</span></span>  

 <span data-ttu-id="8b3c8-108">無。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8b3c8-109">子元素</span><span class="sxs-lookup"><span data-stu-id="8b3c8-109">Child Elements</span></span>  

 <span data-ttu-id="8b3c8-110">無。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b3c8-111">父項目</span><span class="sxs-lookup"><span data-stu-id="8b3c8-111">Parent Elements</span></span>  
  
|<span data-ttu-id="8b3c8-112">項目</span><span class="sxs-lookup"><span data-stu-id="8b3c8-112">Element</span></span>|<span data-ttu-id="8b3c8-113">描述</span><span class="sxs-lookup"><span data-stu-id="8b3c8-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8b3c8-114">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8b3c8-115">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="8b3c8-116">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-116">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="8b3c8-117">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-117">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8b3c8-118">指定收集、儲存和路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-118">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b3c8-119">備註</span><span class="sxs-lookup"><span data-stu-id="8b3c8-119">Remarks</span></span>  

 <span data-ttu-id="8b3c8-120">`<clear>`元素會從集合中移除追蹤來源的所有接聽 `Listeners` 程式，包括 <xref:System.Diagnostics.DefaultTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-120">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="8b3c8-121">您可以使用專案， `<clear>` 然後再使用 `<add>` 元素來確定集合中沒有其他使用中的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="8b3c8-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="8b3c8-122">Configuration File</span></span>  

 <span data-ttu-id="8b3c8-123">此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b3c8-124">範例</span><span class="sxs-lookup"><span data-stu-id="8b3c8-124">Example</span></span>  

 <span data-ttu-id="8b3c8-125">下列範例示範如何使用專案， `<clear>` 再使用專案將接聽 `<add>` `console` `textListener` 程式和追蹤來源的集合加入至 `Listeners` 集合 `TraceSourceApp` 。</span><span class="sxs-lookup"><span data-stu-id="8b3c8-125">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b3c8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b3c8-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="8b3c8-127">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8b3c8-127">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8b3c8-128">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="8b3c8-128">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
