---
ms.openlocfilehash: e7d35045892c62f759aad5067962ac5c15a9fb8b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602926"
---

<span data-ttu-id="1da7b-101">.NET Core SDK 和 .NET Core 執行時間都可以在下載之後手動安裝。</span><span class="sxs-lookup"><span data-stu-id="1da7b-101">Both .NET Core SDK and .NET Core Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="1da7b-102">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="1da7b-102">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="1da7b-103">首先，從下列其中一個網站下載 SDK 或執行時間的二進位版本：</span><span class="sxs-lookup"><span data-stu-id="1da7b-103">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="1da7b-104">✔️ [.net 5.0 preview 下載](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="1da7b-104">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="1da7b-105">✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="1da7b-105">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="1da7b-106">❌[.Net Core 3.0 下載](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="1da7b-106">❌ [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="1da7b-107">❌[.Net Core 2.2 下載](https://dotnet.microsoft.com/download/dotnet-core/2.2)</span><span class="sxs-lookup"><span data-stu-id="1da7b-107">❌ [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2)</span></span>
- <span data-ttu-id="1da7b-108">✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="1da7b-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>

<span data-ttu-id="1da7b-109">接下來，將下載的檔案解壓縮，並使用 `export` 命令來設定 .Net core 所使用的變數，然後確保 .Net core 在 PATH 中。</span><span class="sxs-lookup"><span data-stu-id="1da7b-109">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="1da7b-110">若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先下載 .NET Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="1da7b-110">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="1da7b-111">然後，開啟終端機，並從儲存檔案的目錄執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="1da7b-111">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="1da7b-112">上述 `export` 命令只會對其執行所在的終端機會話提供 .NET Core CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="1da7b-112">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="1da7b-113">您可以編輯您的 shell 設定檔，以永久新增命令。</span><span class="sxs-lookup"><span data-stu-id="1da7b-113">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="1da7b-114">有許多不同的 shell 可供 Linux 使用，而且每個都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="1da7b-114">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="1da7b-115">例如：</span><span class="sxs-lookup"><span data-stu-id="1da7b-115">For example:</span></span>
>
> - <span data-ttu-id="1da7b-116">**Bash Shell**： *~/. bash_profile*， *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="1da7b-116">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="1da7b-117">**Korn Shell**： *~/.kshrc*或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="1da7b-117">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="1da7b-118">**Z Shell**： *~/.zshrc*或 *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="1da7b-118">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="1da7b-119">為您的 shell 編輯適當的原始程式檔，並將新增 `:$HOME/dotnet` 至現有 `PATH` 語句的結尾。</span><span class="sxs-lookup"><span data-stu-id="1da7b-119">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="1da7b-120">如果未 `PATH` 包含任何語句，請加入具有的新行 `export PATH=$PATH:$HOME/dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="1da7b-120">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="1da7b-121">此外，將新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="1da7b-121">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="1da7b-122">這種方法可讓您將不同的版本安裝到不同的位置，並明確選擇哪一個應用程式要使用哪一個。</span><span class="sxs-lookup"><span data-stu-id="1da7b-122">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
