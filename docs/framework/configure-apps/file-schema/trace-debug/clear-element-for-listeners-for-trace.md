---
title: <clear>用於<listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153538"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="9f382-102">\<清除>元素，\<用於>跟蹤\<>的攔截器</span><span class="sxs-lookup"><span data-stu-id="9f382-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="9f382-103">清除追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="9f382-103">Clears the `Listeners` collection for trace.</span></span>  

<span data-ttu-id="9f382-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9f382-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9f382-105">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="9f382-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="9f382-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<跟蹤>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="9f382-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="9f382-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<聽眾>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="9f382-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="9f382-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<明確>**</span><span class="sxs-lookup"><span data-stu-id="9f382-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9f382-109">語法</span><span class="sxs-lookup"><span data-stu-id="9f382-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f382-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9f382-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9f382-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9f382-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f382-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9f382-112">Attributes</span></span>  
 <span data-ttu-id="9f382-113">無。</span><span class="sxs-lookup"><span data-stu-id="9f382-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9f382-114">子元素</span><span class="sxs-lookup"><span data-stu-id="9f382-114">Child Elements</span></span>  
 <span data-ttu-id="9f382-115">無。</span><span class="sxs-lookup"><span data-stu-id="9f382-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f382-116">父項目</span><span class="sxs-lookup"><span data-stu-id="9f382-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9f382-117">元素</span><span class="sxs-lookup"><span data-stu-id="9f382-117">Element</span></span>|<span data-ttu-id="9f382-118">描述</span><span class="sxs-lookup"><span data-stu-id="9f382-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9f382-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="9f382-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9f382-120">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="9f382-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="9f382-121">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="9f382-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="9f382-122">包含收集、存儲和路由消息的攔截器。</span><span class="sxs-lookup"><span data-stu-id="9f382-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="9f382-123">攔截器將跟蹤輸出定向到適當的目標。</span><span class="sxs-lookup"><span data-stu-id="9f382-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f382-124">備註</span><span class="sxs-lookup"><span data-stu-id="9f382-124">Remarks</span></span>  
 <span data-ttu-id="9f382-125">該`<clear>`元素從跟蹤集合中刪除`Listeners`所有攔截器。</span><span class="sxs-lookup"><span data-stu-id="9f382-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="9f382-126">在使用 元素`<clear>`之前，`<add>`可以使用 該元素來確定集合中沒有其他活動攔截器。</span><span class="sxs-lookup"><span data-stu-id="9f382-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="9f382-127">您可以通過`Listeners`在<xref:System.Diagnostics.TraceListenerCollection.Clear%2A><xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>屬性上調用 方法 （）`System.Diagnostics.Trace.Listeners.Clear()`以程式設計方式清除集合。</span><span class="sxs-lookup"><span data-stu-id="9f382-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="9f382-128">此元素可用於電腦設定檔 （Machine.config） 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="9f382-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f382-129">元素`<clear>`從<xref:System.Diagnostics.DefaultTraceListener>`Listeners`集合中刪除 ， 更改<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>、 、<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>和<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>方法的行為。</span><span class="sxs-lookup"><span data-stu-id="9f382-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="9f382-130">調用`Assert`或`Fail`方法通常會導致顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="9f382-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="9f382-131">但是，如果 不在<xref:System.Diagnostics.DefaultTraceListener>`Listeners`集合中，則不會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="9f382-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f382-132">範例</span><span class="sxs-lookup"><span data-stu-id="9f382-132">Example</span></span>  
 <span data-ttu-id="9f382-133">下面的示例`<clear>`演示如何在使用`<add>`元素將攔截器`console`添加到跟蹤`Listeners`集合之前使用元素。</span><span class="sxs-lookup"><span data-stu-id="9f382-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="9f382-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f382-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="9f382-135">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="9f382-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9f382-136">\<刪除></span><span class="sxs-lookup"><span data-stu-id="9f382-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="9f382-137">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="9f382-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
