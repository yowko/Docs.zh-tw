---
title: <generatePublisherEvidence> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 24a5ea02992a5bce681b5bab4fb7f75505bd225d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154098"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="48779-102">\<generatePublisherEvidence> 元素</span><span class="sxs-lookup"><span data-stu-id="48779-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="48779-103">指定運行時是否為代碼訪問<xref:System.Security.Policy.Publisher>安全性 （CAS） 創建證據。</span><span class="sxs-lookup"><span data-stu-id="48779-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="48779-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="48779-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="48779-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="48779-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="48779-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<生成發行者證據>**</span><span class="sxs-lookup"><span data-stu-id="48779-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48779-107">語法</span><span class="sxs-lookup"><span data-stu-id="48779-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48779-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="48779-108">Attributes and Elements</span></span>  
 <span data-ttu-id="48779-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="48779-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48779-110">屬性</span><span class="sxs-lookup"><span data-stu-id="48779-110">Attributes</span></span>  
  
|<span data-ttu-id="48779-111">屬性</span><span class="sxs-lookup"><span data-stu-id="48779-111">Attribute</span></span>|<span data-ttu-id="48779-112">描述</span><span class="sxs-lookup"><span data-stu-id="48779-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="48779-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="48779-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="48779-114">指定運行時是否創建<xref:System.Security.Policy.Publisher>證據。</span><span class="sxs-lookup"><span data-stu-id="48779-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="48779-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="48779-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="48779-116">值</span><span class="sxs-lookup"><span data-stu-id="48779-116">Value</span></span>|<span data-ttu-id="48779-117">描述</span><span class="sxs-lookup"><span data-stu-id="48779-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="48779-118">不創建<xref:System.Security.Policy.Publisher>證據。</span><span class="sxs-lookup"><span data-stu-id="48779-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="48779-119">創建<xref:System.Security.Policy.Publisher>證據。</span><span class="sxs-lookup"><span data-stu-id="48779-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="48779-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="48779-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48779-121">子元素</span><span class="sxs-lookup"><span data-stu-id="48779-121">Child Elements</span></span>  
 <span data-ttu-id="48779-122">無。</span><span class="sxs-lookup"><span data-stu-id="48779-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48779-123">父項目</span><span class="sxs-lookup"><span data-stu-id="48779-123">Parent Elements</span></span>  
  
|<span data-ttu-id="48779-124">元素</span><span class="sxs-lookup"><span data-stu-id="48779-124">Element</span></span>|<span data-ttu-id="48779-125">描述</span><span class="sxs-lookup"><span data-stu-id="48779-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="48779-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="48779-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="48779-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="48779-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48779-128">備註</span><span class="sxs-lookup"><span data-stu-id="48779-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48779-129">在 .NET 框架 4 及更高版本中，此元素對程式集載入時間沒有影響。</span><span class="sxs-lookup"><span data-stu-id="48779-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="48779-130">有關詳細資訊，請參閱[安全更改](../../../security/security-changes.md)中的"安全性原則簡化"部分。</span><span class="sxs-lookup"><span data-stu-id="48779-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="48779-131">通用語言運行時 （CLR） 嘗試在載入時驗證身份驗證簽名，以創建程式集<xref:System.Security.Policy.Publisher>的證據。</span><span class="sxs-lookup"><span data-stu-id="48779-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="48779-132">但是，預設情況下，大多數應用程式不需要<xref:System.Security.Policy.Publisher>證據。</span><span class="sxs-lookup"><span data-stu-id="48779-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="48779-133">標準 CAS 策略不依賴于<xref:System.Security.Policy.PublisherMembershipCondition>。</span><span class="sxs-lookup"><span data-stu-id="48779-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="48779-134">您應該避免與驗證發行者簽名相關的不必要的啟動成本，除非您的應用程式在具有自訂 CAS 策略的電腦上執行，或者打算滿足部分信任環境中的需求<xref:System.Security.Permissions.PublisherIdentityPermission>。</span><span class="sxs-lookup"><span data-stu-id="48779-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="48779-135">（對標識許可權的要求總是在完全信任的環境中成功。</span><span class="sxs-lookup"><span data-stu-id="48779-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48779-136">我們建議服務使用 元素`<generatePublisherEvidence>`來提高啟動性能。</span><span class="sxs-lookup"><span data-stu-id="48779-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="48779-137">使用此元素還有助於避免可能導致超時和服務啟動取消的延遲。</span><span class="sxs-lookup"><span data-stu-id="48779-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="48779-138">組態檔</span><span class="sxs-lookup"><span data-stu-id="48779-138">Configuration File</span></span>  
 <span data-ttu-id="48779-139">此元素只能在應用程式佈建檔中使用。</span><span class="sxs-lookup"><span data-stu-id="48779-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48779-140">範例</span><span class="sxs-lookup"><span data-stu-id="48779-140">Example</span></span>  
 <span data-ttu-id="48779-141">下面的示例演示如何使用 元素`<generatePublisherEvidence>`來禁用檢查應用程式的 CAS 發行者策略。</span><span class="sxs-lookup"><span data-stu-id="48779-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48779-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48779-142">See also</span></span>

- [<span data-ttu-id="48779-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="48779-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="48779-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="48779-144">Configuration File Schema</span></span>](../index.md)
