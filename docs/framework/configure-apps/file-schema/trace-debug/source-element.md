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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153291"
---
# <a name="source-element"></a><span data-ttu-id="929b2-102">\<source> 項目</span><span class="sxs-lookup"><span data-stu-id="929b2-102">\<source> Element</span></span>
<span data-ttu-id="929b2-103">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="929b2-103">Specifies a trace source that initiates tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a><span data-ttu-id="929b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="929b2-104">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="929b2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="929b2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="929b2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="929b2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="929b2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="929b2-107">Attributes</span></span>  
  
|<span data-ttu-id="929b2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="929b2-108">Attribute</span></span>|<span data-ttu-id="929b2-109">描述</span><span class="sxs-lookup"><span data-stu-id="929b2-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="929b2-110">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="929b2-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="929b2-111">指定追蹤來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="929b2-111">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="929b2-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="929b2-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="929b2-113">指定應用程式中追蹤參數實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="929b2-113">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="929b2-114">如果在專案中找不到參數 `<switches>` ，則值會指定參數的層級。</span><span class="sxs-lookup"><span data-stu-id="929b2-114">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="929b2-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="929b2-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="929b2-116">指定追蹤參數的類型。</span><span class="sxs-lookup"><span data-stu-id="929b2-116">Specifies the type of the trace switch.</span></span> <span data-ttu-id="929b2-117">如果存在的話，類型必須是有效的類別名稱，而且不能是空字串。</span><span class="sxs-lookup"><span data-stu-id="929b2-117">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="929b2-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="929b2-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="929b2-119">針對該追蹤來源的方法所識別的追蹤來源特定屬性，指定其值 <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> 。</span><span class="sxs-lookup"><span data-stu-id="929b2-119">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="929b2-120">子元素</span><span class="sxs-lookup"><span data-stu-id="929b2-120">Child Elements</span></span>  
  
|<span data-ttu-id="929b2-121">元素</span><span class="sxs-lookup"><span data-stu-id="929b2-121">Element</span></span>|<span data-ttu-id="929b2-122">描述</span><span class="sxs-lookup"><span data-stu-id="929b2-122">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="929b2-123">包含收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="929b2-123">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="929b2-124">父項目</span><span class="sxs-lookup"><span data-stu-id="929b2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="929b2-125">元素</span><span class="sxs-lookup"><span data-stu-id="929b2-125">Element</span></span>|<span data-ttu-id="929b2-126">描述</span><span class="sxs-lookup"><span data-stu-id="929b2-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="929b2-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="929b2-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="929b2-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="929b2-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="929b2-129">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="929b2-129">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="929b2-130">備註</span><span class="sxs-lookup"><span data-stu-id="929b2-130">Remarks</span></span>  
 <span data-ttu-id="929b2-131">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="929b2-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="929b2-132">範例</span><span class="sxs-lookup"><span data-stu-id="929b2-132">Example</span></span>  
 <span data-ttu-id="929b2-133">下列範例顯示如何使用專案 `<source>` 來新增追蹤來源 `mySource` ，以及設定名為之來源交換器的層級 `sourceSwitch` 。</span><span class="sxs-lookup"><span data-stu-id="929b2-133">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="929b2-134">隨即加入主控台追蹤接聽程式，將追蹤資訊寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="929b2-134">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="929b2-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="929b2-135">See also</span></span>

- [<span data-ttu-id="929b2-136">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="929b2-136">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="929b2-137">追蹤參數</span><span class="sxs-lookup"><span data-stu-id="929b2-137">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
