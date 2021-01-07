---
title: 在 Linux 上使用嵌入式管理單元安裝 .NET
description: 示範如何在 Linux 上使用貼齊來安裝 .NET SDK 或 .NET 執行時間。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 741933b5ca6f01d73b388675fe7f8a43c4efb0f9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970960"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a>安裝具有嵌入式管理單元的 .NET SDK 或 .NET 執行時間

使用嵌入式管理套件來安裝 .NET SDK 或 .NET 執行時間。 快照是內建于您的 Linux 散發套件管理員的絕佳替代方案。 本文說明如何透過 [ [貼齊](https://snapcraft.io/dotnet-sdk)] 來安裝 .net。

「貼齊」是應用程式及其相依性的組合，可在不需要跨多個不同 Linux 發行版本進行修改的情況下運作。 快照可從貼齊存放區中探索並安裝。 如需貼齊的詳細資訊，請參閱 [開始使用嵌入式管理單元](https://snapcraft.io/docs/getting-started)。

> [!CAUTION]
> Windows 10 上的 WSL2 不支援嵌入式管理套件。 或者，您也可使用[ `dotnet-install` 腳本](linux-scripted-manual.md#scripted-install)或封裝管理員來進行特定的 WSL2 散發。 不建議您這麼做，但您可以嘗試 [從 snapcraft 論壇](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033)啟用貼齊不支援的因應措施。

## <a name="net-releases"></a>.NET 版本

只有✔️支援的 .NET SDK 版本可透過 [貼齊] 使用。 所有版本的 .NET 執行時間都可透過從2.1 版開始的貼齊來取得。 下表列出 .NET (和 .NET Core) 版本：

| 支援✔️ | ❌ 支援 |
|-------------|---------------|
| 5.0         | 3.0           |
| 3.1 (LTS)    | 2.2           |
| 2.1 (LTS)    | 2.0           |
|             | 1.1           |
|             | 1.0           |

如需 .NET 版本生命週期的詳細資訊，請參閱 [.Net Core 和 .net 5 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

## <a name="sdk-or-runtime"></a>SDK 或執行時間

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a>安裝 SDK

.NET SDK 的貼齊套件都是在相同的識別碼下發布： `dotnet-sdk` 。 您可以藉由指定通道來安裝特定版本的 SDK。 SDK 包含對應的執行時間。 下表列出這些通道：

| .NET 版本 | 貼齊套件或頻道  |
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

此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。 您可以選擇任何想要 `{alias}` 的名稱。 例如，您可以在由 snap：進行安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-sdk.dotnet dotnet50` 。 當您使用命令時 `dotnet50` ，將會叫用這個特定的 .net 版本。 但是，選擇不同的別名與大部分的教學課程和範例都不相容，因為它們預期 `dotnet` 會使用命令。

## <a name="install-the-runtime"></a>安裝執行階段

.NET 執行時間的貼齊套件會各自以自己的套件識別碼發佈。 下表列出封裝識別碼：

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

此命令的格式為： `sudo snap alias {package}.{command} {alias}` 。 您可以選擇任何想要 `{alias}` 的名稱。 例如，您可以在由 snap：進行安裝的特定版本之後，將命令命名為 `sudo snap alias dotnet-runtime-50.dotnet dotnet50` 。 當您使用命令時 `dotnet50` ，將會叫用特定版本的 .net。 但是，選擇不同的別名與大部分的教學課程和範例都不相容，因為它們預期 `dotnet` 會有命令可供使用。

## <a name="tlsssl-certificate-errors"></a>TLS/SSL 憑證錯誤

透過 Snap 安裝 .NET 時，可能會在某些散發版本上找不到 .NET TLS/SSL 憑證，而且您可能會在下列情況收到錯誤 `restore` ：

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

憑證位置會因發行版本而異。 以下是已遇到問題的散發版本位置。

| 散發 | 位置                                            |
|--------------|-----------------------------------------------------|
| **Fedora**   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| **OpenSUSE** | `/etc/ssl/ca-bundle.pem`                            |
| **Solus**    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a>後續步驟

- [如何啟用 .NET CLI 的 TAB 鍵自動完成](../tools/enable-tab-autocomplete.md)
- [教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code](../tutorials/with-visual-studio-code.md)
