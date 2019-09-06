---
title: <shadowCopyVerifyByTimestamp> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79d44ff255b1fc12efc6e8488eeab231b9276b90
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252311"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="f34f4-102">\<shadowCopyVerifyByTimestamp> 項目</span><span class="sxs-lookup"><span data-stu-id="f34f4-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="f34f4-103">指定陰影複製是否使用 .NET Framework 4 中引進的預設啟動行為，或還原為舊版 .NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="f34f4-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
<span data-ttu-id="f34f4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f34f4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f34f4-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="f34f4-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="f34f4-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Shadowcopyverifybytimestamp> >**</span><span class="sxs-lookup"><span data-stu-id="f34f4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f34f4-107">語法</span><span class="sxs-lookup"><span data-stu-id="f34f4-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f34f4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f34f4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f34f4-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f34f4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f34f4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f34f4-110">Attributes</span></span>  
  
|<span data-ttu-id="f34f4-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f34f4-111">Attribute</span></span>|<span data-ttu-id="f34f4-112">描述</span><span class="sxs-lookup"><span data-stu-id="f34f4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f34f4-113">enabled</span><span class="sxs-lookup"><span data-stu-id="f34f4-113">enabled</span></span>|<span data-ttu-id="f34f4-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f34f4-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="f34f4-115">指定在啟動時，使用陰影複製的應用程式域是否比較元件時間戳記，以判斷元件在陰影複製元件之前是否已更新。</span><span class="sxs-lookup"><span data-stu-id="f34f4-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f34f4-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="f34f4-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="f34f4-117">值</span><span class="sxs-lookup"><span data-stu-id="f34f4-117">Value</span></span>|<span data-ttu-id="f34f4-118">說明</span><span class="sxs-lookup"><span data-stu-id="f34f4-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f34f4-119">true</span><span class="sxs-lookup"><span data-stu-id="f34f4-119">true</span></span>|<span data-ttu-id="f34f4-120">在啟動時，只會複製自上次複製到陰影複製目錄後已更新的元件。</span><span class="sxs-lookup"><span data-stu-id="f34f4-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="f34f4-121">這是 .NET Framework 4 的預設值。</span><span class="sxs-lookup"><span data-stu-id="f34f4-121">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="f34f4-122">false</span><span class="sxs-lookup"><span data-stu-id="f34f4-122">false</span></span>|<span data-ttu-id="f34f4-123">還原為舊版 .NET Framework 的啟動行為，也就是在啟動時複製所有檔案。</span><span class="sxs-lookup"><span data-stu-id="f34f4-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f34f4-124">子元素</span><span class="sxs-lookup"><span data-stu-id="f34f4-124">Child Elements</span></span>  
 <span data-ttu-id="f34f4-125">無。</span><span class="sxs-lookup"><span data-stu-id="f34f4-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f34f4-126">父項目</span><span class="sxs-lookup"><span data-stu-id="f34f4-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f34f4-127">項目</span><span class="sxs-lookup"><span data-stu-id="f34f4-127">Element</span></span>|<span data-ttu-id="f34f4-128">說明</span><span class="sxs-lookup"><span data-stu-id="f34f4-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f34f4-129">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f34f4-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f34f4-130">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="f34f4-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f34f4-131">備註</span><span class="sxs-lookup"><span data-stu-id="f34f4-131">Remarks</span></span>  
 <span data-ttu-id="f34f4-132">從 .NET Framework 4 開始，只有在其時間戳記指出自最後一次複製到陰影複製目錄之後，才會將元件陰影複製。</span><span class="sxs-lookup"><span data-stu-id="f34f4-132">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="f34f4-133">如此可改善許多使用陰影複製之應用程式的啟動時間，如[陰影複製元件](../../../app-domains/shadow-copy-assemblies.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="f34f4-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="f34f4-134">組件更新比例與頻率相當高的應用程式可能不會受益於這種行為變更。</span><span class="sxs-lookup"><span data-stu-id="f34f4-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="f34f4-135">在這種情況下，您可以使用此項目還原舊版 .NET Framework 的行為。</span><span class="sxs-lookup"><span data-stu-id="f34f4-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f34f4-136">範例</span><span class="sxs-lookup"><span data-stu-id="f34f4-136">Example</span></span>  
 <span data-ttu-id="f34f4-137">下列範例顯示如何在 .NET Framework 4 中停用陰影複製的預設啟動行為，並還原為舊版 .NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="f34f4-137">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f34f4-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f34f4-138">See also</span></span>

- [<span data-ttu-id="f34f4-139">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f34f4-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f34f4-140">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f34f4-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f34f4-141">陰影複製組件</span><span class="sxs-lookup"><span data-stu-id="f34f4-141">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
