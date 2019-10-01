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
ms.openlocfilehash: c161f842192396101dcc6850f3b3da328958eac3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697090"
---
# <a name="switches-element"></a><span data-ttu-id="01378-102">@no__t 0switches > 元素</span><span class="sxs-lookup"><span data-stu-id="01378-102">\<switches> Element</span></span>
<span data-ttu-id="01378-103">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="01378-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
[<span data-ttu-id="01378-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="01378-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="01378-105">&nbsp; @ no__t-1[ **\<system. 診斷 >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="01378-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="01378-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<switches >**</span><span class="sxs-lookup"><span data-stu-id="01378-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01378-107">語法</span><span class="sxs-lookup"><span data-stu-id="01378-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01378-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="01378-108">Attributes and Elements</span></span>  
 <span data-ttu-id="01378-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="01378-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01378-110">屬性</span><span class="sxs-lookup"><span data-stu-id="01378-110">Attributes</span></span>  
 <span data-ttu-id="01378-111">無。</span><span class="sxs-lookup"><span data-stu-id="01378-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01378-112">子元素</span><span class="sxs-lookup"><span data-stu-id="01378-112">Child Elements</span></span>  
  
|<span data-ttu-id="01378-113">元素</span><span class="sxs-lookup"><span data-stu-id="01378-113">Element</span></span>|<span data-ttu-id="01378-114">描述</span><span class="sxs-lookup"><span data-stu-id="01378-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01378-115">\<add></span><span class="sxs-lookup"><span data-stu-id="01378-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="01378-116">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="01378-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01378-117">父項目</span><span class="sxs-lookup"><span data-stu-id="01378-117">Parent Elements</span></span>  
  
|<span data-ttu-id="01378-118">項目</span><span class="sxs-lookup"><span data-stu-id="01378-118">Element</span></span>|<span data-ttu-id="01378-119">描述</span><span class="sxs-lookup"><span data-stu-id="01378-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="01378-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="01378-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="01378-121">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="01378-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01378-122">備註</span><span class="sxs-lookup"><span data-stu-id="01378-122">Remarks</span></span>  
 <span data-ttu-id="01378-123">您可以變更追蹤參數的層級，方法是將它放在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="01378-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="01378-124">如果參數為 <xref:System.Diagnostics.BooleanSwitch>，您可以開啟或關閉它。</span><span class="sxs-lookup"><span data-stu-id="01378-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="01378-125">如果參數為 <xref:System.Diagnostics.TraceSwitch>，您可以為其指派不同的層級，以指定應用程式輸出的追蹤或 debug 訊息的類型。</span><span class="sxs-lookup"><span data-stu-id="01378-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01378-126">範例</span><span class="sxs-lookup"><span data-stu-id="01378-126">Example</span></span>  
 <span data-ttu-id="01378-127">下列範例示範如何使用 **\<切換>** 要設定項目`General`追蹤參數設<xref:System.Diagnostics.TraceLevel>層級，並且啟用`Data`布林追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="01378-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01378-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01378-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="01378-129">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="01378-129">Trace and Debug Settings Schema</span></span>](index.md)
 