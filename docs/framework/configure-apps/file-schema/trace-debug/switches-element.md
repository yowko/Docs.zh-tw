---
title: <switches> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: bdd6efdec1e118075495002509c7367c1162baba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176093"
---
# <a name="switches-element"></a><span data-ttu-id="b856e-102">\<switches> 項目</span><span class="sxs-lookup"><span data-stu-id="b856e-102">\<switches> Element</span></span>

<span data-ttu-id="b856e-103">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="b856e-103">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="b856e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b856e-104">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b856e-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b856e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b856e-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b856e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b856e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="b856e-107">Attributes</span></span>  

 <span data-ttu-id="b856e-108">無。</span><span class="sxs-lookup"><span data-stu-id="b856e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b856e-109">子元素</span><span class="sxs-lookup"><span data-stu-id="b856e-109">Child Elements</span></span>  
  
|<span data-ttu-id="b856e-110">項目</span><span class="sxs-lookup"><span data-stu-id="b856e-110">Element</span></span>|<span data-ttu-id="b856e-111">描述</span><span class="sxs-lookup"><span data-stu-id="b856e-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="b856e-112">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="b856e-112">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b856e-113">父項目</span><span class="sxs-lookup"><span data-stu-id="b856e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b856e-114">項目</span><span class="sxs-lookup"><span data-stu-id="b856e-114">Element</span></span>|<span data-ttu-id="b856e-115">描述</span><span class="sxs-lookup"><span data-stu-id="b856e-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b856e-116">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="b856e-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="b856e-117">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="b856e-117">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b856e-118">備註</span><span class="sxs-lookup"><span data-stu-id="b856e-118">Remarks</span></span>  

 <span data-ttu-id="b856e-119">您可以藉由將追蹤參數放在設定檔中，來變更其層級。</span><span class="sxs-lookup"><span data-stu-id="b856e-119">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="b856e-120">如果參數為 <xref:System.Diagnostics.BooleanSwitch> ，您可以開啟或關閉它。</span><span class="sxs-lookup"><span data-stu-id="b856e-120">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="b856e-121">如果參數為 <xref:System.Diagnostics.TraceSwitch> ，您可以指派不同的層級給它，以指定應用程式所輸出的追蹤或偵錯工具訊息的類型。</span><span class="sxs-lookup"><span data-stu-id="b856e-121">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b856e-122">範例</span><span class="sxs-lookup"><span data-stu-id="b856e-122">Example</span></span>  

 <span data-ttu-id="b856e-123">下列範例示範如何使用專案 **\<switch>** 將 `General` 追蹤參數設定為 <xref:System.Diagnostics.TraceLevel> 層級，並啟用 `Data` 布林值追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="b856e-123">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b856e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b856e-124">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="b856e-125">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b856e-125">Trace and Debug Settings Schema</span></span>](index.md)
