---
title: <security> 的 <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: bed7f4ce325e0d5e387e310ca15a3b72ac93f18e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936549"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="e7acc-102">\<wsDualHttpBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="e7acc-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="e7acc-103">定義[ \<wsDualHttpBinding >](wsdualhttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="e7acc-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="e7acc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e7acc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e7acc-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e7acc-105">\<bindings></span></span>  
<span data-ttu-id="e7acc-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e7acc-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="e7acc-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="e7acc-107">\<binding></span></span>  
<span data-ttu-id="e7acc-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="e7acc-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7acc-109">語法</span><span class="sxs-lookup"><span data-stu-id="e7acc-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7acc-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e7acc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e7acc-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e7acc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7acc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e7acc-112">Attributes</span></span>  
  
|<span data-ttu-id="e7acc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e7acc-113">Attribute</span></span>|<span data-ttu-id="e7acc-114">描述</span><span class="sxs-lookup"><span data-stu-id="e7acc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7acc-115">模式</span><span class="sxs-lookup"><span data-stu-id="e7acc-115">mode</span></span>|<span data-ttu-id="e7acc-116">選擇性.</span><span class="sxs-lookup"><span data-stu-id="e7acc-116">-   Optional.</span></span> <span data-ttu-id="e7acc-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="e7acc-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="e7acc-118">預設值為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="e7acc-118">The default value is `Message`.</span></span> <span data-ttu-id="e7acc-119">此屬性的型別為 <xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="e7acc-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e7acc-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="e7acc-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="e7acc-121">值</span><span class="sxs-lookup"><span data-stu-id="e7acc-121">Value</span></span>|<span data-ttu-id="e7acc-122">說明</span><span class="sxs-lookup"><span data-stu-id="e7acc-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e7acc-123">None</span><span class="sxs-lookup"><span data-stu-id="e7acc-123">None</span></span>|<span data-ttu-id="e7acc-124">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="e7acc-124">Security is disabled.</span></span>|  
|<span data-ttu-id="e7acc-125">訊息</span><span class="sxs-lookup"><span data-stu-id="e7acc-125">Message</span></span>|<span data-ttu-id="e7acc-126">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="e7acc-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7acc-127">子元素</span><span class="sxs-lookup"><span data-stu-id="e7acc-127">Child Elements</span></span>  
  
|<span data-ttu-id="e7acc-128">項目</span><span class="sxs-lookup"><span data-stu-id="e7acc-128">Element</span></span>|<span data-ttu-id="e7acc-129">說明</span><span class="sxs-lookup"><span data-stu-id="e7acc-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7acc-130">\<message></span><span class="sxs-lookup"><span data-stu-id="e7acc-130">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="e7acc-131">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="e7acc-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="e7acc-132">此項目的型別為 <xref:System.ServiceModel.MessageSecurityOverHttp>。</span><span class="sxs-lookup"><span data-stu-id="e7acc-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7acc-133">父項目</span><span class="sxs-lookup"><span data-stu-id="e7acc-133">Parent Elements</span></span>  
  
|<span data-ttu-id="e7acc-134">項目</span><span class="sxs-lookup"><span data-stu-id="e7acc-134">Element</span></span>|<span data-ttu-id="e7acc-135">描述</span><span class="sxs-lookup"><span data-stu-id="e7acc-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7acc-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="e7acc-136">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e7acc-137">定義[ \<wsDualHttpBinding >](wsdualhttpbinding.md)的所有系結功能。</span><span class="sxs-lookup"><span data-stu-id="e7acc-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7acc-138">備註</span><span class="sxs-lookup"><span data-stu-id="e7acc-138">Remarks</span></span>  
 <span data-ttu-id="e7acc-139">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="e7acc-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="e7acc-140">用戶端應該使用安全性確保本身只連接其信任的服務。</span><span class="sxs-lookup"><span data-stu-id="e7acc-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7acc-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7acc-141">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="e7acc-142">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="e7acc-142">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e7acc-143">繫結</span><span class="sxs-lookup"><span data-stu-id="e7acc-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e7acc-144">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e7acc-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e7acc-145">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="e7acc-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e7acc-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="e7acc-146">\<binding></span></span>](../../../misc/binding.md)
