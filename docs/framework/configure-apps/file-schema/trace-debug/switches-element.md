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
ms.openlocfilehash: 92a1c8db43579048945d76082e3ebd2862efd7ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920434"
---
# <a name="switches-element"></a><span data-ttu-id="f4816-102">\<切換 > 元素</span><span class="sxs-lookup"><span data-stu-id="f4816-102">\<switches> Element</span></span>
<span data-ttu-id="f4816-103">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="f4816-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="f4816-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f4816-104">\<configuration></span></span>  
<span data-ttu-id="f4816-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="f4816-105">\<system.diagnostics></span></span>  
<span data-ttu-id="f4816-106">\<切換 ></span><span class="sxs-lookup"><span data-stu-id="f4816-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4816-107">語法</span><span class="sxs-lookup"><span data-stu-id="f4816-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4816-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f4816-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f4816-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f4816-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4816-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f4816-110">Attributes</span></span>  
 <span data-ttu-id="f4816-111">無。</span><span class="sxs-lookup"><span data-stu-id="f4816-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f4816-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f4816-112">Child Elements</span></span>  
  
|<span data-ttu-id="f4816-113">項目</span><span class="sxs-lookup"><span data-stu-id="f4816-113">Element</span></span>|<span data-ttu-id="f4816-114">描述</span><span class="sxs-lookup"><span data-stu-id="f4816-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4816-115">\<add></span><span class="sxs-lookup"><span data-stu-id="f4816-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="f4816-116">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="f4816-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4816-117">父項目</span><span class="sxs-lookup"><span data-stu-id="f4816-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f4816-118">項目</span><span class="sxs-lookup"><span data-stu-id="f4816-118">Element</span></span>|<span data-ttu-id="f4816-119">說明</span><span class="sxs-lookup"><span data-stu-id="f4816-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f4816-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f4816-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="f4816-121">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="f4816-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4816-122">備註</span><span class="sxs-lookup"><span data-stu-id="f4816-122">Remarks</span></span>  
 <span data-ttu-id="f4816-123">您可以變更追蹤參數的層級, 方法是將它放在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="f4816-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="f4816-124">如果參數是<xref:System.Diagnostics.BooleanSwitch>, 您可以開啟和關閉它。</span><span class="sxs-lookup"><span data-stu-id="f4816-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="f4816-125">如果參數是<xref:System.Diagnostics.TraceSwitch>, 您可以為其指派不同的層級, 以指定應用程式輸出的追蹤或 debug 訊息的類型。</span><span class="sxs-lookup"><span data-stu-id="f4816-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4816-126">範例</span><span class="sxs-lookup"><span data-stu-id="f4816-126">Example</span></span>  
 <span data-ttu-id="f4816-127">下列範例示範如何使用 **\<切換>** 要設定項目`General`追蹤參數設<xref:System.Diagnostics.TraceLevel>層級，並且啟用`Data`布林追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="f4816-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4816-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4816-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="f4816-129">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f4816-129">Trace and Debug Settings Schema</span></span>](index.md)
