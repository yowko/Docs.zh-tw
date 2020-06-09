---
ms.openlocfilehash: e7d35045892c62f759aad5067962ac5c15a9fb8b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602926"
---

.NET Core SDK 和 .NET Core 執行時間都可以在下載之後手動安裝。 如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。 首先，從下列其中一個網站下載 SDK 或執行時間的二進位版本：

- ✔️ [.net 5.0 preview 下載](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ❌[.Net Core 3.0 下載](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- ❌[.Net Core 2.2 下載](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- ✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)

接下來，將下載的檔案解壓縮，並使用 `export` 命令來設定 .Net core 所使用的變數，然後確保 .Net core 在 PATH 中。

若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先下載 .NET Core 二進位版本。 然後，開啟終端機，並從儲存檔案的目錄執行下列命令。

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
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
