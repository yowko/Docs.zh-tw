---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 6c9c77f96ff6032de43d9b5a257bc0796a19b858
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667375"
---
# <a name="certificatereference"></a><span data-ttu-id="2d4c1-101">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="2d4c1-101">\<certificateReference></span></span>
<span data-ttu-id="2d4c1-102">指定用來尋找和驗證 X.509 憑證的憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="2d4c1-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="2d4c1-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="2d4c1-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="2d4c1-104">\<federationConfiguration></span></span>  
<span data-ttu-id="2d4c1-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="2d4c1-105">\<serviceCertificate></span></span>  
<span data-ttu-id="2d4c1-106">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="2d4c1-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d4c1-107">語法</span><span class="sxs-lookup"><span data-stu-id="2d4c1-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d4c1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2d4c1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2d4c1-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d4c1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2d4c1-110">Attributes</span></span>  
  
|<span data-ttu-id="2d4c1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2d4c1-111">Attribute</span></span>|<span data-ttu-id="2d4c1-112">描述</span><span class="sxs-lookup"><span data-stu-id="2d4c1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d4c1-113">storeName</span><span class="sxs-lookup"><span data-stu-id="2d4c1-113">storeName</span></span>|<span data-ttu-id="2d4c1-114">X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="2d4c1-115">預設值是"My"。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-115">The default is "My".</span></span> <span data-ttu-id="2d4c1-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-116">Optional.</span></span>|  
|<span data-ttu-id="2d4c1-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="2d4c1-117">storeLocation</span></span>|<span data-ttu-id="2d4c1-118">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區位置。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="2d4c1-119">預設值為"LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="2d4c1-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-120">Optional.</span></span>|  
|<span data-ttu-id="2d4c1-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="2d4c1-121">x509FindType</span></span>|<span data-ttu-id="2d4c1-122"><xref:System.Security.Cryptography.X509Certificates.X509FindType>值，指定所要執行的搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="2d4c1-123">預設值為"FindBySubjectDistinguishedName 」。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="2d4c1-124">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-124">Optional.</span></span>|  
|<span data-ttu-id="2d4c1-125">findValue</span><span class="sxs-lookup"><span data-stu-id="2d4c1-125">findValue</span></span>|<span data-ttu-id="2d4c1-126">要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="2d4c1-127">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-127">Optional.</span></span>|  
|<span data-ttu-id="2d4c1-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="2d4c1-128">isChainIncluded</span></span>|<span data-ttu-id="2d4c1-129">指定是否應該執行驗證所使用的憑證鏈結。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="2d4c1-130">預設值為"true";使用憑證鏈結，會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="2d4c1-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d4c1-132">子元素</span><span class="sxs-lookup"><span data-stu-id="2d4c1-132">Child Elements</span></span>  
 <span data-ttu-id="2d4c1-133">None</span><span class="sxs-lookup"><span data-stu-id="2d4c1-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d4c1-134">父項目</span><span class="sxs-lookup"><span data-stu-id="2d4c1-134">Parent Elements</span></span>  
  
|<span data-ttu-id="2d4c1-135">項目</span><span class="sxs-lookup"><span data-stu-id="2d4c1-135">Element</span></span>|<span data-ttu-id="2d4c1-136">描述</span><span class="sxs-lookup"><span data-stu-id="2d4c1-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d4c1-137">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="2d4c1-137">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="2d4c1-138">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d4c1-139">備註</span><span class="sxs-lookup"><span data-stu-id="2d4c1-139">Remarks</span></span>  
 <span data-ttu-id="2d4c1-140">`<certificateReference>`項目會指定用來尋找和驗證 X.509 憑證的憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="2d4c1-141">指定的子項目為時`<serviceCertficate>`項目，它會指定用來加密和解密權杖的 X.509 憑證的位置和驗證設定。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-141">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="2d4c1-142">`<certificateReference>`項目由<xref:System.ServiceModel.Configuration.CertificateReferenceElement>類別。</span><span class="sxs-lookup"><span data-stu-id="2d4c1-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
