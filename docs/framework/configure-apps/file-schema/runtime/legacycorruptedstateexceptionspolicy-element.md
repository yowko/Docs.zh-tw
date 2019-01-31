---
title: <legacyCorruptedStateExceptionsPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a787315ff8b016beff8fb8457619a462e5f3180
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264619"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="ead22-102">\<legacyCorruptedStateExceptionsPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="ead22-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="ead22-103">指定 common language runtime 是否允許 managed 程式碼攔截存取違規和其他損毀的狀態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ead22-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="ead22-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ead22-104">\<configuration></span></span>  
<span data-ttu-id="ead22-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="ead22-105">\<runtime></span></span>  
<span data-ttu-id="ead22-106">\<legacyCorruptedStateExceptionsPolicy></span><span class="sxs-lookup"><span data-stu-id="ead22-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ead22-107">語法</span><span class="sxs-lookup"><span data-stu-id="ead22-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ead22-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ead22-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ead22-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ead22-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ead22-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ead22-110">Attributes</span></span>  
  
|<span data-ttu-id="ead22-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ead22-111">Attribute</span></span>|<span data-ttu-id="ead22-112">描述</span><span class="sxs-lookup"><span data-stu-id="ead22-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ead22-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ead22-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ead22-114">指定應用程式會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="ead22-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ead22-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="ead22-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ead22-116">值</span><span class="sxs-lookup"><span data-stu-id="ead22-116">Value</span></span>|<span data-ttu-id="ead22-117">描述</span><span class="sxs-lookup"><span data-stu-id="ead22-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ead22-118">應用程式不會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="ead22-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="ead22-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="ead22-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ead22-120">應用程式會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="ead22-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ead22-121">子元素</span><span class="sxs-lookup"><span data-stu-id="ead22-121">Child Elements</span></span>  
 <span data-ttu-id="ead22-122">無。</span><span class="sxs-lookup"><span data-stu-id="ead22-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ead22-123">父項目</span><span class="sxs-lookup"><span data-stu-id="ead22-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ead22-124">項目</span><span class="sxs-lookup"><span data-stu-id="ead22-124">Element</span></span>|<span data-ttu-id="ead22-125">描述</span><span class="sxs-lookup"><span data-stu-id="ead22-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ead22-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ead22-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ead22-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="ead22-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ead22-128">備註</span><span class="sxs-lookup"><span data-stu-id="ead22-128">Remarks</span></span>  
 <span data-ttu-id="ead22-129">在.NET Framework 3.5 和更早版本中，通用語言執行平台允許受管理的程式碼，以擷取損毀處理序狀態已引發的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ead22-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="ead22-130">存取違規是這種類型的例外狀況的範例。</span><span class="sxs-lookup"><span data-stu-id="ead22-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="ead22-131">開頭[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]受管理的程式碼不會再會攔截這些類型中的例外狀況的`catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="ead22-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="ead22-132">不過，您可以覆寫這項變更，並維護兩種方式中的損毀的狀態例外狀況的處理：</span><span class="sxs-lookup"><span data-stu-id="ead22-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
-   <span data-ttu-id="ead22-133">設定`<legacyCorruptedStateExceptionsPolicy>`項目的`enabled`屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="ead22-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="ead22-134">此組態設定會套用的 processwide，而且會影響所有方法。</span><span class="sxs-lookup"><span data-stu-id="ead22-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="ead22-135">-或-</span><span class="sxs-lookup"><span data-stu-id="ead22-135">-or-</span></span>  
  
-   <span data-ttu-id="ead22-136">適用於<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>屬性設定為包含例外狀況的方法`catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="ead22-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="ead22-137">這個組態項目是僅適用於[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]和更新版本。</span><span class="sxs-lookup"><span data-stu-id="ead22-137">This configuration element is available only in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ead22-138">範例</span><span class="sxs-lookup"><span data-stu-id="ead22-138">Example</span></span>  
 <span data-ttu-id="ead22-139">下列範例示範如何指定應用程式應該還原成之前的行為[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，並擷取所有損毀狀態例外狀況失敗。</span><span class="sxs-lookup"><span data-stu-id="ead22-139">The following example shows how to specify that the application should revert to the behavior before the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ead22-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ead22-140">See also</span></span>
- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="ead22-141">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ead22-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ead22-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="ead22-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
