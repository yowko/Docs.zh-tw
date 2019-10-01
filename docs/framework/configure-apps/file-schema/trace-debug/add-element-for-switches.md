---
title: <switches> 的 <add> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 2edc890049d62913d693ad61d8d814d012c0f482
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697186"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="df64d-102">\<switches 的 @no__t 0add > 元素 ></span><span class="sxs-lookup"><span data-stu-id="df64d-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="df64d-103">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="df64d-103">Specifies the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="df64d-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="df64d-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="df64d-105">&nbsp; @ no__t-1[ **\<system. 診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="df64d-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="df64d-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<switches >** ](switches-element.md)</span><span class="sxs-lookup"><span data-stu-id="df64d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)</span></span>  
<span data-ttu-id="df64d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="df64d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df64d-108">語法</span><span class="sxs-lookup"><span data-stu-id="df64d-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df64d-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="df64d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="df64d-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="df64d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df64d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="df64d-111">Attributes</span></span>  
  
|<span data-ttu-id="df64d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="df64d-112">Attribute</span></span>|<span data-ttu-id="df64d-113">描述</span><span class="sxs-lookup"><span data-stu-id="df64d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df64d-114">**name**</span><span class="sxs-lookup"><span data-stu-id="df64d-114">**name**</span></span>|<span data-ttu-id="df64d-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="df64d-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="df64d-116">指定參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="df64d-116">Specifies the name of the switch.</span></span> <span data-ttu-id="df64d-117">這個屬性的值會對應至傳遞給 switch 函數的*displayName*參數。</span><span class="sxs-lookup"><span data-stu-id="df64d-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="df64d-118">**value**</span><span class="sxs-lookup"><span data-stu-id="df64d-118">**value**</span></span>|<span data-ttu-id="df64d-119">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="df64d-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="df64d-120">指定參數的層級。</span><span class="sxs-lookup"><span data-stu-id="df64d-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df64d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="df64d-121">Child Elements</span></span>  
 <span data-ttu-id="df64d-122">無。</span><span class="sxs-lookup"><span data-stu-id="df64d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df64d-123">父項目</span><span class="sxs-lookup"><span data-stu-id="df64d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="df64d-124">項目</span><span class="sxs-lookup"><span data-stu-id="df64d-124">Element</span></span>|<span data-ttu-id="df64d-125">描述</span><span class="sxs-lookup"><span data-stu-id="df64d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="df64d-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="df64d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="df64d-127">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="df64d-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="df64d-128">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="df64d-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df64d-129">備註</span><span class="sxs-lookup"><span data-stu-id="df64d-129">Remarks</span></span>  
 <span data-ttu-id="df64d-130">您可以變更追蹤參數的層級，方法是將它放在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="df64d-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="df64d-131">如果參數為 <xref:System.Diagnostics.BooleanSwitch>，您可以開啟或關閉它。</span><span class="sxs-lookup"><span data-stu-id="df64d-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="df64d-132">如果參數為 <xref:System.Diagnostics.TraceSwitch>，您可以為其指派不同的層級，以指定應用程式輸出的追蹤或 debug 訊息的類型。</span><span class="sxs-lookup"><span data-stu-id="df64d-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df64d-133">範例</span><span class="sxs-lookup"><span data-stu-id="df64d-133">Example</span></span>  
 <span data-ttu-id="df64d-134">下列範例示範如何使用 **\<新增>** 要設定項目`General`追蹤參數設<xref:System.Diagnostics.TraceLevel>層級，並且啟用`Data`布林追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="df64d-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df64d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df64d-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="df64d-136">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="df64d-136">Trace and Debug Settings Schema</span></span>](index.md)
