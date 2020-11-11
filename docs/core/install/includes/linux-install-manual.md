---
ms.openlocfilehash: 3932cf51b5194dba7956cd62ced3985a2e6311f0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506795"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

您也可以下載並手動安裝 SDK 和執行時間，作為套件管理員的替代方案。 手動安裝通常會做為持續整合測試的一部分，或在不支援的 Linux 發行版本上執行。 針對開發人員或使用者，通常最好使用套件管理員。

如果您安裝的是 .NET SDK，就不需要安裝對應的執行時間。 首先，從下列其中一個網站下載 SDK 或執行時間的 **二進位** 版本：

- ✔️ [.net 5.0 下載](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [所有 .NET Core 下載](https://dotnet.microsoft.com/download/dotnet-core)

接下來，將下載的檔案解壓縮，並使用 `export` 命令設定 .net 所使用的變數，然後確定 .net 是在 PATH 中。

若要將執行時間解壓縮，並讓 .NET CLI 命令可在終端機上使用，請先下載 .NET 二進位版本。 然後，開啟終端機，並從儲存檔案的目錄執行下列命令。 保存檔案名稱可能會因您所下載的內容而有所不同。

**使用下列命令，將執行時間解壓縮** ：

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**使用下列命令將 SDK 解壓縮** ：

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> 上述 `export` 命令只會讓執行的終端機會話提供 .NET CLI 命令。
>
> 您可以編輯 shell 設定檔，以永久新增命令。 Linux 有一些不同的 shell 可用，而且每個都有不同的設定檔。 例如︰
>
> - **Bash Shell** ： *~/.bash_profile* ， *~/.bashrc*
> - **Korn Shell** ： *~/.kshrc* 或 *. profile*
> - **Z Shell** ： *~/.zshrc* 或 *. zprofile*
>
> 編輯您 shell 的適當原始程式檔，並新增 `:$HOME/dotnet` 至現有語句的結尾 `PATH` 。 如果未 `PATH` 包含任何語句，請使用加入新的一行 `export PATH=$PATH:$HOME/dotnet` 。
>
> 此外，新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。

這種方法可讓您將不同的版本安裝到不同的位置，並明確地選擇哪個應用程式要使用哪一個版本。
