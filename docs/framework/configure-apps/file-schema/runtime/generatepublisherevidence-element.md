---
title: "&lt;generatePublisherEvidence&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 78293c396687f9c0c99ffdfbe94cf1f3c548289d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltgeneratepublisherevidencegt-element"></a><span data-ttu-id="35939-102">&lt;generatePublisherEvidence&gt;項目</span><span class="sxs-lookup"><span data-stu-id="35939-102">&lt;generatePublisherEvidence&gt; Element</span></span>
<span data-ttu-id="35939-103">指定執行階段是否會建立<xref:System.Security.Policy.Publisher>用於程式碼存取安全性 (CAS) 的辨識項。</span><span class="sxs-lookup"><span data-stu-id="35939-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="35939-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="35939-104">\<configuration></span></span>  
<span data-ttu-id="35939-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="35939-105">\<runtime></span></span>  
<span data-ttu-id="35939-106">\<generatePublisherEvidence ></span><span class="sxs-lookup"><span data-stu-id="35939-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35939-107">語法</span><span class="sxs-lookup"><span data-stu-id="35939-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35939-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="35939-108">Attributes and Elements</span></span>  
 <span data-ttu-id="35939-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="35939-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35939-110">屬性</span><span class="sxs-lookup"><span data-stu-id="35939-110">Attributes</span></span>  
  
|<span data-ttu-id="35939-111">屬性</span><span class="sxs-lookup"><span data-stu-id="35939-111">Attribute</span></span>|<span data-ttu-id="35939-112">描述</span><span class="sxs-lookup"><span data-stu-id="35939-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="35939-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="35939-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="35939-114">指定執行階段是否會建立<xref:System.Security.Policy.Publisher>辨識項。</span><span class="sxs-lookup"><span data-stu-id="35939-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="35939-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="35939-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="35939-116">值</span><span class="sxs-lookup"><span data-stu-id="35939-116">Value</span></span>|<span data-ttu-id="35939-117">說明</span><span class="sxs-lookup"><span data-stu-id="35939-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="35939-118">不會建立<xref:System.Security.Policy.Publisher>辨識項。</span><span class="sxs-lookup"><span data-stu-id="35939-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="35939-119">建立<xref:System.Security.Policy.Publisher>辨識項。</span><span class="sxs-lookup"><span data-stu-id="35939-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="35939-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="35939-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35939-121">子元素</span><span class="sxs-lookup"><span data-stu-id="35939-121">Child Elements</span></span>  
 <span data-ttu-id="35939-122">無。</span><span class="sxs-lookup"><span data-stu-id="35939-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35939-123">父項目</span><span class="sxs-lookup"><span data-stu-id="35939-123">Parent Elements</span></span>  
  
|<span data-ttu-id="35939-124">項目</span><span class="sxs-lookup"><span data-stu-id="35939-124">Element</span></span>|<span data-ttu-id="35939-125">描述</span><span class="sxs-lookup"><span data-stu-id="35939-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="35939-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="35939-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="35939-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="35939-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35939-128">備註</span><span class="sxs-lookup"><span data-stu-id="35939-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35939-129">在[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]和更新版本中，這個項目具有組件載入時間不會影響。</span><span class="sxs-lookup"><span data-stu-id="35939-129">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="35939-130">如需詳細資訊，請參閱中的 「 安全性原則簡化 」 一節[安全性變更](../../../../../docs/framework/security/security-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="35939-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="35939-131">Common language runtime (CLR) 會嘗試驗證 Authenticode 簽章在載入時間，以建立<xref:System.Security.Policy.Publisher>組件的辨識項。</span><span class="sxs-lookup"><span data-stu-id="35939-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="35939-132">不過，根據預設，大部分的應用程式不需要<xref:System.Security.Policy.Publisher>辨識項。</span><span class="sxs-lookup"><span data-stu-id="35939-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="35939-133">標準的 CAS 原則不會依賴<xref:System.Security.Policy.PublisherMembershipCondition>。</span><span class="sxs-lookup"><span data-stu-id="35939-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="35939-134">您應該避免與驗證的簽章，除非應用程式具有自訂的 CAS 原則的電腦上執行，或想要滿足需求的相關聯的不必要的啟動成本<xref:System.Security.Permissions.PublisherIdentityPermission>在部分信任環境中。</span><span class="sxs-lookup"><span data-stu-id="35939-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="35939-135">（一律要求的識別權限成功在完全信任環境中）。</span><span class="sxs-lookup"><span data-stu-id="35939-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35939-136">我們建議，服務會使用`<generatePublisherEvidence>`項目，以改善啟動效能。</span><span class="sxs-lookup"><span data-stu-id="35939-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="35939-137">使用這個項目，也有助於避免逾時和服務啟動後取消可能會造成的延遲。</span><span class="sxs-lookup"><span data-stu-id="35939-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="35939-138">組態檔</span><span class="sxs-lookup"><span data-stu-id="35939-138">Configuration File</span></span>  
 <span data-ttu-id="35939-139">此項目只能用於應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="35939-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35939-140">範例</span><span class="sxs-lookup"><span data-stu-id="35939-140">Example</span></span>  
 <span data-ttu-id="35939-141">下列範例示範如何使用`<generatePublisherEvidence>`停用檢查 CA 發行者原則中的應用程式的項目。</span><span class="sxs-lookup"><span data-stu-id="35939-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35939-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35939-142">See Also</span></span>  
 [<span data-ttu-id="35939-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="35939-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="35939-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="35939-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
