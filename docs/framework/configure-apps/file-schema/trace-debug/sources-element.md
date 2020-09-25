---
title: <sources> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
ms.openlocfilehash: 670fb359f892d83feac56c849361c4b980d9a922
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173805"
---
# <a name="sources-element"></a><span data-ttu-id="dca8c-102">\<sources> 項目</span><span class="sxs-lookup"><span data-stu-id="dca8c-102">\<sources> Element</span></span>

<span data-ttu-id="dca8c-103">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="dca8c-103">Specifies trace sources that initiate tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**

## <a name="syntax"></a><span data-ttu-id="dca8c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="dca8c-104">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dca8c-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dca8c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="dca8c-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dca8c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dca8c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="dca8c-107">Attributes</span></span>  

 <span data-ttu-id="dca8c-108">無。</span><span class="sxs-lookup"><span data-stu-id="dca8c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dca8c-109">子元素</span><span class="sxs-lookup"><span data-stu-id="dca8c-109">Child Elements</span></span>  
  
|<span data-ttu-id="dca8c-110">項目</span><span class="sxs-lookup"><span data-stu-id="dca8c-110">Element</span></span>|<span data-ttu-id="dca8c-111">描述</span><span class="sxs-lookup"><span data-stu-id="dca8c-111">Description</span></span>|  
|-------------|-----------------|  
|[\<source>](source-element.md)|<span data-ttu-id="dca8c-112">必要元素。</span><span class="sxs-lookup"><span data-stu-id="dca8c-112">Required element.</span></span><br /><br /> <span data-ttu-id="dca8c-113">指定起始追蹤訊息的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="dca8c-113">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dca8c-114">父項目</span><span class="sxs-lookup"><span data-stu-id="dca8c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="dca8c-115">項目</span><span class="sxs-lookup"><span data-stu-id="dca8c-115">Element</span></span>|<span data-ttu-id="dca8c-116">描述</span><span class="sxs-lookup"><span data-stu-id="dca8c-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dca8c-117">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="dca8c-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="dca8c-118">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="dca8c-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dca8c-119">備註</span><span class="sxs-lookup"><span data-stu-id="dca8c-119">Remarks</span></span>  

 <span data-ttu-id="dca8c-120">此元素可用於電腦設定檔 ( # A0) 和應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="dca8c-120">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dca8c-121">範例</span><span class="sxs-lookup"><span data-stu-id="dca8c-121">Example</span></span>  

 <span data-ttu-id="dca8c-122">下列範例示範如何使用專案 `<sources>` 來加入追蹤來源 `mySource` ，以及設定名為之來源參數的層級 `sourceSwitch` 。</span><span class="sxs-lookup"><span data-stu-id="dca8c-122">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="dca8c-123">加入的主控台追蹤接聽程式會將追蹤資訊寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="dca8c-123">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"
                     initializeData="Error" />  
               </add>  
               <remove name="Default" />  
            </listeners>  
         </source>  
      </sources>  
      <switches>  
         <add name="sourceSwitch" value="Warning" />  
      </switches>
   </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dca8c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dca8c-124">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="dca8c-125">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="dca8c-125">Trace and Debug Settings Schema</span></span>](index.md)
- [\<source>](source-element.md)
