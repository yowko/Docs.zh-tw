---
title: <remove><listeners> For 的元素<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: edd27dd262004aead7db4d81db8ecab0e831dac1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926998"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="068aa-102">\<為來源 > 的\< \<接聽程式 > 移除 > 元素</span><span class="sxs-lookup"><span data-stu-id="068aa-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="068aa-103">從追蹤來源的 `Listeners` 集合移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="068aa-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="068aa-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="068aa-104">\<configuration></span></span>  
<span data-ttu-id="068aa-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="068aa-105">\<system.diagnostics></span></span>  
<span data-ttu-id="068aa-106">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="068aa-106">\<sources></span></span>  
<span data-ttu-id="068aa-107">\<來源 ></span><span class="sxs-lookup"><span data-stu-id="068aa-107">\<source></span></span>  
<span data-ttu-id="068aa-108">\<接聽程式 ></span><span class="sxs-lookup"><span data-stu-id="068aa-108">\<listeners></span></span>  
<span data-ttu-id="068aa-109">\<remove></span><span class="sxs-lookup"><span data-stu-id="068aa-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="068aa-110">語法</span><span class="sxs-lookup"><span data-stu-id="068aa-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="068aa-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="068aa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="068aa-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="068aa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="068aa-113">屬性</span><span class="sxs-lookup"><span data-stu-id="068aa-113">Attributes</span></span>  
  
|<span data-ttu-id="068aa-114">屬性</span><span class="sxs-lookup"><span data-stu-id="068aa-114">Attribute</span></span>|<span data-ttu-id="068aa-115">說明</span><span class="sxs-lookup"><span data-stu-id="068aa-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="068aa-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="068aa-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="068aa-117">要從`Listeners`集合中移除的接聽程式名稱。</span><span class="sxs-lookup"><span data-stu-id="068aa-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="068aa-118">子元素</span><span class="sxs-lookup"><span data-stu-id="068aa-118">Child Elements</span></span>  
 <span data-ttu-id="068aa-119">無。</span><span class="sxs-lookup"><span data-stu-id="068aa-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="068aa-120">父項目</span><span class="sxs-lookup"><span data-stu-id="068aa-120">Parent Elements</span></span>  
  
|<span data-ttu-id="068aa-121">項目</span><span class="sxs-lookup"><span data-stu-id="068aa-121">Element</span></span>|<span data-ttu-id="068aa-122">描述</span><span class="sxs-lookup"><span data-stu-id="068aa-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="068aa-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="068aa-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="068aa-124">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="068aa-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="068aa-125">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="068aa-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="068aa-126">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="068aa-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="068aa-127">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="068aa-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="068aa-128">備註</span><span class="sxs-lookup"><span data-stu-id="068aa-128">Remarks</span></span>  
 <span data-ttu-id="068aa-129">元素會從追蹤來源的`Listeners`集合中移除指定的接聽程式。 `<remove>`</span><span class="sxs-lookup"><span data-stu-id="068aa-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="068aa-130">您`Listeners`可以在<xref:System.Diagnostics.TraceListenerCollection.Remove%2A> 實例<xref:System.Diagnostics.TraceSource>的<xref:System.Diagnostics.TraceSource.Listeners%2A>屬性上呼叫方法, 以程式設計方式從集合中移除追蹤來源的元素。</span><span class="sxs-lookup"><span data-stu-id="068aa-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="068aa-131">此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="068aa-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="068aa-132">範例</span><span class="sxs-lookup"><span data-stu-id="068aa-132">Example</span></span>  
 <span data-ttu-id="068aa-133">下列範例示範如何使用`<remove>`專案, 然後再`<add>`使用專案, 將接聽程式加入`console`至追蹤來源`Listeners` `TraceSourceApp`的集合。</span><span class="sxs-lookup"><span data-stu-id="068aa-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="068aa-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="068aa-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="068aa-135">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="068aa-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="068aa-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="068aa-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="068aa-137">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="068aa-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
