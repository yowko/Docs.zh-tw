---
ms.openlocfilehash: 3932cf51b5194dba7956cd62ced3985a2e6311f0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506795"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="9bf1c-101">您也可以下載並手動安裝 SDK 和執行時間，作為套件管理員的替代方案。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-101">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="9bf1c-102">手動安裝通常會做為持續整合測試的一部分，或在不支援的 Linux 發行版本上執行。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-102">Manual install is usually performed as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="9bf1c-103">針對開發人員或使用者，通常最好使用套件管理員。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-103">For a developer or user, it's generally better to use a package manager.</span></span>

<span data-ttu-id="9bf1c-104">如果您安裝的是 .NET SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-104">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="9bf1c-105">首先，從下列其中一個網站下載 SDK 或執行時間的 **二進位** 版本：</span><span class="sxs-lookup"><span data-stu-id="9bf1c-105">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="9bf1c-106">✔️ [.net 5.0 下載](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="9bf1c-106">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="9bf1c-107">✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="9bf1c-107">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="9bf1c-108">✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="9bf1c-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="9bf1c-109">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="9bf1c-109">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="9bf1c-110">接下來，將下載的檔案解壓縮，並使用 `export` 命令設定 .net 所使用的變數，然後確定 .net 是在 PATH 中。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-110">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="9bf1c-111">若要將執行時間解壓縮，並讓 .NET CLI 命令可在終端機上使用，請先下載 .NET 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-111">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="9bf1c-112">然後，開啟終端機，並從儲存檔案的目錄執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-112">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="9bf1c-113">保存檔案名稱可能會因您所下載的內容而有所不同。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-113">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="9bf1c-114">**使用下列命令，將執行時間解壓縮**：</span><span class="sxs-lookup"><span data-stu-id="9bf1c-114">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="9bf1c-115">**使用下列命令將 SDK 解壓縮**：</span><span class="sxs-lookup"><span data-stu-id="9bf1c-115">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="9bf1c-116">上述 `export` 命令只會讓執行的終端機會話提供 .NET CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-116">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="9bf1c-117">您可以編輯 shell 設定檔，以永久新增命令。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-117">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="9bf1c-118">Linux 有一些不同的 shell 可用，而且每個都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-118">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="9bf1c-119">例如：</span><span class="sxs-lookup"><span data-stu-id="9bf1c-119">For example:</span></span>
>
> - <span data-ttu-id="9bf1c-120">**Bash Shell**： *~/.bash_profile*， *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="9bf1c-120">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="9bf1c-121">**Korn Shell**： *~/.kshrc* 或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="9bf1c-121">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="9bf1c-122">**Z Shell**： *~/.zshrc* 或 *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="9bf1c-122">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="9bf1c-123">編輯您 shell 的適當原始程式檔，並新增 `:$HOME/dotnet` 至現有語句的結尾 `PATH` 。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-123">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="9bf1c-124">如果未 `PATH` 包含任何語句，請使用加入新的一行 `export PATH=$PATH:$HOME/dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-124">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="9bf1c-125">此外，新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-125">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="9bf1c-126">這種方法可讓您將不同的版本安裝到不同的位置，並明確地選擇哪個應用程式要使用哪一個版本。</span><span class="sxs-lookup"><span data-stu-id="9bf1c-126">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
