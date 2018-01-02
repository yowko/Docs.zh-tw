---
title: "&lt;shadowCopyVerifyByTimestamp&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bae98c91c8a9b68ec7c21b142bc9f004c7bc1394
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a><span data-ttu-id="a2844-102">&lt;shadowCopyVerifyByTimestamp&gt;項目</span><span class="sxs-lookup"><span data-stu-id="a2844-102">&lt;shadowCopyVerifyByTimestamp&gt; Element</span></span>
<span data-ttu-id="a2844-103">指定陰影複製是否使用在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 引進的預設啟動行為，或是要還原成舊版 .NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="a2844-103">Specifies whether shadow copying uses the default startup behavior introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a2844-104">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="a2844-104">\<configuration> Element</span></span>  
<span data-ttu-id="a2844-105">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="a2844-105">\<runtime> Element</span></span>  
<span data-ttu-id="a2844-106">\<shadowCopyVerifyByTimestamp > 項目</span><span class="sxs-lookup"><span data-stu-id="a2844-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2844-107">語法</span><span class="sxs-lookup"><span data-stu-id="a2844-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2844-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a2844-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a2844-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a2844-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2844-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a2844-110">Attributes</span></span>  
  
|<span data-ttu-id="a2844-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a2844-111">Attribute</span></span>|<span data-ttu-id="a2844-112">描述</span><span class="sxs-lookup"><span data-stu-id="a2844-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2844-113">enabled</span><span class="sxs-lookup"><span data-stu-id="a2844-113">enabled</span></span>|<span data-ttu-id="a2844-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a2844-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a2844-115">指定是否使用陰影複製的應用程式定義域時啟動，以判斷是否已更新組件陰影複製組件之前比較組件的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="a2844-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a2844-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="a2844-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="a2844-117">值</span><span class="sxs-lookup"><span data-stu-id="a2844-117">Value</span></span>|<span data-ttu-id="a2844-118">描述</span><span class="sxs-lookup"><span data-stu-id="a2844-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a2844-119">true</span><span class="sxs-lookup"><span data-stu-id="a2844-119">true</span></span>|<span data-ttu-id="a2844-120">在啟動時，會將複製的已更新，因此在上一次複製到陰影複製目錄組件。</span><span class="sxs-lookup"><span data-stu-id="a2844-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="a2844-121">這是預設值[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a2844-121">This is the default for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>|  
|<span data-ttu-id="a2844-122">false</span><span class="sxs-lookup"><span data-stu-id="a2844-122">false</span></span>|<span data-ttu-id="a2844-123">已複製所有檔案，在啟動還原的舊版.NET Framework 中，啟動行為。</span><span class="sxs-lookup"><span data-stu-id="a2844-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2844-124">子元素</span><span class="sxs-lookup"><span data-stu-id="a2844-124">Child Elements</span></span>  
 <span data-ttu-id="a2844-125">無。</span><span class="sxs-lookup"><span data-stu-id="a2844-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2844-126">父項目</span><span class="sxs-lookup"><span data-stu-id="a2844-126">Parent Elements</span></span>  
  
|<span data-ttu-id="a2844-127">項目</span><span class="sxs-lookup"><span data-stu-id="a2844-127">Element</span></span>|<span data-ttu-id="a2844-128">描述</span><span class="sxs-lookup"><span data-stu-id="a2844-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a2844-129">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a2844-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a2844-130">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="a2844-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2844-131">備註</span><span class="sxs-lookup"><span data-stu-id="a2844-131">Remarks</span></span>  
 <span data-ttu-id="a2844-132">從開始[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，組件是陰影複製，只有當其時間戳記表示自上次在複製到陰影複製目錄已變更。</span><span class="sxs-lookup"><span data-stu-id="a2844-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="a2844-133">這可改善使用陰影複製，許多應用程式的啟動時間中所述[陰影複製組件](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="a2844-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="a2844-134">組件更新比例與頻率相當高的應用程式可能不會受益於這種行為變更。</span><span class="sxs-lookup"><span data-stu-id="a2844-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="a2844-135">在這種情況下，您可以使用此項目還原舊版 .NET Framework 的行為。</span><span class="sxs-lookup"><span data-stu-id="a2844-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2844-136">範例</span><span class="sxs-lookup"><span data-stu-id="a2844-136">Example</span></span>  
 <span data-ttu-id="a2844-137">下列範例示範如何停用預設啟動行為的陰影複製在[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，並還原為舊版.NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="a2844-137">The following example shows how to disable the default startup behavior of shadow copying in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2844-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="a2844-138">See Also</span></span>  
 [<span data-ttu-id="a2844-139">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a2844-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="a2844-140">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a2844-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a2844-141">陰影複製組件</span><span class="sxs-lookup"><span data-stu-id="a2844-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
