---
title: <source> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: b7144b0a7004ba32b21cbc98513df574a5a9e1d9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195177"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="bcf20-102">\<source> 的 \<listeners> 項目</span><span class="sxs-lookup"><span data-stu-id="bcf20-102">\<listeners> Element for \<source></span></span>

<span data-ttu-id="bcf20-103">在的集合中加入或移除接聽 <xref:System.Diagnostics.TraceSource.Listeners%2A> 程式 <xref:System.Diagnostics.TraceSource> 。</span><span class="sxs-lookup"><span data-stu-id="bcf20-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="bcf20-104">接聽程式會將追蹤輸出導向至適當的目標，例如記錄檔、視窗或文字檔。</span><span class="sxs-lookup"><span data-stu-id="bcf20-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a><span data-ttu-id="bcf20-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bcf20-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcf20-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bcf20-106">Attributes and Elements</span></span>  

 <span data-ttu-id="bcf20-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bcf20-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcf20-108">屬性</span><span class="sxs-lookup"><span data-stu-id="bcf20-108">Attributes</span></span>  

 <span data-ttu-id="bcf20-109">無。</span><span class="sxs-lookup"><span data-stu-id="bcf20-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bcf20-110">子元素</span><span class="sxs-lookup"><span data-stu-id="bcf20-110">Child Elements</span></span>  
  
|<span data-ttu-id="bcf20-111">項目</span><span class="sxs-lookup"><span data-stu-id="bcf20-111">Element</span></span>|<span data-ttu-id="bcf20-112">描述</span><span class="sxs-lookup"><span data-stu-id="bcf20-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="bcf20-113">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="bcf20-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="bcf20-114">從集合中移除接聽程式 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="bcf20-114">Removes a listener from the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="bcf20-115">清除追蹤來源的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="bcf20-115">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bcf20-116">父項目</span><span class="sxs-lookup"><span data-stu-id="bcf20-116">Parent Elements</span></span>  
  
|<span data-ttu-id="bcf20-117">項目</span><span class="sxs-lookup"><span data-stu-id="bcf20-117">Element</span></span>|<span data-ttu-id="bcf20-118">描述</span><span class="sxs-lookup"><span data-stu-id="bcf20-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bcf20-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bcf20-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bcf20-120">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="bcf20-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="bcf20-121">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="bcf20-121">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="bcf20-122">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="bcf20-122">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcf20-123">備註</span><span class="sxs-lookup"><span data-stu-id="bcf20-123">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="bcf20-124">組態檔</span><span class="sxs-lookup"><span data-stu-id="bcf20-124">Configuration File</span></span>  

 <span data-ttu-id="bcf20-125">此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="bcf20-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcf20-126">範例</span><span class="sxs-lookup"><span data-stu-id="bcf20-126">Example</span></span>  

 <span data-ttu-id="bcf20-127">下列範例示範如何使用專案 `<listeners>` 將主控台追蹤接聽程式加入至 `mySource` 來源，以及移除預設的追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="bcf20-127">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bcf20-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcf20-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="bcf20-129">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bcf20-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bcf20-130">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="bcf20-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
