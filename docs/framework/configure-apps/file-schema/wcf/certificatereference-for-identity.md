---
title: "&lt;身分識別&gt;的 &lt;certificateReference&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 883ae318e32493013f009f3580ef102e4d39b3e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificatereferencegt-for-ltidentitygt"></a><span data-ttu-id="58002-102">&lt;身分識別&gt;的 &lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="58002-102">&lt;certificateReference&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="58002-103">指定 X.509 憑證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="58002-103">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="58002-104">使用這個身分識別連接至端點的安全 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 用戶端會確認伺服器提供的宣告是否包含用來建構這個身分識別的身分識別宣告。</span><span class="sxs-lookup"><span data-stu-id="58002-104">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity verifies that the claims presented by the server contain the identity claim used to construct this identity.</span></span>  
  
 <span data-ttu-id="58002-105">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="58002-105">\<identity></span></span>  
<span data-ttu-id="58002-106">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="58002-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58002-107">語法</span><span class="sxs-lookup"><span data-stu-id="58002-107">Syntax</span></span>  
  
```xml  
<certificateReference   
        findValue="String"   
    isChainIncluded="Boolean"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
  
    storeLocation="LocalMachine/CurrentUser"  
  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
</certificateReference>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58002-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="58002-108">Attributes and Elements</span></span>  
 <span data-ttu-id="58002-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="58002-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58002-110">屬性</span><span class="sxs-lookup"><span data-stu-id="58002-110">Attributes</span></span>  
  
|<span data-ttu-id="58002-111">屬性</span><span class="sxs-lookup"><span data-stu-id="58002-111">Attribute</span></span>|<span data-ttu-id="58002-112">描述</span><span class="sxs-lookup"><span data-stu-id="58002-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58002-113">findValue</span><span class="sxs-lookup"><span data-stu-id="58002-113">findValue</span></span>|<span data-ttu-id="58002-114">指定要在 X.509 憑證存放區中搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="58002-114">Specifies the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="58002-115">這個屬性所包含的型別必須滿足指定之 `X509FindType` 值的需求。</span><span class="sxs-lookup"><span data-stu-id="58002-115">The type contained in this attribute must satisfy the requirements of the specified `X509FindType` value.</span></span> <span data-ttu-id="58002-116">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="58002-116">The default is an empty string.</span></span>|  
|<span data-ttu-id="58002-117">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="58002-117">isChainIncluded</span></span>|<span data-ttu-id="58002-118">布林值，這個值會指定是否使用憑證鏈結完成驗證。</span><span class="sxs-lookup"><span data-stu-id="58002-118">A Boolean value that specifies if the validation is done using a certificate chain.</span></span>|  
|<span data-ttu-id="58002-119">storeLocation</span><span class="sxs-lookup"><span data-stu-id="58002-119">storeLocation</span></span>|<span data-ttu-id="58002-120">指定用戶端可用來驗證伺服器憑證之憑證存放區的位置。</span><span class="sxs-lookup"><span data-stu-id="58002-120">Specifies the location of the certificate store that the client can use to validate the server’s certificate.</span></span><br /><br /> <span data-ttu-id="58002-121">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="58002-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="58002-122">-LocalMachine: 指派憑證存放區至本機電腦。</span><span class="sxs-lookup"><span data-stu-id="58002-122">-   LocalMachine: The cert store assigned to the local machine.</span></span><br /><span data-ttu-id="58002-123">-CurrentUser: 指派憑證存放區目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="58002-123">-   CurrentUser: The cert store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="58002-124">預設值為 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="58002-124">The default value is LocalMachine.</span></span><br /><br /> <span data-ttu-id="58002-125">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="58002-125">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
|<span data-ttu-id="58002-126">storeName</span><span class="sxs-lookup"><span data-stu-id="58002-126">storeName</span></span>|<span data-ttu-id="58002-127">指定要開啟之 X.509 憑證存放區的名稱。</span><span class="sxs-lookup"><span data-stu-id="58002-127">Specifies the name of the X.509 certificate store to open.</span></span><br /><br /> <span data-ttu-id="58002-128">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="58002-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="58002-129">-AddressBook： 其他使用者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="58002-129">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="58002-130">-AuthRoot： 協力廠商憑證授權單位 (Ca) 的存放區的憑證。</span><span class="sxs-lookup"><span data-stu-id="58002-130">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="58002-131">-CertificateAuthority： 中繼 Ca 的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="58002-131">-   CertificateAuthority: Certificate store for intermediate CAs.</span></span><br /><span data-ttu-id="58002-132">-不允許： 憑證已撤銷之憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="58002-132">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="58002-133">-My： 憑證個人憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="58002-133">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="58002-134">-Root： 信任根 Ca 的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="58002-134">-   Root: Certificate store for trusted root CAs.</span></span><br /><span data-ttu-id="58002-135">-TrustedPeople： 直接信任之人員和資源的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="58002-135">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="58002-136">-TrustedPublisher： 直接信任之發行者的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="58002-136">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="58002-137">預設值為 My。</span><span class="sxs-lookup"><span data-stu-id="58002-137">The default value is My.</span></span><br /><br /> <span data-ttu-id="58002-138">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreName>。</span><span class="sxs-lookup"><span data-stu-id="58002-138">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreName>.</span></span>|  
|<span data-ttu-id="58002-139">X509FindType</span><span class="sxs-lookup"><span data-stu-id="58002-139">X509FindType</span></span>|<span data-ttu-id="58002-140">指定要執行之 X.509 搜尋的型別。</span><span class="sxs-lookup"><span data-stu-id="58002-140">Specifies the type of X.509 search to be executed.</span></span> <span data-ttu-id="58002-141">`findValue` 屬性所包含的型別必須滿足指定之 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="58002-141">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="58002-142">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="58002-142">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="58002-143">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="58002-143">-   FindByThumbPrint</span></span><br /><span data-ttu-id="58002-144">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="58002-144">-   FindBySubjectName</span></span><br /><span data-ttu-id="58002-145">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="58002-145">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="58002-146">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="58002-146">-   FindByIssuerName</span></span><br /><span data-ttu-id="58002-147">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="58002-147">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="58002-148">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="58002-148">-   FindBySerialNumber</span></span><br /><span data-ttu-id="58002-149">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="58002-149">-   FindByTimeValid</span></span><br /><span data-ttu-id="58002-150">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="58002-150">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="58002-151">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="58002-151">-   FindByTemplateName</span></span><br /><span data-ttu-id="58002-152">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="58002-152">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="58002-153">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="58002-153">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="58002-154">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="58002-154">-   FindByExtension</span></span><br /><span data-ttu-id="58002-155">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="58002-155">-   FindByKeyUsage</span></span><br /><span data-ttu-id="58002-156">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="58002-156">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="58002-157">預設值為 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="58002-157">The default value is FindBySubjectDistinguishedName.</span></span><br /><br /> <span data-ttu-id="58002-158">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509FindType>。</span><span class="sxs-lookup"><span data-stu-id="58002-158">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58002-159">子元素</span><span class="sxs-lookup"><span data-stu-id="58002-159">Child Elements</span></span>  
 <span data-ttu-id="58002-160">無。</span><span class="sxs-lookup"><span data-stu-id="58002-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58002-161">父項目</span><span class="sxs-lookup"><span data-stu-id="58002-161">Parent Elements</span></span>  
  
|<span data-ttu-id="58002-162">項目</span><span class="sxs-lookup"><span data-stu-id="58002-162">Element</span></span>|<span data-ttu-id="58002-163">說明</span><span class="sxs-lookup"><span data-stu-id="58002-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58002-164">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="58002-164">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="58002-165">指定設定，這個設定可讓其他端點與此端點交換訊息時啟用端點驗證。</span><span class="sxs-lookup"><span data-stu-id="58002-165">Specifies settings that enable the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58002-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58002-166">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>
