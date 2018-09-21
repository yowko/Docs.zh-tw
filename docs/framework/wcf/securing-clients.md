---
title: 確保用戶端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e0bed1e47302cc80a04498f39144177acdbc9ae6
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537408"
---
# <a name="securing-clients"></a><span data-ttu-id="74310-102">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="74310-102">Securing Clients</span></span>
<span data-ttu-id="74310-103">在 Windows Communication Foundation (WCF) 中，服務說明用戶端的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="74310-103">In Windows Communication Foundation (WCF), the service dictates the security requirements for clients.</span></span> <span data-ttu-id="74310-104">也就是說，服務會指定使用哪一個安全性模式，以及用戶端是否必須提供認證。</span><span class="sxs-lookup"><span data-stu-id="74310-104">That is, the service specifies what security mode to use, and whether or not the client must provide a credential.</span></span> <span data-ttu-id="74310-105">因此，保護用戶端安全的程序便十分簡單，只要使用從服務 (如果已發行) 取得的中繼資料並建立用戶端即可。</span><span class="sxs-lookup"><span data-stu-id="74310-105">The process of securing a client, therefore, is simple: use the metadata obtained from the service (if it is published) and build a client.</span></span> <span data-ttu-id="74310-106">中繼資料指定如何設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="74310-106">The metadata specifies how to configure the client.</span></span> <span data-ttu-id="74310-107">如果服務要求用戶端提供認證，則您必須取得符合要求的認證。</span><span class="sxs-lookup"><span data-stu-id="74310-107">If the service requires that the client supply a credential, then you must obtain a credential that fits the requirement.</span></span> <span data-ttu-id="74310-108">本主題將進一步探討此程序。</span><span class="sxs-lookup"><span data-stu-id="74310-108">This topic discusses the process in further detail.</span></span> <span data-ttu-id="74310-109">如需建立安全服務的詳細資訊，請參閱[Securing Services](../../../docs/framework/wcf/securing-services.md)。</span><span class="sxs-lookup"><span data-stu-id="74310-109">For more information about creating a secure service, see [Securing Services](../../../docs/framework/wcf/securing-services.md).</span></span>  
  
## <a name="the-service-specifies-security"></a><span data-ttu-id="74310-110">指定安全性的服務</span><span class="sxs-lookup"><span data-stu-id="74310-110">The Service Specifies Security</span></span>  
 <span data-ttu-id="74310-111">根據預設，WCF 繫結已啟用安全性功能。</span><span class="sxs-lookup"><span data-stu-id="74310-111">By default, WCF bindings have security features enabled.</span></span> <span data-ttu-id="74310-112">(例外狀況是 <xref:System.ServiceModel.BasicHttpBinding>)。因此，如果服務已使用 WCF 建立的是較有可能實作安全性以確保驗證、 機密性和完整性。</span><span class="sxs-lookup"><span data-stu-id="74310-112">(The exception is the <xref:System.ServiceModel.BasicHttpBinding>.) Therefore, if the service was created using WCF, there is a greater chance that it will implement security to ensure authentication, confidentiality, and integrity.</span></span> <span data-ttu-id="74310-113">在該情況下，服務提供的中繼資料將指示它需要什麼來建立安全的通訊通道。</span><span class="sxs-lookup"><span data-stu-id="74310-113">In that case, the metadata the service provides will indicate what it requires to establish a secure communication channel.</span></span> <span data-ttu-id="74310-114">如果服務中繼資料沒有任何安全性需要，那麼就沒有方法強制服務採用安全性配置 (例如透過 HTTP 的 Secure Sockets Layer (SSL))。</span><span class="sxs-lookup"><span data-stu-id="74310-114">If the service metadata does not include any security requirements, there is no way to impose a security scheme, such as Secure Sockets Layer (SSL) over HTTP, on a service.</span></span> <span data-ttu-id="74310-115">如果服務要求用戶端提供認證，則用戶端開發人員、部署人員或管理員必須提供用戶端用來向服務驗證的實際認證。</span><span class="sxs-lookup"><span data-stu-id="74310-115">If, however, the service requires the client to supply a credential, then the client developer, deployer, or administrator must supply the actual credential that the client will use to authenticate itself to the service.</span></span>  
  
## <a name="obtaining-metadata"></a><span data-ttu-id="74310-116">取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="74310-116">Obtaining Metadata</span></span>  
 <span data-ttu-id="74310-117">建立用戶端時，第一個步驟是取得與用戶端通訊的服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="74310-117">When creating a client, the first step is to obtain the metadata for the service that the client will communicate with.</span></span> <span data-ttu-id="74310-118">有兩種方法可以達到這個目的：</span><span class="sxs-lookup"><span data-stu-id="74310-118">This can be done in two ways.</span></span> <span data-ttu-id="74310-119">首先，如果服務發行中繼資料交換 (MEX) 端點，或透過 HTTP 或 HTTPS 提供它的中繼資料，您可以下載的中繼資料使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)，如此就會產生兩者用戶端，以及您在組態檔的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="74310-119">First, if the service publishes a metadata exchange (MEX) endpoint or makes its metadata available over HTTP or HTTPS, you can download the metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), which generates both code files for a client as well as a configuration file.</span></span> <span data-ttu-id="74310-120">(如需使用工具的詳細資訊，請參閱[使用 WCF 用戶端存取服務](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)。)如果服務未發行 MEX 端點，而且也沒有透過 HTTP 或 HTTPS 提供它的中繼資料，您必須向服務建立者要求描述安全性需求與中繼資料的文件。</span><span class="sxs-lookup"><span data-stu-id="74310-120">(For more information about using the tool, see [Accessing Services Using a WCF Client](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).) If the service does not publish a MEX endpoint and also does not make its metadata available over HTTP or HTTPS, you must contact the service creator for documentation that describes the security requirements and the metadata.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74310-121">建議使用來自受信任來源且不可竄改的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="74310-121">It is recommended that the metadata come from a trusted source and that it not be tampered with.</span></span> <span data-ttu-id="74310-122">使用 HTTP 通訊協定擷取的中繼資料會以純文字傳送出去且可以竄改。</span><span class="sxs-lookup"><span data-stu-id="74310-122">Metadata retrieved using the HTTP protocol is sent in clear text and can be tampered with.</span></span> <span data-ttu-id="74310-123">如果服務使用 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> 和 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> 屬性，請以服務建立者提供的 URL 來使用 HTTPS 通訊協定下載資料。</span><span class="sxs-lookup"><span data-stu-id="74310-123">If the service uses the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> and <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> properties, use the URL the service creator supplied to download the data using the HTTPS protocol.</span></span>  
  
## <a name="validating-security"></a><span data-ttu-id="74310-124">驗證安全性</span><span class="sxs-lookup"><span data-stu-id="74310-124">Validating Security</span></span>  
 <span data-ttu-id="74310-125">中繼來源可以區分成兩大類別：信任來源與不受信任的來源。</span><span class="sxs-lookup"><span data-stu-id="74310-125">Metadata sources can be divided into two broad categories: trust sources and untrusted sources.</span></span> <span data-ttu-id="74310-126">如果您信任來源，而且已從該來源的安全 MEX 端點下載用戶端程式碼和其他中繼資料，那麼您可以建立用戶端，提供用戶端正確的認證，並且毫無後顧之憂地執行它。</span><span class="sxs-lookup"><span data-stu-id="74310-126">If you trust a source and have downloaded the client code and other metadata from that source's secure MEX endpoint, then you can build the client, supply it with the right credentials, and run it with no other concerns.</span></span>  
  
 <span data-ttu-id="74310-127">如果您選擇從您對它幾乎一無所知的來源下載用戶端和中繼資料，請務必驗證程式碼使用的安全性措施。</span><span class="sxs-lookup"><span data-stu-id="74310-127">However, if you elect to download a client and metadata from a source that you know little about, be sure to validate the security measures the code uses.</span></span> <span data-ttu-id="74310-128">例如，您不可以只建立傳送您的個人資料或財務資料到服務的用戶端，除非該服務僅要求機密性和完整性。</span><span class="sxs-lookup"><span data-stu-id="74310-128">For example, you must not simply create a client that sends your personal or financial information to a service unless the service demands confidentiality and integrity (at the very least).</span></span> <span data-ttu-id="74310-129">您服務擁有者的信任應該可達到您願意公開這類資訊的程度，因為他或她將會看到這些資訊。</span><span class="sxs-lookup"><span data-stu-id="74310-129">You should trust the owner of the service to the extent that you are willing to disclose such information because such information will be visible to him or her.</span></span>  
  
 <span data-ttu-id="74310-130">因此，通常在使用來自不受信任來源的程式碼和中繼資料時，請檢查程式碼和中繼資料，以確保其符合您要求的安全性等級。</span><span class="sxs-lookup"><span data-stu-id="74310-130">As a rule, therefore, when using code and metadata from an untrusted source, check the code and metadata to ensure that it meets the security level that you require.</span></span>  
  
## <a name="setting-a-client-credential"></a><span data-ttu-id="74310-131">設定用戶端認證</span><span class="sxs-lookup"><span data-stu-id="74310-131">Setting a Client Credential</span></span>  
 <span data-ttu-id="74310-132">在用戶端上設定用戶端認證是由兩個步驟所組成：</span><span class="sxs-lookup"><span data-stu-id="74310-132">Setting a client credential on a client consists of two steps:</span></span>  
  
1.  <span data-ttu-id="74310-133">判斷*用戶端認證類型*服務要求。</span><span class="sxs-lookup"><span data-stu-id="74310-133">Determine the *client credential type* the service requires.</span></span> <span data-ttu-id="74310-134">這可以由兩個方法的其中之一完成。</span><span class="sxs-lookup"><span data-stu-id="74310-134">This is accomplished by one of two methods.</span></span> <span data-ttu-id="74310-135">首先，如果您有來自服務建立者的文件，文件中應指出服務需要的用戶端認證類型 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="74310-135">First, if you have documentation from the service creator, it should specify the client credential type (if any) the service requires.</span></span> <span data-ttu-id="74310-136">再者，如果您只有 Svcutil.exe 工具產生的組態檔，您可以檢查個別的繫結來判斷需要哪一種認證類型。</span><span class="sxs-lookup"><span data-stu-id="74310-136">Second, if you have only a configuration file generated by the Svcutil.exe tool, you can examine the individual bindings to determine what credential type is required.</span></span>  
  
2.  <span data-ttu-id="74310-137">指定實際的用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="74310-137">Specify an actual client credential.</span></span> <span data-ttu-id="74310-138">實際的用戶端認證稱為*用戶端認證值*以區分它與類型。</span><span class="sxs-lookup"><span data-stu-id="74310-138">The actual client credential is called a *client credential value* to distinguish it from the type.</span></span> <span data-ttu-id="74310-139">例如，如果用戶端認證類型指定憑證，您必須提供由服務信任的憑證授權單位核發的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="74310-139">For example, if the client credential type specifies a certificate, you must supply an X.509 certificate that is issued by a certification authority the service trusts.</span></span>  
  
### <a name="determining-the-client-credential-type"></a><span data-ttu-id="74310-140">判斷用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="74310-140">Determining the Client Credential Type</span></span>  
 <span data-ttu-id="74310-141">如果您有 Svcutil.exe 工具產生的檔案，請檢查組態[\<繫結 >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)區段可決定哪些用戶端認證類型是必要項。</span><span class="sxs-lookup"><span data-stu-id="74310-141">If you have the configuration file the Svcutil.exe tool generated, examine the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section to determine what client credential type is required.</span></span> <span data-ttu-id="74310-142">在該部分內有指定安全性需要的繫結程序項目。</span><span class="sxs-lookup"><span data-stu-id="74310-142">Within the section are binding elements that specify the security requirements.</span></span> <span data-ttu-id="74310-143">具體來說，檢查\<安全性 > 的每個繫結項目。</span><span class="sxs-lookup"><span data-stu-id="74310-143">Specifically, examine the \<security> Element of each binding.</span></span> <span data-ttu-id="74310-144">該項目包括 `mode` 屬性，您可以將該屬性設定為三個可能值 (`Message`、`Transport` 或 `TransportWithMessageCredential`) 的其中之一。</span><span class="sxs-lookup"><span data-stu-id="74310-144">That element includes the `mode` attribute, which you can set to one of three possible values (`Message`, `Transport`, or `TransportWithMessageCredential`).</span></span> <span data-ttu-id="74310-145">屬性的值決定模式，而模式決定哪一個子項目是重要的。</span><span class="sxs-lookup"><span data-stu-id="74310-145">The value of the attribute determines the mode, and the mode determines which of the child elements is significant.</span></span>  
  
 <span data-ttu-id="74310-146">`<security>`項目可以包含`<transport>`或`<message>`項目，或兩者。</span><span class="sxs-lookup"><span data-stu-id="74310-146">The `<security>` element can contain either a `<transport>` or `<message>` element, or both.</span></span> <span data-ttu-id="74310-147">重要的項目就是符合安全性模式的項目。</span><span class="sxs-lookup"><span data-stu-id="74310-147">The significant element is the one that matches the security mode.</span></span> <span data-ttu-id="74310-148">例如，下列程式碼指定安全性模式為 `"Message"`，而且 `<message>` 項目的用戶端認證類型是 `"Certificate"`。</span><span class="sxs-lookup"><span data-stu-id="74310-148">For example, the following code specifies that the security mode is `"Message"`, and the client credential type for the `<message>` element is `"Certificate"`.</span></span> <span data-ttu-id="74310-149">在這個情況中，可以忽略 `<transport>` 項目。</span><span class="sxs-lookup"><span data-stu-id="74310-149">In this case, the `<transport>` element can be ignored.</span></span> <span data-ttu-id="74310-150">但 `<message>` 項目指定必須提供 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="74310-150">However, the `<message>` element specifies that an X.509 certificate must be supplied.</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"   
                      realm="" />  
           <message clientCredentialType="Certificate"   
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"   
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="74310-151">請注意，如果 `clientCredentialType` 屬性已設定為 `"Windows"`，如下列範例所示，您不需要提供實際的認證值。</span><span class="sxs-lookup"><span data-stu-id="74310-151">Note that if the `clientCredentialType` attribute is set to `"Windows"`, as shown in the following example, you do not need to supply an actual credential value.</span></span> <span data-ttu-id="74310-152">這是因為 Windows 整合式安全性已提供執行用戶端之人員的實際認證 (Kerberos 權杖)。</span><span class="sxs-lookup"><span data-stu-id="74310-152">This is because the Windows integrated security provides the actual credential (a Kerberos token) of the person who is running the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a><span data-ttu-id="74310-153">設定用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="74310-153">Setting the Client Credential Value</span></span>  
 <span data-ttu-id="74310-154">如果用戶端必須提供認證，請使用適當方法設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="74310-154">If it is determined that the client must supply a credential, use the appropriate method to configure the client.</span></span> <span data-ttu-id="74310-155">例如，使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法設定用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="74310-155">For example, to set a client certificate, use the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span>  
  
 <span data-ttu-id="74310-156">常見的認證形式是 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="74310-156">A common form of credential is the X.509 certificate.</span></span> <span data-ttu-id="74310-157">您可以用兩種方式提供認證：</span><span class="sxs-lookup"><span data-stu-id="74310-157">You can supply the credential in two ways:</span></span>  
  
-   <span data-ttu-id="74310-158">以程式設計方式將它編寫在您的用戶端程式碼中 (使用 `SetCertificate` 方法)。</span><span class="sxs-lookup"><span data-stu-id="74310-158">By programming it in your client code (using the `SetCertificate` method).</span></span>  
  
 <span data-ttu-id="74310-159">藉由新增[\<行為 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)用戶端組態檔區段及使用`clientCredentials`項目 （如下所示）。</span><span class="sxs-lookup"><span data-stu-id="74310-159">By adding a [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the configuration file for the client and using the `clientCredentials` element (shown below).</span></span>  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a><span data-ttu-id="74310-160">設定\<clientCredentials > 程式碼中的值</span><span class="sxs-lookup"><span data-stu-id="74310-160">Setting a \<clientCredentials> Value in Code</span></span>  
 <span data-ttu-id="74310-161">若要設定[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)值中的程式碼，您必須存取<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>屬性<xref:System.ServiceModel.ClientBase%601>類別。</span><span class="sxs-lookup"><span data-stu-id="74310-161">To set a [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) value in code, you must access the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="74310-162">該屬性傳回允許存取各種認證類型的 <xref:System.ServiceModel.Description.ClientCredentials> 物件，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="74310-162">The property returns a <xref:System.ServiceModel.Description.ClientCredentials> object that allows access to various credential types, as shown in the following table.</span></span>  
  
|<span data-ttu-id="74310-163">ClientCredential 屬性</span><span class="sxs-lookup"><span data-stu-id="74310-163">ClientCredential Property</span></span>|<span data-ttu-id="74310-164">描述</span><span class="sxs-lookup"><span data-stu-id="74310-164">Description</span></span>|<span data-ttu-id="74310-165">注意</span><span class="sxs-lookup"><span data-stu-id="74310-165">Notes</span></span>|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|<span data-ttu-id="74310-166">傳回 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential></span><span class="sxs-lookup"><span data-stu-id="74310-166">Returns an <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential></span></span>|<span data-ttu-id="74310-167">代表用戶端向服務進行驗證時提供的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="74310-167">Represents an X.509 certificate provided by the client to authenticate itself to the service.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|<span data-ttu-id="74310-168">傳回 <xref:System.ServiceModel.Security.HttpDigestClientCredential></span><span class="sxs-lookup"><span data-stu-id="74310-168">Returns an <xref:System.ServiceModel.Security.HttpDigestClientCredential></span></span>|<span data-ttu-id="74310-169">代表 HTTP 摘要式認證。</span><span class="sxs-lookup"><span data-stu-id="74310-169">Represents an HTTP digest credential.</span></span> <span data-ttu-id="74310-170">此認證是使用者名稱與密碼的雜湊。</span><span class="sxs-lookup"><span data-stu-id="74310-170">The credential is a hash of the user name and password.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|<span data-ttu-id="74310-171">傳回 <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="74310-171">Returns an <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>|<span data-ttu-id="74310-172">代表安全性權杖服務核發的自訂安全性權杖，常使用於聯合案例中。</span><span class="sxs-lookup"><span data-stu-id="74310-172">Represents a custom security token issued by a Security Token Service, commonly used in federation scenarios.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|<span data-ttu-id="74310-173">傳回 <xref:System.ServiceModel.Security.PeerCredential></span><span class="sxs-lookup"><span data-stu-id="74310-173">Returns a <xref:System.ServiceModel.Security.PeerCredential></span></span>|<span data-ttu-id="74310-174">代表用在 Windows 網域上參與對等網狀結構的對等認證。</span><span class="sxs-lookup"><span data-stu-id="74310-174">Represents a Peer credential for participation in a Peer mesh on a Windows domain.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|<span data-ttu-id="74310-175">傳回 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential></span><span class="sxs-lookup"><span data-stu-id="74310-175">Returns an <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential></span></span>|<span data-ttu-id="74310-176">代表超出範圍交涉中的服務所提供的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="74310-176">Represents an X.509 certificate provided by the service in an out-of-band negotiation.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|<span data-ttu-id="74310-177">傳回 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential></span><span class="sxs-lookup"><span data-stu-id="74310-177">Returns a <xref:System.ServiceModel.Security.UserNamePasswordClientCredential></span></span>|<span data-ttu-id="74310-178">代表使用者名稱和密碼組。</span><span class="sxs-lookup"><span data-stu-id="74310-178">Represents a user name and password pair.</span></span>|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|<span data-ttu-id="74310-179">傳回 <xref:System.ServiceModel.Security.WindowsClientCredential></span><span class="sxs-lookup"><span data-stu-id="74310-179">Returns a <xref:System.ServiceModel.Security.WindowsClientCredential></span></span>|<span data-ttu-id="74310-180">代表 Windows 用戶端認證 (Kerberos 認證)。</span><span class="sxs-lookup"><span data-stu-id="74310-180">Represents a Windows client credential (a Kerberos credential).</span></span> <span data-ttu-id="74310-181">類別的屬性是唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="74310-181">The properties of the class are read-only.</span></span>|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a><span data-ttu-id="74310-182">設定\<clientCredentials > 組態中的值</span><span class="sxs-lookup"><span data-stu-id="74310-182">Setting a \<clientCredentials> Value in Configuration</span></span>  
 <span data-ttu-id="74310-183">使用端點行為，為的子元素指定認證值[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目。</span><span class="sxs-lookup"><span data-stu-id="74310-183">Credential values are specified by using an endpoint behavior as child elements of the [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span> <span data-ttu-id="74310-184">使用的項目視用戶端認證類型而定。</span><span class="sxs-lookup"><span data-stu-id="74310-184">The element used depends on the client credential type.</span></span> <span data-ttu-id="74310-185">例如，下列範例示範設定 X.509 憑證使用的組態 <[\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)。</span><span class="sxs-lookup"><span data-stu-id="74310-185">For example, the following example shows the configuration to set an X.509 certificate using the <[\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"   
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>              
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="74310-186">若要設定的用戶端認證組態中，新增[ \<endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)至組態檔的項目。</span><span class="sxs-lookup"><span data-stu-id="74310-186">To set the client credential in configuration, add an [\<endpointBehaviors>](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element to the configuration file.</span></span> <span data-ttu-id="74310-187">此外，您必須將新增的行為項目連結至服務的端點使用`behaviorConfiguration`的屬性[\<端點 >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)項目，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="74310-187">Additionally, the added behavior element must be linked to the service's endpoint using the `behaviorConfiguration` attribute of the [\<endpoint>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element as shown in the following example.</span></span> <span data-ttu-id="74310-188">`behaviorConfiguration` 屬性的值必須與 `name` 屬性的值相符。</span><span class="sxs-lookup"><span data-stu-id="74310-188">The value of the `behaviorConfiguration` attribute must match the value of the behavior `name` attribute.</span></span>  
  
 `<configuration>`  
  
 `<system.serviceModel>`  
  
 `<client>`  
  
 `<endpoint address="http://localhost/servicemodelsamples/service.svc"`  
  
 `binding="wsHttpBinding"`  
  
 `bindingConfiguration="Binding1"`  
  
 `behaviorConfiguration="myEndpointBehavior"`  
  
 `contract="Microsoft.ServiceModel.Samples.ICalculator" />`  
  
 `</client>`  
  
 `</system.serviceModel>`  
  
 `</configuration>`  
  
> [!NOTE]
>  <span data-ttu-id="74310-189">使用應用程式組態檔無法設定某些用戶端認證值，例如使用者名稱和密碼，或者 Windows 使用者和密碼值。</span><span class="sxs-lookup"><span data-stu-id="74310-189">Some of the client credential values cannot be set using application configuration files, for example, user name and password, or Windows user and password values.</span></span> <span data-ttu-id="74310-190">這類認證值只能在程式碼中指定。</span><span class="sxs-lookup"><span data-stu-id="74310-190">Such credential values can be specified only in code.</span></span>  
  
 <span data-ttu-id="74310-191">如需有關如何設定用戶端憑證的詳細資訊，請參閱 < [How to: Specify Client Credential Values](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="74310-191">For more information about setting the client credential, see [How to: Specify Client Credential Values](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74310-192">`ClientCredentialType` 設定為 `SecurityMode` 時，會忽略 `"TransportWithMessageCredential",`，如下列範例組態所示。</span><span class="sxs-lookup"><span data-stu-id="74310-192">`ClientCredentialType` is ignored when `SecurityMode` is set to `"TransportWithMessageCredential",` as shown in the following sample configuration.</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"   
               establishSecurityContext="false"    
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74310-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74310-193">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [<span data-ttu-id="74310-194">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="74310-194">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
 [<span data-ttu-id="74310-195">設定編輯器工具 (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="74310-195">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="74310-196">保護服務安全</span><span class="sxs-lookup"><span data-stu-id="74310-196">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="74310-197">使用 WCF 用戶端存取服務</span><span class="sxs-lookup"><span data-stu-id="74310-197">Accessing Services Using a WCF Client</span></span>](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [<span data-ttu-id="74310-198">如何：指定用戶端認證值</span><span class="sxs-lookup"><span data-stu-id="74310-198">How to: Specify Client Credential Values</span></span>](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [<span data-ttu-id="74310-199">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="74310-199">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="74310-200">如何：指定用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="74310-200">How to: Specify the Client Credential Type</span></span>](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
