---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 6e8267f170dbb26381564be7b66df5f617156885
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271937"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="7c9f5-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="7c9f5-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="7c9f5-102">提供選擇性組態<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="7c9f5-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7c9f5-103">\<system.identityModel></span></span>  
<span data-ttu-id="7c9f5-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7c9f5-104">\<identityConfiguration></span></span>  
<span data-ttu-id="7c9f5-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="7c9f5-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="7c9f5-106">\<add></span><span class="sxs-lookup"><span data-stu-id="7c9f5-106">\<add></span></span>  
<span data-ttu-id="7c9f5-107">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="7c9f5-107">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9f5-108">語法</span><span class="sxs-lookup"><span data-stu-id="7c9f5-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c9f5-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7c9f5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7c9f5-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c9f5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7c9f5-111">Attributes</span></span>  
  
|<span data-ttu-id="7c9f5-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7c9f5-112">Attribute</span></span>|<span data-ttu-id="7c9f5-113">描述</span><span class="sxs-lookup"><span data-stu-id="7c9f5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c9f5-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="7c9f5-114">certificateValidationMode</span></span>|<span data-ttu-id="7c9f5-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要使用的 X.509 憑證驗證模式。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="7c9f5-116">預設值為"PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-116">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="7c9f5-117">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="7c9f5-117">mapToWindows</span></span>|<span data-ttu-id="7c9f5-118">指定的權杖處理常式是否應該使用內送的 「 UPN 」 宣告，將驗證權杖對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-118">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="7c9f5-119">預設值為"false"。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-119">The default is "false".</span></span>|  
|<span data-ttu-id="7c9f5-120">revocationMode</span><span class="sxs-lookup"><span data-stu-id="7c9f5-120">revocationMode</span></span>|<span data-ttu-id="7c9f5-121"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要使用的 X.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-121">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="7c9f5-122">預設值為 「 上線 」。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-122">The default value is "Online".</span></span>|  
|<span data-ttu-id="7c9f5-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="7c9f5-123">trustedStoreLocation</span></span>|<span data-ttu-id="7c9f5-124">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="7c9f5-125">預設值為"LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-125">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="7c9f5-126">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="7c9f5-126">certificateValidator</span></span>|<span data-ttu-id="7c9f5-127">自訂型別衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-127">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="7c9f5-128">如果`certificateValidationMode`屬性是 「 自訂 」，此類型的執行個體使用的簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-128">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c9f5-129">子元素</span><span class="sxs-lookup"><span data-stu-id="7c9f5-129">Child Elements</span></span>  
 <span data-ttu-id="7c9f5-130">無</span><span class="sxs-lookup"><span data-stu-id="7c9f5-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c9f5-131">父項目</span><span class="sxs-lookup"><span data-stu-id="7c9f5-131">Parent Elements</span></span>  
  
|<span data-ttu-id="7c9f5-132">項目</span><span class="sxs-lookup"><span data-stu-id="7c9f5-132">Element</span></span>|<span data-ttu-id="7c9f5-133">描述</span><span class="sxs-lookup"><span data-stu-id="7c9f5-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c9f5-134">\<add></span><span class="sxs-lookup"><span data-stu-id="7c9f5-134">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="7c9f5-135">將指定的安全性權杖處理常式加入至 權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="7c9f5-135">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7c9f5-136">範例</span><span class="sxs-lookup"><span data-stu-id="7c9f5-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
