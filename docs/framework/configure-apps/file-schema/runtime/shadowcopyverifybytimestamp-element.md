---
title: <shadowCopyVerifyByTimestamp> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115732"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="d7805-102">\<shadowCopyVerifyByTimestamp> 項目</span><span class="sxs-lookup"><span data-stu-id="d7805-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="d7805-103">指定陰影複製是否使用 .NET Framework 4 中引進的預設啟動行為，或還原為舊版 .NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="d7805-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a><span data-ttu-id="d7805-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7805-104">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7805-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d7805-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d7805-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d7805-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7805-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d7805-107">Attributes</span></span>  
  
|<span data-ttu-id="d7805-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d7805-108">Attribute</span></span>|<span data-ttu-id="d7805-109">描述</span><span class="sxs-lookup"><span data-stu-id="d7805-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7805-110">已啟用</span><span class="sxs-lookup"><span data-stu-id="d7805-110">enabled</span></span>|<span data-ttu-id="d7805-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d7805-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="d7805-112">指定在啟動時，使用陰影複製的應用程式域是否比較元件時間戳記，以判斷元件在陰影複製元件之前是否已更新。</span><span class="sxs-lookup"><span data-stu-id="d7805-112">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d7805-113">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="d7805-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="d7805-114">值</span><span class="sxs-lookup"><span data-stu-id="d7805-114">Value</span></span>|<span data-ttu-id="d7805-115">描述</span><span class="sxs-lookup"><span data-stu-id="d7805-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7805-116">true</span><span class="sxs-lookup"><span data-stu-id="d7805-116">true</span></span>|<span data-ttu-id="d7805-117">在啟動時，只會複製自上次複製到陰影複製目錄後已更新的元件。</span><span class="sxs-lookup"><span data-stu-id="d7805-117">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="d7805-118">這是 .NET Framework 4 的預設值。</span><span class="sxs-lookup"><span data-stu-id="d7805-118">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="d7805-119">false</span><span class="sxs-lookup"><span data-stu-id="d7805-119">false</span></span>|<span data-ttu-id="d7805-120">還原為舊版 .NET Framework 的啟動行為，也就是在啟動時複製所有檔案。</span><span class="sxs-lookup"><span data-stu-id="d7805-120">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7805-121">子元素</span><span class="sxs-lookup"><span data-stu-id="d7805-121">Child Elements</span></span>  
 <span data-ttu-id="d7805-122">無。</span><span class="sxs-lookup"><span data-stu-id="d7805-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7805-123">父項目</span><span class="sxs-lookup"><span data-stu-id="d7805-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d7805-124">元素</span><span class="sxs-lookup"><span data-stu-id="d7805-124">Element</span></span>|<span data-ttu-id="d7805-125">描述</span><span class="sxs-lookup"><span data-stu-id="d7805-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d7805-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d7805-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d7805-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="d7805-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7805-128">備註</span><span class="sxs-lookup"><span data-stu-id="d7805-128">Remarks</span></span>  
 <span data-ttu-id="d7805-129">從 .NET Framework 4 開始，只有在其時間戳記指出自最後一次複製到陰影複製目錄之後，才會將元件陰影複製。</span><span class="sxs-lookup"><span data-stu-id="d7805-129">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="d7805-130">如此可改善許多使用陰影複製之應用程式的啟動時間，如[陰影複製元件](../../../app-domains/shadow-copy-assemblies.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="d7805-130">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="d7805-131">組件更新比例與頻率相當高的應用程式可能不會受益於這種行為變更。</span><span class="sxs-lookup"><span data-stu-id="d7805-131">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="d7805-132">在這種情況下，您可以使用此項目還原舊版 .NET Framework 的行為。</span><span class="sxs-lookup"><span data-stu-id="d7805-132">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7805-133">範例</span><span class="sxs-lookup"><span data-stu-id="d7805-133">Example</span></span>  
 <span data-ttu-id="d7805-134">下列範例顯示如何在 .NET Framework 4 中停用陰影複製的預設啟動行為，並還原為舊版 .NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="d7805-134">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7805-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7805-135">See also</span></span>

- [<span data-ttu-id="d7805-136">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="d7805-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d7805-137">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="d7805-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d7805-138">陰影複製組件</span><span class="sxs-lookup"><span data-stu-id="d7805-138">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
