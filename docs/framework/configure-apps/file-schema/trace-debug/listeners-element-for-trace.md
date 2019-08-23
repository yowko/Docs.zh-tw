---
title: <trace> 的 <listeners> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: e4550d4c4cd9ff37c5937ad366cccf91387c0e3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927012"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="ab934-102">\<追蹤 > 的接聽\<程式 > 元素</span><span class="sxs-lookup"><span data-stu-id="ab934-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="ab934-103">指定收集、儲存及路由傳送訊息的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="ab934-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="ab934-104">接聽程式會將追蹤輸出導向至適當的目標。</span><span class="sxs-lookup"><span data-stu-id="ab934-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="ab934-105">\<configuration > 元素</span><span class="sxs-lookup"><span data-stu-id="ab934-105">\<configuration> Element</span></span>  
<span data-ttu-id="ab934-106">\<> 元素的診斷</span><span class="sxs-lookup"><span data-stu-id="ab934-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="ab934-107">\<追蹤 > 元素</span><span class="sxs-lookup"><span data-stu-id="ab934-107">\<trace> Element</span></span>  
<span data-ttu-id="ab934-108">\<追蹤 > 的接聽\<程式 > 元素</span><span class="sxs-lookup"><span data-stu-id="ab934-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab934-109">語法</span><span class="sxs-lookup"><span data-stu-id="ab934-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab934-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ab934-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ab934-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ab934-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab934-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ab934-112">Attributes</span></span>  
 <span data-ttu-id="ab934-113">無。</span><span class="sxs-lookup"><span data-stu-id="ab934-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab934-114">子元素</span><span class="sxs-lookup"><span data-stu-id="ab934-114">Child Elements</span></span>  
  
|<span data-ttu-id="ab934-115">項目</span><span class="sxs-lookup"><span data-stu-id="ab934-115">Element</span></span>|<span data-ttu-id="ab934-116">描述</span><span class="sxs-lookup"><span data-stu-id="ab934-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab934-117">\<add></span><span class="sxs-lookup"><span data-stu-id="ab934-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="ab934-118">將接聽項新增至 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="ab934-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="ab934-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="ab934-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="ab934-120">清除追蹤的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="ab934-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="ab934-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="ab934-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="ab934-122">從`Listeners`集合中移除接聽程式。</span><span class="sxs-lookup"><span data-stu-id="ab934-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab934-123">父項目</span><span class="sxs-lookup"><span data-stu-id="ab934-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ab934-124">項目</span><span class="sxs-lookup"><span data-stu-id="ab934-124">Element</span></span>|<span data-ttu-id="ab934-125">描述</span><span class="sxs-lookup"><span data-stu-id="ab934-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ab934-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ab934-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ab934-127">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="ab934-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="ab934-128">包含用於收集、儲存及路由傳送追蹤訊息的接聽項。</span><span class="sxs-lookup"><span data-stu-id="ab934-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab934-129">備註</span><span class="sxs-lookup"><span data-stu-id="ab934-129">Remarks</span></span>  
 <span data-ttu-id="ab934-130">和類別會共用相同的接聽程式集合。 <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace></span><span class="sxs-lookup"><span data-stu-id="ab934-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="ab934-131">如果您將接聽程式物件加入其中一個類別中的集合, 另一個類別會使用相同的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="ab934-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="ab934-132">隨附于 .NET Framework 的接聽程式類別衍生自<xref:System.Diagnostics.TraceListener>類別。</span><span class="sxs-lookup"><span data-stu-id="ab934-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ab934-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="ab934-133">Configuration File</span></span>  
 <span data-ttu-id="ab934-134">此元素可用於電腦設定檔 (Machine.config) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="ab934-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab934-135">範例</span><span class="sxs-lookup"><span data-stu-id="ab934-135">Example</span></span>  
 <span data-ttu-id="ab934-136">下列範例示範如何使用 **\<接聽程式>** 加入接聽程式的項目`MyListener`並`MyEventListener`來**接聽程式**集合。</span><span class="sxs-lookup"><span data-stu-id="ab934-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="ab934-137">`MyListener`建立名`MyListener.log`為的檔案, 並將輸出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="ab934-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="ab934-138">`MyEventListener`在事件記錄檔中建立專案。</span><span class="sxs-lookup"><span data-stu-id="ab934-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ab934-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab934-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="ab934-140">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ab934-140">Trace and Debug Settings Schema</span></span>](index.md)
