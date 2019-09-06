---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 76eeea635fd65486a1c16bea15a49018876dae99
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251685"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="a58b2-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="a58b2-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="a58b2-102">提供<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類別或衍生類別的選擇性設定。</span><span class="sxs-lookup"><span data-stu-id="a58b2-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="a58b2-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a58b2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a58b2-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="a58b2-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="a58b2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="a58b2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="a58b2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="a58b2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="a58b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="a58b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="a58b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<x509SecurityTokenHandlerRequirement >**</span><span class="sxs-lookup"><span data-stu-id="a58b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a58b2-109">語法</span><span class="sxs-lookup"><span data-stu-id="a58b2-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a58b2-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a58b2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a58b2-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a58b2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a58b2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a58b2-112">Attributes</span></span>  
  
|<span data-ttu-id="a58b2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a58b2-113">Attribute</span></span>|<span data-ttu-id="a58b2-114">描述</span><span class="sxs-lookup"><span data-stu-id="a58b2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a58b2-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a58b2-115">certificateValidationMode</span></span>|<span data-ttu-id="a58b2-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值, 指定要用於 x.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="a58b2-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="a58b2-117">預設值為 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="a58b2-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="a58b2-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="a58b2-118">mapToWindows</span></span>|<span data-ttu-id="a58b2-119">指定權杖處理常式是否應使用傳入的 UPN 宣告, 將驗證權杖對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="a58b2-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="a58b2-120">預設值為 "false"。</span><span class="sxs-lookup"><span data-stu-id="a58b2-120">The default is "false".</span></span>|  
|<span data-ttu-id="a58b2-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="a58b2-121">revocationMode</span></span>|<span data-ttu-id="a58b2-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值, 指定要用於 x.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="a58b2-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="a58b2-123">預設值為 "Online"。</span><span class="sxs-lookup"><span data-stu-id="a58b2-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="a58b2-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a58b2-124">trustedStoreLocation</span></span>|<span data-ttu-id="a58b2-125"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>值, 指定 x.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="a58b2-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="a58b2-126">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="a58b2-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="a58b2-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="a58b2-127">certificateValidator</span></span>|<span data-ttu-id="a58b2-128">衍生自的自訂類型<xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="a58b2-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="a58b2-129">`certificateValidationMode`如果屬性為 "Custom", 則會使用此類型的實例進行簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="a58b2-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a58b2-130">子元素</span><span class="sxs-lookup"><span data-stu-id="a58b2-130">Child Elements</span></span>  
 <span data-ttu-id="a58b2-131">None</span><span class="sxs-lookup"><span data-stu-id="a58b2-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a58b2-132">父項目</span><span class="sxs-lookup"><span data-stu-id="a58b2-132">Parent Elements</span></span>  
  
|<span data-ttu-id="a58b2-133">項目</span><span class="sxs-lookup"><span data-stu-id="a58b2-133">Element</span></span>|<span data-ttu-id="a58b2-134">描述</span><span class="sxs-lookup"><span data-stu-id="a58b2-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a58b2-135">\<add></span><span class="sxs-lookup"><span data-stu-id="a58b2-135">\<add></span></span>](add.md)|<span data-ttu-id="a58b2-136">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="a58b2-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a58b2-137">範例</span><span class="sxs-lookup"><span data-stu-id="a58b2-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
