---
title: 在 Linux 上手動安裝 .NET-.NET
description: 示範如何在 Linux 上沒有套件管理員的情況下安裝 .NET SDK 和 .NET 執行時間。 使用安裝腳本或手動解壓縮二進位檔。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 5879d4d66aba8bfa00caadbe3c33d6df0d7da59a
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970961"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a>手動安裝 .NET SDK 或 .NET 執行時間

Linux 上支援 .NET，本文說明如何使用安裝腳本或解壓縮二進位檔，在 Linux 上安裝 .NET。 如需支援內建封裝管理員的發行版本清單，請參閱 [在 Linux 上安裝 .net](linux.md)。

您也可以使用 [貼齊] 來安裝 .NET。 如需詳細資訊，請參閱 [安裝 .NET SDK 或含 Snap 的 .Net 運行](linux-snap.md)時間。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a>.NET 版本

下表列出 .NET (和 .NET Core) 版本：

| 支援✔️ | ❌ 支援 |
|-------------|---------------|
| 5.0         | 3.0           |
| 3.1 (LTS)    | 2.2           |
| 2.1 (LTS)    | 2.0           |
|             | 1.1           |
|             | 1.0           |

如需 .NET 版本生命週期的詳細資訊，請參閱 [.Net Core 和 .net 5 支援原則](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。

## <a name="dependencies"></a>相依性

當您安裝 .NET 時，可能不會安裝特定的相依性，例如在 [手動安裝](#manual-install)時。 下列清單詳細說明 Microsoft 支援的 Linux 發行版本，以及您可能需要安裝的相依性。 查看 [散發] 頁面以取得詳細資訊：

- [Alpine](linux-alpine.md#dependencies)
- [Debian](linux-debian.md#dependencies)
- [CentOS](linux-centos.md#dependencies)
- [Fedora](linux-fedora.md#dependencies)
- [RHEL](linux-rhel.md#dependencies)
- [SLES](linux-sles.md#dependencies)
- [Ubuntu](linux-ubuntu.md#dependencies)

如需相依性的一般資訊，請參閱 [獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。

### <a name="rpm-dependencies"></a>RPM 相依性

如果之前未列出您的散發套件，而且是以 RPM 為基礎的，您可能需要下列相依性：

- krb5-libs
- libicu
- openssl-libs

如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您必須安裝 **相容性 compat-openssl10**。

### <a name="deb-dependencies"></a>DEB 相依性

如果之前未列出您的散發套件，而且是以 debian 為基礎的，您可能需要下列相依性：

- libc6
- libgcc1
- libgssapi-krb5.keytab-2
- libicu67
- libssl1.0.0 1。1
- libstdc + + 6
- zlib1g

### <a name="common-dependencies"></a>常見的相依性

若為使用 *system.string 元件的 .net 應用程式，* 您也需要下列相依性：

- [libgdiplus (6.0.1 版或更新版本) ](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > 您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。 如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。

## <a name="scripted-install"></a>腳本式安裝

[Dotnet 安裝腳本](../tools/dotnet-install-script.md)用於自動化和非系統管理員安裝的 **SDK** 和 **運行** 時間。 您可以從 <https://dot.net/v1/dotnet-install.sh> 下載指令碼。

腳本預設會安裝最新的 SDK [長期支援 (LTS) ](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，也就是 .net Core 3.1。 若要安裝目前版本，這可能不是 (LTS) 版本，請使用 `-c Current` 參數。

```bash
./dotnet-install.sh -c Current
```

若要安裝 .NET 執行時間，而不是 SDK，請使用 `--runtime` 參數。

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

您可以藉由修改 `-c` 參數來指定特定版本，以安裝特定版本。 下列命令會安裝 .NET SDK 5.0。

```bash
./dotnet-install.sh -c 5.0
```

如需詳細資訊，請參閱 [dotnet-安裝腳本參考](../tools/dotnet-install-script.md)。

## <a name="manual-install"></a>手動安裝

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

您也可以下載並手動安裝 SDK 和執行時間，作為套件管理員的替代方案。 手動安裝通常用來做為持續整合測試的一部分，或在不受支援的 Linux 發行版本上。 針對開發人員或使用者，最好使用套件管理員。

如果您安裝的是 .NET SDK，就不需要安裝對應的執行時間。 首先，從下列其中一個網站下載 SDK 或執行時間的 **二進位** 版本：

- ✔️ [.net 5.0 下載](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [所有 .NET Core 下載](https://dotnet.microsoft.com/download/dotnet-core)

接下來，將下載的檔案解壓縮，並使用 `export` 命令設定 .net 所使用的變數，然後確定 .net 是在 PATH 中。

若要將執行時間解壓縮，並讓 .NET CLI 命令可在終端機上使用，請先下載 .NET 二進位版本。 然後，開啟終端機，並從儲存檔案的目錄執行下列命令。 保存檔案名稱可能會因您所下載的內容而有所不同。

**使用下列命令，將執行時間解壓縮**：

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**使用下列命令將 SDK 解壓縮**：

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> 上述 `export` 命令只會讓執行的終端機會話提供 .NET CLI 命令。
>
> 您可以編輯 shell 設定檔，以永久新增命令。 Linux 有一些不同的 shell 可用，而且每個都有不同的設定檔。 例如：
>
> - **Bash Shell**： *~/.bash_profile*， *~/.bashrc*
> - **Korn Shell**： *~/.kshrc* 或 *. profile*
> - **Z Shell**： *~/.zshrc* 或 *. zprofile*
>
> 編輯您 shell 的適當原始程式檔，並新增 `:$HOME/dotnet` 至現有語句的結尾 `PATH` 。 如果未 `PATH` 包含任何語句，請使用加入新的一行 `export PATH=$PATH:$HOME/dotnet` 。
>
> 此外，新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。

這種方法可讓您將不同的版本安裝到不同的位置，並明確地選擇哪個應用程式要使用哪一個版本。

## <a name="next-steps"></a>後續步驟

- [如何啟用 .NET CLI 的 TAB 鍵自動完成](../tools/enable-tab-autocomplete.md)
- [教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code](../tutorials/with-visual-studio-code.md)
