---
title: "&lt;新增&gt;元素&lt;參數&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: de1acb37f3236598e9d8a74a188033d18b65ac8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="d54f2-102">&lt;新增&gt;元素&lt;參數&gt;</span><span class="sxs-lookup"><span data-stu-id="d54f2-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="d54f2-103">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="d54f2-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="d54f2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d54f2-104">\<configuration></span></span>  
<span data-ttu-id="d54f2-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d54f2-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d54f2-106">\<參數 ></span><span class="sxs-lookup"><span data-stu-id="d54f2-106">\<switches></span></span>  
<span data-ttu-id="d54f2-107">\<add></span><span class="sxs-lookup"><span data-stu-id="d54f2-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d54f2-108">語法</span><span class="sxs-lookup"><span data-stu-id="d54f2-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d54f2-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d54f2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d54f2-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d54f2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d54f2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d54f2-111">Attributes</span></span>  
  
|<span data-ttu-id="d54f2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d54f2-112">Attribute</span></span>|<span data-ttu-id="d54f2-113">說明</span><span class="sxs-lookup"><span data-stu-id="d54f2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d54f2-114">**name**</span><span class="sxs-lookup"><span data-stu-id="d54f2-114">**name**</span></span>|<span data-ttu-id="d54f2-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d54f2-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="d54f2-116">指定參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d54f2-116">Specifies the name of the switch.</span></span> <span data-ttu-id="d54f2-117">這個屬性的值會對應到*displayName*傳遞至參數的建構函式的參數。</span><span class="sxs-lookup"><span data-stu-id="d54f2-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="d54f2-118">**value**</span><span class="sxs-lookup"><span data-stu-id="d54f2-118">**value**</span></span>|<span data-ttu-id="d54f2-119">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d54f2-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="d54f2-120">指定的交換器層級。</span><span class="sxs-lookup"><span data-stu-id="d54f2-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d54f2-121">子元素</span><span class="sxs-lookup"><span data-stu-id="d54f2-121">Child Elements</span></span>  
 <span data-ttu-id="d54f2-122">無。</span><span class="sxs-lookup"><span data-stu-id="d54f2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d54f2-123">父項目</span><span class="sxs-lookup"><span data-stu-id="d54f2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d54f2-124">項目</span><span class="sxs-lookup"><span data-stu-id="d54f2-124">Element</span></span>|<span data-ttu-id="d54f2-125">描述</span><span class="sxs-lookup"><span data-stu-id="d54f2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d54f2-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d54f2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="d54f2-127">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="d54f2-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d54f2-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="d54f2-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d54f2-129">備註</span><span class="sxs-lookup"><span data-stu-id="d54f2-129">Remarks</span></span>  
 <span data-ttu-id="d54f2-130">您可以變更的層級的追蹤參數，以將它放置在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="d54f2-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="d54f2-131">如果已切換<xref:System.Diagnostics.BooleanSwitch>，您可以開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="d54f2-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="d54f2-132">如果已切換<xref:System.Diagnostics.TraceSwitch>、 您可以指派不同層級，以便指定類型的追蹤或偵錯訊息的應用程式輸出。</span><span class="sxs-lookup"><span data-stu-id="d54f2-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d54f2-133">範例</span><span class="sxs-lookup"><span data-stu-id="d54f2-133">Example</span></span>  
 <span data-ttu-id="d54f2-134">下列範例示範如何使用**\<新增 >**項目來設定`General`追蹤參數<xref:System.Diagnostics.TraceLevel>層級，並且啟用`Data`布林追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="d54f2-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d54f2-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d54f2-135">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="d54f2-136">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d54f2-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
