---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152810"
---
# <a name="certificatereference"></a><span data-ttu-id="b05ec-101">\<證書參考></span><span class="sxs-lookup"><span data-stu-id="b05ec-101">\<certificateReference></span></span>
<span data-ttu-id="b05ec-102">指定用於在憑證存放區中查找和驗證 X.509 憑證的設置。</span><span class="sxs-lookup"><span data-stu-id="b05ec-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="b05ec-103">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b05ec-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b05ec-104">&nbsp;&nbsp;[**\<系統.身份模型.服務>**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="b05ec-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="b05ec-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<聯合配置>**](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="b05ec-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="b05ec-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務證書>**](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="b05ec-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="b05ec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<證書參考>**</span><span class="sxs-lookup"><span data-stu-id="b05ec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b05ec-108">語法</span><span class="sxs-lookup"><span data-stu-id="b05ec-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b05ec-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b05ec-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b05ec-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b05ec-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b05ec-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b05ec-111">Attributes</span></span>  
  
|<span data-ttu-id="b05ec-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b05ec-112">Attribute</span></span>|<span data-ttu-id="b05ec-113">描述</span><span class="sxs-lookup"><span data-stu-id="b05ec-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b05ec-114">storeName</span><span class="sxs-lookup"><span data-stu-id="b05ec-114">storeName</span></span>|<span data-ttu-id="b05ec-115">X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="b05ec-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="b05ec-116">預設值為"我的"。</span><span class="sxs-lookup"><span data-stu-id="b05ec-116">The default is "My".</span></span> <span data-ttu-id="b05ec-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b05ec-117">Optional.</span></span>|  
|<span data-ttu-id="b05ec-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="b05ec-118">storeLocation</span></span>|<span data-ttu-id="b05ec-119">指定<xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 憑證存儲的位置的值。</span><span class="sxs-lookup"><span data-stu-id="b05ec-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="b05ec-120">預設值為"本地電腦"。</span><span class="sxs-lookup"><span data-stu-id="b05ec-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="b05ec-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b05ec-121">Optional.</span></span>|  
|<span data-ttu-id="b05ec-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="b05ec-122">x509FindType</span></span>|<span data-ttu-id="b05ec-123">指定<xref:System.Security.Cryptography.X509Certificates.X509FindType>要執行的搜索類型的值。</span><span class="sxs-lookup"><span data-stu-id="b05ec-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="b05ec-124">預設值為"查找主題分辨名稱"。</span><span class="sxs-lookup"><span data-stu-id="b05ec-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="b05ec-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b05ec-125">Optional.</span></span>|  
|<span data-ttu-id="b05ec-126">findValue</span><span class="sxs-lookup"><span data-stu-id="b05ec-126">findValue</span></span>|<span data-ttu-id="b05ec-127">要在 X.509 憑證存放區內搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="b05ec-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="b05ec-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b05ec-128">Optional.</span></span>|  
|<span data-ttu-id="b05ec-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="b05ec-129">isChainIncluded</span></span>|<span data-ttu-id="b05ec-130">指定是否應使用憑證連結執行驗證。</span><span class="sxs-lookup"><span data-stu-id="b05ec-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="b05ec-131">預設值為"true";預設值為"true"，為"true"，為"true";為驗證是使用憑證連結執行的。</span><span class="sxs-lookup"><span data-stu-id="b05ec-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="b05ec-132">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b05ec-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b05ec-133">子元素</span><span class="sxs-lookup"><span data-stu-id="b05ec-133">Child Elements</span></span>  
 <span data-ttu-id="b05ec-134">None</span><span class="sxs-lookup"><span data-stu-id="b05ec-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b05ec-135">父項目</span><span class="sxs-lookup"><span data-stu-id="b05ec-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b05ec-136">元素</span><span class="sxs-lookup"><span data-stu-id="b05ec-136">Element</span></span>|<span data-ttu-id="b05ec-137">描述</span><span class="sxs-lookup"><span data-stu-id="b05ec-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b05ec-138">\<服務證書></span><span class="sxs-lookup"><span data-stu-id="b05ec-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="b05ec-139">配置用於加密和解密權杖的證書。</span><span class="sxs-lookup"><span data-stu-id="b05ec-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b05ec-140">備註</span><span class="sxs-lookup"><span data-stu-id="b05ec-140">Remarks</span></span>  
 <span data-ttu-id="b05ec-141">該`<certificateReference>`元素指定用於在憑證存放區中查找和驗證 X.509 憑證的設置。</span><span class="sxs-lookup"><span data-stu-id="b05ec-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="b05ec-142">當它指定為`<serviceCertificate>`元素的子項目時，它指定用於加密和解密權杖的 X.509 憑證的位置和驗證設置。</span><span class="sxs-lookup"><span data-stu-id="b05ec-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="b05ec-143">元素`<certificateReference>`由類<xref:System.ServiceModel.Configuration.CertificateReferenceElement>表示。</span><span class="sxs-lookup"><span data-stu-id="b05ec-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
