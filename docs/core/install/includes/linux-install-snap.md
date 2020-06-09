---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602912"
---

[您可以從 [貼齊存放區] 取得 .NET Core。](https://snapcraft.io/dotnet-sdk)

「貼齊」是應用程式及其相依性的組合，不需要在許多不同的 Linux 散發套件上進行修改即可運作。 您可以從 [貼齊存放區] 探索和安裝快照。 如需有關貼齊的詳細資訊，請參閱[開始使用貼齊](https://snapcraft.io/docs/getting-started)。

只有支援的 .NET Core 版本可透過 [貼齊] 取得。

### <a name="install-the-sdk"></a>安裝 SDK

.NET Core SDK 的貼齊封裝都是以相同的識別碼發佈： `dotnet-sdk` 。 您可以藉由指定通道來安裝特定版本的 SDK。 SDK 包含 coresponding 執行時間。 下表列出通道：

| .NET Core 版本 | 貼齊套件             |
|-------------------|--------------------------|
| 3.1 （LTS）         | `3.1` 或 `latest/stable` |
| 2.1 （LTS）         | `2.1`                    |
| .NET 5.0 preview  | `5.0/beta`               |

使用 `snap install` 命令來安裝 .NET Core SDK 的貼齊套件。 使用 `--channel` 參數來指出要安裝的版本。 如果省略此參數， `latest/stable` 則會使用。 在此範例中， `3.1` 會指定：

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

接下來， `dotnet` 使用命令來註冊系統的命令 `snap alias` ：

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。 您可以選擇您想要 `{alias}` 的任何名稱。 例如，您可以在 [貼齊：] 安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-sdk.dotnet dotnet31` 。 當您使用命令時 `dotnet31` ，您將會叫用此特定版本的 .net。 但這與大部分的教學課程和範例不相容，因為它們預期 `dotnet` 會有命令可供使用。

### <a name="install-the-runtime"></a>安裝執行階段

.NET Core 執行時間的貼齊套件會分別以自己的套件識別碼發行。 下表列出套件識別碼：

| .NET Core 版本 | 貼齊套件        |
|-------------------|---------------------|
| 3.1 （LTS）         | `dotnet-runtime-31` |
| 3.0               | `dotnet-runtime-30` |
| 2.2               | `dotnet-runtime-22` |
| 2.1 （LTS）         | `dotnet-runtime-21` |

使用 `snap install` 命令來安裝 .Net Core 執行時間嵌入式管理套件。 在此範例中，會安裝 .NET Core 3.1：

```bash
sudo snap install dotnet-runtime-31 --classic
```

接下來， `dotnet` 使用命令來註冊系統的命令 `snap alias` ：

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。 您可以選擇您想要 `{alias}` 的任何名稱。 例如，您可以在 [貼齊：] 安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-runtime-31.dotnet dotnet31` 。 當您使用命令時 `dotnet31` ，您將會叫用此特定版本的 .net。 但這與大部分的教學課程和範例不相容，因為它們預期 `dotnet` 會有命令可供使用。

### <a name="ssl-certificate-errors"></a>SSL 憑證錯誤

透過貼齊安裝 .NET 時，可能會在某些散發版本上找不到 .NET SSL 憑證，而且您可能會在下列情況收到類似以下的錯誤 `restore` ：

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

若要解決此問題，請設定幾個環境變數：

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

憑證位置會因散發版本而異。 以下是我們遇到此問題的散發版本位置。

* Fedora`/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`
* OpenSUSE`/etc/ssl/ca-bundle.pem`
* Solus -`/etc/ssl/certs/ca-certificates.crt`
