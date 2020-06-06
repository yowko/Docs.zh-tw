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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153408"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="6107b-102">\<source> 的 \<listeners> 項目</span><span class="sxs-lookup"><span data-stu-id="6107b-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="6107b-103">在的集合中加入或移除接聽 <xref:System.Diagnostics.TraceSource.Listeners%2A> 程式 <xref:System.Diagnostics.TraceSource> 。</span><span class="sxs-lookup"><span data-stu-id="6107b-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="6107b-104">接聽程式會將追蹤輸出導向至適當的目標，例如記錄檔、視窗或文字檔。</span><span class="sxs-lookup"><span data-stu-id="6107b-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a><span data-ttu-id="6107b-105">語法</span><span class="sxs-lookup"><span data-stu-id="6107b-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6107b-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6107b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6107b-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6107b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6107b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6107b-108">Attributes</span></span>  
 <span data-ttu-id="6107b-109">無。</span><span class="sxs-lookup"><span data-stu-id="6107b-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6107b-110">子元素</span><span class="sxs-lookup"><span data-stu-id="6107b-110">Child Elements</span></span>  
  
|<span data-ttu-id="6107b-111">元素</span><span class="sxs-lookup"><span data-stu-id="6107b-111">Element</span></span>|<span data-ttu-id="6107b-112">描述</span><span class="sxs-lookup"><span data-stu-id="6107b-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="6107b-113">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="6107b-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="6107b-114">從集合中移除接聽程式 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="6107b-114">Removes a listener from the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="6107b-115">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="6107b-115">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6107b-116">父項目</span><span class="sxs-lookup"><span data-stu-id="6107b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6107b-117">元素</span><span class="sxs-lookup"><span data-stu-id="6107b-117">Element</span></span>|<span data-ttu-id="6107b-118">描述</span><span class="sxs-lookup"><span data-stu-id="6107b-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6107b-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6107b-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6107b-120">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="6107b-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="6107b-121">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="6107b-121">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="6107b-122">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="6107b-122">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6107b-123">備註</span><span class="sxs-lookup"><span data-stu-id="6107b-123">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6107b-124">組態檔</span><span class="sxs-lookup"><span data-stu-id="6107b-124">Configuration File</span></span>  
 <span data-ttu-id="6107b-125">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="6107b-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6107b-126">範例</span><span class="sxs-lookup"><span data-stu-id="6107b-126">Example</span></span>  
 <span data-ttu-id="6107b-127">下列範例顯示如何使用專案， `<listeners>` 將主控台追蹤接聽程式加入至 `mySource` 來源，並移除預設的追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6107b-127">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6107b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6107b-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="6107b-129">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6107b-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6107b-130">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="6107b-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
