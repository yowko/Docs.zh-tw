---
title: 作法：建立開發時要使用的暫時憑證
description: 瞭解如何使用 PowerShell Cmdlet 來建立兩個暫時性的 x.509 憑證，以用於開發安全的 WCF 服務或用戶端。
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 0907f7f8a3767db9d83e5deaae1d86141fbee7b0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557407"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="b4015-103">作法：建立開發時要使用的暫時憑證</span><span class="sxs-lookup"><span data-stu-id="b4015-103">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="b4015-104">使用 Windows Communication Foundation (WCF) 開發安全服務或用戶端時，通常需要提供要作為認證使用的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="b4015-104">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="b4015-105">憑證通常是憑證鏈結的一部分，在電腦的 [受信任的根憑證授權單位] 存放區中有根授權。</span><span class="sxs-lookup"><span data-stu-id="b4015-105">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="b4015-106">具有憑證鏈結可讓您設定一組憑證的範圍，其中根授權通常來自您的組織或企業單位。</span><span class="sxs-lookup"><span data-stu-id="b4015-106">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="b4015-107">如果要在開發期間進行模擬，您可以建立兩種憑證以滿足安全性需求。</span><span class="sxs-lookup"><span data-stu-id="b4015-107">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="b4015-108">第一種是放在 [受信任的根憑證授權單位] 存放區中的自我簽署憑證，而第二種憑證是從第一種建立的，並放在個人存放區或本機位置，或目前使用者位置的個人存放區。</span><span class="sxs-lookup"><span data-stu-id="b4015-108">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="b4015-109">本主題逐步解說使用 Powershell [new-selfsignedcertificate) ](/powershell/module/pkiclient/new-selfsignedcertificate) Cmdlet 來建立這兩個憑證的步驟。</span><span class="sxs-lookup"><span data-stu-id="b4015-109">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4015-110">新 New-selfsignedcertificate 指令程式所產生的憑證僅供測試用途。</span><span class="sxs-lookup"><span data-stu-id="b4015-110">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="b4015-111">當部署服務或用戶端時，請確定使用由憑證授權單位所提供的適當憑證。</span><span class="sxs-lookup"><span data-stu-id="b4015-111">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="b4015-112">這可能是來自您組織中的 Windows Server 憑證伺服器或協力廠商。</span><span class="sxs-lookup"><span data-stu-id="b4015-112">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="b4015-113">根據預設， [new-selfsignedcertificate](/powershell/module/pkiclient/new-selfsignedcertificate) 指令程式會建立自我簽署的憑證，而且這些憑證不安全。</span><span class="sxs-lookup"><span data-stu-id="b4015-113">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="b4015-114">將自我簽署的憑證放在 [受信任的根憑證授權單位] 存放區，可讓您建立更緊密模擬部署環境的開發環境。</span><span class="sxs-lookup"><span data-stu-id="b4015-114">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="b4015-115">如需建立和使用憑證的詳細資訊，請參閱 [使用憑證](working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="b4015-115">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="b4015-116">如需使用憑證做為認證的詳細資訊，請參閱 [保護服務與用戶端](securing-services-and-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="b4015-116">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="b4015-117">如需有關使用 Microsoft Authenticode 技術的教學課程，請參閱 [Authenticode 概觀與教學課程 (英文)](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="b4015-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85)).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="b4015-118">建立自我簽署根授權憑證及匯出私密金鑰</span><span class="sxs-lookup"><span data-stu-id="b4015-118">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="b4015-119">下列命令會在目前使用者的個人存放區中建立主體名稱為 ">rootca.pem" 的自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="b4015-119">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

<span data-ttu-id="b4015-120">我們需要將憑證匯出至 PFX 檔案，以便在稍後的步驟中將其匯入至所需的位置。</span><span class="sxs-lookup"><span data-stu-id="b4015-120">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="b4015-121">匯出具有私密金鑰的憑證時，需要密碼才能保護它。</span><span class="sxs-lookup"><span data-stu-id="b4015-121">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="b4015-122">我們會將密碼儲存在中 `SecureString` ，並使用 [get-pfxcertificate](/powershell/module/pkiclient/export-pfxcertificate) Cmdlet 將具有相關私密金鑰的憑證匯出至 PFX 檔案。</span><span class="sxs-lookup"><span data-stu-id="b4015-122">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="b4015-123">我們也會使用 [Export 憑證](/powershell/module/pkiclient/export-certificate) Cmdlet 將公開憑證儲存至 CRT 檔案中。</span><span class="sxs-lookup"><span data-stu-id="b4015-123">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="b4015-124">建立由根授權憑證簽署的新憑證</span><span class="sxs-lookup"><span data-stu-id="b4015-124">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="b4015-125">下列命令會 `RootCA` 使用簽發者的私密金鑰，建立以 "SignedByRootCA" 主體名稱簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="b4015-125">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="b4015-126">同樣地，我們會將具有私密金鑰的已簽署憑證儲存至 PFX 檔案，而將公開金鑰儲存至 CRT 檔案中。</span><span class="sxs-lookup"><span data-stu-id="b4015-126">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="b4015-127">在受信任的根憑證授權單位存放區中安裝憑證</span><span class="sxs-lookup"><span data-stu-id="b4015-127">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="b4015-128">在建立自我簽署憑證之後，您就可以將它安裝在 [受信任的根憑證授權單位] 存放區中。</span><span class="sxs-lookup"><span data-stu-id="b4015-128">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="b4015-129">此時任何使用憑證簽署的憑證都受到電腦的信任。</span><span class="sxs-lookup"><span data-stu-id="b4015-129">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="b4015-130">因此，當您不再需要憑證時，請立刻從存放區中將其刪除。</span><span class="sxs-lookup"><span data-stu-id="b4015-130">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="b4015-131">當您刪除這個根授權憑證時，使用該憑證簽署的所有其他憑證都會變成未經授權的。</span><span class="sxs-lookup"><span data-stu-id="b4015-131">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="b4015-132">根授權憑證只是一種機制，可依需要設定一組憑證的範圍。</span><span class="sxs-lookup"><span data-stu-id="b4015-132">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="b4015-133">例如，在對等應用程式中，通常不需要根授權，因為您只是藉由個體提供的憑證而信任其身分識別。</span><span class="sxs-lookup"><span data-stu-id="b4015-133">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="b4015-134">在受信任的根憑證授權單位中安裝自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="b4015-134">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="b4015-135">請開啟憑證嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="b4015-135">Open the certificate snap-in.</span></span> <span data-ttu-id="b4015-136">如需詳細資訊，請參閱 [做法：使用 MMC 嵌入式管理單元檢視憑證](how-to-view-certificates-with-the-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="b4015-136">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="b4015-137">開啟資料夾以儲存憑證，可以是 [ **本機電腦** ] 或 [ **目前使用者**]。</span><span class="sxs-lookup"><span data-stu-id="b4015-137">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="b4015-138">開啟 [ **受信任的根憑證授權單位** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b4015-138">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="b4015-139">用滑鼠右鍵依序按一下 [ **憑證** ] 資料夾、[ **所有工作**] 和 [ **匯入**]。</span><span class="sxs-lookup"><span data-stu-id="b4015-139">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="b4015-140">遵循螢幕上的 wizard 指示，將 >rootca.pem .pfx 匯入到存放區。</span><span class="sxs-lookup"><span data-stu-id="b4015-140">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="b4015-141">使用憑證搭配 WCF</span><span class="sxs-lookup"><span data-stu-id="b4015-141">Using certificates With WCF</span></span>

<span data-ttu-id="b4015-142">設定暫時憑證之後，您可以用它來開發可將憑證指定為用戶端認證類型的 WCF 方案。</span><span class="sxs-lookup"><span data-stu-id="b4015-142">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="b4015-143">例如，下列 XML 組態會指定訊息安全性，而且將憑證指定為用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="b4015-143">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="b4015-144">若要將憑證指定為用戶端認證類型</span><span class="sxs-lookup"><span data-stu-id="b4015-144">To specify a certificate as the client credential type</span></span>

1. <span data-ttu-id="b4015-145">在服務的組態檔中，使用下列 XML 將安全性模式設定為訊息，而且將用戶端認證類型設定為憑證。</span><span class="sxs-lookup"><span data-stu-id="b4015-145">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

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

2. <span data-ttu-id="b4015-146">在用戶端的設定檔中，使用下列 XML 來指定在使用者的存放區中找到該憑證，並搜尋 SubjectName 欄位中的值 "CohoWinery" 來找到該憑證。</span><span class="sxs-lookup"><span data-stu-id="b4015-146">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

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

<span data-ttu-id="b4015-147">如需在 WCF 中使用憑證的詳細資訊，請參閱 [Working with Certificates](working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="b4015-147">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="b4015-148">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="b4015-148">.NET Framework security</span></span>

<span data-ttu-id="b4015-149">請用滑鼠右鍵按一下憑證，然後按一下 [ **刪除** ]，以確定從 [ **受信任的根憑證授權單位** ] 和 [ **個人**] 資料夾中刪除暫時的根授權憑證。</span><span class="sxs-lookup"><span data-stu-id="b4015-149">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4015-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4015-150">See also</span></span>

- [<span data-ttu-id="b4015-151">使用憑證</span><span class="sxs-lookup"><span data-stu-id="b4015-151">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="b4015-152">作法：使用 MMC 嵌入式管理單元來檢視憑證</span><span class="sxs-lookup"><span data-stu-id="b4015-152">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="b4015-153">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="b4015-153">Securing Services and Clients</span></span>](securing-services-and-clients.md)
