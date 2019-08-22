---
title: <bypassTrustedAppStrongNames> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aac7079d941e6774ca6c00fbece8ff72fbf3f0e1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663877"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="6919b-102">\<bypassTrustedAppStrongNames> 項目</span><span class="sxs-lookup"><span data-stu-id="6919b-102">\<bypassTrustedAppStrongNames> Element</span></span>
<span data-ttu-id="6919b-103">指定是否要在已載入完全信任<xref:System.AppDomain>的完全信任元件上略過強式名稱驗證。</span><span class="sxs-lookup"><span data-stu-id="6919b-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="6919b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6919b-104">\<configuration></span></span>  
<span data-ttu-id="6919b-105">\<執行時間 ></span><span class="sxs-lookup"><span data-stu-id="6919b-105">\<runtime></span></span>  
<span data-ttu-id="6919b-106">\<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="6919b-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6919b-107">語法</span><span class="sxs-lookup"><span data-stu-id="6919b-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6919b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6919b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6919b-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6919b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6919b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6919b-110">Attributes</span></span>  
  
|<span data-ttu-id="6919b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6919b-111">Attribute</span></span>|<span data-ttu-id="6919b-112">說明</span><span class="sxs-lookup"><span data-stu-id="6919b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6919b-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6919b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6919b-114">指定是否啟用避免為完全信任元件驗證強式名稱的略過功能。</span><span class="sxs-lookup"><span data-stu-id="6919b-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="6919b-115">啟用這項功能時, 在載入元件時, 不會驗證強式名稱是否正確。</span><span class="sxs-lookup"><span data-stu-id="6919b-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="6919b-116">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6919b-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6919b-117">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="6919b-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="6919b-118">值</span><span class="sxs-lookup"><span data-stu-id="6919b-118">Value</span></span>|<span data-ttu-id="6919b-119">說明</span><span class="sxs-lookup"><span data-stu-id="6919b-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="6919b-120">當元件載入至完全信任<xref:System.AppDomain>時, 不會驗證完全信任元件上的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="6919b-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="6919b-121">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="6919b-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="6919b-122">當元件載入至完全信任<xref:System.AppDomain>時, 會驗證完全信任元件上的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="6919b-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="6919b-123">強式名稱簽章只會檢查簽名碼正確性;它不會與另一個強式名稱進行比較, 以符合相符項。</span><span class="sxs-lookup"><span data-stu-id="6919b-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6919b-124">子元素</span><span class="sxs-lookup"><span data-stu-id="6919b-124">Child Elements</span></span>  
 <span data-ttu-id="6919b-125">無。</span><span class="sxs-lookup"><span data-stu-id="6919b-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6919b-126">父項目</span><span class="sxs-lookup"><span data-stu-id="6919b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="6919b-127">項目</span><span class="sxs-lookup"><span data-stu-id="6919b-127">Element</span></span>|<span data-ttu-id="6919b-128">描述</span><span class="sxs-lookup"><span data-stu-id="6919b-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6919b-129">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6919b-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6919b-130">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="6919b-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6919b-131">備註</span><span class="sxs-lookup"><span data-stu-id="6919b-131">Remarks</span></span>  
 <span data-ttu-id="6919b-132">強式名稱略過功能可避免完全信任元件的強式名稱簽章驗證的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="6919b-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="6919b-133">略過功能適用於任何以強式名稱簽署並具有下列特性的組件：</span><span class="sxs-lookup"><span data-stu-id="6919b-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
- <span data-ttu-id="6919b-134">完全信任而不<xref:System.Security.Policy.StrongName>含辨識項 (例如, `MyComputer`具有區域辨識項)。</span><span class="sxs-lookup"><span data-stu-id="6919b-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
- <span data-ttu-id="6919b-135">載入到完全信任的 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="6919b-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="6919b-136">從 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性下的位置載入。</span><span class="sxs-lookup"><span data-stu-id="6919b-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="6919b-137">不延遲簽署。</span><span class="sxs-lookup"><span data-stu-id="6919b-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6919b-138">若已使用登錄機碼為電腦上的所有應用程式關閉略過功能, 此設定檔案設定就不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="6919b-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="6919b-139">如需詳細資訊，請參閱[如何：停用強式名稱略過功能](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)。</span><span class="sxs-lookup"><span data-stu-id="6919b-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6919b-140">範例</span><span class="sxs-lookup"><span data-stu-id="6919b-140">Example</span></span>  
 <span data-ttu-id="6919b-141">下列範例顯示如何指定行為, 以驗證完全信任元件上的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="6919b-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6919b-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6919b-142">See also</span></span>

- [<span data-ttu-id="6919b-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6919b-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6919b-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="6919b-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6919b-145">如何：停用強式名稱略過功能</span><span class="sxs-lookup"><span data-stu-id="6919b-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)
