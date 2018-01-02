---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7cb9eb1e7e80837e8036a8241a3a6bd679ed5e11
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="d66c4-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="d66c4-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="d66c4-103">提供選擇性組態<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="d66c4-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="d66c4-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="d66c4-104">\<system.identityModel></span></span>  
<span data-ttu-id="d66c4-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d66c4-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d66c4-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d66c4-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d66c4-107">\<add></span><span class="sxs-lookup"><span data-stu-id="d66c4-107">\<add></span></span>  
<span data-ttu-id="d66c4-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="d66c4-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d66c4-109">語法</span><span class="sxs-lookup"><span data-stu-id="d66c4-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d66c4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d66c4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d66c4-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d66c4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d66c4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d66c4-112">Attributes</span></span>  
  
|<span data-ttu-id="d66c4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d66c4-113">Attribute</span></span>|<span data-ttu-id="d66c4-114">描述</span><span class="sxs-lookup"><span data-stu-id="d66c4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d66c4-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="d66c4-115">certificateValidationMode</span></span>|<span data-ttu-id="d66c4-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要使用的 X.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="d66c4-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d66c4-117">預設值為"PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="d66c4-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="d66c4-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="d66c4-118">mapToWindows</span></span>|<span data-ttu-id="d66c4-119">指定權杖處理常式是否應該使用連入的 UPN 宣告，將驗證語彙基元對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d66c4-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="d66c4-120">預設為"false"。</span><span class="sxs-lookup"><span data-stu-id="d66c4-120">The default is "false".</span></span>|  
|<span data-ttu-id="d66c4-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="d66c4-121">revocationMode</span></span>|<span data-ttu-id="d66c4-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要使用的 X.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="d66c4-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d66c4-123">預設值為 「 上線 」。</span><span class="sxs-lookup"><span data-stu-id="d66c4-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="d66c4-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="d66c4-124">trustedStoreLocation</span></span>|<span data-ttu-id="d66c4-125">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="d66c4-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="d66c4-126">預設值是 「 本機電腦 」。</span><span class="sxs-lookup"><span data-stu-id="d66c4-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="d66c4-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="d66c4-127">certificateValidator</span></span>|<span data-ttu-id="d66c4-128">自訂型別衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="d66c4-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="d66c4-129">如果`certificateValidationMode`屬性是 「 自訂 」，此類型的執行個體用於簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="d66c4-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d66c4-130">子元素</span><span class="sxs-lookup"><span data-stu-id="d66c4-130">Child Elements</span></span>  
 <span data-ttu-id="d66c4-131">無</span><span class="sxs-lookup"><span data-stu-id="d66c4-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d66c4-132">父項目</span><span class="sxs-lookup"><span data-stu-id="d66c4-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d66c4-133">項目</span><span class="sxs-lookup"><span data-stu-id="d66c4-133">Element</span></span>|<span data-ttu-id="d66c4-134">描述</span><span class="sxs-lookup"><span data-stu-id="d66c4-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d66c4-135">\<add></span><span class="sxs-lookup"><span data-stu-id="d66c4-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="d66c4-136">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="d66c4-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d66c4-137">範例</span><span class="sxs-lookup"><span data-stu-id="d66c4-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
