---
title: <generatePublisherEvidence> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645350"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="bf652-102">\<generatePublisherEvidence> 元素</span><span class="sxs-lookup"><span data-stu-id="bf652-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="bf652-103">指定運行時是否為代碼存<xref:System.Security.Policy.Publisher>取 安全性 (CAS) 創建證據。</span><span class="sxs-lookup"><span data-stu-id="bf652-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="bf652-104">[**\<設定>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf652-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bf652-105">&nbsp;&nbsp;[**\<執行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf652-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="bf652-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<產生發行者證據>**</span><span class="sxs-lookup"><span data-stu-id="bf652-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf652-107">語法</span><span class="sxs-lookup"><span data-stu-id="bf652-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf652-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bf652-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bf652-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bf652-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf652-110">屬性</span><span class="sxs-lookup"><span data-stu-id="bf652-110">Attributes</span></span>  
  
|<span data-ttu-id="bf652-111">屬性</span><span class="sxs-lookup"><span data-stu-id="bf652-111">Attribute</span></span>|<span data-ttu-id="bf652-112">描述</span><span class="sxs-lookup"><span data-stu-id="bf652-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bf652-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="bf652-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bf652-114">指定執行時是否創建<xref:System.Security.Policy.Publisher>證據。</span><span class="sxs-lookup"><span data-stu-id="bf652-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bf652-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="bf652-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bf652-116">值</span><span class="sxs-lookup"><span data-stu-id="bf652-116">Value</span></span>|<span data-ttu-id="bf652-117">描述</span><span class="sxs-lookup"><span data-stu-id="bf652-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="bf652-118">不創建<xref:System.Security.Policy.Publisher>證據。</span><span class="sxs-lookup"><span data-stu-id="bf652-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="bf652-119">創建<xref:System.Security.Policy.Publisher>證據。</span><span class="sxs-lookup"><span data-stu-id="bf652-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="bf652-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="bf652-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf652-121">子元素</span><span class="sxs-lookup"><span data-stu-id="bf652-121">Child Elements</span></span>  
 <span data-ttu-id="bf652-122">無。</span><span class="sxs-lookup"><span data-stu-id="bf652-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf652-123">父項目</span><span class="sxs-lookup"><span data-stu-id="bf652-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bf652-124">元素</span><span class="sxs-lookup"><span data-stu-id="bf652-124">Element</span></span>|<span data-ttu-id="bf652-125">描述</span><span class="sxs-lookup"><span data-stu-id="bf652-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf652-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bf652-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bf652-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="bf652-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf652-128">備註</span><span class="sxs-lookup"><span data-stu-id="bf652-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf652-129">在 .NET 框架 4 及更高版本中,此元素對程式集載入時間沒有影響。</span><span class="sxs-lookup"><span data-stu-id="bf652-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="bf652-130">有關詳細資訊,請參閱[安全更改](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)中的"安全策略簡化"部分。</span><span class="sxs-lookup"><span data-stu-id="bf652-130">For more information, see the "Security Policy Simplification" section in [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="bf652-131">通用語言執行時 (CLR) 嘗試在載入時驗證身份驗證簽名,以創建<xref:System.Security.Policy.Publisher>程式集 的證據。</span><span class="sxs-lookup"><span data-stu-id="bf652-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="bf652-132">但是,默認情況下,大多數應用程式不需要<xref:System.Security.Policy.Publisher>證據。</span><span class="sxs-lookup"><span data-stu-id="bf652-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="bf652-133">標準 CAS 政策不<xref:System.Security.Policy.PublisherMembershipCondition>依賴於 。</span><span class="sxs-lookup"><span data-stu-id="bf652-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="bf652-134">您應該避免與驗證發行者簽名相關的不必要的啟動成本,除非您的應用程式在具有自訂 CAS 策略的電腦上執行,或者打算滿足部分信任環境<xref:System.Security.Permissions.PublisherIdentityPermission>中的需求 。</span><span class="sxs-lookup"><span data-stu-id="bf652-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="bf652-135">(對標識許可權的要求總是在完全信任的環境中成功。</span><span class="sxs-lookup"><span data-stu-id="bf652-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf652-136">我們建議服務使用`<generatePublisherEvidence>`元素來提高啟動性能。</span><span class="sxs-lookup"><span data-stu-id="bf652-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="bf652-137">使用此元素還有助於避免可能導致超時和服務啟動取消的延遲。</span><span class="sxs-lookup"><span data-stu-id="bf652-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="bf652-138">組態檔</span><span class="sxs-lookup"><span data-stu-id="bf652-138">Configuration File</span></span>  
 <span data-ttu-id="bf652-139">此元素只能在應用程式配置檔中使用。</span><span class="sxs-lookup"><span data-stu-id="bf652-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf652-140">範例</span><span class="sxs-lookup"><span data-stu-id="bf652-140">Example</span></span>  
 <span data-ttu-id="bf652-141">下面的範例展示如何使用`<generatePublisherEvidence>`元素來禁用檢查應用程式的 CAS 發行者策略。</span><span class="sxs-lookup"><span data-stu-id="bf652-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf652-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf652-142">See also</span></span>

- [<span data-ttu-id="bf652-143">執行時設定架構</span><span class="sxs-lookup"><span data-stu-id="bf652-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bf652-144">設定檔案架構</span><span class="sxs-lookup"><span data-stu-id="bf652-144">Configuration File Schema</span></span>](../index.md)
