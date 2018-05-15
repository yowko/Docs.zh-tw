---
title: '&lt;legacyCorruptedStateExceptionsPolicy&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6228aaf4c7da70337d9d1a99adcb78f71a0039b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a><span data-ttu-id="ae522-102">&lt;legacyCorruptedStateExceptionsPolicy&gt;項目</span><span class="sxs-lookup"><span data-stu-id="ae522-102">&lt;legacyCorruptedStateExceptionsPolicy&gt; Element</span></span>
<span data-ttu-id="ae522-103">指定 common language runtime 是否允許受管理的程式碼，以擷取存取違規和其他損毀的狀態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ae522-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="ae522-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ae522-104">\<configuration></span></span>  
<span data-ttu-id="ae522-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="ae522-105">\<runtime></span></span>  
<span data-ttu-id="ae522-106">\<legacyCorruptedStateExceptionsPolicy ></span><span class="sxs-lookup"><span data-stu-id="ae522-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae522-107">語法</span><span class="sxs-lookup"><span data-stu-id="ae522-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae522-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ae522-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ae522-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ae522-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae522-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ae522-110">Attributes</span></span>  
  
|<span data-ttu-id="ae522-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ae522-111">Attribute</span></span>|<span data-ttu-id="ae522-112">描述</span><span class="sxs-lookup"><span data-stu-id="ae522-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ae522-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ae522-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ae522-114">指定應用程式將會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="ae522-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ae522-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="ae522-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ae522-116">值</span><span class="sxs-lookup"><span data-stu-id="ae522-116">Value</span></span>|<span data-ttu-id="ae522-117">描述</span><span class="sxs-lookup"><span data-stu-id="ae522-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ae522-118">應用程式不會抓取損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="ae522-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="ae522-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="ae522-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ae522-120">應用程式將會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="ae522-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae522-121">子項目</span><span class="sxs-lookup"><span data-stu-id="ae522-121">Child Elements</span></span>  
 <span data-ttu-id="ae522-122">無。</span><span class="sxs-lookup"><span data-stu-id="ae522-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae522-123">父項目</span><span class="sxs-lookup"><span data-stu-id="ae522-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ae522-124">項目</span><span class="sxs-lookup"><span data-stu-id="ae522-124">Element</span></span>|<span data-ttu-id="ae522-125">描述</span><span class="sxs-lookup"><span data-stu-id="ae522-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ae522-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ae522-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ae522-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="ae522-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae522-128">備註</span><span class="sxs-lookup"><span data-stu-id="ae522-128">Remarks</span></span>  
 <span data-ttu-id="ae522-129">在.NET Framework 3.5 或更早版本中，通用語言執行平台允許 managed 程式碼來攔截已損毀處理序狀態所引發的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ae522-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="ae522-130">存取違規是這種類型的例外狀況的範例。</span><span class="sxs-lookup"><span data-stu-id="ae522-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="ae522-131">從開始[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、 managed 程式碼不再攔截這些類型中的例外狀況的`catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="ae522-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="ae522-132">不過，您可以覆寫這項變更，並維護兩種方式中的損毀的狀態例外狀況的處理：</span><span class="sxs-lookup"><span data-stu-id="ae522-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
-   <span data-ttu-id="ae522-133">設定`<legacyCorruptedStateExceptionsPolicy>`項目的`enabled`屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="ae522-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="ae522-134">此組態設定會套用的 processwide，而且會影響所有方法。</span><span class="sxs-lookup"><span data-stu-id="ae522-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="ae522-135">-或-</span><span class="sxs-lookup"><span data-stu-id="ae522-135">-or-</span></span>  
  
-   <span data-ttu-id="ae522-136">套用<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>包含例外狀況的方法，此屬性`catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="ae522-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="ae522-137">這個組態項目是僅適用於[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]和更新版本。</span><span class="sxs-lookup"><span data-stu-id="ae522-137">This configuration element is available only in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae522-138">範例</span><span class="sxs-lookup"><span data-stu-id="ae522-138">Example</span></span>  
 <span data-ttu-id="ae522-139">下列範例示範如何指定應用程式應該還原成之前的行為[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，並攔截所有損毀狀態例外狀況失敗。</span><span class="sxs-lookup"><span data-stu-id="ae522-139">The following example shows how to specify that the application should revert to the behavior before the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae522-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae522-140">See Also</span></span>  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [<span data-ttu-id="ae522-141">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ae522-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ae522-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="ae522-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
