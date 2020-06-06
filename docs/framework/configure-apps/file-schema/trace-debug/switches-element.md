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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153226"
---
# <a name="switches-element"></a><span data-ttu-id="4e489-102">\<switches> 項目</span><span class="sxs-lookup"><span data-stu-id="4e489-102">\<switches> Element</span></span>
<span data-ttu-id="4e489-103">包含追蹤參數及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4e489-103">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="4e489-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e489-104">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e489-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4e489-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4e489-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4e489-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e489-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4e489-107">Attributes</span></span>  
 <span data-ttu-id="4e489-108">無。</span><span class="sxs-lookup"><span data-stu-id="4e489-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4e489-109">子元素</span><span class="sxs-lookup"><span data-stu-id="4e489-109">Child Elements</span></span>  
  
|<span data-ttu-id="4e489-110">元素</span><span class="sxs-lookup"><span data-stu-id="4e489-110">Element</span></span>|<span data-ttu-id="4e489-111">描述</span><span class="sxs-lookup"><span data-stu-id="4e489-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="4e489-112">指定設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4e489-112">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4e489-113">父項目</span><span class="sxs-lookup"><span data-stu-id="4e489-113">Parent Elements</span></span>  
  
|<span data-ttu-id="4e489-114">元素</span><span class="sxs-lookup"><span data-stu-id="4e489-114">Element</span></span>|<span data-ttu-id="4e489-115">描述</span><span class="sxs-lookup"><span data-stu-id="4e489-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4e489-116">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4e489-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="4e489-117">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="4e489-117">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e489-118">備註</span><span class="sxs-lookup"><span data-stu-id="4e489-118">Remarks</span></span>  
 <span data-ttu-id="4e489-119">您可以變更追蹤參數的層級，方法是將它放在設定檔中。</span><span class="sxs-lookup"><span data-stu-id="4e489-119">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="4e489-120">如果參數是 <xref:System.Diagnostics.BooleanSwitch> ，您可以開啟和關閉它。</span><span class="sxs-lookup"><span data-stu-id="4e489-120">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="4e489-121">如果參數是 <xref:System.Diagnostics.TraceSwitch> ，您可以為其指派不同的層級，以指定應用程式輸出的追蹤或 debug 訊息的類型。</span><span class="sxs-lookup"><span data-stu-id="4e489-121">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e489-122">範例</span><span class="sxs-lookup"><span data-stu-id="4e489-122">Example</span></span>  
 <span data-ttu-id="4e489-123">下列範例顯示如何使用專案 **\<switch>** `General` ，將追蹤參數設定為 <xref:System.Diagnostics.TraceLevel> 層級，並啟用 `Data` 布林追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="4e489-123">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e489-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e489-124">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="4e489-125">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4e489-125">Trace and Debug Settings Schema</span></span>](index.md)
