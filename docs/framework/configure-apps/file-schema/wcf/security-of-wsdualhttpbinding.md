---
title: <security> 的 <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: c6f9e34724ccc3a0d05da3e1886b4f0bcbaae064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670439"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="93358-102">\<security> of \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="93358-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="93358-103">定義的安全性功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="93358-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="93358-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="93358-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="93358-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="93358-105">\<bindings></span></span>  
<span data-ttu-id="93358-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="93358-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="93358-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="93358-107">\<binding></span></span>  
<span data-ttu-id="93358-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="93358-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93358-109">語法</span><span class="sxs-lookup"><span data-stu-id="93358-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93358-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="93358-110">Attributes and Elements</span></span>  
 <span data-ttu-id="93358-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="93358-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93358-112">屬性</span><span class="sxs-lookup"><span data-stu-id="93358-112">Attributes</span></span>  
  
|<span data-ttu-id="93358-113">屬性</span><span class="sxs-lookup"><span data-stu-id="93358-113">Attribute</span></span>|<span data-ttu-id="93358-114">描述</span><span class="sxs-lookup"><span data-stu-id="93358-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93358-115">模式</span><span class="sxs-lookup"><span data-stu-id="93358-115">mode</span></span>|<span data-ttu-id="93358-116">-選擇性。</span><span class="sxs-lookup"><span data-stu-id="93358-116">-   Optional.</span></span> <span data-ttu-id="93358-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="93358-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="93358-118">預設值為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="93358-118">The default value is `Message`.</span></span> <span data-ttu-id="93358-119">此屬性的型別為 <xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="93358-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="93358-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="93358-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="93358-121">值</span><span class="sxs-lookup"><span data-stu-id="93358-121">Value</span></span>|<span data-ttu-id="93358-122">描述</span><span class="sxs-lookup"><span data-stu-id="93358-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="93358-123">None</span><span class="sxs-lookup"><span data-stu-id="93358-123">None</span></span>|<span data-ttu-id="93358-124">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="93358-124">Security is disabled.</span></span>|  
|<span data-ttu-id="93358-125">訊息</span><span class="sxs-lookup"><span data-stu-id="93358-125">Message</span></span>|<span data-ttu-id="93358-126">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="93358-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93358-127">子元素</span><span class="sxs-lookup"><span data-stu-id="93358-127">Child Elements</span></span>  
  
|<span data-ttu-id="93358-128">項目</span><span class="sxs-lookup"><span data-stu-id="93358-128">Element</span></span>|<span data-ttu-id="93358-129">描述</span><span class="sxs-lookup"><span data-stu-id="93358-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93358-130">\<message></span><span class="sxs-lookup"><span data-stu-id="93358-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="93358-131">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="93358-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="93358-132">此項目的型別為 <xref:System.ServiceModel.MessageSecurityOverHttp>。</span><span class="sxs-lookup"><span data-stu-id="93358-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93358-133">父項目</span><span class="sxs-lookup"><span data-stu-id="93358-133">Parent Elements</span></span>  
  
|<span data-ttu-id="93358-134">項目</span><span class="sxs-lookup"><span data-stu-id="93358-134">Element</span></span>|<span data-ttu-id="93358-135">描述</span><span class="sxs-lookup"><span data-stu-id="93358-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93358-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="93358-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="93358-137">定義的所有繫結功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="93358-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93358-138">備註</span><span class="sxs-lookup"><span data-stu-id="93358-138">Remarks</span></span>  
 <span data-ttu-id="93358-139">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="93358-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="93358-140">用戶端應該使用安全性確保本身只連接其信任的服務。</span><span class="sxs-lookup"><span data-stu-id="93358-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93358-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93358-141">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="93358-142">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="93358-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="93358-143">繫結</span><span class="sxs-lookup"><span data-stu-id="93358-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="93358-144">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="93358-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="93358-145">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="93358-145">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="93358-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="93358-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
