---
title: '&lt;generatePublisherEvidence&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f56bbef6ed6decf6be4246f649665db4cf0f766
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltgeneratepublisherevidencegt-element"></a><span data-ttu-id="0b74a-102">&lt;generatePublisherEvidence&gt;項目</span><span class="sxs-lookup"><span data-stu-id="0b74a-102">&lt;generatePublisherEvidence&gt; Element</span></span>
<span data-ttu-id="0b74a-103">指定執行階段是否會建立<xref:System.Security.Policy.Publisher>用於程式碼存取安全性 (CAS) 的辨識項。</span><span class="sxs-lookup"><span data-stu-id="0b74a-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="0b74a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0b74a-104">\<configuration></span></span>  
<span data-ttu-id="0b74a-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="0b74a-105">\<runtime></span></span>  
<span data-ttu-id="0b74a-106">\<generatePublisherEvidence ></span><span class="sxs-lookup"><span data-stu-id="0b74a-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b74a-107">語法</span><span class="sxs-lookup"><span data-stu-id="0b74a-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b74a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0b74a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0b74a-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0b74a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b74a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0b74a-110">Attributes</span></span>  
  
|<span data-ttu-id="0b74a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0b74a-111">Attribute</span></span>|<span data-ttu-id="0b74a-112">描述</span><span class="sxs-lookup"><span data-stu-id="0b74a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0b74a-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0b74a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0b74a-114">指定執行階段是否會建立<xref:System.Security.Policy.Publisher>辨識項。</span><span class="sxs-lookup"><span data-stu-id="0b74a-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0b74a-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="0b74a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="0b74a-116">值</span><span class="sxs-lookup"><span data-stu-id="0b74a-116">Value</span></span>|<span data-ttu-id="0b74a-117">描述</span><span class="sxs-lookup"><span data-stu-id="0b74a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0b74a-118">不會建立<xref:System.Security.Policy.Publisher>辨識項。</span><span class="sxs-lookup"><span data-stu-id="0b74a-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="0b74a-119">建立<xref:System.Security.Policy.Publisher>辨識項。</span><span class="sxs-lookup"><span data-stu-id="0b74a-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="0b74a-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="0b74a-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b74a-121">子項目</span><span class="sxs-lookup"><span data-stu-id="0b74a-121">Child Elements</span></span>  
 <span data-ttu-id="0b74a-122">無。</span><span class="sxs-lookup"><span data-stu-id="0b74a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b74a-123">父項目</span><span class="sxs-lookup"><span data-stu-id="0b74a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0b74a-124">項目</span><span class="sxs-lookup"><span data-stu-id="0b74a-124">Element</span></span>|<span data-ttu-id="0b74a-125">描述</span><span class="sxs-lookup"><span data-stu-id="0b74a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0b74a-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0b74a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0b74a-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="0b74a-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b74a-128">備註</span><span class="sxs-lookup"><span data-stu-id="0b74a-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b74a-129">在[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]和更新版本中，這個項目具有組件載入時間不會影響。</span><span class="sxs-lookup"><span data-stu-id="0b74a-129">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="0b74a-130">如需詳細資訊，請參閱中的 「 安全性原則簡化 」 一節[安全性變更](../../../../../docs/framework/security/security-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="0b74a-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="0b74a-131">Common language runtime (CLR) 會嘗試驗證 Authenticode 簽章在載入時間，以建立<xref:System.Security.Policy.Publisher>組件的辨識項。</span><span class="sxs-lookup"><span data-stu-id="0b74a-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="0b74a-132">不過，根據預設，大部分的應用程式不需要<xref:System.Security.Policy.Publisher>辨識項。</span><span class="sxs-lookup"><span data-stu-id="0b74a-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="0b74a-133">標準的 CAS 原則不會依賴<xref:System.Security.Policy.PublisherMembershipCondition>。</span><span class="sxs-lookup"><span data-stu-id="0b74a-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="0b74a-134">您應該避免與驗證的簽章，除非應用程式具有自訂的 CAS 原則的電腦上執行，或想要滿足需求的相關聯的不必要的啟動成本<xref:System.Security.Permissions.PublisherIdentityPermission>在部分信任環境中。</span><span class="sxs-lookup"><span data-stu-id="0b74a-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="0b74a-135">（一律要求的識別權限成功在完全信任環境中）。</span><span class="sxs-lookup"><span data-stu-id="0b74a-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b74a-136">我們建議，服務會使用`<generatePublisherEvidence>`項目，以改善啟動效能。</span><span class="sxs-lookup"><span data-stu-id="0b74a-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="0b74a-137">使用這個項目，也有助於避免逾時和服務啟動後取消可能會造成的延遲。</span><span class="sxs-lookup"><span data-stu-id="0b74a-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0b74a-138">組態檔</span><span class="sxs-lookup"><span data-stu-id="0b74a-138">Configuration File</span></span>  
 <span data-ttu-id="0b74a-139">此項目只能用於應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="0b74a-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b74a-140">範例</span><span class="sxs-lookup"><span data-stu-id="0b74a-140">Example</span></span>  
 <span data-ttu-id="0b74a-141">下列範例示範如何使用`<generatePublisherEvidence>`停用檢查 CA 發行者原則中的應用程式的項目。</span><span class="sxs-lookup"><span data-stu-id="0b74a-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b74a-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b74a-142">See Also</span></span>  
 [<span data-ttu-id="0b74a-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0b74a-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="0b74a-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="0b74a-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
