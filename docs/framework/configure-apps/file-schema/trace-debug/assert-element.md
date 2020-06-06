---
title: <assert> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: f3c1a1670139a8262dea449bfff99c7c1c19f088
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088939"
---
# <a name="assert-element"></a><span data-ttu-id="d8803-102">\<assert> 項目</span><span class="sxs-lookup"><span data-stu-id="d8803-102">\<assert> Element</span></span>
<span data-ttu-id="d8803-103">指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8803-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a><span data-ttu-id="d8803-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8803-104">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8803-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8803-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d8803-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d8803-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8803-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d8803-107">Attributes</span></span>  
  
|<span data-ttu-id="d8803-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d8803-108">Attribute</span></span>|<span data-ttu-id="d8803-109">描述</span><span class="sxs-lookup"><span data-stu-id="d8803-109">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="d8803-110">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d8803-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d8803-111">指定當**Debug. Assert**方法評估為**false**時，是否要顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="d8803-111">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="d8803-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d8803-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d8803-113">指定在**Debug. Assert**評估為**false**時，要寫入訊息的檔案名。</span><span class="sxs-lookup"><span data-stu-id="d8803-113">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="d8803-114">assertuienabled 屬性</span><span class="sxs-lookup"><span data-stu-id="d8803-114">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="d8803-115">值</span><span class="sxs-lookup"><span data-stu-id="d8803-115">Value</span></span>|<span data-ttu-id="d8803-116">描述</span><span class="sxs-lookup"><span data-stu-id="d8803-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="d8803-117">顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="d8803-117">Displays the message box.</span></span> <span data-ttu-id="d8803-118">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="d8803-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="d8803-119">不會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="d8803-119">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8803-120">子元素</span><span class="sxs-lookup"><span data-stu-id="d8803-120">Child Elements</span></span>  
 <span data-ttu-id="d8803-121">無。</span><span class="sxs-lookup"><span data-stu-id="d8803-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8803-122">父項目</span><span class="sxs-lookup"><span data-stu-id="d8803-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d8803-123">元素</span><span class="sxs-lookup"><span data-stu-id="d8803-123">Element</span></span>|<span data-ttu-id="d8803-124">描述</span><span class="sxs-lookup"><span data-stu-id="d8803-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d8803-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d8803-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d8803-126">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="d8803-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8803-127">備註</span><span class="sxs-lookup"><span data-stu-id="d8803-127">Remarks</span></span>  
 <span data-ttu-id="d8803-128">元素中的兩個屬性 **\<assert>** 都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d8803-128">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="d8803-129">您可以停用訊息方塊，但不指定要寫入訊息的檔案，或者您也可以指定要寫入訊息的檔案，同時讓訊息方塊保持啟用。</span><span class="sxs-lookup"><span data-stu-id="d8803-129">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8803-130">範例</span><span class="sxs-lookup"><span data-stu-id="d8803-130">Example</span></span>  
 <span data-ttu-id="d8803-131">下列範例顯示當您呼叫**Debug. Assert**並將訊息寫入時，如何停用顯示訊息方塊 `c:\log.txt` 。</span><span class="sxs-lookup"><span data-stu-id="d8803-131">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8803-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8803-132">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="d8803-133">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d8803-133">Trace and Debug Settings Schema</span></span>](index.md)
