---
title: <source> 項目
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153291"
---
# <a name="source-element"></a><span data-ttu-id="4a28e-102">\<源>元素</span><span class="sxs-lookup"><span data-stu-id="4a28e-102">\<source> Element</span></span>
<span data-ttu-id="4a28e-103">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="4a28e-103">Specifies a trace source that initiates tracing messages.</span></span>  

<span data-ttu-id="4a28e-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4a28e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4a28e-105">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="4a28e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="4a28e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<來源>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="4a28e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="4a28e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<源>**</span><span class="sxs-lookup"><span data-stu-id="4a28e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4a28e-108">語法</span><span class="sxs-lookup"><span data-stu-id="4a28e-108">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a28e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4a28e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4a28e-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4a28e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a28e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4a28e-111">Attributes</span></span>  
  
|<span data-ttu-id="4a28e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4a28e-112">Attribute</span></span>|<span data-ttu-id="4a28e-113">描述</span><span class="sxs-lookup"><span data-stu-id="4a28e-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="4a28e-114">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="4a28e-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4a28e-115">指定跟蹤源的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a28e-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="4a28e-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="4a28e-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4a28e-117">指定應用程式中跟蹤開關實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a28e-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="4a28e-118">如果在`<switches>`元素中未標識交換器，則值指定交換器的級別。</span><span class="sxs-lookup"><span data-stu-id="4a28e-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="4a28e-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="4a28e-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4a28e-120">指定跟蹤開關的類型。</span><span class="sxs-lookup"><span data-stu-id="4a28e-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="4a28e-121">如果存在，則類型必須是有效的類名稱，不能為空字串。</span><span class="sxs-lookup"><span data-stu-id="4a28e-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="4a28e-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="4a28e-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4a28e-123">指定由該跟蹤源的方法標識的<xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A>特定于跟蹤源的屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4a28e-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a28e-124">子元素</span><span class="sxs-lookup"><span data-stu-id="4a28e-124">Child Elements</span></span>  
  
|<span data-ttu-id="4a28e-125">元素</span><span class="sxs-lookup"><span data-stu-id="4a28e-125">Element</span></span>|<span data-ttu-id="4a28e-126">描述</span><span class="sxs-lookup"><span data-stu-id="4a28e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a28e-127">\<聽眾></span><span class="sxs-lookup"><span data-stu-id="4a28e-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="4a28e-128">包含收集、存儲和路由消息的攔截器。</span><span class="sxs-lookup"><span data-stu-id="4a28e-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a28e-129">父項目</span><span class="sxs-lookup"><span data-stu-id="4a28e-129">Parent Elements</span></span>  
  
|<span data-ttu-id="4a28e-130">元素</span><span class="sxs-lookup"><span data-stu-id="4a28e-130">Element</span></span>|<span data-ttu-id="4a28e-131">描述</span><span class="sxs-lookup"><span data-stu-id="4a28e-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4a28e-132">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4a28e-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4a28e-133">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4a28e-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="4a28e-134">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="4a28e-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a28e-135">備註</span><span class="sxs-lookup"><span data-stu-id="4a28e-135">Remarks</span></span>  
 <span data-ttu-id="4a28e-136">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="4a28e-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a28e-137">範例</span><span class="sxs-lookup"><span data-stu-id="4a28e-137">Example</span></span>  
 <span data-ttu-id="4a28e-138">下面的示例演示如何使用 元素`<source>`添加跟蹤源`mySource`，並為名為 的`sourceSwitch`源交換器設置級別。</span><span class="sxs-lookup"><span data-stu-id="4a28e-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="4a28e-139">添加了將跟蹤資訊寫入主控台的主控台跟蹤攔截器。</span><span class="sxs-lookup"><span data-stu-id="4a28e-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
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
  
## <a name="see-also"></a><span data-ttu-id="4a28e-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a28e-140">See also</span></span>

- [<span data-ttu-id="4a28e-141">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="4a28e-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4a28e-142">追蹤參數</span><span class="sxs-lookup"><span data-stu-id="4a28e-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
