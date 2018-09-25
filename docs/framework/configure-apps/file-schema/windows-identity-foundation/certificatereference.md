---
title: '&lt;CertificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: e04dc90134aadfb8af7b0800c7144963d267f513
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075079"
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="aafeb-102">&lt;CertificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="aafeb-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="aafeb-103">指定用來尋找和驗證 X.509 憑證的憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="aafeb-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="aafeb-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="aafeb-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="aafeb-105">\<Federationconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="aafeb-105">\<federationConfiguration></span></span>  
<span data-ttu-id="aafeb-106">\<v ></span><span class="sxs-lookup"><span data-stu-id="aafeb-106">\<serviceCertificate></span></span>  
<span data-ttu-id="aafeb-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="aafeb-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aafeb-108">語法</span><span class="sxs-lookup"><span data-stu-id="aafeb-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aafeb-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aafeb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="aafeb-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="aafeb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aafeb-111">屬性</span><span class="sxs-lookup"><span data-stu-id="aafeb-111">Attributes</span></span>  
  
|<span data-ttu-id="aafeb-112">屬性</span><span class="sxs-lookup"><span data-stu-id="aafeb-112">Attribute</span></span>|<span data-ttu-id="aafeb-113">描述</span><span class="sxs-lookup"><span data-stu-id="aafeb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aafeb-114">storeName</span><span class="sxs-lookup"><span data-stu-id="aafeb-114">storeName</span></span>|<span data-ttu-id="aafeb-115">X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="aafeb-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="aafeb-116">預設值是"My"。</span><span class="sxs-lookup"><span data-stu-id="aafeb-116">The default is "My".</span></span> <span data-ttu-id="aafeb-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="aafeb-117">Optional.</span></span>|  
|<span data-ttu-id="aafeb-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="aafeb-118">storeLocation</span></span>|<span data-ttu-id="aafeb-119">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區位置。</span><span class="sxs-lookup"><span data-stu-id="aafeb-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="aafeb-120">預設值為"LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="aafeb-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="aafeb-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="aafeb-121">Optional.</span></span>|  
|<span data-ttu-id="aafeb-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="aafeb-122">x509FindType</span></span>|<span data-ttu-id="aafeb-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType>值，指定所要執行的搜尋的類型。</span><span class="sxs-lookup"><span data-stu-id="aafeb-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="aafeb-124">預設值為"FindBySubjectDistinguishedName 」。</span><span class="sxs-lookup"><span data-stu-id="aafeb-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="aafeb-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="aafeb-125">Optional.</span></span>|  
|<span data-ttu-id="aafeb-126">findValue</span><span class="sxs-lookup"><span data-stu-id="aafeb-126">findValue</span></span>|<span data-ttu-id="aafeb-127">要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="aafeb-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="aafeb-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="aafeb-128">Optional.</span></span>|  
|<span data-ttu-id="aafeb-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="aafeb-129">isChainIncluded</span></span>|<span data-ttu-id="aafeb-130">指定是否應該執行驗證所使用的憑證鏈結。</span><span class="sxs-lookup"><span data-stu-id="aafeb-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="aafeb-131">預設值為"true";使用憑證鏈結，會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="aafeb-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="aafeb-132">選擇性。</span><span class="sxs-lookup"><span data-stu-id="aafeb-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aafeb-133">子元素</span><span class="sxs-lookup"><span data-stu-id="aafeb-133">Child Elements</span></span>  
 <span data-ttu-id="aafeb-134">無</span><span class="sxs-lookup"><span data-stu-id="aafeb-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aafeb-135">父項目</span><span class="sxs-lookup"><span data-stu-id="aafeb-135">Parent Elements</span></span>  
  
|<span data-ttu-id="aafeb-136">項目</span><span class="sxs-lookup"><span data-stu-id="aafeb-136">Element</span></span>|<span data-ttu-id="aafeb-137">描述</span><span class="sxs-lookup"><span data-stu-id="aafeb-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aafeb-138">\<v ></span><span class="sxs-lookup"><span data-stu-id="aafeb-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="aafeb-139">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="aafeb-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aafeb-140">備註</span><span class="sxs-lookup"><span data-stu-id="aafeb-140">Remarks</span></span>  
 <span data-ttu-id="aafeb-141">`<certificateReference>`項目會指定用來尋找和驗證 X.509 憑證的憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="aafeb-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="aafeb-142">指定的子項目為時`<serviceCertficate>`項目，它會指定用來加密和解密權杖的 X.509 憑證的位置和驗證設定。</span><span class="sxs-lookup"><span data-stu-id="aafeb-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="aafeb-143">`<certificateReference>`項目由<xref:System.ServiceModel.Configuration.CertificateReferenceElement>類別。</span><span class="sxs-lookup"><span data-stu-id="aafeb-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
