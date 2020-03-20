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
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153226"
---
# <a name="switches-element"></a><span data-ttu-id="a4140-102">\<切換>元素</span><span class="sxs-lookup"><span data-stu-id="a4140-102">\<switches> Element</span></span>
<span data-ttu-id="a4140-103">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="a4140-103">Contains trace switches and the level where the trace switches are set.</span></span>  

<span data-ttu-id="a4140-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4140-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a4140-105">&nbsp;&nbsp;[**\<系統.診斷>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="a4140-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="a4140-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<開關>**</span><span class="sxs-lookup"><span data-stu-id="a4140-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a4140-107">語法</span><span class="sxs-lookup"><span data-stu-id="a4140-107">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4140-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a4140-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a4140-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a4140-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4140-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a4140-110">Attributes</span></span>  
 <span data-ttu-id="a4140-111">無。</span><span class="sxs-lookup"><span data-stu-id="a4140-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a4140-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a4140-112">Child Elements</span></span>  
  
|<span data-ttu-id="a4140-113">元素</span><span class="sxs-lookup"><span data-stu-id="a4140-113">Element</span></span>|<span data-ttu-id="a4140-114">描述</span><span class="sxs-lookup"><span data-stu-id="a4140-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4140-115">\<添加></span><span class="sxs-lookup"><span data-stu-id="a4140-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="a4140-116">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="a4140-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4140-117">父項目</span><span class="sxs-lookup"><span data-stu-id="a4140-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a4140-118">元素</span><span class="sxs-lookup"><span data-stu-id="a4140-118">Element</span></span>|<span data-ttu-id="a4140-119">描述</span><span class="sxs-lookup"><span data-stu-id="a4140-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a4140-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a4140-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="a4140-121">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="a4140-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4140-122">備註</span><span class="sxs-lookup"><span data-stu-id="a4140-122">Remarks</span></span>  
 <span data-ttu-id="a4140-123">通過將跟蹤開關放入設定檔中，可以更改跟蹤開關的級別。</span><span class="sxs-lookup"><span data-stu-id="a4140-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="a4140-124">如果開關為 ，<xref:System.Diagnostics.BooleanSwitch>則可以打開和關閉開關。</span><span class="sxs-lookup"><span data-stu-id="a4140-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="a4140-125">如果交換器為 ，<xref:System.Diagnostics.TraceSwitch>則可以為其分配不同級別以指定應用程式輸出的跟蹤類型或調試消息。</span><span class="sxs-lookup"><span data-stu-id="a4140-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4140-126">範例</span><span class="sxs-lookup"><span data-stu-id="a4140-126">Example</span></span>  
 <span data-ttu-id="a4140-127">下面的示例演示如何使用**\<開關>** 元素將`General`跟蹤開關設置為<xref:System.Diagnostics.TraceLevel>級別，並啟用`Data`布林跟蹤開關。</span><span class="sxs-lookup"><span data-stu-id="a4140-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4140-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4140-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="a4140-129">跟蹤和調試設置架構</span><span class="sxs-lookup"><span data-stu-id="a4140-129">Trace and Debug Settings Schema</span></span>](index.md)
