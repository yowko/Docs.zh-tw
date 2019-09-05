---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252127"
---
# <a name="certificatevalidation"></a><span data-ttu-id="39537-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="39537-101">\<certificateValidation></span></span>
<span data-ttu-id="39537-102">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="39537-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="39537-103">如果特定處理常式已設定自己的驗證器, 則會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="39537-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
<span data-ttu-id="39537-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="39537-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="39537-105">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="39537-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="39537-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="39537-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="39537-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateValidation >**</span><span class="sxs-lookup"><span data-stu-id="39537-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39537-108">語法</span><span class="sxs-lookup"><span data-stu-id="39537-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39537-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="39537-109">Attributes and Elements</span></span>  
 <span data-ttu-id="39537-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="39537-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39537-111">屬性</span><span class="sxs-lookup"><span data-stu-id="39537-111">Attributes</span></span>  
  
|<span data-ttu-id="39537-112">屬性</span><span class="sxs-lookup"><span data-stu-id="39537-112">Attribute</span></span>|<span data-ttu-id="39537-113">說明</span><span class="sxs-lookup"><span data-stu-id="39537-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39537-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="39537-114">certificateValidationMode</span></span>|<span data-ttu-id="39537-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值, 指定要用於 x.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="39537-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="39537-116">預設值為 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="39537-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="39537-117">若要指定自訂驗證程式, 請將此屬性設定為 "custom", 並使用[ \<certificateValidator >](certificatevalidator.md)元素指定驗證程式。</span><span class="sxs-lookup"><span data-stu-id="39537-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="39537-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="39537-118">Optional.</span></span>|  
|<span data-ttu-id="39537-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="39537-119">revocationMode</span></span>|<span data-ttu-id="39537-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值, 指定要用於 x.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="39537-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="39537-121">預設值為 "Online"。</span><span class="sxs-lookup"><span data-stu-id="39537-121">The default value is "Online".</span></span> <span data-ttu-id="39537-122">選擇性。</span><span class="sxs-lookup"><span data-stu-id="39537-122">Optional.</span></span>|  
|<span data-ttu-id="39537-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="39537-123">trustedStoreLocation</span></span>|<span data-ttu-id="39537-124"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>值, 指定 x.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="39537-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="39537-125">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="39537-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="39537-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="39537-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39537-127">子元素</span><span class="sxs-lookup"><span data-stu-id="39537-127">Child Elements</span></span>  
  
|<span data-ttu-id="39537-128">項目</span><span class="sxs-lookup"><span data-stu-id="39537-128">Element</span></span>|<span data-ttu-id="39537-129">描述</span><span class="sxs-lookup"><span data-stu-id="39537-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39537-130">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="39537-130">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="39537-131">指定憑證驗證的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="39537-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="39537-132">只有當`certificateValidationMode` [ \<certificateValidation >](certificatevalidation.md)元素的屬性設定為 "Custom" 時, 才會使用此類型。</span><span class="sxs-lookup"><span data-stu-id="39537-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39537-133">父項目</span><span class="sxs-lookup"><span data-stu-id="39537-133">Parent Elements</span></span>  
  
|<span data-ttu-id="39537-134">項目</span><span class="sxs-lookup"><span data-stu-id="39537-134">Element</span></span>|<span data-ttu-id="39537-135">描述</span><span class="sxs-lookup"><span data-stu-id="39537-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39537-136">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="39537-136">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="39537-137">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="39537-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="39537-138">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="39537-138">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="39537-139">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="39537-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39537-140">備註</span><span class="sxs-lookup"><span data-stu-id="39537-140">Remarks</span></span>  
 <span data-ttu-id="39537-141">元素可以在專案`<identityConfiguration>`下的服務層級或專案底下的安全性權杖`<securityTokenHandlerConfiguration>`處理常式集合層級指定。 `<certificateValidation>`</span><span class="sxs-lookup"><span data-stu-id="39537-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="39537-142">權杖處理常式集合上的設定會覆寫在服務上指定的值。</span><span class="sxs-lookup"><span data-stu-id="39537-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="39537-143">某些權杖處理常式可讓您在設定中指定憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="39537-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="39537-144">個別權杖處理常式上的設定會覆寫在服務層級和安全性權杖處理常式集合中指定的值。</span><span class="sxs-lookup"><span data-stu-id="39537-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39537-145">範例</span><span class="sxs-lookup"><span data-stu-id="39537-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
