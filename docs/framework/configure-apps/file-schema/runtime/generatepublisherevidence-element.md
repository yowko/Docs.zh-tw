---
title: <generatePublisherEvidence> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 11592b055641c0fa2d2b968547dcc5aa40c94600
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541780"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="2b6b5-102">\<generatePublisherEvidence> 項目</span><span class="sxs-lookup"><span data-stu-id="2b6b5-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="2b6b5-103">指定執行時間是否 <xref:System.Security.Policy.Publisher> 為代碼啟用安全性建立證據， (CAS) 。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a><span data-ttu-id="2b6b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b6b5-104">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b6b5-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2b6b5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2b6b5-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b6b5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="2b6b5-107">Attributes</span></span>  
  
|<span data-ttu-id="2b6b5-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2b6b5-108">Attribute</span></span>|<span data-ttu-id="2b6b5-109">描述</span><span class="sxs-lookup"><span data-stu-id="2b6b5-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2b6b5-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="2b6b5-111">指定執行時間是否要建立辨識項 <xref:System.Security.Policy.Publisher> 。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-111">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2b6b5-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="2b6b5-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="2b6b5-113">值</span><span class="sxs-lookup"><span data-stu-id="2b6b5-113">Value</span></span>|<span data-ttu-id="2b6b5-114">描述</span><span class="sxs-lookup"><span data-stu-id="2b6b5-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2b6b5-115">不會建立辨識項 <xref:System.Security.Policy.Publisher> 。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-115">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="2b6b5-116">建立辨識項 <xref:System.Security.Policy.Publisher> 。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-116">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="2b6b5-117">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-117">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b6b5-118">子元素</span><span class="sxs-lookup"><span data-stu-id="2b6b5-118">Child Elements</span></span>  
 <span data-ttu-id="2b6b5-119">無。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b6b5-120">父項目</span><span class="sxs-lookup"><span data-stu-id="2b6b5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2b6b5-121">項目</span><span class="sxs-lookup"><span data-stu-id="2b6b5-121">Element</span></span>|<span data-ttu-id="2b6b5-122">描述</span><span class="sxs-lookup"><span data-stu-id="2b6b5-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2b6b5-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2b6b5-124">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b6b5-125">備註</span><span class="sxs-lookup"><span data-stu-id="2b6b5-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b6b5-126">在 .NET Framework 4 和更新版本中，此元素不會影響元件載入時間。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-126">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="2b6b5-127">如需詳細資訊，請參閱 [安全性變更](/previous-versions/dotnet/framework/security/security-changes)中的「安全性原則簡化」一節。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-127">For more information, see the "Security Policy Simplification" section in [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="2b6b5-128">Common language runtime (CLR) 會嘗試在載入時驗證 Authenticode 簽章，以建立元件的辨識項 <xref:System.Security.Policy.Publisher> 。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-128">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="2b6b5-129">不過，根據預設，大部分的應用程式都不需要辨識項 <xref:System.Security.Policy.Publisher> 。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-129">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="2b6b5-130">標準 CAS 原則不依賴 <xref:System.Security.Policy.PublisherMembershipCondition> 。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-130">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="2b6b5-131">除非您的應用程式是在具有自訂 CAS 原則的電腦上執行，或想要 <xref:System.Security.Permissions.PublisherIdentityPermission> 在部分信任環境中滿足的需求，否則您應該避免與驗證發行者簽章相關的不必要啟動成本。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-131">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="2b6b5-132">在完全信任環境中，身分識別許可權的 (要求一律會成功。 ) </span><span class="sxs-lookup"><span data-stu-id="2b6b5-132">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b6b5-133">我們建議服務使用 `<generatePublisherEvidence>` 元素來改善啟動效能。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-133">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="2b6b5-134">使用這個元素也有助於避免延遲，而這可能會導致服務啟動的時間和取消。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-134">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2b6b5-135">組態檔</span><span class="sxs-lookup"><span data-stu-id="2b6b5-135">Configuration File</span></span>  
 <span data-ttu-id="2b6b5-136">此元素只能用在應用程式佈建檔中。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-136">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b6b5-137">範例</span><span class="sxs-lookup"><span data-stu-id="2b6b5-137">Example</span></span>  
 <span data-ttu-id="2b6b5-138">下列範例顯示如何使用專案 `<generatePublisherEvidence>` 來停用應用程式的 CAS 發行者原則檢查。</span><span class="sxs-lookup"><span data-stu-id="2b6b5-138">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b6b5-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b6b5-139">See also</span></span>

- [<span data-ttu-id="2b6b5-140">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="2b6b5-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b6b5-141">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="2b6b5-141">Configuration File Schema</span></span>](../index.md)
