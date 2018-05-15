---
title: '&lt;certificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e0f9a826a4c8d292346d9efee7970a82b88fb612
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="35925-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="35925-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="35925-103">指定用來尋找和驗證 x.509 憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="35925-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="35925-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="35925-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="35925-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="35925-105">\<federationConfiguration></span></span>  
<span data-ttu-id="35925-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="35925-106">\<serviceCertificate></span></span>  
<span data-ttu-id="35925-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="35925-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35925-108">語法</span><span class="sxs-lookup"><span data-stu-id="35925-108">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35925-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="35925-109">Attributes and Elements</span></span>  
 <span data-ttu-id="35925-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="35925-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35925-111">屬性</span><span class="sxs-lookup"><span data-stu-id="35925-111">Attributes</span></span>  
  
|<span data-ttu-id="35925-112">屬性</span><span class="sxs-lookup"><span data-stu-id="35925-112">Attribute</span></span>|<span data-ttu-id="35925-113">描述</span><span class="sxs-lookup"><span data-stu-id="35925-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35925-114">storeName</span><span class="sxs-lookup"><span data-stu-id="35925-114">storeName</span></span>|<span data-ttu-id="35925-115">X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="35925-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="35925-116">預設值是"My"。</span><span class="sxs-lookup"><span data-stu-id="35925-116">The default is "My".</span></span> <span data-ttu-id="35925-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="35925-117">Optional.</span></span>|  
|<span data-ttu-id="35925-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="35925-118">storeLocation</span></span>|<span data-ttu-id="35925-119">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區的位置。</span><span class="sxs-lookup"><span data-stu-id="35925-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="35925-120">預設值是 「 本機電腦 」。</span><span class="sxs-lookup"><span data-stu-id="35925-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="35925-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="35925-121">Optional.</span></span>|  
|<span data-ttu-id="35925-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="35925-122">x509FindType</span></span>|<span data-ttu-id="35925-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType>值，指定所要執行的搜尋類型。</span><span class="sxs-lookup"><span data-stu-id="35925-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="35925-124">預設值為"FindBySubjectDistinguishedName"。</span><span class="sxs-lookup"><span data-stu-id="35925-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="35925-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="35925-125">Optional.</span></span>|  
|<span data-ttu-id="35925-126">findValue</span><span class="sxs-lookup"><span data-stu-id="35925-126">findValue</span></span>|<span data-ttu-id="35925-127">要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="35925-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="35925-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="35925-128">Optional.</span></span>|  
|<span data-ttu-id="35925-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="35925-129">isChainIncluded</span></span>|<span data-ttu-id="35925-130">指定是否應該使用憑證鏈結中執行驗證。</span><span class="sxs-lookup"><span data-stu-id="35925-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="35925-131">預設值為"true";使用憑證鏈結會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="35925-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="35925-132">選擇性。</span><span class="sxs-lookup"><span data-stu-id="35925-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35925-133">子項目</span><span class="sxs-lookup"><span data-stu-id="35925-133">Child Elements</span></span>  
 <span data-ttu-id="35925-134">無</span><span class="sxs-lookup"><span data-stu-id="35925-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35925-135">父項目</span><span class="sxs-lookup"><span data-stu-id="35925-135">Parent Elements</span></span>  
  
|<span data-ttu-id="35925-136">項目</span><span class="sxs-lookup"><span data-stu-id="35925-136">Element</span></span>|<span data-ttu-id="35925-137">描述</span><span class="sxs-lookup"><span data-stu-id="35925-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35925-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="35925-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="35925-139">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="35925-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35925-140">備註</span><span class="sxs-lookup"><span data-stu-id="35925-140">Remarks</span></span>  
 <span data-ttu-id="35925-141">`<certificateReference>`項目會指定用來尋找和驗證 x.509 憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="35925-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="35925-142">指定為子元素時`<serviceCertficate>`項目，它會指定用來加密和解密權杖的 X.509 憑證的位置和驗證設定。</span><span class="sxs-lookup"><span data-stu-id="35925-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="35925-143">`<certificateReference>`項目由<xref:System.ServiceModel.Configuration.CertificateReferenceElement>類別。</span><span class="sxs-lookup"><span data-stu-id="35925-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
