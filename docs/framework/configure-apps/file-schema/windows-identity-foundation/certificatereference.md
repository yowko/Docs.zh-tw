---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c8acf4b6d6e6e8a0fcf7d73139a1d2c5ea03f063
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="2a62c-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="2a62c-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="2a62c-103">指定用來尋找和驗證 x.509 憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="2a62c-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="2a62c-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="2a62c-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="2a62c-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2a62c-105">\<federationConfiguration></span></span>  
<span data-ttu-id="2a62c-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2a62c-106">\<serviceCertificate></span></span>  
<span data-ttu-id="2a62c-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="2a62c-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a62c-108">語法</span><span class="sxs-lookup"><span data-stu-id="2a62c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a62c-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2a62c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2a62c-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2a62c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a62c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2a62c-111">Attributes</span></span>  
  
|<span data-ttu-id="2a62c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2a62c-112">Attribute</span></span>|<span data-ttu-id="2a62c-113">說明</span><span class="sxs-lookup"><span data-stu-id="2a62c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a62c-114">storeName</span><span class="sxs-lookup"><span data-stu-id="2a62c-114">storeName</span></span>|<span data-ttu-id="2a62c-115">X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="2a62c-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="2a62c-116">預設值是"My"。</span><span class="sxs-lookup"><span data-stu-id="2a62c-116">The default is "My".</span></span> <span data-ttu-id="2a62c-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="2a62c-117">Optional.</span></span>|  
|<span data-ttu-id="2a62c-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="2a62c-118">storeLocation</span></span>|<span data-ttu-id="2a62c-119">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區的位置。</span><span class="sxs-lookup"><span data-stu-id="2a62c-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="2a62c-120">預設值是 「 本機電腦 」。</span><span class="sxs-lookup"><span data-stu-id="2a62c-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="2a62c-121">選擇項。</span><span class="sxs-lookup"><span data-stu-id="2a62c-121">Optional.</span></span>|  
|<span data-ttu-id="2a62c-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="2a62c-122">x509FindType</span></span>|<span data-ttu-id="2a62c-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType>值，指定所要執行的搜尋類型。</span><span class="sxs-lookup"><span data-stu-id="2a62c-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="2a62c-124">預設值為"FindBySubjectDistinguishedName"。</span><span class="sxs-lookup"><span data-stu-id="2a62c-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="2a62c-125">選擇項。</span><span class="sxs-lookup"><span data-stu-id="2a62c-125">Optional.</span></span>|  
|<span data-ttu-id="2a62c-126">findValue</span><span class="sxs-lookup"><span data-stu-id="2a62c-126">findValue</span></span>|<span data-ttu-id="2a62c-127">要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="2a62c-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="2a62c-128">選擇項。</span><span class="sxs-lookup"><span data-stu-id="2a62c-128">Optional.</span></span>|  
|<span data-ttu-id="2a62c-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="2a62c-129">isChainIncluded</span></span>|<span data-ttu-id="2a62c-130">指定是否應該使用憑證鏈結中執行驗證。</span><span class="sxs-lookup"><span data-stu-id="2a62c-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="2a62c-131">預設值為"true";使用憑證鏈結會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="2a62c-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="2a62c-132">選擇項。</span><span class="sxs-lookup"><span data-stu-id="2a62c-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a62c-133">子元素</span><span class="sxs-lookup"><span data-stu-id="2a62c-133">Child Elements</span></span>  
 <span data-ttu-id="2a62c-134">無</span><span class="sxs-lookup"><span data-stu-id="2a62c-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a62c-135">父項目</span><span class="sxs-lookup"><span data-stu-id="2a62c-135">Parent Elements</span></span>  
  
|<span data-ttu-id="2a62c-136">項目</span><span class="sxs-lookup"><span data-stu-id="2a62c-136">Element</span></span>|<span data-ttu-id="2a62c-137">說明</span><span class="sxs-lookup"><span data-stu-id="2a62c-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a62c-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2a62c-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="2a62c-139">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="2a62c-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a62c-140">備註</span><span class="sxs-lookup"><span data-stu-id="2a62c-140">Remarks</span></span>  
 <span data-ttu-id="2a62c-141">`<certificateReference>`項目會指定用來尋找和驗證 x.509 憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="2a62c-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="2a62c-142">指定為子元素時`<serviceCertficate>`項目，它會指定用來加密和解密權杖的 X.509 憑證的位置和驗證設定。</span><span class="sxs-lookup"><span data-stu-id="2a62c-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="2a62c-143">`<certificateReference>`項目由<xref:System.ServiceModel.Configuration.CertificateReferenceElement>類別。</span><span class="sxs-lookup"><span data-stu-id="2a62c-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
