---
title: "&lt;wsDualHttpBinding&gt; 的 &lt;security&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 72d1c451efe267d098ef4d529194905ee14d6ae3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="15f0b-102">&lt;wsDualHttpBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="15f0b-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="15f0b-103">定義的安全性功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="15f0b-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="15f0b-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="15f0b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="15f0b-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="15f0b-105">\<bindings></span></span>  
<span data-ttu-id="15f0b-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="15f0b-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="15f0b-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="15f0b-107">\<binding></span></span>  
<span data-ttu-id="15f0b-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="15f0b-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15f0b-109">語法</span><span class="sxs-lookup"><span data-stu-id="15f0b-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15f0b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="15f0b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="15f0b-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="15f0b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15f0b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="15f0b-112">Attributes</span></span>  
  
|<span data-ttu-id="15f0b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="15f0b-113">Attribute</span></span>|<span data-ttu-id="15f0b-114">描述</span><span class="sxs-lookup"><span data-stu-id="15f0b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15f0b-115">模式</span><span class="sxs-lookup"><span data-stu-id="15f0b-115">mode</span></span>|<span data-ttu-id="15f0b-116">選擇性的。</span><span class="sxs-lookup"><span data-stu-id="15f0b-116">-   Optional.</span></span> <span data-ttu-id="15f0b-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="15f0b-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="15f0b-118">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="15f0b-118">The default value is `Message`.</span></span> <span data-ttu-id="15f0b-119">此屬性的型別為 <xref:System.ServiceModel.WSDualHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="15f0b-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="15f0b-120">Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="15f0b-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="15f0b-121">值</span><span class="sxs-lookup"><span data-stu-id="15f0b-121">Value</span></span>|<span data-ttu-id="15f0b-122">描述</span><span class="sxs-lookup"><span data-stu-id="15f0b-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15f0b-123">無</span><span class="sxs-lookup"><span data-stu-id="15f0b-123">None</span></span>|<span data-ttu-id="15f0b-124">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="15f0b-124">Security is disabled.</span></span>|  
|<span data-ttu-id="15f0b-125">訊息</span><span class="sxs-lookup"><span data-stu-id="15f0b-125">Message</span></span>|<span data-ttu-id="15f0b-126">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="15f0b-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15f0b-127">子元素</span><span class="sxs-lookup"><span data-stu-id="15f0b-127">Child Elements</span></span>  
  
|<span data-ttu-id="15f0b-128">項目</span><span class="sxs-lookup"><span data-stu-id="15f0b-128">Element</span></span>|<span data-ttu-id="15f0b-129">說明</span><span class="sxs-lookup"><span data-stu-id="15f0b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15f0b-130">\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="15f0b-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="15f0b-131">定義訊息層級安全性的設定。</span><span class="sxs-lookup"><span data-stu-id="15f0b-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="15f0b-132">此項目的型別為 <xref:System.ServiceModel.MessageSecurityOverHttp>。</span><span class="sxs-lookup"><span data-stu-id="15f0b-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15f0b-133">父項目</span><span class="sxs-lookup"><span data-stu-id="15f0b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="15f0b-134">項目</span><span class="sxs-lookup"><span data-stu-id="15f0b-134">Element</span></span>|<span data-ttu-id="15f0b-135">說明</span><span class="sxs-lookup"><span data-stu-id="15f0b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15f0b-136">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="15f0b-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="15f0b-137">定義的所有繫結功能[ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="15f0b-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15f0b-138">備註</span><span class="sxs-lookup"><span data-stu-id="15f0b-138">Remarks</span></span>  
 <span data-ttu-id="15f0b-139">雙重繫結會向服務公開用戶端的 IP 位址，</span><span class="sxs-lookup"><span data-stu-id="15f0b-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="15f0b-140">用戶端應該使用安全性確保本身只連接其信任的服務。</span><span class="sxs-lookup"><span data-stu-id="15f0b-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f0b-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15f0b-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="15f0b-142">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="15f0b-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="15f0b-143">繫結</span><span class="sxs-lookup"><span data-stu-id="15f0b-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="15f0b-144">設定系統提供繫結</span><span class="sxs-lookup"><span data-stu-id="15f0b-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="15f0b-145">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="15f0b-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="15f0b-146">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="15f0b-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
