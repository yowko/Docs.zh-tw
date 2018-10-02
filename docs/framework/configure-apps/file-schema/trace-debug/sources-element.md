---
title: '&lt;來源&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a9c5c5529e349eca2ba089ed6fb71da4bd48430a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033242"
---
# <a name="ltsourcesgt-element"></a><span data-ttu-id="7ed18-102">&lt;來源&gt;項目</span><span class="sxs-lookup"><span data-stu-id="7ed18-102">&lt;sources&gt; Element</span></span>
<span data-ttu-id="7ed18-103">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="7ed18-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="7ed18-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7ed18-104">\<configuration></span></span>  
<span data-ttu-id="7ed18-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="7ed18-105">\<system.diagnostics></span></span>  
<span data-ttu-id="7ed18-106">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="7ed18-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ed18-107">語法</span><span class="sxs-lookup"><span data-stu-id="7ed18-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ed18-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7ed18-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7ed18-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7ed18-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ed18-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7ed18-110">Attributes</span></span>  
 <span data-ttu-id="7ed18-111">無。</span><span class="sxs-lookup"><span data-stu-id="7ed18-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7ed18-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7ed18-112">Child Elements</span></span>  
  
|<span data-ttu-id="7ed18-113">項目</span><span class="sxs-lookup"><span data-stu-id="7ed18-113">Element</span></span>|<span data-ttu-id="7ed18-114">描述</span><span class="sxs-lookup"><span data-stu-id="7ed18-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ed18-115">\<source></span><span class="sxs-lookup"><span data-stu-id="7ed18-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="7ed18-116">必要項目。</span><span class="sxs-lookup"><span data-stu-id="7ed18-116">Required element.</span></span><br /><br /> <span data-ttu-id="7ed18-117">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="7ed18-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ed18-118">父項目</span><span class="sxs-lookup"><span data-stu-id="7ed18-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7ed18-119">項目</span><span class="sxs-lookup"><span data-stu-id="7ed18-119">Element</span></span>|<span data-ttu-id="7ed18-120">描述</span><span class="sxs-lookup"><span data-stu-id="7ed18-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7ed18-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="7ed18-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7ed18-122">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="7ed18-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ed18-123">備註</span><span class="sxs-lookup"><span data-stu-id="7ed18-123">Remarks</span></span>  
 <span data-ttu-id="7ed18-124">這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="7ed18-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ed18-125">範例</span><span class="sxs-lookup"><span data-stu-id="7ed18-125">Example</span></span>  
 <span data-ttu-id="7ed18-126">下列範例示範如何使用`<sources>`要加入追蹤來源項目`mySource`]，將來源交換器層級設定為 [ `sourceSwitch`。</span><span class="sxs-lookup"><span data-stu-id="7ed18-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="7ed18-127">主控台追蹤接聽程式會加入，將追蹤資訊寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="7ed18-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ed18-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed18-128">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 [<span data-ttu-id="7ed18-129">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7ed18-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="7ed18-130">\<source></span><span class="sxs-lookup"><span data-stu-id="7ed18-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
