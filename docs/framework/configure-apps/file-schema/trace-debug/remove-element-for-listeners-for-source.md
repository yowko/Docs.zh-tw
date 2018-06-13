---
title: '&lt;移除&gt;元素&lt;接聽程式&gt;如&lt;來源&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cc6772e7a9b98f09df21fd1acf24f578b66ae51e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754271"
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="43c08-102">&lt;移除&gt;元素&lt;接聽程式&gt;如&lt;來源&gt;</span><span class="sxs-lookup"><span data-stu-id="43c08-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="43c08-103">從追蹤來源的 `Listeners` 集合移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="43c08-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="43c08-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="43c08-104">\<configuration></span></span>  
<span data-ttu-id="43c08-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="43c08-105">\<system.diagnostics></span></span>  
<span data-ttu-id="43c08-106">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="43c08-106">\<sources></span></span>  
<span data-ttu-id="43c08-107">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="43c08-107">\<source></span></span>  
<span data-ttu-id="43c08-108">\<接聽項 ></span><span class="sxs-lookup"><span data-stu-id="43c08-108">\<listeners></span></span>  
<span data-ttu-id="43c08-109">\<remove></span><span class="sxs-lookup"><span data-stu-id="43c08-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43c08-110">語法</span><span class="sxs-lookup"><span data-stu-id="43c08-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43c08-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="43c08-111">Attributes and Elements</span></span>  
 <span data-ttu-id="43c08-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="43c08-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43c08-113">屬性</span><span class="sxs-lookup"><span data-stu-id="43c08-113">Attributes</span></span>  
  
|<span data-ttu-id="43c08-114">屬性</span><span class="sxs-lookup"><span data-stu-id="43c08-114">Attribute</span></span>|<span data-ttu-id="43c08-115">描述</span><span class="sxs-lookup"><span data-stu-id="43c08-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="43c08-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="43c08-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="43c08-117">要移除的接聽程式名稱`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="43c08-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43c08-118">子項目</span><span class="sxs-lookup"><span data-stu-id="43c08-118">Child Elements</span></span>  
 <span data-ttu-id="43c08-119">無。</span><span class="sxs-lookup"><span data-stu-id="43c08-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43c08-120">父項目</span><span class="sxs-lookup"><span data-stu-id="43c08-120">Parent Elements</span></span>  
  
|<span data-ttu-id="43c08-121">項目</span><span class="sxs-lookup"><span data-stu-id="43c08-121">Element</span></span>|<span data-ttu-id="43c08-122">描述</span><span class="sxs-lookup"><span data-stu-id="43c08-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43c08-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="43c08-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="43c08-124">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="43c08-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="43c08-125">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="43c08-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="43c08-126">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="43c08-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="43c08-127">指定接聽程式以收集、 儲存和路由傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="43c08-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43c08-128">備註</span><span class="sxs-lookup"><span data-stu-id="43c08-128">Remarks</span></span>  
 <span data-ttu-id="43c08-129">`<remove>`項目會移除指定的接聽程式從`Listeners`追蹤來源的集合。</span><span class="sxs-lookup"><span data-stu-id="43c08-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="43c08-130">您可以移除的項目從`Listeners`集合以程式設計方式呼叫的追蹤來源<xref:System.Diagnostics.TraceListenerCollection.Remove%2A>方法<xref:System.Diagnostics.TraceSource.Listeners%2A>屬性<xref:System.Diagnostics.TraceSource>執行個體。</span><span class="sxs-lookup"><span data-stu-id="43c08-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="43c08-131">此項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="43c08-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43c08-132">範例</span><span class="sxs-lookup"><span data-stu-id="43c08-132">Example</span></span>  
 <span data-ttu-id="43c08-133">下列範例示範如何使用`<remove>`之前使用的項目`<add>`加入接聽程式的項目`console`至`Listeners`追蹤來源的集合`TraceSourceApp`。</span><span class="sxs-lookup"><span data-stu-id="43c08-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43c08-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43c08-134">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="43c08-135">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="43c08-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="43c08-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="43c08-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)  
 [<span data-ttu-id="43c08-137">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="43c08-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
