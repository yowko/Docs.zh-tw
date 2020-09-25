---
title: <trace> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 59d078f8dc573a1ce949d225f497dd4500fe808f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173857"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="c125a-102">\<trace> 的 \<listeners> 項目</span><span class="sxs-lookup"><span data-stu-id="c125a-102">\<listeners> Element for \<trace></span></span>

<span data-ttu-id="c125a-103">指定收集、儲存和路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="c125a-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="c125a-104">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="c125a-104">Listeners direct the tracing output to an appropriate target.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**

## <a name="syntax"></a><span data-ttu-id="c125a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c125a-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c125a-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c125a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c125a-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c125a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c125a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c125a-108">Attributes</span></span>  

 <span data-ttu-id="c125a-109">無。</span><span class="sxs-lookup"><span data-stu-id="c125a-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c125a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c125a-110">Child Elements</span></span>  
  
|<span data-ttu-id="c125a-111">項目</span><span class="sxs-lookup"><span data-stu-id="c125a-111">Element</span></span>|<span data-ttu-id="c125a-112">描述</span><span class="sxs-lookup"><span data-stu-id="c125a-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="c125a-113">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="c125a-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="c125a-114">清除追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="c125a-114">Clears the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="c125a-115">從集合中移除接聽程式 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="c125a-115">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c125a-116">父項目</span><span class="sxs-lookup"><span data-stu-id="c125a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c125a-117">項目</span><span class="sxs-lookup"><span data-stu-id="c125a-117">Element</span></span>|<span data-ttu-id="c125a-118">描述</span><span class="sxs-lookup"><span data-stu-id="c125a-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c125a-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c125a-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c125a-120">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="c125a-120">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="c125a-121">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="c125a-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c125a-122">備註</span><span class="sxs-lookup"><span data-stu-id="c125a-122">Remarks</span></span>  

 <span data-ttu-id="c125a-123"><xref:System.Diagnostics.Debug>和 <xref:System.Diagnostics.Trace> 類別共用相同的接聽**Listeners**程式集合。</span><span class="sxs-lookup"><span data-stu-id="c125a-123">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="c125a-124">如果您在其中一個類別中將接聽程式物件加入至集合，另一個類別會使用相同的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="c125a-124">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="c125a-125">隨附于 .NET Framework 的接聽程式類別衍生自 <xref:System.Diagnostics.TraceListener> 類別。</span><span class="sxs-lookup"><span data-stu-id="c125a-125">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="c125a-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="c125a-126">Configuration File</span></span>  

 <span data-ttu-id="c125a-127">此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="c125a-127">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c125a-128">範例</span><span class="sxs-lookup"><span data-stu-id="c125a-128">Example</span></span>  

 <span data-ttu-id="c125a-129">下列範例示範如何使用專案將接聽程式和接聽程式集合加入至接聽程式 **\<listeners>** `MyListener` `MyEventListener` 。 **Listeners**</span><span class="sxs-lookup"><span data-stu-id="c125a-129">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="c125a-130">`MyListener` 建立名為的檔案 `MyListener.log` ，並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="c125a-130">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="c125a-131">`MyEventListener` 在事件記錄檔中建立專案。</span><span class="sxs-lookup"><span data-stu-id="c125a-131">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c125a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c125a-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="c125a-133">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c125a-133">Trace and Debug Settings Schema</span></span>](index.md)
