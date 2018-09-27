---
title: '&lt;certificateValidation&gt;'
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 29881be43f02d275ad135efd97dc8b25a7409beb
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235451"
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="bf6be-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="bf6be-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="bf6be-103">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="bf6be-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="bf6be-104">如果特定的處理常式設定為使用自己的驗證程式，則會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="bf6be-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="bf6be-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="bf6be-105">\<system.identityModel></span></span>  
<span data-ttu-id="bf6be-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="bf6be-106">\<identityConfiguration></span></span>  
<span data-ttu-id="bf6be-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="bf6be-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6be-108">語法</span><span class="sxs-lookup"><span data-stu-id="bf6be-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf6be-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bf6be-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bf6be-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bf6be-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf6be-111">屬性</span><span class="sxs-lookup"><span data-stu-id="bf6be-111">Attributes</span></span>  
  
|<span data-ttu-id="bf6be-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bf6be-112">Attribute</span></span>|<span data-ttu-id="bf6be-113">描述</span><span class="sxs-lookup"><span data-stu-id="bf6be-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf6be-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="bf6be-114">certificateValidationMode</span></span>|<span data-ttu-id="bf6be-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要使用的 X.509 憑證驗證模式。</span><span class="sxs-lookup"><span data-stu-id="bf6be-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="bf6be-116">預設值為"PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="bf6be-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="bf6be-117">若要指定自訂驗證程式，此屬性設定為"Custom"，並指定使用的驗證[ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)項目。</span><span class="sxs-lookup"><span data-stu-id="bf6be-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="bf6be-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bf6be-118">Optional.</span></span>|  
|<span data-ttu-id="bf6be-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="bf6be-119">revocationMode</span></span>|<span data-ttu-id="bf6be-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要使用的 X.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="bf6be-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="bf6be-121">預設值為 「 上線 」。</span><span class="sxs-lookup"><span data-stu-id="bf6be-121">The default value is "Online".</span></span> <span data-ttu-id="bf6be-122">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bf6be-122">Optional.</span></span>|  
|<span data-ttu-id="bf6be-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="bf6be-123">trustedStoreLocation</span></span>|<span data-ttu-id="bf6be-124">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="bf6be-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="bf6be-125">預設值為"LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="bf6be-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="bf6be-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bf6be-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf6be-127">子元素</span><span class="sxs-lookup"><span data-stu-id="bf6be-127">Child Elements</span></span>  
  
|<span data-ttu-id="bf6be-128">項目</span><span class="sxs-lookup"><span data-stu-id="bf6be-128">Element</span></span>|<span data-ttu-id="bf6be-129">描述</span><span class="sxs-lookup"><span data-stu-id="bf6be-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf6be-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="bf6be-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="bf6be-131">指定自訂憑證驗證類型。</span><span class="sxs-lookup"><span data-stu-id="bf6be-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="bf6be-132">只有，會使用這個型別`certificateValidationMode`的屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)元素設定為"Custom"。</span><span class="sxs-lookup"><span data-stu-id="bf6be-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf6be-133">父項目</span><span class="sxs-lookup"><span data-stu-id="bf6be-133">Parent Elements</span></span>  
  
|<span data-ttu-id="bf6be-134">項目</span><span class="sxs-lookup"><span data-stu-id="bf6be-134">Element</span></span>|<span data-ttu-id="bf6be-135">描述</span><span class="sxs-lookup"><span data-stu-id="bf6be-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf6be-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bf6be-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="bf6be-137">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="bf6be-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="bf6be-138">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="bf6be-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="bf6be-139">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="bf6be-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf6be-140">備註</span><span class="sxs-lookup"><span data-stu-id="bf6be-140">Remarks</span></span>  
 <span data-ttu-id="bf6be-141">A`<certificateValidation>`項目可以指定服務層級底下`<identityConfiguration>`項目或之下的安全性權杖處理常式集合層級`<securityTokenHandlerConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="bf6be-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="bf6be-142">權杖處理常式集合上的設定會覆寫所指定的服務。</span><span class="sxs-lookup"><span data-stu-id="bf6be-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="bf6be-143">某些權杖處理常式可讓您在組態中指定的憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="bf6be-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="bf6be-144">服務層級和安全性權杖處理常式集合上設定個別的語彙基元處理常式覆寫所指定。</span><span class="sxs-lookup"><span data-stu-id="bf6be-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf6be-145">範例</span><span class="sxs-lookup"><span data-stu-id="bf6be-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
