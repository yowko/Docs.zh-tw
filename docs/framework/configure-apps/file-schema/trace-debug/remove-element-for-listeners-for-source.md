---
title: <remove>用於<listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153331"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="fab2a-102">\<刪除>源\<>的偵聽\<器>元素</span><span class="sxs-lookup"><span data-stu-id="fab2a-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="fab2a-103">從追蹤來源的 `Listeners` 集合移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="fab2a-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="fab2a-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fab2a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fab2a-105">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="fab2a-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="fab2a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<來源>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="fab2a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="fab2a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<源>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="fab2a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="fab2a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<聽眾>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="fab2a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="fab2a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<刪除>**</span><span class="sxs-lookup"><span data-stu-id="fab2a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fab2a-110">語法</span><span class="sxs-lookup"><span data-stu-id="fab2a-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fab2a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fab2a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fab2a-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fab2a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fab2a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fab2a-113">Attributes</span></span>  
  
|<span data-ttu-id="fab2a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="fab2a-114">Attribute</span></span>|<span data-ttu-id="fab2a-115">描述</span><span class="sxs-lookup"><span data-stu-id="fab2a-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="fab2a-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="fab2a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="fab2a-117">要從`Listeners`集合中刪除的攔截器的名稱。</span><span class="sxs-lookup"><span data-stu-id="fab2a-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fab2a-118">子元素</span><span class="sxs-lookup"><span data-stu-id="fab2a-118">Child Elements</span></span>  
 <span data-ttu-id="fab2a-119">無。</span><span class="sxs-lookup"><span data-stu-id="fab2a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fab2a-120">父項目</span><span class="sxs-lookup"><span data-stu-id="fab2a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fab2a-121">元素</span><span class="sxs-lookup"><span data-stu-id="fab2a-121">Element</span></span>|<span data-ttu-id="fab2a-122">描述</span><span class="sxs-lookup"><span data-stu-id="fab2a-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fab2a-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="fab2a-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fab2a-124">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="fab2a-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="fab2a-125">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="fab2a-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="fab2a-126">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="fab2a-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="fab2a-127">指定收集、存儲和路由消息的攔截器。</span><span class="sxs-lookup"><span data-stu-id="fab2a-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fab2a-128">備註</span><span class="sxs-lookup"><span data-stu-id="fab2a-128">Remarks</span></span>  
 <span data-ttu-id="fab2a-129">該`<remove>`元素從跟蹤源的集合中刪除`Listeners`指定的攔截器。</span><span class="sxs-lookup"><span data-stu-id="fab2a-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="fab2a-130">`Listeners`您可以通過調用<xref:System.Diagnostics.TraceListenerCollection.Remove%2A><xref:System.Diagnostics.TraceSource>實例<xref:System.Diagnostics.TraceSource.Listeners%2A>屬性上的方法，以程式設計方式從跟蹤源的集合中刪除元素。</span><span class="sxs-lookup"><span data-stu-id="fab2a-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="fab2a-131">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="fab2a-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fab2a-132">範例</span><span class="sxs-lookup"><span data-stu-id="fab2a-132">Example</span></span>  
 <span data-ttu-id="fab2a-133">下面的`<remove>`示例演示如何在使用`<add>`元素將攔截器`console`添加到跟蹤源`Listeners``TraceSourceApp`的集合之前使用 元素。</span><span class="sxs-lookup"><span data-stu-id="fab2a-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fab2a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fab2a-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="fab2a-135">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="fab2a-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fab2a-136">\<明確></span><span class="sxs-lookup"><span data-stu-id="fab2a-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="fab2a-137">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="fab2a-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
