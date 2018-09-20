---
title: HOW TO：建立開發時要使用的暫時憑證
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: 2d0301b040d0fd9865eaf5c3f96fe320ccfd8488
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46485307"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>HOW TO：建立開發時要使用的暫時憑證

開發安全的服務或使用 Windows Communication Foundation (WCF) 用戶端時，通常必須提供要用做為認證的 X.509 憑證。 憑證通常是憑證鏈結的一部分，在電腦的 [受信任的根憑證授權單位] 存放區中有根授權。 具有憑證鏈結可讓您設定一組憑證的範圍，其中根授權通常來自您的組織或企業單位。 如果要在開發期間進行模擬，您可以建立兩種憑證以滿足安全性需求。 第一種是放在 [受信任的根憑證授權單位] 存放區中的自我簽署憑證，而第二種憑證是從第一種建立的，並放在個人存放區或本機位置，或目前使用者位置的個人存放區。 本主題逐步解說的步驟來建立這兩個憑證，使用 Powershell [New-selfsignedcertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet。

> [!IMPORTANT]
> 僅供測試用途提供 New-selfsignedcertificate cmdlet 會產生憑證。 當部署服務或用戶端時，請確定使用由憑證授權單位所提供的適當憑證。 這可能是您組織中的 Windows Server 憑證伺服器，或第三方。
>
> 根據預設， [New-selfsignedcertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet 會建立自我簽署的憑證，以及這些憑證是不安全。 將自我簽署的憑證放在受信任的根憑證授權單位存放區可讓您建立更能夠模擬您的部署環境的開發環境。

 如需有關建立及使用憑證的詳細資訊，請參閱 < [Working with Certificates](working-with-certificates.md)。 如需使用憑證做為認證的詳細資訊，請參閱[Securing Services and Clients](securing-services-and-clients.md)。 如需有關使用 Microsoft Authenticode 技術的教學課程，請參閱 < [Authenticode 概觀與教學課程](https://go.microsoft.com/fwlink/?LinkId=88919)。

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>建立自我簽署根授權憑證及匯出私密金鑰

下列命令會建立自我簽署的憑證的主體名稱為"RootCA 「 目前使用者個人存放區中。

```powershell
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```

我們需要將憑證匯出為 PFX 檔案，使其可以匯入到需要在稍後步驟中的位置。 當使用私密金鑰匯出憑證，才能保護它需要的密碼。 我們將儲存的密碼`SecureString`並用[Export-pfxcertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet 來將憑證匯出為 PFX 檔案相關聯的私密金鑰。 我們也將公開金鑰的憑證儲存到使用 CRT 檔案[匯出憑證](/powershell/module/pkiclient/export-certificate)cmdlet。

```powershell
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>建立由根授權憑證簽署的新憑證

下列命令會建立所簽署的憑證`RootCA`主體名稱為"SignedByRootCA 」 使用的簽發者的私密金鑰。

```powershell
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

同樣地，我們將儲存的簽署的憑證與私用的索引鍵到 PFX 檔案，並只將 CRT 檔案的公用金鑰。

```powershell
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>在受信任的根憑證授權單位存放區中安裝憑證

在建立自我簽署憑證之後，您就可以將它安裝在 [受信任的根憑證授權單位] 存放區中。 此時任何使用憑證簽署的憑證都受到電腦的信任。 因此，當您不再需要憑證時，請立刻從存放區中將其刪除。 當您刪除這個根授權憑證時，使用該憑證簽署的所有其他憑證都會變成未經授權的。 根授權憑證只是一種機制，可依需要設定一組憑證的範圍。 例如，在對等應用程式中，通常不需要根授權，因為您只是藉由個體提供的憑證而信任其身分識別。

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>在受信任的根憑證授權單位中安裝自我簽署憑證

1. 請開啟憑證嵌入式管理單元。 如需詳細資訊，請參閱[如何：使用 MMC 嵌入式管理單元來檢視憑證](how-to-view-certificates-with-the-mmc-snap-in.md)。

2. 開啟資料夾以儲存憑證，可以是 [ **本機電腦** ] 或 [ **目前使用者**]。

3. 開啟 [ **受信任的根憑證授權單位** ] 資料夾。

4. 用滑鼠右鍵依序按一下 [ **憑證** ] 資料夾、[ **所有工作**] 和 [ **匯入**]。

5. 請依照螢幕上的精靈指示，將 TempCa.cer 匯入存放區中。

## <a name="using-certificates-with-wcf"></a>使用憑證與 WCF

設定暫時憑證之後，您可以用它來開發可將憑證指定為用戶端認證類型的 WCF 方案。 例如，下列 XML 組態會指定訊息安全性，而且將憑證指定為用戶端認證類型。

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>若要將憑證指定為用戶端認證類型

- 在服務的組態檔中，使用下列 XML 將安全性模式設定為訊息，而且將用戶端認證類型設定為憑證。

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

在用戶端的組態檔，請使用下列 XML 來指定憑證位於使用者的存放區，並且可搜尋在 SubjectName 欄位中的值"CohoWinery"。

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

如需在 WCF 中使用憑證的詳細資訊，請參閱[Working with Certificates](working-with-certificates.md)。

## <a name="net-framework-security"></a>.NET Framework 安全性

請用滑鼠右鍵按一下憑證，然後按一下 [ **刪除** ]，以確定從 [ **受信任的根憑證授權單位** ] 和 [ **個人**] 資料夾中刪除暫時的根授權憑證。

## <a name="see-also"></a>另請參閱

- [使用憑證](working-with-certificates.md)
- [如何：使用 MMC 嵌入式管理單元來檢視憑證](how-to-view-certificates-with-the-mmc-snap-in.md)
- [保護服務和用戶端的安全](securing-services-and-clients.md)