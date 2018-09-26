---
title: '&lt;判斷提示&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b15e569ff6e42298c0a1de02f77ab7c302c70d86
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193508"
---
# <a name="ltassertgt-element"></a><span data-ttu-id="0a258-102">&lt;判斷提示&gt;項目</span><span class="sxs-lookup"><span data-stu-id="0a258-102">&lt;assert&gt; Element</span></span>
<span data-ttu-id="0a258-103">指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a258-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="0a258-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0a258-104">\<configuration></span></span>  
<span data-ttu-id="0a258-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="0a258-105">\<system.diagnostics></span></span>  
<span data-ttu-id="0a258-106">\<判斷提示 ></span><span class="sxs-lookup"><span data-stu-id="0a258-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a258-107">語法</span><span class="sxs-lookup"><span data-stu-id="0a258-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a258-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0a258-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0a258-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0a258-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a258-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0a258-110">Attributes</span></span>  
  
|<span data-ttu-id="0a258-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0a258-111">Attribute</span></span>|<span data-ttu-id="0a258-112">描述</span><span class="sxs-lookup"><span data-stu-id="0a258-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="0a258-113">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="0a258-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0a258-114">指定是否要顯示訊息方塊的時機**Debug.Assert**方法會評估要**false**。</span><span class="sxs-lookup"><span data-stu-id="0a258-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="0a258-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="0a258-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0a258-116">指定要寫入訊息，如果檔案名稱**Debug.Assert**評估為**false**。</span><span class="sxs-lookup"><span data-stu-id="0a258-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="0a258-117">assertuienabled 屬性</span><span class="sxs-lookup"><span data-stu-id="0a258-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="0a258-118">值</span><span class="sxs-lookup"><span data-stu-id="0a258-118">Value</span></span>|<span data-ttu-id="0a258-119">描述</span><span class="sxs-lookup"><span data-stu-id="0a258-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="0a258-120">顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="0a258-120">Displays the message box.</span></span> <span data-ttu-id="0a258-121">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="0a258-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="0a258-122">不會顯示訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="0a258-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a258-123">子元素</span><span class="sxs-lookup"><span data-stu-id="0a258-123">Child Elements</span></span>  
 <span data-ttu-id="0a258-124">無。</span><span class="sxs-lookup"><span data-stu-id="0a258-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a258-125">父項目</span><span class="sxs-lookup"><span data-stu-id="0a258-125">Parent Elements</span></span>  
  
|<span data-ttu-id="0a258-126">項目</span><span class="sxs-lookup"><span data-stu-id="0a258-126">Element</span></span>|<span data-ttu-id="0a258-127">描述</span><span class="sxs-lookup"><span data-stu-id="0a258-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0a258-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0a258-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0a258-129">指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。</span><span class="sxs-lookup"><span data-stu-id="0a258-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a258-130">備註</span><span class="sxs-lookup"><span data-stu-id="0a258-130">Remarks</span></span>  
 <span data-ttu-id="0a258-131">在這兩個屬性**\<判斷提示 >** 是選擇性的項目。</span><span class="sxs-lookup"><span data-stu-id="0a258-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="0a258-132">您可以將訊息方塊停用未指定要寫入至訊息的檔案，或者您可以指定要寫入訊息時保留訊息方塊，啟用檔案。</span><span class="sxs-lookup"><span data-stu-id="0a258-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a258-133">範例</span><span class="sxs-lookup"><span data-stu-id="0a258-133">Example</span></span>  
 <span data-ttu-id="0a258-134">下列範例示範如何停用顯示訊息方塊，當您呼叫**Debug.Assert**寫入到訊息`c:\log.txt`。</span><span class="sxs-lookup"><span data-stu-id="0a258-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a258-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a258-135">See Also</span></span>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="0a258-136">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0a258-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
