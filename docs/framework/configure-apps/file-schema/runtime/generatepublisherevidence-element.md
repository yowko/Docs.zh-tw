---
title: <generatePublisherEvidence> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: b04ef53d6e9c3d954b0925ea8634b3d220b36af7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116581"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="3e8f9-102">\<generatePublisherEvidence > 元素</span><span class="sxs-lookup"><span data-stu-id="3e8f9-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="3e8f9-103">指定執行時間是否建立代碼啟用安全性（CAS） <xref:System.Security.Policy.Publisher> 辨識項。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="3e8f9-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e8f9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3e8f9-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="3e8f9-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="3e8f9-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<generatePublisherEvidence >**</span><span class="sxs-lookup"><span data-stu-id="3e8f9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e8f9-107">語法</span><span class="sxs-lookup"><span data-stu-id="3e8f9-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e8f9-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3e8f9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3e8f9-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e8f9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3e8f9-110">Attributes</span></span>  
  
|<span data-ttu-id="3e8f9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3e8f9-111">Attribute</span></span>|<span data-ttu-id="3e8f9-112">描述</span><span class="sxs-lookup"><span data-stu-id="3e8f9-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3e8f9-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3e8f9-114">指定執行時間是否建立 <xref:System.Security.Policy.Publisher> 辨識項。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3e8f9-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="3e8f9-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3e8f9-116">值</span><span class="sxs-lookup"><span data-stu-id="3e8f9-116">Value</span></span>|<span data-ttu-id="3e8f9-117">描述</span><span class="sxs-lookup"><span data-stu-id="3e8f9-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3e8f9-118">不會建立 <xref:System.Security.Policy.Publisher> 辨識項。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="3e8f9-119">建立 <xref:System.Security.Policy.Publisher> 辨識項。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="3e8f9-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e8f9-121">子項目</span><span class="sxs-lookup"><span data-stu-id="3e8f9-121">Child Elements</span></span>  
 <span data-ttu-id="3e8f9-122">無。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e8f9-123">父項目</span><span class="sxs-lookup"><span data-stu-id="3e8f9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3e8f9-124">項目</span><span class="sxs-lookup"><span data-stu-id="3e8f9-124">Element</span></span>|<span data-ttu-id="3e8f9-125">描述</span><span class="sxs-lookup"><span data-stu-id="3e8f9-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3e8f9-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3e8f9-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e8f9-128">備註</span><span class="sxs-lookup"><span data-stu-id="3e8f9-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e8f9-129">在 .NET Framework 4 和更新版本中，這個元素不會影響元件載入時間。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="3e8f9-130">如需詳細資訊，請參閱[安全性變更](../../../security/security-changes.md)中的「安全性原則簡化」一節。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="3e8f9-131">Common language runtime （CLR）會在載入時嘗試驗證 Authenticode 簽章，以建立元件 <xref:System.Security.Policy.Publisher> 辨識項。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="3e8f9-132">不過，根據預設，大部分的應用程式都不需要 <xref:System.Security.Policy.Publisher> 辨識項。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="3e8f9-133">標準 CAS 原則不依賴 <xref:System.Security.Policy.PublisherMembershipCondition>。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="3e8f9-134">除非您的應用程式是在具有自訂 CAS 原則的電腦上執行，或想要滿足部分信任環境中 <xref:System.Security.Permissions.PublisherIdentityPermission> 的需求，否則您應該避免與驗證發行者簽章相關聯的不必要啟動成本。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="3e8f9-135">（在完全信任環境中，身分識別許可權的需求一律會成功）。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e8f9-136">我們建議服務使用 `<generatePublisherEvidence>` 元素來改善啟動效能。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="3e8f9-137">使用這個元素也有助於避免延遲，這可能會造成超時和取消服務啟動。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3e8f9-138">組態檔</span><span class="sxs-lookup"><span data-stu-id="3e8f9-138">Configuration File</span></span>  
 <span data-ttu-id="3e8f9-139">這個元素只能用在應用程式佈建檔中。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e8f9-140">範例</span><span class="sxs-lookup"><span data-stu-id="3e8f9-140">Example</span></span>  
 <span data-ttu-id="3e8f9-141">下列範例示範如何使用 `<generatePublisherEvidence>` 專案來停用應用程式的 CAS 發行者原則檢查。</span><span class="sxs-lookup"><span data-stu-id="3e8f9-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e8f9-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e8f9-142">See also</span></span>

- [<span data-ttu-id="3e8f9-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3e8f9-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3e8f9-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="3e8f9-144">Configuration File Schema</span></span>](../index.md)
