---
title: 適用于 <trace> <listeners> 的 <remove> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 56d1e56514aed98d5f3b9f7363e461af6ac68a8c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697223"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="c6618-102">\<trace 的 \<listeners > 的 @no__t 0remove > 元素 ></span><span class="sxs-lookup"><span data-stu-id="c6618-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="c6618-103">從接聽**項集合中**移除接聽程式。</span><span class="sxs-lookup"><span data-stu-id="c6618-103">Removes a listener from the **Listeners** collection.</span></span>  
  
[<span data-ttu-id="c6618-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="c6618-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c6618-105">&nbsp; @ no__t-1[ **\<system. 診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6618-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="c6618-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6618-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="c6618-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="c6618-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="c6618-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="c6618-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6618-109">語法</span><span class="sxs-lookup"><span data-stu-id="c6618-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6618-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c6618-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c6618-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c6618-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6618-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c6618-112">Attributes</span></span>  
  
|<span data-ttu-id="c6618-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c6618-113">Attribute</span></span>|<span data-ttu-id="c6618-114">描述</span><span class="sxs-lookup"><span data-stu-id="c6618-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6618-115">**name**</span><span class="sxs-lookup"><span data-stu-id="c6618-115">**name**</span></span>|<span data-ttu-id="c6618-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c6618-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c6618-117">要從接聽**項集合中**移除的接聽程式名稱。</span><span class="sxs-lookup"><span data-stu-id="c6618-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6618-118">子元素</span><span class="sxs-lookup"><span data-stu-id="c6618-118">Child Elements</span></span>  
 <span data-ttu-id="c6618-119">無。</span><span class="sxs-lookup"><span data-stu-id="c6618-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6618-120">父項目</span><span class="sxs-lookup"><span data-stu-id="c6618-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c6618-121">項目</span><span class="sxs-lookup"><span data-stu-id="c6618-121">Element</span></span>|<span data-ttu-id="c6618-122">描述</span><span class="sxs-lookup"><span data-stu-id="c6618-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c6618-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c6618-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="c6618-124">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="c6618-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="c6618-125">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="c6618-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c6618-126">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="c6618-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="c6618-127">設定 ASP.NET 追蹤服務。</span><span class="sxs-lookup"><span data-stu-id="c6618-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6618-128">備註</span><span class="sxs-lookup"><span data-stu-id="c6618-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6618-129">從 @no__t 1 集合中移除 <xref:System.Diagnostics.DefaultTraceListener>，會改變 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>、<xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>、<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> 和 @no__t 5 方法的行為。</span><span class="sxs-lookup"><span data-stu-id="c6618-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="c6618-130">呼叫 `Assert` 或 @no__t 1 方法通常會導致訊息方塊顯示，但如果 <xref:System.Diagnostics.DefaultTraceListener> 不在 `Listeners` 集合中，則不會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="c6618-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6618-131">範例</span><span class="sxs-lookup"><span data-stu-id="c6618-131">Example</span></span>  
 <span data-ttu-id="c6618-132">下列範例顯示如何從追蹤接聽項集合中移除預設**的追蹤接聽**程式。</span><span class="sxs-lookup"><span data-stu-id="c6618-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6618-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6618-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="c6618-134">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c6618-134">Trace and Debug Settings Schema</span></span>](index.md)
