---
title: '&lt;Bypasstrustedappstrongnames>&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 725e2ee19c97cf2642134058ece07b32455516a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565471"
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a><span data-ttu-id="451e3-102">&lt;Bypasstrustedappstrongnames>&gt;項目</span><span class="sxs-lookup"><span data-stu-id="451e3-102">&lt;bypassTrustedAppStrongNames&gt; Element</span></span>
<span data-ttu-id="451e3-103">指定是否略過載入至完全信任的完全信任組件的強式名稱的驗證<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="451e3-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="451e3-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="451e3-104">\<configuration></span></span>  
<span data-ttu-id="451e3-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="451e3-105">\<runtime></span></span>  
<span data-ttu-id="451e3-106">\<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="451e3-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="451e3-107">語法</span><span class="sxs-lookup"><span data-stu-id="451e3-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="451e3-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="451e3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="451e3-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="451e3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="451e3-110">屬性</span><span class="sxs-lookup"><span data-stu-id="451e3-110">Attributes</span></span>  
  
|<span data-ttu-id="451e3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="451e3-111">Attribute</span></span>|<span data-ttu-id="451e3-112">描述</span><span class="sxs-lookup"><span data-stu-id="451e3-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="451e3-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="451e3-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="451e3-114">指定是否啟用可避免驗證完全信任組件的強式名稱略過功能。</span><span class="sxs-lookup"><span data-stu-id="451e3-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="451e3-115">啟用這項功能時，強式名稱不會驗證正確載入的組件時。</span><span class="sxs-lookup"><span data-stu-id="451e3-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="451e3-116">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="451e3-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="451e3-117">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="451e3-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="451e3-118">值</span><span class="sxs-lookup"><span data-stu-id="451e3-118">Value</span></span>|<span data-ttu-id="451e3-119">描述</span><span class="sxs-lookup"><span data-stu-id="451e3-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="451e3-120">載入至完全信任組件時，不會驗證在完全信任組件的強式名稱簽章<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="451e3-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="451e3-121">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="451e3-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="451e3-122">在完全信任組件的強式名稱簽章會驗證載入至完全信任組件時<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="451e3-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="451e3-123">強式名稱簽章只會檢查簽章正確性;它不是相較於另一個比對的強式名稱。</span><span class="sxs-lookup"><span data-stu-id="451e3-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="451e3-124">子元素</span><span class="sxs-lookup"><span data-stu-id="451e3-124">Child Elements</span></span>  
 <span data-ttu-id="451e3-125">無。</span><span class="sxs-lookup"><span data-stu-id="451e3-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="451e3-126">父項目</span><span class="sxs-lookup"><span data-stu-id="451e3-126">Parent Elements</span></span>  
  
|<span data-ttu-id="451e3-127">項目</span><span class="sxs-lookup"><span data-stu-id="451e3-127">Element</span></span>|<span data-ttu-id="451e3-128">描述</span><span class="sxs-lookup"><span data-stu-id="451e3-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="451e3-129">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="451e3-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="451e3-130">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="451e3-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="451e3-131">備註</span><span class="sxs-lookup"><span data-stu-id="451e3-131">Remarks</span></span>  
 <span data-ttu-id="451e3-132">強式名稱略過功能可避免完全信任組件的強式名稱簽章驗證的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="451e3-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="451e3-133">略過功能適用於任何以強式名稱簽署並具有下列特性的組件：</span><span class="sxs-lookup"><span data-stu-id="451e3-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="451e3-134">而不需要完全信任<xref:System.Security.Policy.StrongName>辨識項 (例如，具有`MyComputer`區域辨識項)。</span><span class="sxs-lookup"><span data-stu-id="451e3-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="451e3-135">載入到完全信任的 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="451e3-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="451e3-136">從 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性下的位置載入。</span><span class="sxs-lookup"><span data-stu-id="451e3-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="451e3-137">不延遲簽署。</span><span class="sxs-lookup"><span data-stu-id="451e3-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="451e3-138">如果略過功能已關閉的電腦上的所有應用程式所使用的登錄機碼，此組態檔設定沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="451e3-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="451e3-139">如需詳細資訊，請參閱[＜How to：停用強式名稱略過功能](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)。</span><span class="sxs-lookup"><span data-stu-id="451e3-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="451e3-140">範例</span><span class="sxs-lookup"><span data-stu-id="451e3-140">Example</span></span>  
 <span data-ttu-id="451e3-141">下列範例示範如何指定驗證完全信任組件的強式名稱簽章的行為。</span><span class="sxs-lookup"><span data-stu-id="451e3-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="451e3-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="451e3-142">See also</span></span>
- [<span data-ttu-id="451e3-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="451e3-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="451e3-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="451e3-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="451e3-145">如何：停用強式名稱略過功能</span><span class="sxs-lookup"><span data-stu-id="451e3-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
