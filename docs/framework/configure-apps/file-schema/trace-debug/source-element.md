---
title: <source> 項目
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: a528e0f77efea6df7379a0f01495bc09d2ed0b24
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254479"
---
# <a name="source-element"></a><span data-ttu-id="11340-102">\<來源 > 項目</span><span class="sxs-lookup"><span data-stu-id="11340-102">\<source> Element</span></span>
<span data-ttu-id="11340-103">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="11340-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="11340-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="11340-104">\<configuration></span></span>  
<span data-ttu-id="11340-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="11340-105">\<system.diagnostics></span></span>  
<span data-ttu-id="11340-106">\<sources></span><span class="sxs-lookup"><span data-stu-id="11340-106">\<sources></span></span>  
<span data-ttu-id="11340-107">\<source></span><span class="sxs-lookup"><span data-stu-id="11340-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11340-108">語法</span><span class="sxs-lookup"><span data-stu-id="11340-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11340-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="11340-109">Attributes and Elements</span></span>  
 <span data-ttu-id="11340-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="11340-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11340-111">屬性</span><span class="sxs-lookup"><span data-stu-id="11340-111">Attributes</span></span>  
  
|<span data-ttu-id="11340-112">屬性</span><span class="sxs-lookup"><span data-stu-id="11340-112">Attribute</span></span>|<span data-ttu-id="11340-113">描述</span><span class="sxs-lookup"><span data-stu-id="11340-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="11340-114">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="11340-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="11340-115">指定追蹤來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="11340-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="11340-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="11340-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="11340-117">應用程式中，指定追蹤交換器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="11340-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="11340-118">如果參數不會識別在`<switches>`項目，值會指定此參數的層級。</span><span class="sxs-lookup"><span data-stu-id="11340-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="11340-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="11340-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="11340-120">指定追蹤參數的類型。</span><span class="sxs-lookup"><span data-stu-id="11340-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="11340-121">如果有的話，類型必須是有效的類別名稱，並不能是空字串。</span><span class="sxs-lookup"><span data-stu-id="11340-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="11340-122">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="11340-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="11340-123">指定追蹤來源特定屬性所識別的值<xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A>該追蹤來源的方法。</span><span class="sxs-lookup"><span data-stu-id="11340-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11340-124">子元素</span><span class="sxs-lookup"><span data-stu-id="11340-124">Child Elements</span></span>  
  
|<span data-ttu-id="11340-125">項目</span><span class="sxs-lookup"><span data-stu-id="11340-125">Element</span></span>|<span data-ttu-id="11340-126">描述</span><span class="sxs-lookup"><span data-stu-id="11340-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11340-127">\<listeners></span><span class="sxs-lookup"><span data-stu-id="11340-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="11340-128">包含用於收集、 儲存及路由傳送訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="11340-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11340-129">父項目</span><span class="sxs-lookup"><span data-stu-id="11340-129">Parent Elements</span></span>  
  
|<span data-ttu-id="11340-130">項目</span><span class="sxs-lookup"><span data-stu-id="11340-130">Element</span></span>|<span data-ttu-id="11340-131">描述</span><span class="sxs-lookup"><span data-stu-id="11340-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="11340-132">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="11340-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="11340-133">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="11340-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="11340-134">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="11340-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11340-135">備註</span><span class="sxs-lookup"><span data-stu-id="11340-135">Remarks</span></span>  
 <span data-ttu-id="11340-136">這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="11340-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11340-137">範例</span><span class="sxs-lookup"><span data-stu-id="11340-137">Example</span></span>  
 <span data-ttu-id="11340-138">下列範例示範如何使用`<source>`要加入追蹤來源項目`mySource`]，將來源交換器層級設定為 [ `sourceSwitch`。</span><span class="sxs-lookup"><span data-stu-id="11340-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="11340-139">主控台追蹤接聽程式會加入，將追蹤資訊寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="11340-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11340-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11340-140">See also</span></span>
- [<span data-ttu-id="11340-141">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="11340-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="11340-142">追蹤參數</span><span class="sxs-lookup"><span data-stu-id="11340-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
