---
title: 作法：建立開發時要使用的暫時憑證
description: 瞭解如何使用 PowerShell Cmdlet 來建立兩個暫時性的 x.509 憑證，以用於開發安全的 WCF 服務或用戶端。
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: a249f0de00c45b1588762ffa0f826e890f961334
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91607768"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>作法：建立開發時要使用的暫時憑證

使用 Windows Communication Foundation (WCF) 開發安全服務或用戶端時，通常需要提供要作為認證使用的 x.509 憑證。 憑證通常是憑證鏈結的一部分，在電腦的 [受信任的根憑證授權單位] 存放區中有根授權。 具有憑證鏈結可讓您設定一組憑證的範圍，其中根授權通常來自您的組織或企業單位。 如果要在開發期間進行模擬，您可以建立兩種憑證以滿足安全性需求。 第一種是放在 [受信任的根憑證授權單位] 存放區中的自我簽署憑證，而第二種憑證是從第一種建立的，並放在個人存放區或本機位置，或目前使用者位置的個人存放區。 本主題逐步解說使用 PowerShell [new-selfsignedcertificate) ](/powershell/module/pkiclient/new-selfsignedcertificate) Cmdlet 來建立這兩個憑證的步驟。

> [!IMPORTANT]
> 新 New-selfsignedcertificate 指令程式所產生的憑證僅供測試用途。 當部署服務或用戶端時，請確定使用由憑證授權單位所提供的適當憑證。 這可能是來自您組織中的 Windows Server 憑證伺服器或協力廠商。
>
> 根據預設， [new-selfsignedcertificate](/powershell/module/pkiclient/new-selfsignedcertificate) 指令程式會建立自我簽署的憑證，而且這些憑證不安全。 將自我簽署的憑證放在 [受信任的根憑證授權單位] 存放區，可讓您建立更緊密模擬部署環境的開發環境。

 如需建立和使用憑證的詳細資訊，請參閱 [使用憑證](working-with-certificates.md)。 如需使用憑證做為認證的詳細資訊，請參閱 [保護服務與用戶端](securing-services-and-clients.md)。 如需有關使用 Microsoft Authenticode 技術的教學課程，請參閱 [Authenticode 概觀與教學課程 (英文)](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537360(v=vs.85))。

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>建立自我簽署根授權憑證及匯出私密金鑰

下列命令會在目前使用者的個人存放區中建立主體名稱為 ">rootca.pem" 的自我簽署憑證。

```powershell
$rootcert = New-SelfSignedCertificate -CertStoreLocation Cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("2.5.29.19={text}CA=true") -KeyUsage CertSign,CrlSign,DigitalSignature
```

我們需要將憑證匯出至 PFX 檔案，以便在稍後的步驟中將其匯入至所需的位置。 匯出具有私密金鑰的憑證時，需要密碼才能保護它。 我們會將密碼儲存在中 `SecureString` ，並使用 [get-pfxcertificate](/powershell/module/pkiclient/export-pfxcertificate) Cmdlet 將具有相關私密金鑰的憑證匯出至 PFX 檔案。 我們也會使用 [Export 憑證](/powershell/module/pkiclient/export-certificate) Cmdlet 將公開憑證儲存至 CRT 檔案中。

```powershell
[System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
[String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>建立由根授權憑證簽署的新憑證

下列命令會 `RootCA` 使用簽發者的私密金鑰，建立以 "SignedByRootCA" 主體名稱簽署的憑證。

```powershell
$testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

同樣地，我們會將具有私密金鑰的已簽署憑證儲存至 PFX 檔案，而將公開金鑰儲存至 CRT 檔案中。

```powershell
[String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>在受信任的根憑證授權單位存放區中安裝憑證

在建立自我簽署憑證之後，您就可以將它安裝在 [受信任的根憑證授權單位] 存放區中。 此時任何使用憑證簽署的憑證都受到電腦的信任。 因此，當您不再需要憑證時，請立刻從存放區中將其刪除。 當您刪除這個根授權憑證時，使用該憑證簽署的所有其他憑證都會變成未經授權的。 根授權憑證只是一種機制，可依需要設定一組憑證的範圍。 例如，在對等應用程式中，通常不需要根授權，因為您只是藉由個體提供的憑證而信任其身分識別。

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>在受信任的根憑證授權單位中安裝自我簽署憑證

1. 請開啟憑證嵌入式管理單元。 如需詳細資訊，請參閱 [做法：使用 MMC 嵌入式管理單元檢視憑證](how-to-view-certificates-with-the-mmc-snap-in.md)。

2. 開啟資料夾以儲存憑證，可以是 [ **本機電腦** ] 或 [ **目前使用者**]。

3. 開啟 [ **受信任的根憑證授權單位** ] 資料夾。

4. 用滑鼠右鍵依序按一下 [ **憑證** ] 資料夾、[ **所有工作**] 和 [ **匯入**]。

5. 遵循螢幕上的 wizard 指示，將 >rootca.pem .pfx 匯入到存放區。

## <a name="using-certificates-with-wcf"></a>使用憑證搭配 WCF

設定暫時憑證之後，您可以用它來開發可將憑證指定為用戶端認證類型的 WCF 方案。 例如，下列 XML 組態會指定訊息安全性，而且將憑證指定為用戶端認證類型。

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>若要將憑證指定為用戶端認證類型

1. 在服務的組態檔中，使用下列 XML 將安全性模式設定為訊息，而且將用戶端認證類型設定為憑證。

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

2. 在用戶端的設定檔中，使用下列 XML 來指定在使用者的存放區中找到該憑證，並搜尋 SubjectName 欄位中的值 "CohoWinery" 來找到該憑證。

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

如需在 WCF 中使用憑證的詳細資訊，請參閱 [Working with Certificates](working-with-certificates.md)。

## <a name="net-framework-security"></a>.NET Framework 安全性

請用滑鼠右鍵按一下憑證，然後按一下 [ **刪除** ]，以確定從 [ **受信任的根憑證授權單位** ] 和 [ **個人**] 資料夾中刪除暫時的根授權憑證。

## <a name="see-also"></a>另請參閱

- [使用憑證](working-with-certificates.md)
- [作法：使用 MMC 嵌入式管理單元來檢視憑證](how-to-view-certificates-with-the-mmc-snap-in.md)
- [確保服務與用戶端的安全](securing-services-and-clients.md)
