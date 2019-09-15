---
title: FindPrivateKey 範例-WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 4ba4316489c1494da9421bea5c513e44c6eb50a7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989877"
---
# <a name="findprivatekey-sample"></a>FindPrivateKey 範例

在憑證存放區中尋找與特定 X.509 憑證相關聯的私密金鑰檔案位置和名稱，可能相當困難。 FindPrivateKey.exe 工具有助於進行這個程序。

> [!IMPORTANT]
> FindPrivateKey 是必須先編譯才能使用的範例。 如需如何建立 FindPrivateKey 工具的指示，請參閱 <<c0>若要建立 FindPrivateKey 專案一節。

X.509 憑證是由電腦中的系統管理員或任何使用者所安裝。 不過，在不同帳戶下執行的服務可能會存取憑證。 例如，NETWORK SERVICE 帳戶。

這個帳戶可能無法用來存取私密金鑰檔案，因為憑證原先並非透過這個帳戶來安裝。 FindPrivateKey 工具提供您指定之 X.509 憑證的私密金鑰檔案位置。 一旦知道特定 X.509 憑證的私密金鑰檔案位置之後，您就可以新增權限至此檔案或移除此檔案的權限。

使用憑證來進行安全性的範例會使用*安裝程式 .bat*檔案中的 FindPrivateKey 工具。 一旦找到私密金鑰檔案之後，您就可以使用其他工具（例如*Cacls* ），在檔案上設定適當的存取權限。

在使用者帳戶（例如自我裝載的可執行檔）下執行 Windows Communication Foundation （WCF）服務時，請確定使用者帳戶具有該檔案的唯讀存取權。 在 Internet Information Services （IIS）下執行 WCF 服務時，用來執行服務的預設帳戶是 IIS 7 和更早版本上的網路服務，或是 IIS 7.5 和更新版本上的應用程式集區識別。 如需詳細資訊，請參閱[應用程式集](/iis/manage/configuring-security/application-pool-identities)區身分識別。

## <a name="examples"></a>範例

存取進程沒有讀取權限的憑證時，您會看到類似下列範例的例外狀況訊息：

```output
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

發生這種情況時，請使用 FindPrivateKey 工具來尋找私密金鑰檔案，然後設定服務執行所在進程的存取權限。 例如，您可以使用 Cacls 工具來完成這項作業，如下列範例所示：

```console
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>若要建置 FindPrivateKey 專案

若要下載專案，請造訪[適用于 .NET Framework 4 的 Windows Communication Foundation （WCF）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)。

1. 開啟 [檔案瀏覽器]，然後流覽至安裝範例所在目錄位置下的 [ *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* ] 資料夾。

2. 按兩下 .sln 檔案圖示，在 Visual Studio 中開啟檔案。

3. 在 [**建立**] 功能表中，選取 [**重建方案**]。

4. 建立解決方案會產生檔案：FindPrivateKey .exe。

## <a name="conventionscommand-line-entries"></a>慣例-命令列專案

 "[*option*]" 代表一組選擇性的參數。

 "{*option*}" 代表一組必要的參數。

 "*option1* &#124; *option2*" 代表選項組之間的選擇。

 「值 >」代表要輸入的參數值。 \<

## <a name="usage"></a>使用量

```console
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

其中：

| 參數         | 說明                                                                       |
|-----------------|-----------------------------------------------------------------------------------|
| `<subjectName>` | 憑證的主體名稱                                               |
| `<thumbprint>`  | 憑證的指紋（您可以使用 Certmgr.msc 來尋找此項） |
| `-f`            | 僅輸出檔案名                                                             |
| `-d`            | 僅輸出目錄                                                             |
| `-a`            | 輸出絕對的檔案名                                                         |

如果在命令提示字元中未指定任何參數，則會顯示含有這則資訊的解說文字。

## <a name="examples"></a>範例

這個範例會在目前使用者的個人存放區中，尋找主體名稱為 "CN = localhost" 之憑證的檔案名。

```console
FindPrivateKey My CurrentUser -n "CN=localhost"
```

這個範例會在目前使用者的個人存放區中，尋找主體名稱為 "CN = localhost" 之憑證的檔案名，並輸出完整的目錄路徑。

```console
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

這個範例會在 Local Computer 的 Personal 存放區中尋找指紋為 "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" 之憑證的檔案名稱。

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
