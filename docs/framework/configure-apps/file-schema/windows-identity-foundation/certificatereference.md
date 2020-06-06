---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152810"
---
# \<certificateReference>
<span data-ttu-id="8baf4-101">指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="8baf4-101">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a><span data-ttu-id="8baf4-102">語法</span><span class="sxs-lookup"><span data-stu-id="8baf4-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8baf4-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8baf4-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8baf4-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8baf4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8baf4-105">屬性</span><span class="sxs-lookup"><span data-stu-id="8baf4-105">Attributes</span></span>  
  
|<span data-ttu-id="8baf4-106">屬性</span><span class="sxs-lookup"><span data-stu-id="8baf4-106">Attribute</span></span>|<span data-ttu-id="8baf4-107">描述</span><span class="sxs-lookup"><span data-stu-id="8baf4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8baf4-108">storeName</span><span class="sxs-lookup"><span data-stu-id="8baf4-108">storeName</span></span>|<span data-ttu-id="8baf4-109">X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="8baf4-109">The name of the X.509 certificate store.</span></span> <span data-ttu-id="8baf4-110">預設值為 "My"。</span><span class="sxs-lookup"><span data-stu-id="8baf4-110">The default is "My".</span></span> <span data-ttu-id="8baf4-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8baf4-111">Optional.</span></span>|  
|<span data-ttu-id="8baf4-112">storeLocation</span><span class="sxs-lookup"><span data-stu-id="8baf4-112">storeLocation</span></span>|<span data-ttu-id="8baf4-113"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 x.509 憑證存放區的位置。</span><span class="sxs-lookup"><span data-stu-id="8baf4-113">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="8baf4-114">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="8baf4-114">The default value is "LocalMachine".</span></span> <span data-ttu-id="8baf4-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8baf4-115">Optional.</span></span>|  
|<span data-ttu-id="8baf4-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="8baf4-116">x509FindType</span></span>|<span data-ttu-id="8baf4-117"><xref:System.Security.Cryptography.X509Certificates.X509FindType>值，指定要執行的搜尋類型。</span><span class="sxs-lookup"><span data-stu-id="8baf4-117">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="8baf4-118">預設值為 "FindBySubjectDistinguishedName"。</span><span class="sxs-lookup"><span data-stu-id="8baf4-118">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="8baf4-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8baf4-119">Optional.</span></span>|  
|<span data-ttu-id="8baf4-120">findValue</span><span class="sxs-lookup"><span data-stu-id="8baf4-120">findValue</span></span>|<span data-ttu-id="8baf4-121">要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="8baf4-121">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="8baf4-122">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8baf4-122">Optional.</span></span>|  
|<span data-ttu-id="8baf4-123">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="8baf4-123">isChainIncluded</span></span>|<span data-ttu-id="8baf4-124">指定是否應該使用憑證鏈來執行驗證。</span><span class="sxs-lookup"><span data-stu-id="8baf4-124">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="8baf4-125">預設值為 "true";驗證是使用憑證鏈來執行。</span><span class="sxs-lookup"><span data-stu-id="8baf4-125">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="8baf4-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8baf4-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8baf4-127">子元素</span><span class="sxs-lookup"><span data-stu-id="8baf4-127">Child Elements</span></span>  
 <span data-ttu-id="8baf4-128">無</span><span class="sxs-lookup"><span data-stu-id="8baf4-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8baf4-129">父項目</span><span class="sxs-lookup"><span data-stu-id="8baf4-129">Parent Elements</span></span>  
  
|<span data-ttu-id="8baf4-130">元素</span><span class="sxs-lookup"><span data-stu-id="8baf4-130">Element</span></span>|<span data-ttu-id="8baf4-131">描述</span><span class="sxs-lookup"><span data-stu-id="8baf4-131">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="8baf4-132">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="8baf4-132">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8baf4-133">備註</span><span class="sxs-lookup"><span data-stu-id="8baf4-133">Remarks</span></span>  
 <span data-ttu-id="8baf4-134">`<certificateReference>`元素會指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="8baf4-134">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="8baf4-135">當它指定為專案的子專案時 `<serviceCertificate>` ，它會指定用來加密和解密權杖之 x.509 憑證的位置和驗證設定。</span><span class="sxs-lookup"><span data-stu-id="8baf4-135">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="8baf4-136">`<certificateReference>`元素是由 <xref:System.ServiceModel.Configuration.CertificateReferenceElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="8baf4-136">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
