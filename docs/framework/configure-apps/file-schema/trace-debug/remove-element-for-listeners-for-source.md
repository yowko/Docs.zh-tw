---
title: <remove><listeners>For 的元素<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153331"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="8d904-102">\<remove>\<listeners>For 的元素\<source></span><span class="sxs-lookup"><span data-stu-id="8d904-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="8d904-103">從追蹤來源的 `Listeners` 集合移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="8d904-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="8d904-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d904-104">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d904-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8d904-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8d904-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8d904-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d904-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8d904-107">Attributes</span></span>  
  
|<span data-ttu-id="8d904-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8d904-108">Attribute</span></span>|<span data-ttu-id="8d904-109">描述</span><span class="sxs-lookup"><span data-stu-id="8d904-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="8d904-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="8d904-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="8d904-111">要從集合中移除的接聽程式名稱 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="8d904-111">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d904-112">子元素</span><span class="sxs-lookup"><span data-stu-id="8d904-112">Child Elements</span></span>  
 <span data-ttu-id="8d904-113">無。</span><span class="sxs-lookup"><span data-stu-id="8d904-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d904-114">父項目</span><span class="sxs-lookup"><span data-stu-id="8d904-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8d904-115">元素</span><span class="sxs-lookup"><span data-stu-id="8d904-115">Element</span></span>|<span data-ttu-id="8d904-116">描述</span><span class="sxs-lookup"><span data-stu-id="8d904-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8d904-117">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8d904-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8d904-118">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="8d904-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="8d904-119">包含起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="8d904-119">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="8d904-120">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="8d904-120">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8d904-121">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="8d904-121">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d904-122">備註</span><span class="sxs-lookup"><span data-stu-id="8d904-122">Remarks</span></span>  
 <span data-ttu-id="8d904-123">`<remove>`元素會從追蹤來源的集合中移除指定的接聽 `Listeners` 程式。</span><span class="sxs-lookup"><span data-stu-id="8d904-123">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="8d904-124">您可以在 `Listeners` 實例的屬性上呼叫方法，以程式設計方式從集合中移除追蹤來源的元素 <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> <xref:System.Diagnostics.TraceSource.Listeners%2A> <xref:System.Diagnostics.TraceSource> 。</span><span class="sxs-lookup"><span data-stu-id="8d904-124">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="8d904-125">此元素可用於電腦設定檔（Machine.config）和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="8d904-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d904-126">範例</span><span class="sxs-lookup"><span data-stu-id="8d904-126">Example</span></span>  
 <span data-ttu-id="8d904-127">下列範例示範如何使用專案 `<remove>` ，然後再使用專案 `<add>` ，將接聽 `console` 程式加入至 `Listeners` 追蹤來源的集合 `TraceSourceApp` 。</span><span class="sxs-lookup"><span data-stu-id="8d904-127">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d904-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d904-128">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="8d904-129">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8d904-129">Trace and Debug Settings Schema</span></span>](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="8d904-130">追蹤接聽程式</span><span class="sxs-lookup"><span data-stu-id="8d904-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
