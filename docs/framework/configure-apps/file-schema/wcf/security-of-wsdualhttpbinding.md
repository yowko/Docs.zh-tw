---
title: '&lt;wsDualHttpBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 56755ec62c6e2c35ecdb94e4aa58903ed1216378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555933"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="38223-102">&lt;wsDualHttpBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="38223-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="38223-103">定義的安全性功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="38223-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="38223-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="38223-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="38223-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="38223-105">\<bindings></span></span>  
<span data-ttu-id="38223-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="38223-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="38223-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="38223-107">\<binding></span></span>  
<span data-ttu-id="38223-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="38223-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38223-109">語法</span><span class="sxs-lookup"><span data-stu-id="38223-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38223-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38223-110">Attributes and Elements</span></span>  
 <span data-ttu-id="38223-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="38223-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38223-112">屬性</span><span class="sxs-lookup"><span data-stu-id="38223-112">Attributes</span></span>  
  
|<span data-ttu-id="38223-113">屬性</span><span class="sxs-lookup"><span data-stu-id="38223-113">Attribute</span></span>|<span data-ttu-id="38223-114">描述</span><span class="sxs-lookup"><span data-stu-id="38223-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38223-115">模式</span><span class="sxs-lookup"><span data-stu-id="38223-115">mode</span></span>|<span data-ttu-id="38223-116">-選擇性。</span><span class="sxs-lookup"><span data-stu-id="38223-116">-   Optional.</span></span> <span data-ttu-id="38223-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="38223-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="38223-118">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="38223-118">The default value is `Message`.</span></span> <span data-ttu-id="38223-119">此屬性的型別為 <xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="38223-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="38223-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="38223-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="38223-121">值</span><span class="sxs-lookup"><span data-stu-id="38223-121">Value</span></span>|<span data-ttu-id="38223-122">描述</span><span class="sxs-lookup"><span data-stu-id="38223-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38223-123">無</span><span class="sxs-lookup"><span data-stu-id="38223-123">None</span></span>|<span data-ttu-id="38223-124">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="38223-124">Security is disabled.</span></span>|  
|<span data-ttu-id="38223-125">訊息</span><span class="sxs-lookup"><span data-stu-id="38223-125">Message</span></span>|<span data-ttu-id="38223-126">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="38223-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38223-127">子元素</span><span class="sxs-lookup"><span data-stu-id="38223-127">Child Elements</span></span>  
  
|<span data-ttu-id="38223-128">項目</span><span class="sxs-lookup"><span data-stu-id="38223-128">Element</span></span>|<span data-ttu-id="38223-129">描述</span><span class="sxs-lookup"><span data-stu-id="38223-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38223-130">\<message></span><span class="sxs-lookup"><span data-stu-id="38223-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="38223-131">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="38223-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="38223-132">此項目的型別為 <xref:System.ServiceModel.MessageSecurityOverHttp>。</span><span class="sxs-lookup"><span data-stu-id="38223-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="38223-133">父項目</span><span class="sxs-lookup"><span data-stu-id="38223-133">Parent Elements</span></span>  
  
|<span data-ttu-id="38223-134">項目</span><span class="sxs-lookup"><span data-stu-id="38223-134">Element</span></span>|<span data-ttu-id="38223-135">描述</span><span class="sxs-lookup"><span data-stu-id="38223-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38223-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="38223-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="38223-137">定義的所有繫結功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="38223-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38223-138">備註</span><span class="sxs-lookup"><span data-stu-id="38223-138">Remarks</span></span>  
 <span data-ttu-id="38223-139">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="38223-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="38223-140">用戶端應該使用安全性確保本身只連接其信任的服務。</span><span class="sxs-lookup"><span data-stu-id="38223-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38223-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38223-141">See also</span></span>
- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="38223-142">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="38223-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="38223-143">繫結</span><span class="sxs-lookup"><span data-stu-id="38223-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="38223-144">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="38223-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="38223-145">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="38223-145">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="38223-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="38223-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
