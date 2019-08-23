---
title: <remove><listeners> For 的元素<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 0c5c9efb8a22d26ea5d4467f9628af5935d6dbad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920480"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="61c95-102">\<移除\<追蹤 > 之\<接聽程式 > 的 > 元素</span><span class="sxs-lookup"><span data-stu-id="61c95-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="61c95-103">從接聽項集合中移除接聽程式。</span><span class="sxs-lookup"><span data-stu-id="61c95-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="61c95-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="61c95-104">\<configuration></span></span>  
<span data-ttu-id="61c95-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="61c95-105">\<system.diagnostics></span></span>  
<span data-ttu-id="61c95-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="61c95-106">\<trace></span></span>  
<span data-ttu-id="61c95-107">\<接聽程式 ></span><span class="sxs-lookup"><span data-stu-id="61c95-107">\<listeners></span></span>  
<span data-ttu-id="61c95-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="61c95-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61c95-109">語法</span><span class="sxs-lookup"><span data-stu-id="61c95-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61c95-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="61c95-110">Attributes and Elements</span></span>  
 <span data-ttu-id="61c95-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="61c95-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61c95-112">屬性</span><span class="sxs-lookup"><span data-stu-id="61c95-112">Attributes</span></span>  
  
|<span data-ttu-id="61c95-113">屬性</span><span class="sxs-lookup"><span data-stu-id="61c95-113">Attribute</span></span>|<span data-ttu-id="61c95-114">描述</span><span class="sxs-lookup"><span data-stu-id="61c95-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61c95-115">**name**</span><span class="sxs-lookup"><span data-stu-id="61c95-115">**name**</span></span>|<span data-ttu-id="61c95-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="61c95-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="61c95-117">要從接聽項集合中移除的接聽程式名稱。</span><span class="sxs-lookup"><span data-stu-id="61c95-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61c95-118">子元素</span><span class="sxs-lookup"><span data-stu-id="61c95-118">Child Elements</span></span>  
 <span data-ttu-id="61c95-119">無。</span><span class="sxs-lookup"><span data-stu-id="61c95-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61c95-120">父項目</span><span class="sxs-lookup"><span data-stu-id="61c95-120">Parent Elements</span></span>  
  
|<span data-ttu-id="61c95-121">項目</span><span class="sxs-lookup"><span data-stu-id="61c95-121">Element</span></span>|<span data-ttu-id="61c95-122">描述</span><span class="sxs-lookup"><span data-stu-id="61c95-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="61c95-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="61c95-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="61c95-124">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="61c95-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="61c95-125">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="61c95-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="61c95-126">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="61c95-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="61c95-127">設定 ASP.NET 追蹤服務。</span><span class="sxs-lookup"><span data-stu-id="61c95-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61c95-128">備註</span><span class="sxs-lookup"><span data-stu-id="61c95-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61c95-129"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>從集合中移除, 會改變、、和<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>方法的行為。 `Listeners` <xref:System.Diagnostics.DefaultTraceListener></span><span class="sxs-lookup"><span data-stu-id="61c95-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="61c95-130"><xref:System.Diagnostics.DefaultTraceListener> `Listeners`呼叫或方法`Fail`通常會導致訊息方塊顯示, 但如果不在集合中, 則不會顯示訊息方塊。 `Assert`</span><span class="sxs-lookup"><span data-stu-id="61c95-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61c95-131">範例</span><span class="sxs-lookup"><span data-stu-id="61c95-131">Example</span></span>  
 <span data-ttu-id="61c95-132">下列範例顯示如何從追蹤接聽項集合中移除預設的追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="61c95-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="61c95-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61c95-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="61c95-134">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="61c95-134">Trace and Debug Settings Schema</span></span>](index.md)
