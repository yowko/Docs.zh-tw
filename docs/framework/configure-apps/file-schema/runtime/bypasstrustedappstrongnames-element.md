---
title: '&lt;bypassTrustedAppStrongNames&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6988be28e3129748ee7f7996a66c728ccde3c70b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745379"
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a><span data-ttu-id="5a387-102">&lt;bypassTrustedAppStrongNames&gt;項目</span><span class="sxs-lookup"><span data-stu-id="5a387-102">&lt;bypassTrustedAppStrongNames&gt; Element</span></span>
<span data-ttu-id="5a387-103">指定是否略過強式名稱的完全信任組件載入至完全信任的驗證<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="5a387-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="5a387-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5a387-104">\<configuration></span></span>  
<span data-ttu-id="5a387-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="5a387-105">\<runtime></span></span>  
<span data-ttu-id="5a387-106">\<bypassTrustedAppStrongNames ></span><span class="sxs-lookup"><span data-stu-id="5a387-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a387-107">語法</span><span class="sxs-lookup"><span data-stu-id="5a387-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a387-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a387-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5a387-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5a387-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a387-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5a387-110">Attributes</span></span>  
  
|<span data-ttu-id="5a387-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5a387-111">Attribute</span></span>|<span data-ttu-id="5a387-112">描述</span><span class="sxs-lookup"><span data-stu-id="5a387-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5a387-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5a387-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5a387-114">指定是否啟用不驗證完全信任組件的強式名稱略過功能。</span><span class="sxs-lookup"><span data-stu-id="5a387-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="5a387-115">啟用這項功能時，強式名稱不會驗證正確載入組件時。</span><span class="sxs-lookup"><span data-stu-id="5a387-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="5a387-116">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5a387-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5a387-117">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="5a387-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="5a387-118">值</span><span class="sxs-lookup"><span data-stu-id="5a387-118">Value</span></span>|<span data-ttu-id="5a387-119">描述</span><span class="sxs-lookup"><span data-stu-id="5a387-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="5a387-120">載入至完全信任組件時，不會驗證完整信任組件的強式名稱簽章<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="5a387-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="5a387-121">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="5a387-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="5a387-122">在完全信任組件的強式名稱簽章會驗證載入至完全信任組件時<xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="5a387-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="5a387-123">強式名稱簽章只會檢查簽章正確。它不會與另一個的強式名稱的相符項目。</span><span class="sxs-lookup"><span data-stu-id="5a387-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a387-124">子項目</span><span class="sxs-lookup"><span data-stu-id="5a387-124">Child Elements</span></span>  
 <span data-ttu-id="5a387-125">無。</span><span class="sxs-lookup"><span data-stu-id="5a387-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a387-126">父項目</span><span class="sxs-lookup"><span data-stu-id="5a387-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5a387-127">項目</span><span class="sxs-lookup"><span data-stu-id="5a387-127">Element</span></span>|<span data-ttu-id="5a387-128">描述</span><span class="sxs-lookup"><span data-stu-id="5a387-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a387-129">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5a387-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5a387-130">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="5a387-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a387-131">備註</span><span class="sxs-lookup"><span data-stu-id="5a387-131">Remarks</span></span>  
 <span data-ttu-id="5a387-132">強式名稱略過功能可以避免完全信任組件的強式名稱簽章驗證的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="5a387-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="5a387-133">略過功能適用於任何以強式名稱簽署並具有下列特性的組件：</span><span class="sxs-lookup"><span data-stu-id="5a387-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="5a387-134">不完全受信任<xref:System.Security.Policy.StrongName>辨識項 (例如，具有`MyComputer`區域辨識項)。</span><span class="sxs-lookup"><span data-stu-id="5a387-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="5a387-135">載入到完全信任的 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="5a387-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="5a387-136">從 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性下的位置載入。</span><span class="sxs-lookup"><span data-stu-id="5a387-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="5a387-137">不延遲簽署。</span><span class="sxs-lookup"><span data-stu-id="5a387-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a387-138">如果略過功能已關閉的電腦上的所有應用程式使用的登錄機碼，此組態檔設定沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="5a387-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="5a387-139">如需詳細資訊，請參閱[如何： 停用強式名稱略過功能](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)。</span><span class="sxs-lookup"><span data-stu-id="5a387-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a387-140">範例</span><span class="sxs-lookup"><span data-stu-id="5a387-140">Example</span></span>  
 <span data-ttu-id="5a387-141">下列範例會示範如何指定會在完全信任組件的強式名稱簽章驗證的行為。</span><span class="sxs-lookup"><span data-stu-id="5a387-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a387-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a387-142">See Also</span></span>  
 [<span data-ttu-id="5a387-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5a387-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5a387-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5a387-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5a387-145">如何：停用強式名稱略過功能</span><span class="sxs-lookup"><span data-stu-id="5a387-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
