---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: a6a8185297e1345de9fa20c7d4d0dffbdcd8620f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185388"
---
# \<x509SecurityTokenHandlerRequirement>

<span data-ttu-id="cc46b-101">提供 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 類別或衍生類別的選擇性設定。</span><span class="sxs-lookup"><span data-stu-id="cc46b-101">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="cc46b-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="cc46b-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc46b-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cc46b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="cc46b-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cc46b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc46b-105">屬性</span><span class="sxs-lookup"><span data-stu-id="cc46b-105">Attributes</span></span>  
  
|<span data-ttu-id="cc46b-106">屬性</span><span class="sxs-lookup"><span data-stu-id="cc46b-106">Attribute</span></span>|<span data-ttu-id="cc46b-107">描述</span><span class="sxs-lookup"><span data-stu-id="cc46b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc46b-108">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="cc46b-108">certificateValidationMode</span></span>|<span data-ttu-id="cc46b-109"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要用於 x.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="cc46b-109">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="cc46b-110">預設值為 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="cc46b-110">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="cc46b-111">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="cc46b-111">mapToWindows</span></span>|<span data-ttu-id="cc46b-112">指定權杖處理常式是否應該使用連入的 UPN 宣告，將驗證權杖對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="cc46b-112">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="cc46b-113">預設值為 "false"。</span><span class="sxs-lookup"><span data-stu-id="cc46b-113">The default is "false".</span></span>|  
|<span data-ttu-id="cc46b-114">revocationMode</span><span class="sxs-lookup"><span data-stu-id="cc46b-114">revocationMode</span></span>|<span data-ttu-id="cc46b-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要用於 x.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="cc46b-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="cc46b-116">預設值為 "Online"。</span><span class="sxs-lookup"><span data-stu-id="cc46b-116">The default value is "Online".</span></span>|  
|<span data-ttu-id="cc46b-117">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="cc46b-117">trustedStoreLocation</span></span>|<span data-ttu-id="cc46b-118"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>指定 x.509 憑證存放區的值。</span><span class="sxs-lookup"><span data-stu-id="cc46b-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="cc46b-119">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="cc46b-119">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="cc46b-120">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="cc46b-120">certificateValidator</span></span>|<span data-ttu-id="cc46b-121">衍生自的自訂型別 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 。</span><span class="sxs-lookup"><span data-stu-id="cc46b-121">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="cc46b-122">如果 `certificateValidationMode` 屬性為「自訂」，則會使用此類型的實例進行簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="cc46b-122">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc46b-123">子元素</span><span class="sxs-lookup"><span data-stu-id="cc46b-123">Child Elements</span></span>  

 <span data-ttu-id="cc46b-124">無</span><span class="sxs-lookup"><span data-stu-id="cc46b-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc46b-125">父項目</span><span class="sxs-lookup"><span data-stu-id="cc46b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cc46b-126">項目</span><span class="sxs-lookup"><span data-stu-id="cc46b-126">Element</span></span>|<span data-ttu-id="cc46b-127">描述</span><span class="sxs-lookup"><span data-stu-id="cc46b-127">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="cc46b-128">將指定的安全性權杖處理常式新增至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="cc46b-128">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cc46b-129">範例</span><span class="sxs-lookup"><span data-stu-id="cc46b-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
