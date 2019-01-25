---
title: '&lt;新增&gt;項目&lt;參數&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b0ac45c9d2c5b7ff9630bbeaed4bfcee5ec46fcd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609982"
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="ce1a9-102">&lt;新增&gt;項目&lt;參數&gt;</span><span class="sxs-lookup"><span data-stu-id="ce1a9-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="ce1a9-103">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="ce1a9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ce1a9-104">\<configuration></span></span>  
<span data-ttu-id="ce1a9-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="ce1a9-105">\<system.diagnostics></span></span>  
<span data-ttu-id="ce1a9-106">\<switches></span><span class="sxs-lookup"><span data-stu-id="ce1a9-106">\<switches></span></span>  
<span data-ttu-id="ce1a9-107">\<add></span><span class="sxs-lookup"><span data-stu-id="ce1a9-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce1a9-108">語法</span><span class="sxs-lookup"><span data-stu-id="ce1a9-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce1a9-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ce1a9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ce1a9-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce1a9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ce1a9-111">Attributes</span></span>  
  
|<span data-ttu-id="ce1a9-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ce1a9-112">Attribute</span></span>|<span data-ttu-id="ce1a9-113">描述</span><span class="sxs-lookup"><span data-stu-id="ce1a9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce1a9-114">**name**</span><span class="sxs-lookup"><span data-stu-id="ce1a9-114">**name**</span></span>|<span data-ttu-id="ce1a9-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce1a9-116">指定參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-116">Specifies the name of the switch.</span></span> <span data-ttu-id="ce1a9-117">此屬性的值會對應到*displayName*傳遞至參數的建構函式的參數。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="ce1a9-118">**value**</span><span class="sxs-lookup"><span data-stu-id="ce1a9-118">**value**</span></span>|<span data-ttu-id="ce1a9-119">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce1a9-120">指定的交換器層級。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce1a9-121">子元素</span><span class="sxs-lookup"><span data-stu-id="ce1a9-121">Child Elements</span></span>  
 <span data-ttu-id="ce1a9-122">無。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce1a9-123">父項目</span><span class="sxs-lookup"><span data-stu-id="ce1a9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ce1a9-124">項目</span><span class="sxs-lookup"><span data-stu-id="ce1a9-124">Element</span></span>|<span data-ttu-id="ce1a9-125">描述</span><span class="sxs-lookup"><span data-stu-id="ce1a9-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ce1a9-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="ce1a9-127">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ce1a9-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce1a9-129">備註</span><span class="sxs-lookup"><span data-stu-id="ce1a9-129">Remarks</span></span>  
 <span data-ttu-id="ce1a9-130">您可以將它放在組態檔中，以變更追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="ce1a9-131">如果參數為<xref:System.Diagnostics.BooleanSwitch>，可以先開啟和關閉。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="ce1a9-132">如果參數為<xref:System.Diagnostics.TraceSwitch>，您可以將不同層級指派，以便指定類型的追蹤或偵錯訊息的應用程式輸出。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce1a9-133">範例</span><span class="sxs-lookup"><span data-stu-id="ce1a9-133">Example</span></span>  
 <span data-ttu-id="ce1a9-134">下列範例示範如何使用**\<新增 >** 要設定項目`General`追蹤參數設<xref:System.Diagnostics.TraceLevel>層級，並且啟用`Data`布林追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="ce1a9-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce1a9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce1a9-135">See also</span></span>
- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="ce1a9-136">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ce1a9-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
