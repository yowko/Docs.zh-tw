---
title: <switches> 的 <add> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: d7500620aed1165ff365fee8529230ba252dbc4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120090"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="4104e-102">\<新增 > 項目\<參數 ></span><span class="sxs-lookup"><span data-stu-id="4104e-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="4104e-103">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4104e-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="4104e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4104e-104">\<configuration></span></span>  
<span data-ttu-id="4104e-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="4104e-105">\<system.diagnostics></span></span>  
<span data-ttu-id="4104e-106">\<switches></span><span class="sxs-lookup"><span data-stu-id="4104e-106">\<switches></span></span>  
<span data-ttu-id="4104e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="4104e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4104e-108">語法</span><span class="sxs-lookup"><span data-stu-id="4104e-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4104e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4104e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4104e-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4104e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4104e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4104e-111">Attributes</span></span>  
  
|<span data-ttu-id="4104e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4104e-112">Attribute</span></span>|<span data-ttu-id="4104e-113">描述</span><span class="sxs-lookup"><span data-stu-id="4104e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4104e-114">**name**</span><span class="sxs-lookup"><span data-stu-id="4104e-114">**name**</span></span>|<span data-ttu-id="4104e-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="4104e-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="4104e-116">指定參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="4104e-116">Specifies the name of the switch.</span></span> <span data-ttu-id="4104e-117">此屬性的值會對應到*displayName*傳遞至參數的建構函式的參數。</span><span class="sxs-lookup"><span data-stu-id="4104e-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="4104e-118">**value**</span><span class="sxs-lookup"><span data-stu-id="4104e-118">**value**</span></span>|<span data-ttu-id="4104e-119">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="4104e-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="4104e-120">指定的交換器層級。</span><span class="sxs-lookup"><span data-stu-id="4104e-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4104e-121">子元素</span><span class="sxs-lookup"><span data-stu-id="4104e-121">Child Elements</span></span>  
 <span data-ttu-id="4104e-122">無。</span><span class="sxs-lookup"><span data-stu-id="4104e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4104e-123">父項目</span><span class="sxs-lookup"><span data-stu-id="4104e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4104e-124">項目</span><span class="sxs-lookup"><span data-stu-id="4104e-124">Element</span></span>|<span data-ttu-id="4104e-125">描述</span><span class="sxs-lookup"><span data-stu-id="4104e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4104e-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4104e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="4104e-127">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4104e-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4104e-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4104e-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4104e-129">備註</span><span class="sxs-lookup"><span data-stu-id="4104e-129">Remarks</span></span>  
 <span data-ttu-id="4104e-130">您可以將它放在組態檔中，以變更追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4104e-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="4104e-131">如果參數為<xref:System.Diagnostics.BooleanSwitch>，可以先開啟和關閉。</span><span class="sxs-lookup"><span data-stu-id="4104e-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="4104e-132">如果參數為<xref:System.Diagnostics.TraceSwitch>，您可以將不同層級指派，以便指定類型的追蹤或偵錯訊息的應用程式輸出。</span><span class="sxs-lookup"><span data-stu-id="4104e-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4104e-133">範例</span><span class="sxs-lookup"><span data-stu-id="4104e-133">Example</span></span>  
 <span data-ttu-id="4104e-134">下列範例示範如何使用**\<新增 >** 要設定項目`General`追蹤參數設<xref:System.Diagnostics.TraceLevel>層級，並且啟用`Data`布林追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="4104e-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4104e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4104e-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="4104e-136">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4104e-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
