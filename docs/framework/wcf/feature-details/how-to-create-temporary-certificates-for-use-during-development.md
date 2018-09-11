---
title: HOW TO：建立開發時要使用的暫時憑證
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: ca495c23b30144013b8efe22b7bf6f3cf38b16cd
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273975"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="f055c-102">HOW TO：建立開發時要使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="f055c-102">How to: Create Temporary Certificates for Use During Development</span></span>
<span data-ttu-id="f055c-103">開發安全的服務或使用 Windows Communication Foundation (WCF) 用戶端時，通常必須提供要用做為認證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="f055c-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="f055c-104">憑證通常是憑證鏈結的一部分，在電腦的 [受信任的根憑證授權單位] 存放區中有根授權。</span><span class="sxs-lookup"><span data-stu-id="f055c-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="f055c-105">具有憑證鏈結可讓您設定一組憑證的範圍，其中根授權通常來自您的組織或企業單位。</span><span class="sxs-lookup"><span data-stu-id="f055c-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="f055c-106">如果要在開發期間進行模擬，您可以建立兩種憑證以滿足安全性需求。</span><span class="sxs-lookup"><span data-stu-id="f055c-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="f055c-107">第一種是放在 [受信任的根憑證授權單位] 存放區中的自我簽署憑證，而第二種憑證是從第一種建立的，並放在個人存放區或本機位置，或目前使用者位置的個人存放區。</span><span class="sxs-lookup"><span data-stu-id="f055c-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="f055c-108">本主題逐步解說的步驟來建立這兩個憑證，使用 Powershell [New-selfsignedcertificate)](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f055c-108">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps) cmdlet.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f055c-109">僅供測試用途提供 New-selfsignedcertificate cmdlet 會產生憑證。</span><span class="sxs-lookup"><span data-stu-id="f055c-109">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="f055c-110">當部署服務或用戶端時，請確定使用由憑證授權單位所提供的適當憑證。</span><span class="sxs-lookup"><span data-stu-id="f055c-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="f055c-111">這可能是您組織中的 Windows Server 憑證伺服器，或第三方。</span><span class="sxs-lookup"><span data-stu-id="f055c-111">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>  
>   
>  <span data-ttu-id="f055c-112">根據預設， [New-selfsignedcertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps) cmdlet 會建立自我簽署的憑證，以及這些憑證是不安全。</span><span class="sxs-lookup"><span data-stu-id="f055c-112">By default, the [New-SelfSignedCertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="f055c-113">將自我簽署的憑證放在受信任的根憑證授權單位存放區可讓您建立更能夠模擬您的部署環境的開發環境。</span><span class="sxs-lookup"><span data-stu-id="f055c-113">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>  
  
 <span data-ttu-id="f055c-114">如需有關建立及使用憑證的詳細資訊，請參閱 < [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="f055c-114">For more information about creating and using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="f055c-115">如需使用憑證做為認證的詳細資訊，請參閱[Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="f055c-115">For more information about using a certificate as a credential, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="f055c-116">如需有關使用 Microsoft Authenticode 技術的教學課程，請參閱 < [Authenticode 概觀與教學課程](https://go.microsoft.com/fwlink/?LinkId=88919)。</span><span class="sxs-lookup"><span data-stu-id="f055c-116">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="f055c-117">建立自我簽署根授權憑證及匯出私密金鑰</span><span class="sxs-lookup"><span data-stu-id="f055c-117">To create a self-signed root authority certificate and export the private key</span></span>  
  
<span data-ttu-id="f055c-118">下列命令會建立自我簽署的憑證的主體名稱為"RootCA 「 目前使用者個人存放區中。</span><span class="sxs-lookup"><span data-stu-id="f055c-118">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span> 
```
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```
<span data-ttu-id="f055c-119">我們需要將憑證匯出為 PFX 檔案，使其可以匯入到需要在稍後步驟中的位置。</span><span class="sxs-lookup"><span data-stu-id="f055c-119">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="f055c-120">當使用私密金鑰匯出憑證，才能保護它需要的密碼。</span><span class="sxs-lookup"><span data-stu-id="f055c-120">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="f055c-121">我們將儲存的密碼`SecureString`並用[Export-pfxcertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/export-pfxcertificate?view=win10-ps) cmdlet 來將憑證匯出為 PFX 檔案相關聯的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="f055c-121">We save the password in a `SecureString` and use the [Export-PfxCertificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/export-pfxcertificate?view=win10-ps) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="f055c-122">我們也將公開金鑰的憑證儲存到使用 CRT 檔案[匯出憑證](https://docs.microsoft.com/en-us/powershell/module/pkiclient/export-certificate?view=win10-ps)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f055c-122">We also save just the public certificate into a CRT file using the [Export-Certificate](https://docs.microsoft.com/en-us/powershell/module/pkiclient/export-certificate?view=win10-ps) cmdlet.</span></span>
```
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="f055c-123">建立由根授權憑證簽署的新憑證</span><span class="sxs-lookup"><span data-stu-id="f055c-123">To create a new certificate signed by a root authority certificate</span></span>  
  
<span data-ttu-id="f055c-124">下列命令會建立所簽署的憑證`RootCA`主體名稱為"SignedByRootCA 」 使用的簽發者的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="f055c-124">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>
```
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert 
```
<span data-ttu-id="f055c-125">同樣地，我們將儲存的簽署的憑證與私用的索引鍵到 PFX 檔案，並只將 CRT 檔案的公用金鑰。</span><span class="sxs-lookup"><span data-stu-id="f055c-125">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>
```
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword 
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt        
```
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="f055c-126">在受信任的根憑證授權單位存放區中安裝憑證</span><span class="sxs-lookup"><span data-stu-id="f055c-126">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>  
 <span data-ttu-id="f055c-127">在建立自我簽署憑證之後，您就可以將它安裝在 [受信任的根憑證授權單位] 存放區中。</span><span class="sxs-lookup"><span data-stu-id="f055c-127">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="f055c-128">此時任何使用憑證簽署的憑證都受到電腦的信任。</span><span class="sxs-lookup"><span data-stu-id="f055c-128">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="f055c-129">因此，當您不再需要憑證時，請立刻從存放區中將其刪除。</span><span class="sxs-lookup"><span data-stu-id="f055c-129">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="f055c-130">當您刪除這個根授權憑證時，使用該憑證簽署的所有其他憑證都會變成未經授權的。</span><span class="sxs-lookup"><span data-stu-id="f055c-130">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="f055c-131">根授權憑證只是一種機制，可依需要設定一組憑證的範圍。</span><span class="sxs-lookup"><span data-stu-id="f055c-131">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="f055c-132">例如，在對等應用程式中，通常不需要根授權，因為您只是藉由個體提供的憑證而信任其身分識別。</span><span class="sxs-lookup"><span data-stu-id="f055c-132">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="f055c-133">在受信任的根憑證授權單位中安裝自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="f055c-133">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>  
  
1.  <span data-ttu-id="f055c-134">請開啟憑證嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="f055c-134">Open the certificate snap-in.</span></span> <span data-ttu-id="f055c-135">如需詳細資訊，請參閱[如何：使用 MMC 嵌入式管理單元來檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="f055c-135">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="f055c-136">開啟資料夾以儲存憑證，可以是 [ **本機電腦** ] 或 [ **目前使用者**]。</span><span class="sxs-lookup"><span data-stu-id="f055c-136">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>  
  
3.  <span data-ttu-id="f055c-137">開啟 [ **受信任的根憑證授權單位** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f055c-137">Open the **Trusted Root Certification Authorities** folder.</span></span>  
  
4.  <span data-ttu-id="f055c-138">用滑鼠右鍵依序按一下 [ **憑證** ] 資料夾、[ **所有工作**] 和 [ **匯入**]。</span><span class="sxs-lookup"><span data-stu-id="f055c-138">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>  
  
5.  <span data-ttu-id="f055c-139">請依照螢幕上的精靈指示，將 TempCa.cer 匯入存放區中。</span><span class="sxs-lookup"><span data-stu-id="f055c-139">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>  
  
## <a name="using-certificates-with-wcf"></a><span data-ttu-id="f055c-140">搭配 WCF 使用憑證</span><span class="sxs-lookup"><span data-stu-id="f055c-140">Using Certificates With WCF</span></span>  
 <span data-ttu-id="f055c-141">設定暫時憑證之後，您可以用它來開發可將憑證指定為用戶端認證類型的 WCF 方案。</span><span class="sxs-lookup"><span data-stu-id="f055c-141">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="f055c-142">例如，下列 XML 組態會指定訊息安全性，而且將憑證指定為用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="f055c-142">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="f055c-143">若要將憑證指定為用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="f055c-143">To specify a certificate as the client credential type</span></span>  
  
-   <span data-ttu-id="f055c-144">在服務的組態檔中，使用下列 XML 將安全性模式設定為訊息，而且將用戶端認證類型設定為憑證。</span><span class="sxs-lookup"><span data-stu-id="f055c-144">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 <span data-ttu-id="f055c-145">在用戶端的組態檔，請使用下列 XML 來指定憑證位於使用者的存放區，並且可搜尋在 SubjectName 欄位中的值"CohoWinery"。</span><span class="sxs-lookup"><span data-stu-id="f055c-145">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="f055c-146">如需在 WCF 中使用憑證的詳細資訊，請參閱 [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="f055c-146">For more information about using certificates in WCF, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f055c-147">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="f055c-147">.NET Framework Security</span></span>  
 <span data-ttu-id="f055c-148">請用滑鼠右鍵按一下憑證，然後按一下 [ **刪除** ]，以確定從 [ **受信任的根憑證授權單位** ] 和 [ **個人**] 資料夾中刪除暫時的根授權憑證。</span><span class="sxs-lookup"><span data-stu-id="f055c-148">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f055c-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f055c-149">See Also</span></span>  
 [<span data-ttu-id="f055c-150">使用憑證</span><span class="sxs-lookup"><span data-stu-id="f055c-150">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="f055c-151">如何：使用 MMC 嵌入式管理單元來檢視憑證</span><span class="sxs-lookup"><span data-stu-id="f055c-151">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="f055c-152">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="f055c-152">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
