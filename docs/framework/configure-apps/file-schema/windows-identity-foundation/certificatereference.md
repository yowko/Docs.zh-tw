---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 782ca3344774b8412a18e3cf13bff5f969751ea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252148"
---
# <a name="certificatereference"></a><span data-ttu-id="1bf25-101">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="1bf25-101">\<certificateReference></span></span>
<span data-ttu-id="1bf25-102">指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="1bf25-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="1bf25-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1bf25-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1bf25-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="1bf25-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="1bf25-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="1bf25-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="1bf25-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="1bf25-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="1bf25-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateReference >**</span><span class="sxs-lookup"><span data-stu-id="1bf25-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bf25-108">語法</span><span class="sxs-lookup"><span data-stu-id="1bf25-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bf25-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1bf25-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1bf25-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1bf25-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bf25-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1bf25-111">Attributes</span></span>  
  
|<span data-ttu-id="1bf25-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1bf25-112">Attribute</span></span>|<span data-ttu-id="1bf25-113">描述</span><span class="sxs-lookup"><span data-stu-id="1bf25-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1bf25-114">storeName</span><span class="sxs-lookup"><span data-stu-id="1bf25-114">storeName</span></span>|<span data-ttu-id="1bf25-115">X.509 憑證存儲的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bf25-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="1bf25-116">預設值為 "My"。</span><span class="sxs-lookup"><span data-stu-id="1bf25-116">The default is "My".</span></span> <span data-ttu-id="1bf25-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1bf25-117">Optional.</span></span>|  
|<span data-ttu-id="1bf25-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="1bf25-118">storeLocation</span></span>|<span data-ttu-id="1bf25-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 x.509 憑證存放區的位置。</span><span class="sxs-lookup"><span data-stu-id="1bf25-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="1bf25-120">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="1bf25-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="1bf25-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1bf25-121">Optional.</span></span>|  
|<span data-ttu-id="1bf25-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="1bf25-122">x509FindType</span></span>|<span data-ttu-id="1bf25-123"><xref:System.Security.Cryptography.X509Certificates.X509FindType>值，指定要執行的搜尋類型。</span><span class="sxs-lookup"><span data-stu-id="1bf25-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="1bf25-124">預設值為 "FindBySubjectDistinguishedName"。</span><span class="sxs-lookup"><span data-stu-id="1bf25-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="1bf25-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1bf25-125">Optional.</span></span>|  
|<span data-ttu-id="1bf25-126">findValue</span><span class="sxs-lookup"><span data-stu-id="1bf25-126">findValue</span></span>|<span data-ttu-id="1bf25-127">要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="1bf25-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="1bf25-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1bf25-128">Optional.</span></span>|  
|<span data-ttu-id="1bf25-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="1bf25-129">isChainIncluded</span></span>|<span data-ttu-id="1bf25-130">指定是否應該使用憑證鏈來執行驗證。</span><span class="sxs-lookup"><span data-stu-id="1bf25-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="1bf25-131">預設值為 "true";驗證是使用憑證鏈來執行。</span><span class="sxs-lookup"><span data-stu-id="1bf25-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="1bf25-132">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1bf25-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bf25-133">子元素</span><span class="sxs-lookup"><span data-stu-id="1bf25-133">Child Elements</span></span>  
 <span data-ttu-id="1bf25-134">無</span><span class="sxs-lookup"><span data-stu-id="1bf25-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1bf25-135">父項目</span><span class="sxs-lookup"><span data-stu-id="1bf25-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1bf25-136">項目</span><span class="sxs-lookup"><span data-stu-id="1bf25-136">Element</span></span>|<span data-ttu-id="1bf25-137">說明</span><span class="sxs-lookup"><span data-stu-id="1bf25-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bf25-138">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="1bf25-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="1bf25-139">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="1bf25-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bf25-140">備註</span><span class="sxs-lookup"><span data-stu-id="1bf25-140">Remarks</span></span>  
 <span data-ttu-id="1bf25-141">`<certificateReference>`元素會指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="1bf25-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="1bf25-142">當它指定為專案的子`<serviceCertificate>`專案時，它會指定用來加密和解密權杖之 x.509 憑證的位置和驗證設定。</span><span class="sxs-lookup"><span data-stu-id="1bf25-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="1bf25-143">`<certificateReference>`元素是<xref:System.ServiceModel.Configuration.CertificateReferenceElement>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="1bf25-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
