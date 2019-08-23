---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 8185153eb02c5794b0f6ac02a6837806f2073c07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941912"
---
# <a name="certificatevalidation"></a><span data-ttu-id="4b1d0-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="4b1d0-101">\<certificateValidation></span></span>
<span data-ttu-id="4b1d0-102">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="4b1d0-103">如果特定處理常式已設定自己的驗證器, 則會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="4b1d0-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4b1d0-104">\<system.identityModel></span></span>  
<span data-ttu-id="4b1d0-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4b1d0-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4b1d0-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="4b1d0-106">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b1d0-107">語法</span><span class="sxs-lookup"><span data-stu-id="4b1d0-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b1d0-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4b1d0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4b1d0-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b1d0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4b1d0-110">Attributes</span></span>  
  
|<span data-ttu-id="4b1d0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4b1d0-111">Attribute</span></span>|<span data-ttu-id="4b1d0-112">說明</span><span class="sxs-lookup"><span data-stu-id="4b1d0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b1d0-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="4b1d0-113">certificateValidationMode</span></span>|<span data-ttu-id="4b1d0-114"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值, 指定要用於 x.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-114">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="4b1d0-115">預設值為 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-115">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="4b1d0-116">若要指定自訂驗證程式, 請將此屬性設定為 "custom", 並使用[ \<certificateValidator >](certificatevalidator.md)元素指定驗證程式。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-116">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="4b1d0-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-117">Optional.</span></span>|  
|<span data-ttu-id="4b1d0-118">revocationMode</span><span class="sxs-lookup"><span data-stu-id="4b1d0-118">revocationMode</span></span>|<span data-ttu-id="4b1d0-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值, 指定要用於 x.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="4b1d0-120">預設值為 "Online"。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-120">The default value is "Online".</span></span> <span data-ttu-id="4b1d0-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-121">Optional.</span></span>|  
|<span data-ttu-id="4b1d0-122">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="4b1d0-122">trustedStoreLocation</span></span>|<span data-ttu-id="4b1d0-123"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>值, 指定 x.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="4b1d0-124">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-124">The default value is "LocalMachine".</span></span> <span data-ttu-id="4b1d0-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-125">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b1d0-126">子元素</span><span class="sxs-lookup"><span data-stu-id="4b1d0-126">Child Elements</span></span>  
  
|<span data-ttu-id="4b1d0-127">項目</span><span class="sxs-lookup"><span data-stu-id="4b1d0-127">Element</span></span>|<span data-ttu-id="4b1d0-128">描述</span><span class="sxs-lookup"><span data-stu-id="4b1d0-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b1d0-129">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="4b1d0-129">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="4b1d0-130">指定憑證驗證的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-130">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="4b1d0-131">只有當`certificateValidationMode` [ \<certificateValidation >](certificatevalidation.md)元素的屬性設定為 "Custom" 時, 才會使用此類型。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-131">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b1d0-132">父項目</span><span class="sxs-lookup"><span data-stu-id="4b1d0-132">Parent Elements</span></span>  
  
|<span data-ttu-id="4b1d0-133">項目</span><span class="sxs-lookup"><span data-stu-id="4b1d0-133">Element</span></span>|<span data-ttu-id="4b1d0-134">描述</span><span class="sxs-lookup"><span data-stu-id="4b1d0-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b1d0-135">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4b1d0-135">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="4b1d0-136">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-136">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="4b1d0-137">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="4b1d0-137">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="4b1d0-138">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-138">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b1d0-139">備註</span><span class="sxs-lookup"><span data-stu-id="4b1d0-139">Remarks</span></span>  
 <span data-ttu-id="4b1d0-140">元素可以在專案`<identityConfiguration>`下的服務層級或專案底下的安全性權杖`<securityTokenHandlerConfiguration>`處理常式集合層級指定。 `<certificateValidation>`</span><span class="sxs-lookup"><span data-stu-id="4b1d0-140">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="4b1d0-141">權杖處理常式集合上的設定會覆寫在服務上指定的值。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-141">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="4b1d0-142">某些權杖處理常式可讓您在設定中指定憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-142">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="4b1d0-143">個別權杖處理常式上的設定會覆寫在服務層級和安全性權杖處理常式集合中指定的值。</span><span class="sxs-lookup"><span data-stu-id="4b1d0-143">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b1d0-144">範例</span><span class="sxs-lookup"><span data-stu-id="4b1d0-144">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
