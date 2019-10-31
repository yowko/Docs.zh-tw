---
title: <shadowCopyVerifyByTimestamp> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115732"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="0dee5-102">\<shadowCopyVerifyByTimestamp> 項目</span><span class="sxs-lookup"><span data-stu-id="0dee5-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="0dee5-103">指定陰影複製是否使用 .NET Framework 4 中引進的預設啟動行為，或還原為舊版 .NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="0dee5-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
<span data-ttu-id="0dee5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0dee5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0dee5-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="0dee5-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="0dee5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<shadowcopyverifybytimestamp> >**</span><span class="sxs-lookup"><span data-stu-id="0dee5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dee5-107">語法</span><span class="sxs-lookup"><span data-stu-id="0dee5-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dee5-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0dee5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0dee5-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0dee5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dee5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0dee5-110">Attributes</span></span>  
  
|<span data-ttu-id="0dee5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0dee5-111">Attribute</span></span>|<span data-ttu-id="0dee5-112">描述</span><span class="sxs-lookup"><span data-stu-id="0dee5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0dee5-113">enabled</span><span class="sxs-lookup"><span data-stu-id="0dee5-113">enabled</span></span>|<span data-ttu-id="0dee5-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0dee5-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0dee5-115">指定在啟動時，使用陰影複製的應用程式域是否比較元件時間戳記，以判斷元件在陰影複製元件之前是否已更新。</span><span class="sxs-lookup"><span data-stu-id="0dee5-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0dee5-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="0dee5-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="0dee5-117">值</span><span class="sxs-lookup"><span data-stu-id="0dee5-117">Value</span></span>|<span data-ttu-id="0dee5-118">描述</span><span class="sxs-lookup"><span data-stu-id="0dee5-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0dee5-119">true</span><span class="sxs-lookup"><span data-stu-id="0dee5-119">true</span></span>|<span data-ttu-id="0dee5-120">在啟動時，只會複製自上次複製到陰影複製目錄後已更新的元件。</span><span class="sxs-lookup"><span data-stu-id="0dee5-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="0dee5-121">這是 .NET Framework 4 的預設值。</span><span class="sxs-lookup"><span data-stu-id="0dee5-121">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="0dee5-122">False</span><span class="sxs-lookup"><span data-stu-id="0dee5-122">false</span></span>|<span data-ttu-id="0dee5-123">還原為舊版 .NET Framework 的啟動行為，也就是在啟動時複製所有檔案。</span><span class="sxs-lookup"><span data-stu-id="0dee5-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0dee5-124">子項目</span><span class="sxs-lookup"><span data-stu-id="0dee5-124">Child Elements</span></span>  
 <span data-ttu-id="0dee5-125">無。</span><span class="sxs-lookup"><span data-stu-id="0dee5-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0dee5-126">父項目</span><span class="sxs-lookup"><span data-stu-id="0dee5-126">Parent Elements</span></span>  
  
|<span data-ttu-id="0dee5-127">項目</span><span class="sxs-lookup"><span data-stu-id="0dee5-127">Element</span></span>|<span data-ttu-id="0dee5-128">描述</span><span class="sxs-lookup"><span data-stu-id="0dee5-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0dee5-129">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0dee5-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0dee5-130">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="0dee5-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0dee5-131">備註</span><span class="sxs-lookup"><span data-stu-id="0dee5-131">Remarks</span></span>  
 <span data-ttu-id="0dee5-132">從 .NET Framework 4 開始，只有在其時間戳記指出自最後一次複製到陰影複製目錄之後，才會將元件陰影複製。</span><span class="sxs-lookup"><span data-stu-id="0dee5-132">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="0dee5-133">如此可改善許多使用陰影複製之應用程式的啟動時間，如[陰影複製元件](../../../app-domains/shadow-copy-assemblies.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="0dee5-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="0dee5-134">組件更新比例與頻率相當高的應用程式可能不會受益於這種行為變更。</span><span class="sxs-lookup"><span data-stu-id="0dee5-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="0dee5-135">在這種情況下，您可以使用此項目還原舊版 .NET Framework 的行為。</span><span class="sxs-lookup"><span data-stu-id="0dee5-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dee5-136">範例</span><span class="sxs-lookup"><span data-stu-id="0dee5-136">Example</span></span>  
 <span data-ttu-id="0dee5-137">下列範例顯示如何在 .NET Framework 4 中停用陰影複製的預設啟動行為，並還原為舊版 .NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="0dee5-137">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dee5-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="0dee5-138">See also</span></span>

- [<span data-ttu-id="0dee5-139">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0dee5-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0dee5-140">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="0dee5-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0dee5-141">陰影複製組件</span><span class="sxs-lookup"><span data-stu-id="0dee5-141">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
