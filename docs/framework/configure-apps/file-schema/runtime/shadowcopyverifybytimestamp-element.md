---
title: <shadowCopyVerifyByTimestamp> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1815da141beb3dd1022fe1a74f872aa70b4ded43
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456340"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="ce1b2-102">\<shadowCopyVerifyByTimestamp> 項目</span><span class="sxs-lookup"><span data-stu-id="ce1b2-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="ce1b2-103">指定陰影複製是否使用在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 引進的預設啟動行為，或是要還原成舊版 .NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-103">Specifies whether shadow copying uses the default startup behavior introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ce1b2-104">\<組態 > 項目</span><span class="sxs-lookup"><span data-stu-id="ce1b2-104">\<configuration> Element</span></span>  
<span data-ttu-id="ce1b2-105">\<執行階段 > 項目</span><span class="sxs-lookup"><span data-stu-id="ce1b2-105">\<runtime> Element</span></span>  
<span data-ttu-id="ce1b2-106">\<shadowCopyVerifyByTimestamp> 項目</span><span class="sxs-lookup"><span data-stu-id="ce1b2-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce1b2-107">語法</span><span class="sxs-lookup"><span data-stu-id="ce1b2-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce1b2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ce1b2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ce1b2-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce1b2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ce1b2-110">Attributes</span></span>  
  
|<span data-ttu-id="ce1b2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ce1b2-111">Attribute</span></span>|<span data-ttu-id="ce1b2-112">描述</span><span class="sxs-lookup"><span data-stu-id="ce1b2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce1b2-113">enabled</span><span class="sxs-lookup"><span data-stu-id="ce1b2-113">enabled</span></span>|<span data-ttu-id="ce1b2-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce1b2-115">指定是否使用陰影複製的應用程式定義域時啟動，以判斷是否已更新組件陰影複製組件之前比較的組件時間戳記。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ce1b2-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="ce1b2-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="ce1b2-117">值</span><span class="sxs-lookup"><span data-stu-id="ce1b2-117">Value</span></span>|<span data-ttu-id="ce1b2-118">描述</span><span class="sxs-lookup"><span data-stu-id="ce1b2-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce1b2-119">true</span><span class="sxs-lookup"><span data-stu-id="ce1b2-119">true</span></span>|<span data-ttu-id="ce1b2-120">在啟動時，複製 只有已更新，因此在上一次複製到陰影複製目錄的組件。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="ce1b2-121">這是.NET Framework 4 的預設值。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-121">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="ce1b2-122">False</span><span class="sxs-lookup"><span data-stu-id="ce1b2-122">false</span></span>|<span data-ttu-id="ce1b2-123">還原為舊版.NET Framework 的啟動行為是將在啟動的所有檔案都複製。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce1b2-124">子元素</span><span class="sxs-lookup"><span data-stu-id="ce1b2-124">Child Elements</span></span>  
 <span data-ttu-id="ce1b2-125">無。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce1b2-126">父項目</span><span class="sxs-lookup"><span data-stu-id="ce1b2-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ce1b2-127">項目</span><span class="sxs-lookup"><span data-stu-id="ce1b2-127">Element</span></span>|<span data-ttu-id="ce1b2-128">描述</span><span class="sxs-lookup"><span data-stu-id="ce1b2-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ce1b2-129">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ce1b2-130">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce1b2-131">備註</span><span class="sxs-lookup"><span data-stu-id="ce1b2-131">Remarks</span></span>  
 <span data-ttu-id="ce1b2-132">從.NET Framework 4 開始，組件會陰影複製，只有當其時間戳記表示自上次在複製到陰影複製目錄後有所變更。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-132">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="ce1b2-133">這可改善許多使用陰影複製，應用程式的啟動時間，如中所述[陰影複製組件](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="ce1b2-134">組件更新比例與頻率相當高的應用程式可能不會受益於這種行為變更。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="ce1b2-135">在這種情況下，您可以使用此項目還原舊版 .NET Framework 的行為。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce1b2-136">範例</span><span class="sxs-lookup"><span data-stu-id="ce1b2-136">Example</span></span>  
 <span data-ttu-id="ce1b2-137">下列範例示範如何停用預設啟動行為的陰影複製在.NET Framework 4 中，並還原為舊版.NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="ce1b2-137">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce1b2-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce1b2-138">See also</span></span>

- [<span data-ttu-id="ce1b2-139">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ce1b2-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ce1b2-140">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="ce1b2-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ce1b2-141">陰影複製組件</span><span class="sxs-lookup"><span data-stu-id="ce1b2-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
