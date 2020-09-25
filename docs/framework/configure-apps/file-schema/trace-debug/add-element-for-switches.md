---
title: <switches> 的 <add> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 5be39425363cb6d2a0eca6a0fa3f4154ce857bb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173935"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="4ca79-102">\<switches> 的 \<add> 項目</span><span class="sxs-lookup"><span data-stu-id="4ca79-102">\<add> Element for \<switches></span></span>

<span data-ttu-id="4ca79-103">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4ca79-103">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="4ca79-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4ca79-104">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ca79-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4ca79-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4ca79-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4ca79-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ca79-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4ca79-107">Attributes</span></span>  
  
|<span data-ttu-id="4ca79-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4ca79-108">Attribute</span></span>|<span data-ttu-id="4ca79-109">描述</span><span class="sxs-lookup"><span data-stu-id="4ca79-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ca79-110">**name**</span><span class="sxs-lookup"><span data-stu-id="4ca79-110">**name**</span></span>|<span data-ttu-id="4ca79-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="4ca79-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="4ca79-112">指定參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ca79-112">Specifies the name of the switch.</span></span> <span data-ttu-id="4ca79-113">這個屬性的值會對應至傳遞給 switch 函式的 *displayName* 參數。</span><span class="sxs-lookup"><span data-stu-id="4ca79-113">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="4ca79-114">**value**</span><span class="sxs-lookup"><span data-stu-id="4ca79-114">**value**</span></span>|<span data-ttu-id="4ca79-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="4ca79-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="4ca79-116">指定切換的層級。</span><span class="sxs-lookup"><span data-stu-id="4ca79-116">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ca79-117">子元素</span><span class="sxs-lookup"><span data-stu-id="4ca79-117">Child Elements</span></span>  

 <span data-ttu-id="4ca79-118">無。</span><span class="sxs-lookup"><span data-stu-id="4ca79-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ca79-119">父項目</span><span class="sxs-lookup"><span data-stu-id="4ca79-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4ca79-120">項目</span><span class="sxs-lookup"><span data-stu-id="4ca79-120">Element</span></span>|<span data-ttu-id="4ca79-121">描述</span><span class="sxs-lookup"><span data-stu-id="4ca79-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4ca79-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4ca79-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="4ca79-123">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4ca79-123">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4ca79-124">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4ca79-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ca79-125">備註</span><span class="sxs-lookup"><span data-stu-id="4ca79-125">Remarks</span></span>  

 <span data-ttu-id="4ca79-126">您可以藉由將追蹤參數放在設定檔中，來變更其層級。</span><span class="sxs-lookup"><span data-stu-id="4ca79-126">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="4ca79-127">如果參數為 <xref:System.Diagnostics.BooleanSwitch> ，您可以開啟或關閉它。</span><span class="sxs-lookup"><span data-stu-id="4ca79-127">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="4ca79-128">如果參數為 <xref:System.Diagnostics.TraceSwitch> ，您可以指派不同的層級給它，以指定應用程式所輸出的追蹤或偵錯工具訊息的類型。</span><span class="sxs-lookup"><span data-stu-id="4ca79-128">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ca79-129">範例</span><span class="sxs-lookup"><span data-stu-id="4ca79-129">Example</span></span>  

 <span data-ttu-id="4ca79-130">下列範例示範如何使用專案 **\<add>** 將 `General` 追蹤參數設定為 <xref:System.Diagnostics.TraceLevel> 層級，並啟用 `Data` 布林值追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="4ca79-130">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ca79-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ca79-131">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="4ca79-132">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4ca79-132">Trace and Debug Settings Schema</span></span>](index.md)
