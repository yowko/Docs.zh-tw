---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 583fef7eb364c39890b3f9304770b383c1ea6d2a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183503"
---
# \<certificateValidation>

<span data-ttu-id="fb0c6-101">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-101">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="fb0c6-102">如果特定處理常式設定了自己的驗證程式，則會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-102">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a><span data-ttu-id="fb0c6-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="fb0c6-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb0c6-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fb0c6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fb0c6-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb0c6-106">屬性</span><span class="sxs-lookup"><span data-stu-id="fb0c6-106">Attributes</span></span>  
  
|<span data-ttu-id="fb0c6-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fb0c6-107">Attribute</span></span>|<span data-ttu-id="fb0c6-108">描述</span><span class="sxs-lookup"><span data-stu-id="fb0c6-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fb0c6-109">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="fb0c6-109">certificateValidationMode</span></span>|<span data-ttu-id="fb0c6-110"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要用於 x.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-110">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="fb0c6-111">預設值為 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-111">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="fb0c6-112">若要指定自訂驗證程式，請將此屬性設定為 "Custom"，然後使用專案指定驗證程式 [\<certificateValidator>](certificatevalidator.md) 。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-112">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="fb0c6-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-113">Optional.</span></span>|  
|<span data-ttu-id="fb0c6-114">revocationMode</span><span class="sxs-lookup"><span data-stu-id="fb0c6-114">revocationMode</span></span>|<span data-ttu-id="fb0c6-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要用於 x.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="fb0c6-116">預設值為 "Online"。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-116">The default value is "Online".</span></span> <span data-ttu-id="fb0c6-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-117">Optional.</span></span>|  
|<span data-ttu-id="fb0c6-118">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="fb0c6-118">trustedStoreLocation</span></span>|<span data-ttu-id="fb0c6-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>指定 x.509 憑證存放區的值。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="fb0c6-120">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="fb0c6-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-121">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb0c6-122">子元素</span><span class="sxs-lookup"><span data-stu-id="fb0c6-122">Child Elements</span></span>  
  
|<span data-ttu-id="fb0c6-123">項目</span><span class="sxs-lookup"><span data-stu-id="fb0c6-123">Element</span></span>|<span data-ttu-id="fb0c6-124">描述</span><span class="sxs-lookup"><span data-stu-id="fb0c6-124">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|<span data-ttu-id="fb0c6-125">指定憑證驗證的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-125">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="fb0c6-126">只有當 `certificateValidationMode` 元素的屬性 [\<certificateValidation>](certificatevalidation.md) 設為 "Custom" 時，才會使用這個型別。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-126">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb0c6-127">父項目</span><span class="sxs-lookup"><span data-stu-id="fb0c6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="fb0c6-128">項目</span><span class="sxs-lookup"><span data-stu-id="fb0c6-128">Element</span></span>|<span data-ttu-id="fb0c6-129">描述</span><span class="sxs-lookup"><span data-stu-id="fb0c6-129">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="fb0c6-130">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-130">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="fb0c6-131">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-131">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb0c6-132">備註</span><span class="sxs-lookup"><span data-stu-id="fb0c6-132">Remarks</span></span>  

 <span data-ttu-id="fb0c6-133">專案 `<certificateValidation>` 可以在服務層級的元素底下或在 `<identityConfiguration>` 安全性權杖處理常式集合層級的元素底下指定 `<securityTokenHandlerConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-133">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="fb0c6-134">權杖處理常式集合上的設定會覆寫服務上指定的設定。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-134">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="fb0c6-135">某些權杖處理常式可讓您在設定中指定憑證驗證設定。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-135">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="fb0c6-136">個別標記處理常式上的設定會覆寫在服務層級和安全性權杖處理常式集合中指定的設定。</span><span class="sxs-lookup"><span data-stu-id="fb0c6-136">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb0c6-137">範例</span><span class="sxs-lookup"><span data-stu-id="fb0c6-137">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
