---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: da8ea128466457409334cd0b4ee3246a923f969a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941923"
---
# <a name="certificatereference"></a><span data-ttu-id="2fa46-101">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="2fa46-101">\<certificateReference></span></span>
<span data-ttu-id="2fa46-102">指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="2fa46-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="2fa46-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="2fa46-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="2fa46-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="2fa46-104">\<federationConfiguration></span></span>  
<span data-ttu-id="2fa46-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="2fa46-105">\<serviceCertificate></span></span>  
<span data-ttu-id="2fa46-106">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="2fa46-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa46-107">語法</span><span class="sxs-lookup"><span data-stu-id="2fa46-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fa46-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2fa46-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2fa46-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2fa46-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fa46-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2fa46-110">Attributes</span></span>  
  
|<span data-ttu-id="2fa46-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2fa46-111">Attribute</span></span>|<span data-ttu-id="2fa46-112">描述</span><span class="sxs-lookup"><span data-stu-id="2fa46-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2fa46-113">storeName</span><span class="sxs-lookup"><span data-stu-id="2fa46-113">storeName</span></span>|<span data-ttu-id="2fa46-114">X.509 憑證存儲的名稱。</span><span class="sxs-lookup"><span data-stu-id="2fa46-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="2fa46-115">預設值為 "My"。</span><span class="sxs-lookup"><span data-stu-id="2fa46-115">The default is "My".</span></span> <span data-ttu-id="2fa46-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2fa46-116">Optional.</span></span>|  
|<span data-ttu-id="2fa46-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="2fa46-117">storeLocation</span></span>|<span data-ttu-id="2fa46-118"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>值, 指定 x.509 憑證存放區的位置。</span><span class="sxs-lookup"><span data-stu-id="2fa46-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="2fa46-119">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="2fa46-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="2fa46-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2fa46-120">Optional.</span></span>|  
|<span data-ttu-id="2fa46-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="2fa46-121">x509FindType</span></span>|<span data-ttu-id="2fa46-122"><xref:System.Security.Cryptography.X509Certificates.X509FindType>值, 指定要執行的搜尋類型。</span><span class="sxs-lookup"><span data-stu-id="2fa46-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="2fa46-123">預設值為 "FindBySubjectDistinguishedName"。</span><span class="sxs-lookup"><span data-stu-id="2fa46-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="2fa46-124">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2fa46-124">Optional.</span></span>|  
|<span data-ttu-id="2fa46-125">findValue</span><span class="sxs-lookup"><span data-stu-id="2fa46-125">findValue</span></span>|<span data-ttu-id="2fa46-126">要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="2fa46-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="2fa46-127">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2fa46-127">Optional.</span></span>|  
|<span data-ttu-id="2fa46-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="2fa46-128">isChainIncluded</span></span>|<span data-ttu-id="2fa46-129">指定是否應該使用憑證鏈來執行驗證。</span><span class="sxs-lookup"><span data-stu-id="2fa46-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="2fa46-130">預設值為 "true";驗證是使用憑證鏈來執行。</span><span class="sxs-lookup"><span data-stu-id="2fa46-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="2fa46-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2fa46-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2fa46-132">子元素</span><span class="sxs-lookup"><span data-stu-id="2fa46-132">Child Elements</span></span>  
 <span data-ttu-id="2fa46-133">None</span><span class="sxs-lookup"><span data-stu-id="2fa46-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fa46-134">父項目</span><span class="sxs-lookup"><span data-stu-id="2fa46-134">Parent Elements</span></span>  
  
|<span data-ttu-id="2fa46-135">項目</span><span class="sxs-lookup"><span data-stu-id="2fa46-135">Element</span></span>|<span data-ttu-id="2fa46-136">說明</span><span class="sxs-lookup"><span data-stu-id="2fa46-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fa46-137">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="2fa46-137">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="2fa46-138">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="2fa46-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fa46-139">備註</span><span class="sxs-lookup"><span data-stu-id="2fa46-139">Remarks</span></span>  
 <span data-ttu-id="2fa46-140">`<certificateReference>`元素會指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="2fa46-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="2fa46-141">當它指定為專案的子`<serviceCertificate>`專案時, 它會指定用來加密和解密權杖之 x.509 憑證的位置和驗證設定。</span><span class="sxs-lookup"><span data-stu-id="2fa46-141">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="2fa46-142">`<certificateReference>`元素是<xref:System.ServiceModel.Configuration.CertificateReferenceElement>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="2fa46-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
