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
ms.openlocfilehash: a903d009f2056e65414c1792494fbbd20e224413
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088808"
---
# <a name="sources-element"></a><span data-ttu-id="0a182-102">\<來源 > 元素</span><span class="sxs-lookup"><span data-stu-id="0a182-102">\<sources> Element</span></span>
<span data-ttu-id="0a182-103">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="0a182-103">Specifies trace sources that initiate tracing messages.</span></span>  

<span data-ttu-id="0a182-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0a182-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0a182-105">&nbsp;&nbsp;[ **\<系統診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="0a182-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="0a182-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<來源 >**</span><span class="sxs-lookup"><span data-stu-id="0a182-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0a182-107">語法</span><span class="sxs-lookup"><span data-stu-id="0a182-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a182-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0a182-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0a182-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0a182-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a182-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0a182-110">Attributes</span></span>  
 <span data-ttu-id="0a182-111">無。</span><span class="sxs-lookup"><span data-stu-id="0a182-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0a182-112">子項目</span><span class="sxs-lookup"><span data-stu-id="0a182-112">Child Elements</span></span>  
  
|<span data-ttu-id="0a182-113">項目</span><span class="sxs-lookup"><span data-stu-id="0a182-113">Element</span></span>|<span data-ttu-id="0a182-114">描述</span><span class="sxs-lookup"><span data-stu-id="0a182-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a182-115">\<source></span><span class="sxs-lookup"><span data-stu-id="0a182-115">\<source></span></span>](source-element.md)|<span data-ttu-id="0a182-116">必要項目。</span><span class="sxs-lookup"><span data-stu-id="0a182-116">Required element.</span></span><br /><br /> <span data-ttu-id="0a182-117">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="0a182-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a182-118">父項目</span><span class="sxs-lookup"><span data-stu-id="0a182-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0a182-119">項目</span><span class="sxs-lookup"><span data-stu-id="0a182-119">Element</span></span>|<span data-ttu-id="0a182-120">描述</span><span class="sxs-lookup"><span data-stu-id="0a182-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0a182-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0a182-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0a182-122">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="0a182-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a182-123">備註</span><span class="sxs-lookup"><span data-stu-id="0a182-123">Remarks</span></span>  
 <span data-ttu-id="0a182-124">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="0a182-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a182-125">範例</span><span class="sxs-lookup"><span data-stu-id="0a182-125">Example</span></span>  
 <span data-ttu-id="0a182-126">下列範例示範如何使用 `<sources>` 專案來新增追蹤來源 `mySource` 並設定名為 `sourceSwitch`之來源交換器的層級。</span><span class="sxs-lookup"><span data-stu-id="0a182-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="0a182-127">隨即加入主控台追蹤接聽程式，將追蹤資訊寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="0a182-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0a182-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="0a182-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="0a182-129">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0a182-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0a182-130">\<source></span><span class="sxs-lookup"><span data-stu-id="0a182-130">\<source></span></span>](source-element.md)
