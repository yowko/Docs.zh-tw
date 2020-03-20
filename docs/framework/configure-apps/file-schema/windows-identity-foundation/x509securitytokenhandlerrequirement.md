---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152446"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="0fb5e-101">\<x509 安全權杖處理常式要求></span><span class="sxs-lookup"><span data-stu-id="0fb5e-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="0fb5e-102">為<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類或派生類提供可選配置。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="0fb5e-103">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0fb5e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0fb5e-104">&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="0fb5e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="0fb5e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="0fb5e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="0fb5e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="0fb5e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="0fb5e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<添加>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="0fb5e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="0fb5e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509 安全權杖處理常式要求>**</span><span class="sxs-lookup"><span data-stu-id="0fb5e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb5e-109">語法</span><span class="sxs-lookup"><span data-stu-id="0fb5e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fb5e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0fb5e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0fb5e-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fb5e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0fb5e-112">Attributes</span></span>  
  
|<span data-ttu-id="0fb5e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0fb5e-113">Attribute</span></span>|<span data-ttu-id="0fb5e-114">描述</span><span class="sxs-lookup"><span data-stu-id="0fb5e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0fb5e-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="0fb5e-115">certificateValidationMode</span></span>|<span data-ttu-id="0fb5e-116">指定<xref:System.ServiceModel.Security.X509CertificateValidationMode>要用於 X.509 憑證的驗證模式的值。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="0fb5e-117">預設值為"對等或鏈信任"。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="0fb5e-118">地圖到視窗</span><span class="sxs-lookup"><span data-stu-id="0fb5e-118">mapToWindows</span></span>|<span data-ttu-id="0fb5e-119">指定權杖處理常式是否應通過使用傳入的 UPN 聲明將驗證權杖映射到 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="0fb5e-120">預設值為 "false"。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-120">The default is "false".</span></span>|  
|<span data-ttu-id="0fb5e-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="0fb5e-121">revocationMode</span></span>|<span data-ttu-id="0fb5e-122">指定<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>要用於 X.509 憑證的吊銷模式的值。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="0fb5e-123">預設值為"連線"。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="0fb5e-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="0fb5e-124">trustedStoreLocation</span></span>|<span data-ttu-id="0fb5e-125">指定<xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 憑證存儲的值。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="0fb5e-126">預設值為"本地電腦"。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="0fb5e-127">證書驗證器</span><span class="sxs-lookup"><span data-stu-id="0fb5e-127">certificateValidator</span></span>|<span data-ttu-id="0fb5e-128">派生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="0fb5e-129">如果`certificateValidationMode`屬性為"自訂"，則此類型的實例用於頒發者證書驗證。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fb5e-130">子元素</span><span class="sxs-lookup"><span data-stu-id="0fb5e-130">Child Elements</span></span>  
 <span data-ttu-id="0fb5e-131">None</span><span class="sxs-lookup"><span data-stu-id="0fb5e-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fb5e-132">父項目</span><span class="sxs-lookup"><span data-stu-id="0fb5e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="0fb5e-133">元素</span><span class="sxs-lookup"><span data-stu-id="0fb5e-133">Element</span></span>|<span data-ttu-id="0fb5e-134">描述</span><span class="sxs-lookup"><span data-stu-id="0fb5e-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fb5e-135">\<添加></span><span class="sxs-lookup"><span data-stu-id="0fb5e-135">\<add></span></span>](add.md)|<span data-ttu-id="0fb5e-136">將指定的安全權杖處理常式添加到權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="0fb5e-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0fb5e-137">範例</span><span class="sxs-lookup"><span data-stu-id="0fb5e-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
