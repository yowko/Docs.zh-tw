---
title: "從原始檔建置 .NET Core"
description: "了解如何從原始程式碼建置 .NET Core 和 .NET Core CLI。"
keywords: ".NET, .NET Core, 原始檔, 建置"
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8b49079c-6ede-429a-92d7-ecd2fda1ab0e
ms.workload: dotnetcore
ms.openlocfilehash: 6aa5abd071355b1c1a367b35e9521e6b1af9c945
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="369d8-104">從原始檔建置 .NET Core</span><span class="sxs-lookup"><span data-stu-id="369d8-104">Build .NET Core from source</span></span>

<span data-ttu-id="369d8-105">能夠從原始程式碼建置 .NET Core 很重要，如此一來就能輕鬆地將 .NET Core 移植到新平台、對產品提出貢獻和修正，並建立自訂的 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="369d8-105">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="369d8-106">本文為想要建置及散發自己的 .NET Core 版本的開發人員提供指引。</span><span class="sxs-lookup"><span data-stu-id="369d8-106">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="369d8-107">從原始檔建置 CLR</span><span class="sxs-lookup"><span data-stu-id="369d8-107">Build the CLR from source</span></span>

<span data-ttu-id="369d8-108">您可以在 [GitHub 上的 `dotnet/coreclr` 存放庫](https://github.com/dotnet/coreclr/)中找到 .NET Core CLR 的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="369d8-108">The source code for the .NET CoreCLR can be found in [the `dotnet/coreclr` repository on GitHub](https://github.com/dotnet/coreclr/).</span></span>

<span data-ttu-id="369d8-109">此組建目前相依於下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="369d8-109">The build currently depends on the following prerequisites:</span></span>
* [<span data-ttu-id="369d8-110">Git</span><span class="sxs-lookup"><span data-stu-id="369d8-110">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="369d8-111">CMake</span><span class="sxs-lookup"><span data-stu-id="369d8-111">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="369d8-112">Python</span><span class="sxs-lookup"><span data-stu-id="369d8-112">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="369d8-113">C++ 編譯器。</span><span class="sxs-lookup"><span data-stu-id="369d8-113">a C++ compiler.</span></span>

<span data-ttu-id="369d8-114">安裝這些必要條件之後，您可以叫用 [Core CLR 存放庫](https://github.com/dotnet/coreclr/)基底的組建指令碼 (在 Windows 上為 `build.cmd`，在 Linux 和 macOS 上為 `build.sh`) 來建置 CLR。</span><span class="sxs-lookup"><span data-stu-id="369d8-114">After you've installed these prerequisites are installed, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of [the CoreCLR repository](https://github.com/dotnet/coreclr/).</span></span>

<span data-ttu-id="369d8-115">安裝的元件會隨著作業系統 (OS) 而有所不同。</span><span class="sxs-lookup"><span data-stu-id="369d8-115">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="369d8-116">請參閱特定 OS 的建置指示：</span><span class="sxs-lookup"><span data-stu-id="369d8-116">See the build instructions for your specific OS:</span></span>

 * [<span data-ttu-id="369d8-117">Windows</span><span class="sxs-lookup"><span data-stu-id="369d8-117">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [<span data-ttu-id="369d8-118">Linux</span><span class="sxs-lookup"><span data-stu-id="369d8-118">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [<span data-ttu-id="369d8-119">macOS</span><span class="sxs-lookup"><span data-stu-id="369d8-119">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [<span data-ttu-id="369d8-120">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="369d8-120">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [<span data-ttu-id="369d8-121">NetBSD</span><span class="sxs-lookup"><span data-stu-id="369d8-121">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="369d8-122">無法跨 OS 建置 (僅適用於建置在 X64 上的 ARM)。</span><span class="sxs-lookup"><span data-stu-id="369d8-122">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="369d8-123">您必須在特定平台上，才能建置該平台。</span><span class="sxs-lookup"><span data-stu-id="369d8-123">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="369d8-124">組建有兩個主要的 `buildTypes`：</span><span class="sxs-lookup"><span data-stu-id="369d8-124">The build has two main `buildTypes`:</span></span>

 * <span data-ttu-id="369d8-125">偵錯 (預設)：以最低最佳化來編譯執行階段，並進行額外的執行階段檢查 (判斷提示)。</span><span class="sxs-lookup"><span data-stu-id="369d8-125">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="369d8-126">降低最佳化層級與額外的檢查會讓執行階段的執行變慢，但是有助於偵錯。</span><span class="sxs-lookup"><span data-stu-id="369d8-126">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="369d8-127">這是開發和測試環境的建議設定。</span><span class="sxs-lookup"><span data-stu-id="369d8-127">This is the recommended setting for development and testing environments.</span></span>
 * <span data-ttu-id="369d8-128">發行：以完整最佳化來編譯執行階段，且沒有額外的執行階段檢查。</span><span class="sxs-lookup"><span data-stu-id="369d8-128">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="369d8-129">如此會提高執行階段的效能，但是需要較長的建置時間，且偵錯較為困難。</span><span class="sxs-lookup"><span data-stu-id="369d8-129">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="369d8-130">若要選取此建置類型，請將 `release` 傳遞至建置指令碼。</span><span class="sxs-lookup"><span data-stu-id="369d8-130">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="369d8-131">此外根據預設，組建不只會建立執行階段可執行檔，也會建立所有測試。</span><span class="sxs-lookup"><span data-stu-id="369d8-131">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="369d8-132">由於有相當多的測試，因此如果您只想要試驗變更，這些測試會花費不必要的大量時間。</span><span class="sxs-lookup"><span data-stu-id="369d8-132">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="369d8-133">您可以將 `skiptests` 引數新增至建置指令碼來略過建立測試，如下列範例所示 (在 Unix 電腦上請將 `.\build` 取代為 `./build.sh`)：</span><span class="sxs-lookup"><span data-stu-id="369d8-133">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests 
```

<span data-ttu-id="369d8-134">前一個範例示範如何建置啟用開發階段檢查 (判斷提示) 並停用最佳化的 `Debug` 類別。</span><span class="sxs-lookup"><span data-stu-id="369d8-134">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="369d8-135">若要建置發行 (全速) 類別，請執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="369d8-135">To build the release (full speed) flavor, do the following:</span></span>

```bat 
    .\build release skiptests
```

<span data-ttu-id="369d8-136">您可以使用 -?</span><span class="sxs-lookup"><span data-stu-id="369d8-136">You can find more build options with build by using the -?</span></span> <span data-ttu-id="369d8-137">或 -help 限定詞，找到此組建的更多建置選項。</span><span class="sxs-lookup"><span data-stu-id="369d8-137">or -help qualifier.</span></span>   

### <a name="using-your-build"></a><span data-ttu-id="369d8-138">使用您的組建</span><span class="sxs-lookup"><span data-stu-id="369d8-138">Using Your Build</span></span>

<span data-ttu-id="369d8-139">組建會將其產生的所有檔案放在存放庫的基底 `bin` 目錄下。</span><span class="sxs-lookup"><span data-stu-id="369d8-139">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="369d8-140">*bin\Log* 目錄包含建置期間所產生的記錄檔 (這在建置失敗時會最有用)。</span><span class="sxs-lookup"><span data-stu-id="369d8-140">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="369d8-141">實際輸出位於 *bin\Product\[平台].[CPU 架構].[組建類型]* 目錄下，例如 *bin\Product\Windows_NT.x64.Release*。</span><span class="sxs-lookup"><span data-stu-id="369d8-141">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="369d8-142">雖然建置的「原始」輸出有時很有用，但您通常只對 NuGet 套件有興趣，該套件位於先前輸出目錄的 `.nuget\pkg` 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="369d8-142">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="369d8-143">您有兩個基本技術可使用新的執行階段：</span><span class="sxs-lookup"><span data-stu-id="369d8-143">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="369d8-144">**使用 dotnet.exe 和 NuGet 撰寫應用程式**。</span><span class="sxs-lookup"><span data-stu-id="369d8-144">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="369d8-145">如需使用您剛建立的 NuGet 套件和 'dotnet' 命令列介面 (CLI) 來建立使用新執行階段之程式的指示，請參閱 [Using your .NET Core Runtime Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) (使用您的 .NET Core 執行階段組建)。</span><span class="sxs-lookup"><span data-stu-id="369d8-145">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="369d8-146">非執行階段開發人員預期可能會使用這項技術來取用您的新執行階段。</span><span class="sxs-lookup"><span data-stu-id="369d8-146">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>    

 2. <span data-ttu-id="369d8-147">**使用 corerun.exe 透過未封裝的 DLL 執行應用程式**。</span><span class="sxs-lookup"><span data-stu-id="369d8-147">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="369d8-148">此存放庫也會定義一個與 NuGet 沒有任何相依性的簡單主機，稱為 corerun.exe。</span><span class="sxs-lookup"><span data-stu-id="369d8-148">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="369d8-149">您必須告訴主機何處可取得您實際使用的必要 DLL，而且您必須手動將這些 DLL 收集在一起。</span><span class="sxs-lookup"><span data-stu-id="369d8-149">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="369d8-150">這項技術可供 [Core CLR 存放庫](https://github.com/dotnet/coreclr)中的所有測試使用，並且有助於在本機快速執行「編輯-編譯-偵錯」迴圈，例如初步單元測試。</span><span class="sxs-lookup"><span data-stu-id="369d8-150">This technique is used by all the tests in [the CoreCLR repo](https://github.com/dotnet/coreclr), and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="369d8-151">如需使用這項技術的詳細資料，請參閱 [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) (使用 corerun.exe 執行 .NET Core 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="369d8-151">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="369d8-152">從原始檔建置 CLI</span><span class="sxs-lookup"><span data-stu-id="369d8-152">Build the CLI from source</span></span>

<span data-ttu-id="369d8-153">您可以在 [`dotnet/cli`GitHub 上的存放庫](https://github.com/dotnet/cli/)中找到 .NET Core CLI 的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="369d8-153">The source code for the .NET Core CLI can be found in [the `dotnet/cli` repository on GitHub](https://github.com/dotnet/cli/).</span></span>

<span data-ttu-id="369d8-154">若要建置 .NET Core CLI，您需要在電腦上安裝下列項目。</span><span class="sxs-lookup"><span data-stu-id="369d8-154">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="369d8-155">Windows 和 Linux：</span><span class="sxs-lookup"><span data-stu-id="369d8-155">Windows & Linux:</span></span>
    - <span data-ttu-id="369d8-156">PATH 上的 git</span><span class="sxs-lookup"><span data-stu-id="369d8-156">git on the PATH</span></span>
* <span data-ttu-id="369d8-157">macOS：</span><span class="sxs-lookup"><span data-stu-id="369d8-157">macOS:</span></span>
    - <span data-ttu-id="369d8-158">PATH 上的 git</span><span class="sxs-lookup"><span data-stu-id="369d8-158">git on the PATH</span></span>
    - <span data-ttu-id="369d8-159">Xcode</span><span class="sxs-lookup"><span data-stu-id="369d8-159">Xcode</span></span>
    - <span data-ttu-id="369d8-160">Openssl</span><span class="sxs-lookup"><span data-stu-id="369d8-160">OpenSSL</span></span>

<span data-ttu-id="369d8-161">若要建置，請從根目錄執行 `build.cmd` (在 Windows 上) 或 `build.sh` (在 Linux 和 macOS 上)。</span><span class="sxs-lookup"><span data-stu-id="369d8-161">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="369d8-162">如果您不想要執行測試，請執行 `build.cmd /t:Compile` 或 `./build.sh /t:Compile`。</span><span class="sxs-lookup"><span data-stu-id="369d8-162">If you don't want to execute tests, run `build.cmd /t:Compile` or `./build.sh /t:Compile`.</span></span> <span data-ttu-id="369d8-163">若要在 macOS Sierra 中建置 CLI，您必須執行 `export DOTNET_RUNTIME_ID=osx.10.11-x64` 來設定 DOTNET_RUNTIME_ID 環境變數。</span><span class="sxs-lookup"><span data-stu-id="369d8-163">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="369d8-164">使用您的組建</span><span class="sxs-lookup"><span data-stu-id="369d8-164">Using your build</span></span>

<span data-ttu-id="369d8-165">使用 *artifacts/{os}-{arch}/stage2* 中的 `dotnet` 可執行檔來試用新建置的 CLI。</span><span class="sxs-lookup"><span data-stu-id="369d8-165">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="369d8-166">如果您想要在從目前主控台叫用 `dotnet` 時使用建置輸出，您也可以將 *artifacts/{os}-{arch}/stage2* 新增至 PATH。</span><span class="sxs-lookup"><span data-stu-id="369d8-166">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="369d8-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="369d8-167">See also</span></span>

* [<span data-ttu-id="369d8-168">.NET Core Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="369d8-168">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="369d8-169">.NET Core CLI 開發人員指南</span><span class="sxs-lookup"><span data-stu-id="369d8-169">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="369d8-170">.NET Core 發佈封裝</span><span class="sxs-lookup"><span data-stu-id="369d8-170">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
