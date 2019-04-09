---
title: <remove> 項目<listeners>的 <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 4809c471deb51e0560b438b5a2c8849daad34ca0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120129"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="cdf04-102">\<移除 > 項目\<接聽程式 > 針對\<來源 ></span><span class="sxs-lookup"><span data-stu-id="cdf04-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="cdf04-103">從追蹤來源的 `Listeners` 集合移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="cdf04-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="cdf04-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="cdf04-104">\<configuration></span></span>  
<span data-ttu-id="cdf04-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="cdf04-105">\<system.diagnostics></span></span>  
<span data-ttu-id="cdf04-106">\<sources></span><span class="sxs-lookup"><span data-stu-id="cdf04-106">\<sources></span></span>  
<span data-ttu-id="cdf04-107">\<source></span><span class="sxs-lookup"><span data-stu-id="cdf04-107">\<source></span></span>  
<span data-ttu-id="cdf04-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="cdf04-108">\<listeners></span></span>  
<span data-ttu-id="cdf04-109">\<remove></span><span class="sxs-lookup"><span data-stu-id="cdf04-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdf04-110">語法</span><span class="sxs-lookup"><span data-stu-id="cdf04-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdf04-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cdf04-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cdf04-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cdf04-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdf04-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cdf04-113">Attributes</span></span>  
  
|<span data-ttu-id="cdf04-114">屬性</span><span class="sxs-lookup"><span data-stu-id="cdf04-114">Attribute</span></span>|<span data-ttu-id="cdf04-115">描述</span><span class="sxs-lookup"><span data-stu-id="cdf04-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="cdf04-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="cdf04-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="cdf04-117">若要移除的接聽程式名稱`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="cdf04-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdf04-118">子元素</span><span class="sxs-lookup"><span data-stu-id="cdf04-118">Child Elements</span></span>  
 <span data-ttu-id="cdf04-119">無。</span><span class="sxs-lookup"><span data-stu-id="cdf04-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cdf04-120">父項目</span><span class="sxs-lookup"><span data-stu-id="cdf04-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cdf04-121">項目</span><span class="sxs-lookup"><span data-stu-id="cdf04-121">Element</span></span>|<span data-ttu-id="cdf04-122">描述</span><span class="sxs-lookup"><span data-stu-id="cdf04-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cdf04-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="cdf04-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cdf04-124">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="cdf04-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="cdf04-125">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="cdf04-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="cdf04-126">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="cdf04-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="cdf04-127">指定用於收集、 儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="cdf04-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdf04-128">備註</span><span class="sxs-lookup"><span data-stu-id="cdf04-128">Remarks</span></span>  
 <span data-ttu-id="cdf04-129">`<remove>`項目移除指定的接聽程式從`Listeners`追蹤來源的集合。</span><span class="sxs-lookup"><span data-stu-id="cdf04-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="cdf04-130">您可以移除的項目`Listeners`追蹤來源，以程式設計的方式是藉由呼叫集合<xref:System.Diagnostics.TraceListenerCollection.Remove%2A>方法<xref:System.Diagnostics.TraceSource.Listeners%2A>屬性<xref:System.Diagnostics.TraceSource>執行個體。</span><span class="sxs-lookup"><span data-stu-id="cdf04-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="cdf04-131">這個項目可以用於電腦組態檔 (Machine.config) 和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="cdf04-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdf04-132">範例</span><span class="sxs-lookup"><span data-stu-id="cdf04-132">Example</span></span>  
 <span data-ttu-id="cdf04-133">下列範例示範如何使用`<remove>`項目之前使用`<add>`加入接聽程式的項目`console`要`Listeners`追蹤來源的集合`TraceSourceApp`。</span><span class="sxs-lookup"><span data-stu-id="cdf04-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cdf04-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdf04-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="cdf04-135">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="cdf04-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="cdf04-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="cdf04-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="cdf04-137">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="cdf04-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
