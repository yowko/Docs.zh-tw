---
title: <clear><listeners>For 的元素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153538"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="bc9e9-102">\<clear>\<listeners>For 的元素\<trace></span><span class="sxs-lookup"><span data-stu-id="bc9e9-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="bc9e9-103">清除追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-103">Clears the `Listeners` collection for trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="bc9e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc9e9-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc9e9-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc9e9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bc9e9-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc9e9-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bc9e9-107">Attributes</span></span>  
 <span data-ttu-id="bc9e9-108">無。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bc9e9-109">子元素</span><span class="sxs-lookup"><span data-stu-id="bc9e9-109">Child Elements</span></span>  
 <span data-ttu-id="bc9e9-110">無。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc9e9-111">父項目</span><span class="sxs-lookup"><span data-stu-id="bc9e9-111">Parent Elements</span></span>  
  
|<span data-ttu-id="bc9e9-112">元素</span><span class="sxs-lookup"><span data-stu-id="bc9e9-112">Element</span></span>|<span data-ttu-id="bc9e9-113">描述</span><span class="sxs-lookup"><span data-stu-id="bc9e9-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bc9e9-114">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bc9e9-115">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="bc9e9-116">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-116">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="bc9e9-117">包含收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-117">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="bc9e9-118">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-118">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc9e9-119">備註</span><span class="sxs-lookup"><span data-stu-id="bc9e9-119">Remarks</span></span>  
 <span data-ttu-id="bc9e9-120">`<clear>`元素會從追蹤的集合中移除所有接聽 `Listeners` 程式。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-120">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="bc9e9-121">在使用專案之前，您可以使用專案 `<clear>` `<add>` ，以確保集合中沒有其他作用中的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="bc9e9-122">您可以 `Listeners` <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> 在屬性上呼叫方法（），以程式設計方式清除集合 <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> `System.Diagnostics.Trace.Listeners.Clear()` 。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-122">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="bc9e9-123">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc9e9-124">`<clear>`元素會從集合中移除， <xref:System.Diagnostics.DefaultTraceListener> `Listeners` <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 並改變、、 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> 方法的行為。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-124">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="bc9e9-125">呼叫 `Assert` 或 `Fail` 方法通常會導致顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-125">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="bc9e9-126">不過，如果不在集合中，則不會顯示訊息方塊 <xref:System.Diagnostics.DefaultTraceListener> `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-126">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc9e9-127">範例</span><span class="sxs-lookup"><span data-stu-id="bc9e9-127">Example</span></span>  
 <span data-ttu-id="bc9e9-128">下列範例示範如何使用專案 `<clear>` ，然後再使用專案 `<add>` ，將接聽 `console` 程式加入至追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="bc9e9-128">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc9e9-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc9e9-129">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="bc9e9-130">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bc9e9-130">Trace and Debug Settings Schema</span></span>](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="bc9e9-131">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="bc9e9-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
