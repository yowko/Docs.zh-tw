---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85805447"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="42961-101">作為套件管理員的替代方案，您可以下載並手動安裝 SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="42961-101">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="42961-102">手動安裝通常是在持續整合測試或不支援的 Linux 發行版本中執行。</span><span class="sxs-lookup"><span data-stu-id="42961-102">Manual install is usually performed as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="42961-103">對於開發人員或使用者，通常最好是使用套件管理員。</span><span class="sxs-lookup"><span data-stu-id="42961-103">For a developer or user, it's generally better to use a package manager.</span></span>

<span data-ttu-id="42961-104">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="42961-104">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="42961-105">首先，從下列其中一個網站下載 SDK 或執行時間的**二進位**版本：</span><span class="sxs-lookup"><span data-stu-id="42961-105">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="42961-106">✔️ [.net 5.0 preview 下載](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="42961-106">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="42961-107">✔️ [.Net Core 3.1 下載](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="42961-107">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="42961-108">✔️ [.Net Core 2.1 下載](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="42961-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="42961-109">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="42961-109">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="42961-110">接下來，將下載的檔案解壓縮，並使用 `export` 命令來設定 .Net core 所使用的變數，然後確保 .Net core 在 PATH 中。</span><span class="sxs-lookup"><span data-stu-id="42961-110">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="42961-111">若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先下載 .NET Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="42961-111">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="42961-112">然後，開啟終端機，並從儲存檔案的目錄執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="42961-112">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="42961-113">封存檔案名稱可能會根據您下載的內容而有所不同。</span><span class="sxs-lookup"><span data-stu-id="42961-113">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="42961-114">**使用下列命令來解壓縮運行**時間：</span><span class="sxs-lookup"><span data-stu-id="42961-114">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="42961-115">**使用下列命令來解壓縮 SDK**：</span><span class="sxs-lookup"><span data-stu-id="42961-115">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="42961-116">上述 `export` 命令只會對其執行所在的終端機會話提供 .NET Core CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="42961-116">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="42961-117">您可以編輯您的 shell 設定檔，以永久新增命令。</span><span class="sxs-lookup"><span data-stu-id="42961-117">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="42961-118">有許多不同的 shell 可供 Linux 使用，而且每個都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="42961-118">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="42961-119">例如：</span><span class="sxs-lookup"><span data-stu-id="42961-119">For example:</span></span>
>
> - <span data-ttu-id="42961-120">**Bash Shell**： *~/. bash_profile*， *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="42961-120">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="42961-121">**Korn Shell**： *~/.kshrc*或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="42961-121">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="42961-122">**Z Shell**： *~/.zshrc*或 *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="42961-122">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="42961-123">為您的 shell 編輯適當的原始程式檔，並將新增 `:$HOME/dotnet` 至現有 `PATH` 語句的結尾。</span><span class="sxs-lookup"><span data-stu-id="42961-123">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="42961-124">如果未 `PATH` 包含任何語句，請加入具有的新行 `export PATH=$PATH:$HOME/dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="42961-124">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="42961-125">此外，將新增 `export DOTNET_ROOT=$HOME/dotnet` 至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="42961-125">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="42961-126">這種方法可讓您將不同的版本安裝到不同的位置，並明確選擇哪一個應用程式要使用哪一個。</span><span class="sxs-lookup"><span data-stu-id="42961-126">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
