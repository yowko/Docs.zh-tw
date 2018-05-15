---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8af4a718fc9f4ba7f674d98e13424bb443693c6c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="92db3-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="92db3-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="92db3-103">提供選擇性組態<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="92db3-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="92db3-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="92db3-104">\<system.identityModel></span></span>  
<span data-ttu-id="92db3-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="92db3-105">\<identityConfiguration></span></span>  
<span data-ttu-id="92db3-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="92db3-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="92db3-107">\<add></span><span class="sxs-lookup"><span data-stu-id="92db3-107">\<add></span></span>  
<span data-ttu-id="92db3-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="92db3-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92db3-109">語法</span><span class="sxs-lookup"><span data-stu-id="92db3-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92db3-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="92db3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="92db3-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="92db3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92db3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="92db3-112">Attributes</span></span>  
  
|<span data-ttu-id="92db3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="92db3-113">Attribute</span></span>|<span data-ttu-id="92db3-114">描述</span><span class="sxs-lookup"><span data-stu-id="92db3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92db3-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="92db3-115">certificateValidationMode</span></span>|<span data-ttu-id="92db3-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要使用的 X.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="92db3-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="92db3-117">預設值為"PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="92db3-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="92db3-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="92db3-118">mapToWindows</span></span>|<span data-ttu-id="92db3-119">指定權杖處理常式是否應該使用連入的 UPN 宣告，將驗證語彙基元對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="92db3-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="92db3-120">預設為"false"。</span><span class="sxs-lookup"><span data-stu-id="92db3-120">The default is "false".</span></span>|  
|<span data-ttu-id="92db3-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="92db3-121">revocationMode</span></span>|<span data-ttu-id="92db3-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要使用的 X.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="92db3-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="92db3-123">預設值為 「 上線 」。</span><span class="sxs-lookup"><span data-stu-id="92db3-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="92db3-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="92db3-124">trustedStoreLocation</span></span>|<span data-ttu-id="92db3-125">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="92db3-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="92db3-126">預設值是 「 本機電腦 」。</span><span class="sxs-lookup"><span data-stu-id="92db3-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="92db3-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="92db3-127">certificateValidator</span></span>|<span data-ttu-id="92db3-128">自訂型別衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="92db3-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="92db3-129">如果`certificateValidationMode`屬性是 「 自訂 」，此類型的執行個體用於簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="92db3-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92db3-130">子項目</span><span class="sxs-lookup"><span data-stu-id="92db3-130">Child Elements</span></span>  
 <span data-ttu-id="92db3-131">無</span><span class="sxs-lookup"><span data-stu-id="92db3-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92db3-132">父項目</span><span class="sxs-lookup"><span data-stu-id="92db3-132">Parent Elements</span></span>  
  
|<span data-ttu-id="92db3-133">項目</span><span class="sxs-lookup"><span data-stu-id="92db3-133">Element</span></span>|<span data-ttu-id="92db3-134">描述</span><span class="sxs-lookup"><span data-stu-id="92db3-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92db3-135">\<add></span><span class="sxs-lookup"><span data-stu-id="92db3-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="92db3-136">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="92db3-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="92db3-137">範例</span><span class="sxs-lookup"><span data-stu-id="92db3-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
