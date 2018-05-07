---
title: FindPrivateKey 範例-WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 72e2f49ae7c39b4a0486ec053ff1164c2d833cbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="findprivatekey-sample"></a>FindPrivateKey 範例

在憑證存放區中尋找與特定 X.509 憑證相關聯的私密金鑰檔案位置和名稱，可能相當困難。 FindPrivateKey.exe 工具有助於進行這個程序。

> [!IMPORTANT]
> FindPrivateKey 是必須先編譯才能使用的範例。 請參閱[建置 FindPrivateKey 專案](#to-build-the-findprivatekey-project)> 一節，如需如何建置 FindPrivateKey 工具的指示。

X.509 憑證是由電腦中的系統管理員或任何使用者所安裝。 不過，憑證可能由不同的帳戶下執行的服務存取。 例如，網路服務帳戶。

這個帳戶可能無法用來存取私密金鑰檔案，因為憑證原先並非透過這個帳戶來安裝。 FindPrivateKey 工具提供您指定之 X.509 憑證的私密金鑰檔案位置。 一旦知道特定 X.509 憑證的私密金鑰檔案位置之後，您就可以新增權限至此檔案或移除此檔案的權限。

使用安全性憑證的範例使用中的 FindPrivateKey 工具*Setup.bat*檔案。 一旦找到私密金鑰檔案，您可以使用其他工具例如*Cacls.exe*檔案設定適當的存取權。

當執行 Windows Communication Foundation (WCF) 服務的使用者帳戶，例如自我裝載的可執行檔，請確認使用者帳戶具有唯讀存取檔案。 當執行 WCF 服務在網際網路資訊服務 (IIS) 服務之下執行的預設帳戶是在 IIS 7 和舊版中，網路服務或 IIS 7.5 和更新版本上的應用程式集區身分識別。 如需詳細資訊，請參閱[應用程式集區識別](/iis/manage/configuring-security/application-pool-identities)。

## <a name="examples"></a>範例

存取時的處理程序沒有讀取權限的憑證，您會看到類似下列範例的例外狀況訊息：

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

當發生這種情況時，使用 FindPrivateKey 工具尋找私密金鑰檔案，並將存取權限執行服務的程序。 比方說，這可以使用 Cacls.exe 工具如下列範例所示：

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>若要建置 FindPrivateKey 專案

若要下載的專案，請造訪[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://www.microsoft.com/download/details.aspx?id=21459)。

1. 開啟[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]並瀏覽至*WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS*範例的安裝所在的目錄位置下的資料夾。

2. 按兩下 .sln 檔案圖示，在 Visual Studio 中開啟檔案。

3. 在**建置**功能表上，選取**重建方案**。

4. 建置方案會產生檔案 FindPrivateKey.exe。

## <a name="conventionscommand-line-entries"></a>慣例 — 命令列項目

 "[*選項*]"代表一組選擇性的參數。

 "{*選項*}"代表強制的參數組。

 「*選項 1* &#124; *選項 2*"表示的選項集之間的選擇。

 「\<*值*> 」 表示輸入參數值。

## <a name="usage"></a>使用量

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

其中：

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

如果未不指定任何參數，在命令提示字元，則會顯示這個說明文字。

## <a name="examples"></a>範例

此範例會尋找的檔案名稱的憑證主體名稱為"CN = localhost"，目前使用者的個人存放區中。

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

此範例會尋找的檔案名稱的憑證主體名稱為"CN = localhost"、 在個人存放區目前的使用者和輸出的完整目錄路徑。

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

這個範例會在 Local Computer 的 Personal 存放區中尋找指紋為 "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" 之憑證的檔案名稱。

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
