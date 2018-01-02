---
title: "&lt;交換器&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 64cf3ba9e5529c4a46b2d5365931a47ad2ab211a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltswitchesgt-element"></a><span data-ttu-id="e8464-102">&lt;交換器&gt;項目</span><span class="sxs-lookup"><span data-stu-id="e8464-102">&lt;switches&gt; Element</span></span>
<span data-ttu-id="e8464-103">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="e8464-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="e8464-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e8464-104">\<configuration></span></span>  
<span data-ttu-id="e8464-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e8464-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e8464-106">\<參數 ></span><span class="sxs-lookup"><span data-stu-id="e8464-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8464-107">語法</span><span class="sxs-lookup"><span data-stu-id="e8464-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8464-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e8464-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e8464-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e8464-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8464-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e8464-110">Attributes</span></span>  
 <span data-ttu-id="e8464-111">無。</span><span class="sxs-lookup"><span data-stu-id="e8464-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e8464-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e8464-112">Child Elements</span></span>  
  
|<span data-ttu-id="e8464-113">項目</span><span class="sxs-lookup"><span data-stu-id="e8464-113">Element</span></span>|<span data-ttu-id="e8464-114">描述</span><span class="sxs-lookup"><span data-stu-id="e8464-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8464-115">\<add></span><span class="sxs-lookup"><span data-stu-id="e8464-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="e8464-116">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="e8464-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8464-117">父項目</span><span class="sxs-lookup"><span data-stu-id="e8464-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e8464-118">項目</span><span class="sxs-lookup"><span data-stu-id="e8464-118">Element</span></span>|<span data-ttu-id="e8464-119">描述</span><span class="sxs-lookup"><span data-stu-id="e8464-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e8464-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e8464-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="e8464-121">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="e8464-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8464-122">備註</span><span class="sxs-lookup"><span data-stu-id="e8464-122">Remarks</span></span>  
 <span data-ttu-id="e8464-123">您可以變更的層級的追蹤參數，以將它放置在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="e8464-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="e8464-124">如果已切換<xref:System.Diagnostics.BooleanSwitch>，您可以開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="e8464-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="e8464-125">如果已切換<xref:System.Diagnostics.TraceSwitch>、 您可以指派不同層級，以便指定類型的追蹤或偵錯訊息的應用程式輸出。</span><span class="sxs-lookup"><span data-stu-id="e8464-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8464-126">範例</span><span class="sxs-lookup"><span data-stu-id="e8464-126">Example</span></span>  
 <span data-ttu-id="e8464-127">下列範例示範如何使用**\<切換 >**項目來設定`General`追蹤參數<xref:System.Diagnostics.TraceLevel>層級，並且啟用`Data`布林追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="e8464-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e8464-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8464-128">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="e8464-129">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e8464-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
