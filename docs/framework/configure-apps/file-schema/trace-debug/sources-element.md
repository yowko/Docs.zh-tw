---
title: <sources> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
ms.openlocfilehash: 2a76816ee73f516b3c7544877a77531acaa8e09c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153265"
---
# <a name="sources-element"></a><span data-ttu-id="71bf7-102">\<源>元素</span><span class="sxs-lookup"><span data-stu-id="71bf7-102">\<sources> Element</span></span>
<span data-ttu-id="71bf7-103">指定啟動跟蹤消息的跟蹤源。</span><span class="sxs-lookup"><span data-stu-id="71bf7-103">Specifies trace sources that initiate tracing messages.</span></span>  

<span data-ttu-id="71bf7-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="71bf7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="71bf7-105">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="71bf7-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="71bf7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<來源>**</span><span class="sxs-lookup"><span data-stu-id="71bf7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**</span></span>

## <a name="syntax"></a><span data-ttu-id="71bf7-107">語法</span><span class="sxs-lookup"><span data-stu-id="71bf7-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71bf7-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="71bf7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="71bf7-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="71bf7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71bf7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="71bf7-110">Attributes</span></span>  
 <span data-ttu-id="71bf7-111">無。</span><span class="sxs-lookup"><span data-stu-id="71bf7-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="71bf7-112">子元素</span><span class="sxs-lookup"><span data-stu-id="71bf7-112">Child Elements</span></span>  
  
|<span data-ttu-id="71bf7-113">元素</span><span class="sxs-lookup"><span data-stu-id="71bf7-113">Element</span></span>|<span data-ttu-id="71bf7-114">描述</span><span class="sxs-lookup"><span data-stu-id="71bf7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71bf7-115">\<源></span><span class="sxs-lookup"><span data-stu-id="71bf7-115">\<source></span></span>](source-element.md)|<span data-ttu-id="71bf7-116">必要元素。</span><span class="sxs-lookup"><span data-stu-id="71bf7-116">Required element.</span></span><br /><br /> <span data-ttu-id="71bf7-117">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="71bf7-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71bf7-118">父項目</span><span class="sxs-lookup"><span data-stu-id="71bf7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="71bf7-119">元素</span><span class="sxs-lookup"><span data-stu-id="71bf7-119">Element</span></span>|<span data-ttu-id="71bf7-120">描述</span><span class="sxs-lookup"><span data-stu-id="71bf7-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="71bf7-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="71bf7-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="71bf7-122">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="71bf7-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71bf7-123">備註</span><span class="sxs-lookup"><span data-stu-id="71bf7-123">Remarks</span></span>  
 <span data-ttu-id="71bf7-124">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="71bf7-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71bf7-125">範例</span><span class="sxs-lookup"><span data-stu-id="71bf7-125">Example</span></span>  
 <span data-ttu-id="71bf7-126">下面的示例演示如何使用 元素`<sources>`添加跟蹤源`mySource`，並為名為 的`sourceSwitch`源交換器設置級別。</span><span class="sxs-lookup"><span data-stu-id="71bf7-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="71bf7-127">添加了將跟蹤資訊寫入主控台的主控台跟蹤攔截器。</span><span class="sxs-lookup"><span data-stu-id="71bf7-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"
                     initializeData="Error" />  
               </add>  
               <remove name="Default" />  
            </listeners>  
         </source>  
      </sources>  
      <switches>  
         <add name="sourceSwitch" value="Warning" />  
      </switches>
   </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71bf7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71bf7-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="71bf7-129">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="71bf7-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="71bf7-130">\<源></span><span class="sxs-lookup"><span data-stu-id="71bf7-130">\<source></span></span>](source-element.md)
