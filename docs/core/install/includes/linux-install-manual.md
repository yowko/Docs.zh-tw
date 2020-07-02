---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85805447"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

作為套件管理員的替代方案，您可以下載並手動安裝 SDK 和執行時間。 手動安裝通常是在持續整合測試或不支援的 Linux 發行版本中執行。 對於開發人員或使用者，通常最好是使用套件管理員。

如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。 首先，從下列其中一個網站下載 SDK 或執行時間的**二進位**版本：

- ✔️ [.net 5.0 preview 下載](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [所有 .NET Core 下載](https://dotnet.microsoft.com/download/dotnet-core)

接下來，將下載的檔案解壓縮，並使用 `export` 命令來設定 .Net core 所使用的變數，然後確保 .Net core 在 PATH 中。

若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先下載 .NET Core 二進位版本。 然後，開啟終端機，並從儲存檔案的目錄執行下列命令。 封存檔案名稱可能會根據您下載的內容而有所不同。

**使用下列命令來解壓縮運行**時間：

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**使用下列命令來解壓縮 SDK**：

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> 上述 `export` 命令只會對其執行所在的終端機會話提供 .NET Core CLI 命令。
>
> 您可以編輯您的 shell 設定檔，以永久新增命令。 有許多不同的 shell 可供 Linux 使用，而且每個都有不同的設定檔。 例如：
>
> - **Bash Shell**： *~/. bash_profile*， *~/.bashrc*
> - **Korn Shell**： *~/.kshrc*或 *. profile*
> - **Z Shell**： *~/.zshrc*或 *. zprofile*
>
> 為您的 shell 編輯適當的原始程式檔，並將新增 `:$HOME/dotnet` 至現有 `PATH` 語句的結尾。 如果未 `PATH` 包含任何語句，請加入具有的新行 `export PATH=$PATH:$HOME/dotnet` 。
>
> 此外，將新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。

這種方法可讓您將不同的版本安裝到不同的位置，並明確選擇哪一個應用程式要使用哪一個。
