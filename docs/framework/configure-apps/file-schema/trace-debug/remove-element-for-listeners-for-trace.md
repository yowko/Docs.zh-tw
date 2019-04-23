---
title: <remove> 項目<listeners>的 <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: adf00394bc0bfe808836e74214003cd2078204e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164251"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="e4eca-102">\<移除 > 項目\<接聽程式 > 針對\<追蹤 ></span><span class="sxs-lookup"><span data-stu-id="e4eca-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="e4eca-103">移除接聽程式從**接聽程式**集合。</span><span class="sxs-lookup"><span data-stu-id="e4eca-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="e4eca-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e4eca-104">\<configuration></span></span>  
<span data-ttu-id="e4eca-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="e4eca-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e4eca-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="e4eca-106">\<trace></span></span>  
<span data-ttu-id="e4eca-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="e4eca-107">\<listeners></span></span>  
<span data-ttu-id="e4eca-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="e4eca-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4eca-109">語法</span><span class="sxs-lookup"><span data-stu-id="e4eca-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4eca-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e4eca-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e4eca-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e4eca-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4eca-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e4eca-112">Attributes</span></span>  
  
|<span data-ttu-id="e4eca-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e4eca-113">Attribute</span></span>|<span data-ttu-id="e4eca-114">描述</span><span class="sxs-lookup"><span data-stu-id="e4eca-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4eca-115">**name**</span><span class="sxs-lookup"><span data-stu-id="e4eca-115">**name**</span></span>|<span data-ttu-id="e4eca-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e4eca-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e4eca-117">若要移除的接聽程式名稱**接聽程式**集合。</span><span class="sxs-lookup"><span data-stu-id="e4eca-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4eca-118">子元素</span><span class="sxs-lookup"><span data-stu-id="e4eca-118">Child Elements</span></span>  
 <span data-ttu-id="e4eca-119">無。</span><span class="sxs-lookup"><span data-stu-id="e4eca-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4eca-120">父項目</span><span class="sxs-lookup"><span data-stu-id="e4eca-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e4eca-121">項目</span><span class="sxs-lookup"><span data-stu-id="e4eca-121">Element</span></span>|<span data-ttu-id="e4eca-122">描述</span><span class="sxs-lookup"><span data-stu-id="e4eca-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e4eca-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e4eca-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="e4eca-124">指定的接聽程式會收集、 存放區，並將訊息路由。</span><span class="sxs-lookup"><span data-stu-id="e4eca-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="e4eca-125">接聽程式將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="e4eca-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e4eca-126">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="e4eca-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="e4eca-127">設定 ASP.NET 追蹤服務。</span><span class="sxs-lookup"><span data-stu-id="e4eca-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4eca-128">備註</span><span class="sxs-lookup"><span data-stu-id="e4eca-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4eca-129">移除<xref:System.Diagnostics.DefaultTraceListener>從`Listeners`集合，改變行為<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>，和<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="e4eca-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e4eca-130">呼叫`Assert`或是`Fail`方法通常會導致顯示訊息方塊中，不過，如果不顯示訊息方塊<xref:System.Diagnostics.DefaultTraceListener>不是處於`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="e4eca-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4eca-131">範例</span><span class="sxs-lookup"><span data-stu-id="e4eca-131">Example</span></span>  
 <span data-ttu-id="e4eca-132">下列範例示範如何從追蹤中移除預設的追蹤接聽項**接聽程式**集合。</span><span class="sxs-lookup"><span data-stu-id="e4eca-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4eca-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4eca-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="e4eca-134">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e4eca-134">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
