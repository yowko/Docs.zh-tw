---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 7b8823d792e3f15846a9483d670994be4b368980
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273893"
---
# <a name="certificatevalidation"></a><span data-ttu-id="73c19-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="73c19-101">\<certificateValidation></span></span>
<span data-ttu-id="73c19-102">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="73c19-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="73c19-103">如果特定的處理常式設定為使用自己的驗證程式，則會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="73c19-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="73c19-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="73c19-104">\<system.identityModel></span></span>  
<span data-ttu-id="73c19-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="73c19-105">\<identityConfiguration></span></span>  
<span data-ttu-id="73c19-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="73c19-106">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73c19-107">語法</span><span class="sxs-lookup"><span data-stu-id="73c19-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73c19-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="73c19-108">Attributes and Elements</span></span>  
 <span data-ttu-id="73c19-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="73c19-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73c19-110">屬性</span><span class="sxs-lookup"><span data-stu-id="73c19-110">Attributes</span></span>  
  
|<span data-ttu-id="73c19-111">屬性</span><span class="sxs-lookup"><span data-stu-id="73c19-111">Attribute</span></span>|<span data-ttu-id="73c19-112">描述</span><span class="sxs-lookup"><span data-stu-id="73c19-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73c19-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="73c19-113">certificateValidationMode</span></span>|<span data-ttu-id="73c19-114"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要使用的 X.509 憑證驗證模式。</span><span class="sxs-lookup"><span data-stu-id="73c19-114">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="73c19-115">預設值為"PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="73c19-115">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="73c19-116">若要指定自訂驗證程式，此屬性設定為"Custom"，並指定使用的驗證[ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)項目。</span><span class="sxs-lookup"><span data-stu-id="73c19-116">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="73c19-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="73c19-117">Optional.</span></span>|  
|<span data-ttu-id="73c19-118">revocationMode</span><span class="sxs-lookup"><span data-stu-id="73c19-118">revocationMode</span></span>|<span data-ttu-id="73c19-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要使用的 X.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="73c19-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="73c19-120">預設值為 「 上線 」。</span><span class="sxs-lookup"><span data-stu-id="73c19-120">The default value is "Online".</span></span> <span data-ttu-id="73c19-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="73c19-121">Optional.</span></span>|  
|<span data-ttu-id="73c19-122">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="73c19-122">trustedStoreLocation</span></span>|<span data-ttu-id="73c19-123">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="73c19-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="73c19-124">預設值為"LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="73c19-124">The default value is "LocalMachine".</span></span> <span data-ttu-id="73c19-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="73c19-125">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73c19-126">子元素</span><span class="sxs-lookup"><span data-stu-id="73c19-126">Child Elements</span></span>  
  
|<span data-ttu-id="73c19-127">項目</span><span class="sxs-lookup"><span data-stu-id="73c19-127">Element</span></span>|<span data-ttu-id="73c19-128">描述</span><span class="sxs-lookup"><span data-stu-id="73c19-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73c19-129">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="73c19-129">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="73c19-130">指定自訂憑證驗證類型。</span><span class="sxs-lookup"><span data-stu-id="73c19-130">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="73c19-131">只有，會使用這個型別`certificateValidationMode`的屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)元素設定為"Custom"。</span><span class="sxs-lookup"><span data-stu-id="73c19-131">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73c19-132">父項目</span><span class="sxs-lookup"><span data-stu-id="73c19-132">Parent Elements</span></span>  
  
|<span data-ttu-id="73c19-133">項目</span><span class="sxs-lookup"><span data-stu-id="73c19-133">Element</span></span>|<span data-ttu-id="73c19-134">描述</span><span class="sxs-lookup"><span data-stu-id="73c19-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73c19-135">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="73c19-135">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="73c19-136">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="73c19-136">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="73c19-137">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="73c19-137">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="73c19-138">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="73c19-138">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73c19-139">備註</span><span class="sxs-lookup"><span data-stu-id="73c19-139">Remarks</span></span>  
 <span data-ttu-id="73c19-140">A`<certificateValidation>`項目可以指定服務層級底下`<identityConfiguration>`項目或之下的安全性權杖處理常式集合層級`<securityTokenHandlerConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="73c19-140">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="73c19-141">權杖處理常式集合上的設定會覆寫所指定的服務。</span><span class="sxs-lookup"><span data-stu-id="73c19-141">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="73c19-142">某些權杖處理常式可讓您在組態中指定的憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="73c19-142">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="73c19-143">服務層級和安全性權杖處理常式集合上設定個別的語彙基元處理常式覆寫所指定。</span><span class="sxs-lookup"><span data-stu-id="73c19-143">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73c19-144">範例</span><span class="sxs-lookup"><span data-stu-id="73c19-144">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
