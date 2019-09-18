---
title: 作法：建立開發時要使用的暫時憑證
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: e2df35959f9821c65d694079aefa0ae6ba01897f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053299"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="ef94f-102">作法：建立開發時要使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="ef94f-102">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="ef94f-103">使用 Windows Communication Foundation （WCF）開發安全服務或用戶端時，通常必須提供 x.509 憑證，以做為認證使用。</span><span class="sxs-lookup"><span data-stu-id="ef94f-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="ef94f-104">憑證通常是憑證鏈結的一部分，在電腦的 [受信任的根憑證授權單位] 存放區中有根授權。</span><span class="sxs-lookup"><span data-stu-id="ef94f-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="ef94f-105">具有憑證鏈結可讓您設定一組憑證的範圍，其中根授權通常來自您的組織或企業單位。</span><span class="sxs-lookup"><span data-stu-id="ef94f-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="ef94f-106">如果要在開發期間進行模擬，您可以建立兩種憑證以滿足安全性需求。</span><span class="sxs-lookup"><span data-stu-id="ef94f-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="ef94f-107">第一種是放在 [受信任的根憑證授權單位] 存放區中的自我簽署憑證，而第二種憑證是從第一種建立的，並放在個人存放區或本機位置，或目前使用者位置的個人存放區。</span><span class="sxs-lookup"><span data-stu-id="ef94f-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="ef94f-108">本主題將逐步引導您使用 Powershell [New-SelfSignedCertificate）](/powershell/module/pkiclient/new-selfsignedcertificate) Cmdlet 來建立這兩個憑證。</span><span class="sxs-lookup"><span data-stu-id="ef94f-108">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef94f-109">SelfSignedCertificate Cmdlet 所產生的憑證僅供測試之用。</span><span class="sxs-lookup"><span data-stu-id="ef94f-109">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="ef94f-110">當部署服務或用戶端時，請確定使用由憑證授權單位所提供的適當憑證。</span><span class="sxs-lookup"><span data-stu-id="ef94f-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="ef94f-111">這可能是來自您組織中的 Windows Server 憑證伺服器或協力廠商。</span><span class="sxs-lookup"><span data-stu-id="ef94f-111">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="ef94f-112">根據預設， [SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate)指令程式會建立自我簽署的憑證，而且這些憑證不安全。</span><span class="sxs-lookup"><span data-stu-id="ef94f-112">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="ef94f-113">將自我簽署憑證放在「受信任的根憑證授權單位」存放區，可讓您建立更能更密切模擬部署環境的開發環境。</span><span class="sxs-lookup"><span data-stu-id="ef94f-113">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="ef94f-114">如需建立和使用憑證的詳細資訊，請參閱[使用憑證](working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="ef94f-114">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="ef94f-115">如需使用憑證做為認證的詳細資訊，請參閱[保護服務和用戶端](securing-services-and-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="ef94f-115">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="ef94f-116">如需有關使用 Microsoft Authenticode 技術的教學課程，請參閱 [Authenticode 概觀與教學課程 (英文)](https://go.microsoft.com/fwlink/?LinkId=88919)。</span><span class="sxs-lookup"><span data-stu-id="ef94f-116">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="ef94f-117">建立自我簽署根授權憑證及匯出私密金鑰</span><span class="sxs-lookup"><span data-stu-id="ef94f-117">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="ef94f-118">下列命令會在目前使用者的個人存放區中，建立主體名稱為 "Rootca.cer" 的自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="ef94f-118">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

<span data-ttu-id="ef94f-119">我們需要將憑證匯出到 PFX 檔案，以便將它匯入到稍後步驟所需的位置。</span><span class="sxs-lookup"><span data-stu-id="ef94f-119">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="ef94f-120">以私密金鑰匯出憑證時，需要密碼才能保護它。</span><span class="sxs-lookup"><span data-stu-id="ef94f-120">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="ef94f-121">我們會將密碼儲存在`SecureString`中，並使用[get-pfxcertificate](/powershell/module/pkiclient/export-pfxcertificate) Cmdlet，將具有相關私密金鑰的憑證匯出至 PFX 檔案。</span><span class="sxs-lookup"><span data-stu-id="ef94f-121">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="ef94f-122">我們也會使用[Export-certificate](/powershell/module/pkiclient/export-certificate) Cmdlet，將公開憑證只儲存到 CRT 檔案中。</span><span class="sxs-lookup"><span data-stu-id="ef94f-122">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="ef94f-123">建立由根授權憑證簽署的新憑證</span><span class="sxs-lookup"><span data-stu-id="ef94f-123">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="ef94f-124">下列命令會使用簽發者的私密金鑰， `RootCA`建立由主體名稱為 "SignedByRootCA" 之所簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="ef94f-124">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="ef94f-125">同樣地，我們會將已簽署的憑證連同私密金鑰儲存到 PFX 檔案中，而只將公開金鑰儲存到 CRT 檔案中。</span><span class="sxs-lookup"><span data-stu-id="ef94f-125">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="ef94f-126">在受信任的根憑證授權單位存放區中安裝憑證</span><span class="sxs-lookup"><span data-stu-id="ef94f-126">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="ef94f-127">在建立自我簽署憑證之後，您就可以將它安裝在 [受信任的根憑證授權單位] 存放區中。</span><span class="sxs-lookup"><span data-stu-id="ef94f-127">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="ef94f-128">此時任何使用憑證簽署的憑證都受到電腦的信任。</span><span class="sxs-lookup"><span data-stu-id="ef94f-128">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="ef94f-129">因此，當您不再需要憑證時，請立刻從存放區中將其刪除。</span><span class="sxs-lookup"><span data-stu-id="ef94f-129">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="ef94f-130">當您刪除這個根授權憑證時，使用該憑證簽署的所有其他憑證都會變成未經授權的。</span><span class="sxs-lookup"><span data-stu-id="ef94f-130">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="ef94f-131">根授權憑證只是一種機制，可依需要設定一組憑證的範圍。</span><span class="sxs-lookup"><span data-stu-id="ef94f-131">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="ef94f-132">例如，在對等應用程式中，通常不需要根授權，因為您只是藉由個體提供的憑證而信任其身分識別。</span><span class="sxs-lookup"><span data-stu-id="ef94f-132">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="ef94f-133">在受信任的根憑證授權單位中安裝自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="ef94f-133">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="ef94f-134">請開啟憑證嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="ef94f-134">Open the certificate snap-in.</span></span> <span data-ttu-id="ef94f-135">如需詳細資訊，請參閱[如何：使用 MMC 嵌入式管理](how-to-view-certificates-with-the-mmc-snap-in.md)單元來查看憑證。</span><span class="sxs-lookup"><span data-stu-id="ef94f-135">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="ef94f-136">開啟資料夾以儲存憑證，可以是 [ **本機電腦** ] 或 [ **目前使用者**]。</span><span class="sxs-lookup"><span data-stu-id="ef94f-136">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="ef94f-137">開啟 [ **受信任的根憑證授權單位** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ef94f-137">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="ef94f-138">用滑鼠右鍵依序按一下 [ **憑證** ] 資料夾、[ **所有工作**] 和 [ **匯入**]。</span><span class="sxs-lookup"><span data-stu-id="ef94f-138">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="ef94f-139">依照畫面上的 wizard 指示，將 Rootca.cer 匯入存放區。</span><span class="sxs-lookup"><span data-stu-id="ef94f-139">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="ef94f-140">搭配 WCF 使用憑證</span><span class="sxs-lookup"><span data-stu-id="ef94f-140">Using certificates With WCF</span></span>

<span data-ttu-id="ef94f-141">設定暫時憑證之後，您可以用它來開發可將憑證指定為用戶端認證類型的 WCF 方案。</span><span class="sxs-lookup"><span data-stu-id="ef94f-141">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="ef94f-142">例如，下列 XML 組態會指定訊息安全性，而且將憑證指定為用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="ef94f-142">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="ef94f-143">若要將憑證指定為用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="ef94f-143">To specify a certificate as the client credential type</span></span>

1. <span data-ttu-id="ef94f-144">在服務的組態檔中，使用下列 XML 將安全性模式設定為訊息，而且將用戶端認證類型設定為憑證。</span><span class="sxs-lookup"><span data-stu-id="ef94f-144">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

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

2. <span data-ttu-id="ef94f-145">在用戶端的設定檔中，使用下列 XML 來指定在使用者的存放區中找到該憑證，並藉由搜尋 SubjectName 欄位中的值 "CohoWinery" 來找到該憑證。</span><span class="sxs-lookup"><span data-stu-id="ef94f-145">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

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

<span data-ttu-id="ef94f-146">如需在 WCF 中使用憑證的詳細資訊，請參閱 [Working with Certificates](working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="ef94f-146">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="ef94f-147">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="ef94f-147">.NET Framework security</span></span>

<span data-ttu-id="ef94f-148">請用滑鼠右鍵按一下憑證，然後按一下 [ **刪除** ]，以確定從 [ **受信任的根憑證授權單位** ] 和 [ **個人**] 資料夾中刪除暫時的根授權憑證。</span><span class="sxs-lookup"><span data-stu-id="ef94f-148">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef94f-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef94f-149">See also</span></span>

- [<span data-ttu-id="ef94f-150">使用憑證</span><span class="sxs-lookup"><span data-stu-id="ef94f-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="ef94f-151">如何：使用 MMC 嵌入式管理單元來查看憑證</span><span class="sxs-lookup"><span data-stu-id="ef94f-151">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="ef94f-152">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="ef94f-152">Securing Services and Clients</span></span>](securing-services-and-clients.md)
