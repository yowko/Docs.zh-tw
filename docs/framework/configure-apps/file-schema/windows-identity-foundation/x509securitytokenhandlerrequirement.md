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
ms.openlocfilehash: 66d4e0d6a121f807f5f372b3f39577b0bb3c4ca6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="0cb59-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="0cb59-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="0cb59-103">提供選擇性組態<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="0cb59-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="0cb59-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="0cb59-104">\<system.identityModel></span></span>  
<span data-ttu-id="0cb59-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0cb59-105">\<identityConfiguration></span></span>  
<span data-ttu-id="0cb59-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="0cb59-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="0cb59-107">\<add></span><span class="sxs-lookup"><span data-stu-id="0cb59-107">\<add></span></span>  
<span data-ttu-id="0cb59-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="0cb59-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb59-109">語法</span><span class="sxs-lookup"><span data-stu-id="0cb59-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cb59-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0cb59-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0cb59-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0cb59-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cb59-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0cb59-112">Attributes</span></span>  
  
|<span data-ttu-id="0cb59-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0cb59-113">Attribute</span></span>|<span data-ttu-id="0cb59-114">說明</span><span class="sxs-lookup"><span data-stu-id="0cb59-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0cb59-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="0cb59-115">certificateValidationMode</span></span>|<span data-ttu-id="0cb59-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要使用的 X.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="0cb59-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="0cb59-117">預設值為"PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="0cb59-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="0cb59-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="0cb59-118">mapToWindows</span></span>|<span data-ttu-id="0cb59-119">指定權杖處理常式是否應該使用連入的 UPN 宣告，將驗證語彙基元對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="0cb59-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="0cb59-120">預設為"false"。</span><span class="sxs-lookup"><span data-stu-id="0cb59-120">The default is "false".</span></span>|  
|<span data-ttu-id="0cb59-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="0cb59-121">revocationMode</span></span>|<span data-ttu-id="0cb59-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要使用的 X.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="0cb59-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="0cb59-123">預設值為 「 上線 」。</span><span class="sxs-lookup"><span data-stu-id="0cb59-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="0cb59-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="0cb59-124">trustedStoreLocation</span></span>|<span data-ttu-id="0cb59-125">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="0cb59-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="0cb59-126">預設值是 「 本機電腦 」。</span><span class="sxs-lookup"><span data-stu-id="0cb59-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="0cb59-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="0cb59-127">certificateValidator</span></span>|<span data-ttu-id="0cb59-128">自訂型別衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="0cb59-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="0cb59-129">如果`certificateValidationMode`屬性是 「 自訂 」，此類型的執行個體用於簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="0cb59-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0cb59-130">子元素</span><span class="sxs-lookup"><span data-stu-id="0cb59-130">Child Elements</span></span>  
 <span data-ttu-id="0cb59-131">無</span><span class="sxs-lookup"><span data-stu-id="0cb59-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0cb59-132">父項目</span><span class="sxs-lookup"><span data-stu-id="0cb59-132">Parent Elements</span></span>  
  
|<span data-ttu-id="0cb59-133">項目</span><span class="sxs-lookup"><span data-stu-id="0cb59-133">Element</span></span>|<span data-ttu-id="0cb59-134">描述</span><span class="sxs-lookup"><span data-stu-id="0cb59-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0cb59-135">\<add></span><span class="sxs-lookup"><span data-stu-id="0cb59-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="0cb59-136">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="0cb59-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0cb59-137">範例</span><span class="sxs-lookup"><span data-stu-id="0cb59-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
