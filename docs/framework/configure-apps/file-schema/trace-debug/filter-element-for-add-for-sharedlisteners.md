---
title: <filter>的元素 <add><sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: e140148a342e31d6ade7def8849d8a7738301704
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173922"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="01f28-102">\<filter>的元素 \<add>\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="01f28-102">\<filter> Element for \<add> for \<sharedListeners></span></span>

<span data-ttu-id="01f28-103">將篩選新增至 `sharedListeners` 集合中的接聽項。</span><span class="sxs-lookup"><span data-stu-id="01f28-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="01f28-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="01f28-104">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01f28-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="01f28-105">Attributes and Elements</span></span>  

 <span data-ttu-id="01f28-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="01f28-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01f28-107">屬性</span><span class="sxs-lookup"><span data-stu-id="01f28-107">Attributes</span></span>  
  
|<span data-ttu-id="01f28-108">屬性</span><span class="sxs-lookup"><span data-stu-id="01f28-108">Attribute</span></span>|<span data-ttu-id="01f28-109">描述</span><span class="sxs-lookup"><span data-stu-id="01f28-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01f28-110">**type**</span><span class="sxs-lookup"><span data-stu-id="01f28-110">**type**</span></span>|<span data-ttu-id="01f28-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="01f28-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="01f28-112">指定篩選的類型。</span><span class="sxs-lookup"><span data-stu-id="01f28-112">Specifies the type of the filter.</span></span> <span data-ttu-id="01f28-113">您只能使用) 屬性格式 (類型的完整名稱 <xref:System.Type.FullName%2A?displayProperty=nameWithType> ，也可以使用完整的類型名稱，包括元件資訊 (<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>) 的屬性格式。</span><span class="sxs-lookup"><span data-stu-id="01f28-113">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="01f28-114">如需建立完整型別名稱的詳細資訊，請參閱 [指定完整的類型](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)名稱。</span><span class="sxs-lookup"><span data-stu-id="01f28-114">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="01f28-115">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="01f28-115">**initializeData**</span></span>|<span data-ttu-id="01f28-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="01f28-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="01f28-117">傳遞給指定類別之函式的字串。</span><span class="sxs-lookup"><span data-stu-id="01f28-117">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01f28-118">子元素</span><span class="sxs-lookup"><span data-stu-id="01f28-118">Child Elements</span></span>  

 <span data-ttu-id="01f28-119">無。</span><span class="sxs-lookup"><span data-stu-id="01f28-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01f28-120">父項目</span><span class="sxs-lookup"><span data-stu-id="01f28-120">Parent Elements</span></span>  
  
|<span data-ttu-id="01f28-121">項目</span><span class="sxs-lookup"><span data-stu-id="01f28-121">Element</span></span>|<span data-ttu-id="01f28-122">描述</span><span class="sxs-lookup"><span data-stu-id="01f28-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="01f28-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="01f28-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="01f28-124">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="01f28-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="01f28-125">任何來源或追蹤元素可以參考的接聽項集合。</span><span class="sxs-lookup"><span data-stu-id="01f28-125">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="01f28-126">將接聽程式加入至 **sharedListeners** 集合。</span><span class="sxs-lookup"><span data-stu-id="01f28-126">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01f28-127">備註</span><span class="sxs-lookup"><span data-stu-id="01f28-127">Remarks</span></span>  

 <span data-ttu-id="01f28-128">如果在專案的元素中定義接聽程式 `<add>` `<sharedListeners>` ，則應該在專案的子系中定義該接聽程式的篩選準則 `<filter>` `<add>` 。</span><span class="sxs-lookup"><span data-stu-id="01f28-128">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="01f28-129">此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="01f28-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01f28-130">範例</span><span class="sxs-lookup"><span data-stu-id="01f28-130">Example</span></span>  

 <span data-ttu-id="01f28-131">下列範例示範如何使用專案 `<filter>` ，將篩選加入至集合中的追蹤接聽 `console` 項 `sharedListeners` 。</span><span class="sxs-lookup"><span data-stu-id="01f28-131">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="01f28-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01f28-132">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="01f28-133">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="01f28-133">Trace and Debug Settings Schema</span></span>](index.md)
