---
title: 適用于 <listeners> 的 <remove> 元素 <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 75db45d4e868ce88e030ec6a43c8bdaf788a1102
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088858"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="9a78c-102">\<移除 \<來源的 \<接聽程式 > 元素 > ></span><span class="sxs-lookup"><span data-stu-id="9a78c-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="9a78c-103">從追蹤來源的 `Listeners` 集合移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="9a78c-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="9a78c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9a78c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9a78c-105">&nbsp;&nbsp;[ **\<系統診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="9a78c-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="9a78c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<來源**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="9a78c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="9a78c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**來源 >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="9a78c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="9a78c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](listeners-element-for-source.md)接聽程式 ></span><span class="sxs-lookup"><span data-stu-id="9a78c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="9a78c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="9a78c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9a78c-110">語法</span><span class="sxs-lookup"><span data-stu-id="9a78c-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a78c-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9a78c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9a78c-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9a78c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a78c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9a78c-113">Attributes</span></span>  
  
|<span data-ttu-id="9a78c-114">屬性</span><span class="sxs-lookup"><span data-stu-id="9a78c-114">Attribute</span></span>|<span data-ttu-id="9a78c-115">描述</span><span class="sxs-lookup"><span data-stu-id="9a78c-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="9a78c-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="9a78c-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="9a78c-117">要從 `Listeners` 集合中移除的接聽程式名稱。</span><span class="sxs-lookup"><span data-stu-id="9a78c-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a78c-118">子項目</span><span class="sxs-lookup"><span data-stu-id="9a78c-118">Child Elements</span></span>  
 <span data-ttu-id="9a78c-119">無。</span><span class="sxs-lookup"><span data-stu-id="9a78c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a78c-120">父項目</span><span class="sxs-lookup"><span data-stu-id="9a78c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9a78c-121">項目</span><span class="sxs-lookup"><span data-stu-id="9a78c-121">Element</span></span>|<span data-ttu-id="9a78c-122">描述</span><span class="sxs-lookup"><span data-stu-id="9a78c-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9a78c-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="9a78c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9a78c-124">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="9a78c-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="9a78c-125">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="9a78c-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="9a78c-126">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="9a78c-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="9a78c-127">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="9a78c-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a78c-128">備註</span><span class="sxs-lookup"><span data-stu-id="9a78c-128">Remarks</span></span>  
 <span data-ttu-id="9a78c-129">`<remove>` 元素會從追蹤來源的 `Listeners` 集合中移除指定的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="9a78c-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="9a78c-130">您可以藉由在 <xref:System.Diagnostics.TraceSource> 實例的 <xref:System.Diagnostics.TraceSource.Listeners%2A> 屬性上呼叫 <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> 方法，以程式設計方式從追蹤來源的 `Listeners` 集合中移除元素。</span><span class="sxs-lookup"><span data-stu-id="9a78c-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="9a78c-131">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="9a78c-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a78c-132">範例</span><span class="sxs-lookup"><span data-stu-id="9a78c-132">Example</span></span>  
 <span data-ttu-id="9a78c-133">下列範例示範如何使用 `<remove>` 專案，然後再使用 `<add>` 元素，將接聽程式 `console` 加入至追蹤來源 `TraceSourceApp`的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="9a78c-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="9a78c-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="9a78c-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="9a78c-135">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="9a78c-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9a78c-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="9a78c-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="9a78c-137">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="9a78c-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
