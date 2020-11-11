---
ms.openlocfilehash: 4ab2fc0645f76870dead99b5f45eef763643fb27
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506894"
---

[您可以從「貼齊」存放區使用 .NET Core。](https://snapcraft.io/dotnet-sdk)

「貼齊」是應用程式及其相依性的組合，可在不需要跨多個不同 Linux 發行版本進行修改的情況下運作。 快照可從貼齊存放區中探索並安裝。 如需貼齊的詳細資訊，請參閱 [開始使用嵌入式管理單元](https://snapcraft.io/docs/getting-started)。

只有支援的 .NET Core 版本可透過 [貼齊] 使用。

### <a name="install-the-sdk"></a>安裝 SDK

適用于 .NET SDK 的嵌入式管理套件都會在相同的識別碼下發布： `dotnet-sdk` 。 您可以藉由指定通道來安裝特定版本的 SDK。 SDK 包含 coresponding 執行時間。 下表列出通道：

| .NET 版本 | 貼齊套件             |
|--------------|--------------------------|
| 5.0          | `5.0` 或 `latest/stable` |
| 3.1 (LTS)     | `3.1` 或 `lts/stable`    |
| 2.1 (LTS)     | `2.1`                    |

使用 `snap install` 命令來安裝 .NET SDK 嵌入式管理套件。 使用 `--channel` 參數來指出要安裝的版本。 如果省略此參數， `latest/stable` 則會使用。 在此範例中， `5.0` 指定了：

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

接下來， `dotnet` 使用下列命令註冊系統的命令 `snap alias` ：

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。 您可以選擇任何想要 `{alias}` 的名稱。 例如，您可以在由 snap：進行安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-sdk.dotnet dotnet50` 。 當您使用命令時 `dotnet50` ，將會叫用這個特定的 .net 版本。 但是，這與大部分的教學課程和範例都不相容，因為它們預期 `dotnet` 會有命令可供使用。

### <a name="install-the-runtime"></a>安裝執行階段

適用于 .NET Core 執行時間的貼齊套件會在其專屬套件識別碼下發布。 下表列出封裝識別碼：

| .NET 版本      | 貼齊套件        |
|-------------------|---------------------|
| 5.0               | `dotnet-runtime-50` |
| 3.1 (LTS)          | `dotnet-runtime-31` |
| 3.0               | `dotnet-runtime-30` |
| 2.2               | `dotnet-runtime-22` |
| 2.1 (LTS)          | `dotnet-runtime-21` |

使用 `snap install` 命令來安裝 .Net 執行時間嵌入式管理套件。 在此範例中，會安裝 .NET 5.0：

```bash
sudo snap install dotnet-runtime-50 --classic
```

接下來， `dotnet` 使用下列命令註冊系統的命令 `snap alias` ：

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。 您可以選擇任何想要 `{alias}` 的名稱。 例如，您可以在由 snap：進行安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-runtime-50.dotnet dotnet50` 。 當您使用命令時 `dotnet50` ，將會叫用這個特定的 .net 版本。 但是，這與大部分的教學課程和範例都不相容，因為它們預期 `dotnet` 會有命令可供使用。

### <a name="ssl-certificate-errors"></a>SSL 憑證錯誤

透過 [貼齊] 安裝 .NET 時，可能會在某些散發版本上找不到 .NET SSL 憑證，而且您可能會在下列情況收到類似下面的錯誤 `restore` ：

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

若要解決此問題，請設定一些環境變數：

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

憑證位置會因發行版本而異。 以下是我們遇到問題的散發版本位置。

* Fedora `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`
* OpenSUSE `/etc/ssl/ca-bundle.pem`
* Solus - `/etc/ssl/certs/ca-certificates.crt`
