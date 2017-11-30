---
title: "開始使用 F # Ionide Visual Studio 程式碼中"
description: "了解如何使用 F # 與 Visual Studio 程式碼和 Ionide 外掛程式套件。"
keywords: "visual f #、 f #，功能性程式設計，.NET、 Visual Studio 程式碼，vscode Ionide"
author: cartermp
ms.author: phcart
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 336316eaf474f4c10d63657f178ce4a336ad7a54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-f-in-visual-studio-code-with-ionide"></a><span data-ttu-id="4552c-104">開始使用 F # Ionide Visual Studio 程式碼中</span><span class="sxs-lookup"><span data-stu-id="4552c-104">Getting Started with F# in Visual Studio Code with Ionide</span></span>

<span data-ttu-id="4552c-105">您可以撰寫 F # [Visual Studio Code](https://code.visualstudio.com)與[Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)，以取得使用 IntelliSense 和基本程式碼重構絕佳跨平台的輕量型 IDE 體驗。</span><span class="sxs-lookup"><span data-stu-id="4552c-105">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight IDE experience with IntelliSense and basic code refactorings.</span></span>  <span data-ttu-id="4552c-106">請瀏覽[Ionide.io](http://ionide.io)若要深入了解外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="4552c-106">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4552c-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="4552c-107">Prerequisites</span></span>

<span data-ttu-id="4552c-108">F # 4.0 或更新版本必須安裝在您的電腦使用 Ionide。</span><span class="sxs-lookup"><span data-stu-id="4552c-108">F# 4.0 or higher must be installed on your machine to use Ionide.</span></span>

<span data-ttu-id="4552c-109">您也必須擁有[安裝 git](https://git-scm.com/download)並可使用您的路徑，請使用專案中的範本 Ionide。</span><span class="sxs-lookup"><span data-stu-id="4552c-109">You must also have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span>  <span data-ttu-id="4552c-110">您可以確認它已正確安裝輸入`git`命令 prompt.and 按在**Enter**。</span><span class="sxs-lookup"><span data-stu-id="4552c-110">You can verify that it is installed correctly by typing `git` at a command prompt.and pressing **Enter**.</span></span>

### <a name="windows"></a><span data-ttu-id="4552c-111">Windows</span><span class="sxs-lookup"><span data-stu-id="4552c-111">Windows</span></span>

<span data-ttu-id="4552c-112">如果您是在 Windows 上，您必須安裝 F # 的兩個選項。</span><span class="sxs-lookup"><span data-stu-id="4552c-112">If you're on Windows, you have two options for installing F#.</span></span>

<span data-ttu-id="4552c-113">如果您已經安裝 Visual Studio，且沒有使用 F #，您可以[安裝 Visual F # Tools](get-started-visual-studio.md#installing-f)。</span><span class="sxs-lookup"><span data-stu-id="4552c-113">If you've already installed Visual Studio and don't have F#, you can [Install the Visual F# Tools](get-started-visual-studio.md#installing-f).</span></span>  <span data-ttu-id="4552c-114">這將會安裝所有必要的元件，來撰寫、 編譯及執行 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4552c-114">This will install all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="4552c-115">如果您不想安裝 Visual Studio，請使用下列指示：</span><span class="sxs-lookup"><span data-stu-id="4552c-115">If you prefer not to install Visual Studio, use the following instructions:</span></span>

1. <span data-ttu-id="4552c-116">安裝[.NET Framework 4.5 或更高版本](https://www.microsoft.com/en-US/download/details.aspx?id=30653)如果您執行 Windows 7。</span><span class="sxs-lookup"><span data-stu-id="4552c-116">Install [.NET Framework 4.5 or higher](https://www.microsoft.com/en-US/download/details.aspx?id=30653) if you're running Windows 7.</span></span>  <span data-ttu-id="4552c-117">如果您使用 Windows 8 或更新版本中，您不需要執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="4552c-117">If you're using Windows 8 or higher, you do not need to do this.</span></span>

2. <span data-ttu-id="4552c-118">安裝 Windows SDK 適用於您的作業系統。</span><span class="sxs-lookup"><span data-stu-id="4552c-118">Install the Windows SDK for your OS:</span></span>

    * [<span data-ttu-id="4552c-119">Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="4552c-119">Windows 10 SDK</span></span>](https://dev.windows.com/en-US/downloads/windows-10-sdk)
    * [<span data-ttu-id="4552c-120">Windows 8.1 SDK</span><span class="sxs-lookup"><span data-stu-id="4552c-120">Windows 8.1 SDK</span></span>](http://msdn.microsoft.com/windows/desktop/bg162891)
    * [<span data-ttu-id="4552c-121">Windows 8 SDK</span><span class="sxs-lookup"><span data-stu-id="4552c-121">Windows 8 SDK</span></span>](http://msdn.microsoft.com/windows/hardware/hh852363.aspx)
    * [<span data-ttu-id="4552c-122">Windows 7 SDK</span><span class="sxs-lookup"><span data-stu-id="4552c-122">Windows 7 SDK</span></span>](http://www.microsoft.com/download/details.aspx?id=8279)

3. <span data-ttu-id="4552c-123">安裝[Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159)。</span><span class="sxs-lookup"><span data-stu-id="4552c-123">Install the [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).</span></span>  <span data-ttu-id="4552c-124">您可能也需要安裝[Microsoft Build Tools 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760)。</span><span class="sxs-lookup"><span data-stu-id="4552c-124">You may also need to install [Microsoft Build Tools 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).</span></span>

4. <span data-ttu-id="4552c-125">安裝[Visual F # 工具](https://www.microsoft.com/en-us/download/details.aspx?id=48179)。</span><span class="sxs-lookup"><span data-stu-id="4552c-125">Install the [Visual F# Tools](https://www.microsoft.com/en-us/download/details.aspx?id=48179).</span></span>

<span data-ttu-id="4552c-126">在 64 位元 Windows 中，編譯器和工具可以在這裡找到：</span><span class="sxs-lookup"><span data-stu-id="4552c-126">On 64-bit Windows, the compiler and tools are located here:</span></span>

```
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

<span data-ttu-id="4552c-127">在 32 位元 Windows 中，編譯器工具可以在這裡找到：</span><span class="sxs-lookup"><span data-stu-id="4552c-127">On 32-bit Windows, the compiler tools are located here:</span></span>

```
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

<span data-ttu-id="4552c-128">Ionide 會自動偵測編譯器和工具，但如果不是基於某些原因 （例如，Visual F # 工具已安裝到不同的目錄），您可以手動新增包含的資料夾 (`...\Microsoft SDKs\F#\4.0`) 至您的路徑。</span><span class="sxs-lookup"><span data-stu-id="4552c-128">Ionide automatically detects the compiler and tools, but if it doesn't for some reason (for example, the Visual F# Tools were installed to a different directory), you can manually add the containing folder (`...\Microsoft SDKs\F#\4.0`) to your PATH.</span></span>

### <a name="macos"></a><span data-ttu-id="4552c-129">MacOS</span><span class="sxs-lookup"><span data-stu-id="4552c-129">macOS</span></span>

<span data-ttu-id="4552c-130">MacOS Ionide 使用[Mono](http://www.mono-project.com)。</span><span class="sxs-lookup"><span data-stu-id="4552c-130">On macOS, Ionide uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="4552c-131">安裝 Mono macOS 上最簡單的方式是透過 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="4552c-131">The easiest way to install Mono on macOS is via Homebrew.</span></span>  <span data-ttu-id="4552c-132">只要您的終端機中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4552c-132">Simply type the following into your terminal:</span></span>

```
brew install mono
```

### <a name="linux"></a><span data-ttu-id="4552c-133">Linux</span><span class="sxs-lookup"><span data-stu-id="4552c-133">Linux</span></span>

<span data-ttu-id="4552c-134">在 Linux 上 Ionide 也會使用[Mono](http://www.mono-project.com)。</span><span class="sxs-lookup"><span data-stu-id="4552c-134">On Linux, Ionide also uses [Mono](http://www.mono-project.com).</span></span>  <span data-ttu-id="4552c-135">如果您是在 Debian 或 Ubuntu 上，您可以使用下列項目：</span><span class="sxs-lookup"><span data-stu-id="4552c-135">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="4552c-136">安裝 Visual Studio 程式碼和 Ionide 外掛程式</span><span class="sxs-lookup"><span data-stu-id="4552c-136">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="4552c-137">您可以安裝 Visual Studio 程式碼從[code.visualstudio.com](https://code.visualstudio.com)網站。</span><span class="sxs-lookup"><span data-stu-id="4552c-137">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>  <span data-ttu-id="4552c-138">在這之後，有兩種方式可尋找 Ionide 外掛程式：</span><span class="sxs-lookup"><span data-stu-id="4552c-138">After that, there are two ways to find the Ionide plugin:</span></span>

1. <span data-ttu-id="4552c-139">使用命令選擇區 (Ctrl + Shift + P ⌘ + Shift + P macOS，Ctrl + Shift + P on Linux 上的 Windows 上)，並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4552c-139">Use the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

    ```
    >ext install Ionide
    ```

2. <span data-ttu-id="4552c-140">按一下 擴充功能圖示並搜尋"Ionide 」:</span><span class="sxs-lookup"><span data-stu-id="4552c-140">Click the Extensions icon and search for "Ionide":</span></span>

    ![](media/getting-started-vscode/vscode-ext.png)

<span data-ttu-id="4552c-141">只有 Visual Studio 程式碼中的 F # 支援所需的外掛程式[Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="4552c-141">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>  <span data-ttu-id="4552c-142">不過，您也可以安裝[Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)並取得[偽造](http://fsharp.github.io/FAKE/)支援和[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)取得[Paket](https://fsprojects.github.io/Paket/)支援。</span><span class="sxs-lookup"><span data-stu-id="4552c-142">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) and to get [FAKE](http://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span>  <span data-ttu-id="4552c-143">假造而且 Paket 其他 F # 社群工具，以建置專案，並且分別管理的相依性。</span><span class="sxs-lookup"><span data-stu-id="4552c-143">FAKE and Paket are additonal F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="4552c-144">使用 Ionide 建立第一個專案</span><span class="sxs-lookup"><span data-stu-id="4552c-144">Creating your first project with Ionide</span></span>

<span data-ttu-id="4552c-145">若要建立新的 F # 專案，請在新的資料夾 （您可以將檔案命名任何您喜歡） 中開啟 Visual Studio 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4552c-145">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

![](media/getting-started-vscode/vscode-open-dir.png)

<span data-ttu-id="4552c-146">接下來，開啟命令選擇區 (Ctrl + Shift + P ⌘ + Shift + P macOS，Ctrl + Shift + P on Linux 上的 Windows 上)，並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4552c-146">Next, open the Command Palette (Ctrl+Shift+P on Windows, ⌘+Shift+P on macOS, Ctrl+Shift+P on Linux) and type the following:</span></span>

```
>f#: New Project
```

<span data-ttu-id="4552c-147">這由[FORGE](https://github.com/fsharp-editing/Forge)專案。</span><span class="sxs-lookup"><span data-stu-id="4552c-147">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>  <span data-ttu-id="4552c-148">您應該會看到類似下面的內容：</span><span class="sxs-lookup"><span data-stu-id="4552c-148">You should see something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
<span data-ttu-id="4552c-149">如果您沒有看到上述項目，再試一次命令選擇區中執行下列命令，以重新整理範本： `>F#: Refresh Project Templates`。</span><span class="sxs-lookup"><span data-stu-id="4552c-149">If you don't see the above, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="4552c-150">選取 「 F #:: 新專案 」，請按**Enter**，這會帶您前往此步驟：</span><span class="sxs-lookup"><span data-stu-id="4552c-150">Select "F#: New Project" by hitting **Enter**, which will take you to this step:</span></span>

![](media/getting-started-vscode/vscode-proj-type.png)

<span data-ttu-id="4552c-151">這樣會選取特定類型的專案範本。</span><span class="sxs-lookup"><span data-stu-id="4552c-151">This will select a template for a specific type of project.</span></span>  <span data-ttu-id="4552c-152">有相當幾個選項，例如[FsLab](http://fslab.org)用於資料科學的範本或[Suave](https://suave.io) Web 程式設計的範本。</span><span class="sxs-lookup"><span data-stu-id="4552c-152">There are quite a few options here, such as an [FsLab](http://fslab.org) template for Data Science or [Suave](https://suave.io) template for Web Programming.</span></span>  <span data-ttu-id="4552c-153">本文使用`classlib`範本，因此反白顯示，並叫用**Enter**。</span><span class="sxs-lookup"><span data-stu-id="4552c-153">This article uses the `classlib` template, so highlight that and hit **Enter**.</span></span>  <span data-ttu-id="4552c-154">然後，您會到達下一個步驟：</span><span class="sxs-lookup"><span data-stu-id="4552c-154">You will then reach the following step:</span></span>

![](media/getting-started-vscode/vscode-new-dir.png)

<span data-ttu-id="4552c-155">這可讓您想要的話，在不同的目錄中，建立專案。</span><span class="sxs-lookup"><span data-stu-id="4552c-155">This lets you create the project in a different directory, if you like.</span></span>  <span data-ttu-id="4552c-156">保留空白目前。</span><span class="sxs-lookup"><span data-stu-id="4552c-156">Leave it blank for now.</span></span>  <span data-ttu-id="4552c-157">它會在目前的目錄建立專案。</span><span class="sxs-lookup"><span data-stu-id="4552c-157">It will create the project in the current directory.</span></span>  <span data-ttu-id="4552c-158">一旦您按下**Enter**，您會到達下一個步驟：</span><span class="sxs-lookup"><span data-stu-id="4552c-158">Once you press **Enter**, you will reach the following step:</span></span>

![](media/getting-started-vscode/vscode-proj-name.png)

<span data-ttu-id="4552c-159">這可讓您命名您的專案。</span><span class="sxs-lookup"><span data-stu-id="4552c-159">This lets you name your project.</span></span>  <span data-ttu-id="4552c-160">F # 使用[Pascal 案例](http://c2.com/cgi/wiki?PascalCase)專案名稱。</span><span class="sxs-lookup"><span data-stu-id="4552c-160">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span>  <span data-ttu-id="4552c-161">本文使用`ClassLibraryDemo`做為名稱。</span><span class="sxs-lookup"><span data-stu-id="4552c-161">This article uses `ClassLibraryDemo` as the name.</span></span>  <span data-ttu-id="4552c-162">一旦您輸入您想要為您的專案的名稱，叫用**Enter**。</span><span class="sxs-lookup"><span data-stu-id="4552c-162">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="4552c-163">如果您遵循上述步驟的步驟，您應該取得 Visual Studio 程式碼工作區左邊看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="4552c-163">If you followed the previous step steps, you should get the Visual Studio Code Workspace on the left-hand side to look something like this:</span></span>

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

<span data-ttu-id="4552c-164">此範本會產生幾件事，您會發現很有用：</span><span class="sxs-lookup"><span data-stu-id="4552c-164">This template generates a few things you'll find useful:</span></span>

1. <span data-ttu-id="4552c-165">F # 專案本身，在底下`ClassLibraryDemo`資料夾。</span><span class="sxs-lookup"><span data-stu-id="4552c-165">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="4552c-166">新增套件透過正確的目錄結構[ `Paket` ](http://fsprojects.github.io/Paket/)。</span><span class="sxs-lookup"><span data-stu-id="4552c-166">The correct directory structure for adding packages via [`Paket`](http://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="4552c-167">跨平台建置指令碼[ `FAKE` ](http://fsharp.github.io/FAKE/)。</span><span class="sxs-lookup"><span data-stu-id="4552c-167">A cross-platform build script with [`FAKE`](http://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="4552c-168">`paket.exe`可執行檔可以擷取封裝，並讓您解析的相依性。</span><span class="sxs-lookup"><span data-stu-id="4552c-168">The `paket.exe` executable which can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="4552c-169">A`.gitignore`檔案，如果您想要將這個專案加入 Git 架構的原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="4552c-169">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="4552c-170">撰寫一些程式碼</span><span class="sxs-lookup"><span data-stu-id="4552c-170">Writing some code</span></span>

<span data-ttu-id="4552c-171">開啟*ClassLibraryDemo*資料夾。</span><span class="sxs-lookup"><span data-stu-id="4552c-171">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="4552c-172">您應該會看到下列檔案：</span><span class="sxs-lookup"><span data-stu-id="4552c-172">You should see the following files:</span></span>

1. <span data-ttu-id="4552c-173">`ClassLibraryDemo.fs`定義的類別具有的 F # 實作檔案。</span><span class="sxs-lookup"><span data-stu-id="4552c-173">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="4552c-174">`CassLibraryDemo.fsproj`F # 專案檔用來建置此專案。</span><span class="sxs-lookup"><span data-stu-id="4552c-174">`CassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="4552c-175">`Script.fsx`為 F # 指令碼檔案，檔案載入原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="4552c-175">`Script.fsx`, an F# script file which loads the source file.</span></span>
4. <span data-ttu-id="4552c-176">`paket.references`指定專案相依性的 Paket 檔案。</span><span class="sxs-lookup"><span data-stu-id="4552c-176">`paket.references`, a Paket file which specifies the project dependencies.</span></span>

<span data-ttu-id="4552c-177">開啟`Script.fsx`，並在結尾處加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4552c-177">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="4552c-178">此函式會將文字轉換成一種[Pig 拉丁](https://en.wikipedia.org/wiki/Pig_Latin)。</span><span class="sxs-lookup"><span data-stu-id="4552c-178">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span>  <span data-ttu-id="4552c-179">下一步是評估使用 F # Interactive (FSI)。</span><span class="sxs-lookup"><span data-stu-id="4552c-179">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="4552c-180">反白顯示整個函式 （應為 11 行長度）。</span><span class="sxs-lookup"><span data-stu-id="4552c-180">Highlight the entire function (it should be 11 lines long).</span></span>  <span data-ttu-id="4552c-181">一旦會反白顯示，保存**Alt**金鑰並點擊**Enter**。</span><span class="sxs-lookup"><span data-stu-id="4552c-181">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span>  <span data-ttu-id="4552c-182">您會發現下面顯視窗，它應該會顯示結果類似這樣：</span><span class="sxs-lookup"><span data-stu-id="4552c-182">You'll notice a window pop up below, and it should show something like this:</span></span>

![](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="4552c-183">這並未三件事：</span><span class="sxs-lookup"><span data-stu-id="4552c-183">This did three things:</span></span>

1. <span data-ttu-id="4552c-184">它會啟動 FSI 程序。</span><span class="sxs-lookup"><span data-stu-id="4552c-184">It started the FSI process.</span></span>
2. <span data-ttu-id="4552c-185">它透過 FSI 程序傳送您反白顯示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4552c-185">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="4552c-186">FSI 程序會評估您透過傳送的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4552c-186">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="4552c-187">因為您透過傳送[函式](../language-reference/functions/index.md)，您現在可以呼叫該函式與 FSI ！</span><span class="sxs-lookup"><span data-stu-id="4552c-187">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span>  <span data-ttu-id="4552c-188">在互動式視窗中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4552c-188">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="4552c-189">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="4552c-189">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="4552c-190">現在，讓我們再一次與第一個字母母音。</span><span class="sxs-lookup"><span data-stu-id="4552c-190">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="4552c-191">輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4552c-191">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="4552c-192">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="4552c-192">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="4552c-193">此函式會出現無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="4552c-193">The function appears to be working as expected.</span></span>  <span data-ttu-id="4552c-194">恭喜您，只需要在 Visual Studio 程式碼撰寫您的第一個 F # 函式，並評估與 FSI ！</span><span class="sxs-lookup"><span data-stu-id="4552c-194">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="4552c-195">您可能已經注意到，在以結束 FSI 中的線條`;;`。</span><span class="sxs-lookup"><span data-stu-id="4552c-195">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span>  <span data-ttu-id="4552c-196">這是因為 FSI 可讓您輸入多行。</span><span class="sxs-lookup"><span data-stu-id="4552c-196">This is because FSI allows you to enter multiple lines.</span></span>  <span data-ttu-id="4552c-197">`;;`結尾可讓 FSI 知道完成程式碼。</span><span class="sxs-lookup"><span data-stu-id="4552c-197">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="4552c-198">說明程式碼</span><span class="sxs-lookup"><span data-stu-id="4552c-198">Explaining the code</span></span>

<span data-ttu-id="4552c-199">如果您不確定程式實際上做什麼的程式碼，以下是逐步。</span><span class="sxs-lookup"><span data-stu-id="4552c-199">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="4552c-200">如您所見，`toPigLatin`是函式會取得做為輸入的文字，並將它轉換成該單字的 Pig 拉丁表示法。</span><span class="sxs-lookup"><span data-stu-id="4552c-200">As you can see, `toPigLatin` is a function which takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span>  <span data-ttu-id="4552c-201">這個規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="4552c-201">The rules for this are as follows:</span></span>

<span data-ttu-id="4552c-202">在 word 中的第一個字元開頭母音，"鐘樓"加入文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="4552c-202">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span>  <span data-ttu-id="4552c-203">如果它不會以某個母音開頭，將該第一個字元移至文字的結尾，加入 「 可能 」。</span><span class="sxs-lookup"><span data-stu-id="4552c-203">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="4552c-204">您可能已注意到 FSI 中的下列：</span><span class="sxs-lookup"><span data-stu-id="4552c-204">You may have noticed the following in FSI:</span></span>

```
val toPigLatin : word:string -> string
```

<span data-ttu-id="4552c-205">這指出`toPigLatin`是函式會接受`string`做為輸入 (稱為`word`)，並傳回另一個`string`。</span><span class="sxs-lookup"><span data-stu-id="4552c-205">This states that `toPigLatin` is a function which takes in a `string` as input (called `word`), and returns another `string`.</span></span>  <span data-ttu-id="4552c-206">這稱為[函式的類型簽章](https://fsharpforfunandprofit.com/posts/function-signatures/)，F # 是要了解 F # 程式碼索引鍵的基本部分。</span><span class="sxs-lookup"><span data-stu-id="4552c-206">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span>  <span data-ttu-id="4552c-207">您也會發現這如果您將滑鼠停留在 Visual Studio 程式碼中的函式。</span><span class="sxs-lookup"><span data-stu-id="4552c-207">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="4552c-208">在函式的主體中，您會發現兩個不同的部分：</span><span class="sxs-lookup"><span data-stu-id="4552c-208">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="4552c-209">內部的函式，呼叫`isVowel`，決定如果指定的字元 (`c`) 會編碼母音方法是檢查它是否符合其中一個提供的模式透過[模式比對](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="4552c-209">An inner function, called `isVowel`, which determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="4552c-210">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)的檢查，如果第一個字元是母音，而且建構超出輸入的字元傳回值為基礎的運算式 if 的第一個字元已母音或未驗證：</span><span class="sxs-lookup"><span data-stu-id="4552c-210">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression which checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="4552c-211">流程`toPigLatin`因此：</span><span class="sxs-lookup"><span data-stu-id="4552c-211">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="4552c-212">檢查輸入的字組的第一個字元是否為某個母音。</span><span class="sxs-lookup"><span data-stu-id="4552c-212">Check if the first character of the input word is a vowel.</span></span>  <span data-ttu-id="4552c-213">如果是，請將"鐘樓"附加至文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="4552c-213">If it is, attach "yay" to the end of the word.</span></span>  <span data-ttu-id="4552c-214">否則，將該第一個字元移至文字的結尾，加入 「 可能 」。</span><span class="sxs-lookup"><span data-stu-id="4552c-214">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="4552c-215">沒有最後一注意到關於此： 沒有任何明確指令來從與許多其他語言有不同的函式傳回。</span><span class="sxs-lookup"><span data-stu-id="4552c-215">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span>  <span data-ttu-id="4552c-216">這是因為 F # 是以運算式為基礎，並在函式主體中的最後一個運算式是傳回的值。</span><span class="sxs-lookup"><span data-stu-id="4552c-216">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span>  <span data-ttu-id="4552c-217">因為`if..then..else`本身是運算式的主體`then`區塊或內文`else`區塊將會傳回輸入值而定。</span><span class="sxs-lookup"><span data-stu-id="4552c-217">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="4552c-218">將您的指令碼移到實作檔</span><span class="sxs-lookup"><span data-stu-id="4552c-218">Moving your script code into the implementation file</span></span>

<span data-ttu-id="4552c-219">這篇文章中的先前各節示範常見的第一個步驟，在撰寫 F # 程式碼： 撰寫初始的函式，然後使用 FSI 以互動方式執行。</span><span class="sxs-lookup"><span data-stu-id="4552c-219">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span>  <span data-ttu-id="4552c-220">這稱為 REPL 導向的開發，其中 REPL 代表 「 讀取評估列印迴圈 」。</span><span class="sxs-lookup"><span data-stu-id="4552c-220">This is known as REPL-driven development, where REPL stands for "Read-Evaluate-Print Loop".</span></span>  <span data-ttu-id="4552c-221">它是實驗功能，直到您有工作的好方法。</span><span class="sxs-lookup"><span data-stu-id="4552c-221">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="4552c-222">REPL 導向的開發工作的下一個步驟是將使用中程式碼移至 F # 實作檔。</span><span class="sxs-lookup"><span data-stu-id="4552c-222">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span>  <span data-ttu-id="4552c-223">它可以再編譯 F # 編譯器為可執行的組件。</span><span class="sxs-lookup"><span data-stu-id="4552c-223">It can then be compiled by the F# compiler into an assembly which can be executed.</span></span>

<span data-ttu-id="4552c-224">若要開始，請開啟`ClassLibraryDemo.fs`。</span><span class="sxs-lookup"><span data-stu-id="4552c-224">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="4552c-225">您會發現，某些程式碼已在有。</span><span class="sxs-lookup"><span data-stu-id="4552c-225">You'll notice that some code is already in there.</span></span>  <span data-ttu-id="4552c-226">請繼續並刪除類別定義中，但請務必保留[ `namespace` ](../language-reference/namespaces.md)頂端的宣告。</span><span class="sxs-lookup"><span data-stu-id="4552c-226">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="4552c-227">接下來，建立新[ `module` ](../language-reference/modules.md)呼叫`PigLatin`並複製`toPigLatin`函式匯入它在這種情況：</span><span class="sxs-lookup"><span data-stu-id="4552c-227">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="4552c-228">這是您可以將組織中 F # 程式碼，函式和常見的方法如果您也想要從 C# 或 Visual Basic 專案中呼叫程式碼是有許多方法。</span><span class="sxs-lookup"><span data-stu-id="4552c-228">This is one of the many ways you can organize functions in F# code, and a common approach if you also want to call your code from C# or Visual Basic projects.</span></span>

<span data-ttu-id="4552c-229">接下來，開啟`Script.fsx`檔案一次，並刪除整個`toPigLatin`函式，但務必要保留檔案中的下列兩行：</span><span class="sxs-lookup"><span data-stu-id="4552c-229">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="4552c-230">FSI 以載入指令碼所需的第一行`ClassLibraryDemo.fs`。</span><span class="sxs-lookup"><span data-stu-id="4552c-230">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="4552c-231">第二行在於其便利性： 略過為選擇性，但是您必須輸入`open ClassLibraryDemo`FSI 視窗，如果您想要將`ToPigLatin`模組納入範圍。</span><span class="sxs-lookup"><span data-stu-id="4552c-231">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="4552c-232">接下來，在 FSI 視窗中，呼叫函式`PigLatin`先前定義的模組：</span><span class="sxs-lookup"><span data-stu-id="4552c-232">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="4552c-233">成功！</span><span class="sxs-lookup"><span data-stu-id="4552c-233">Success!</span></span>  <span data-ttu-id="4552c-234">取得與之前相同的結果，但現在已從 F # 實作檔案載入。</span><span class="sxs-lookup"><span data-stu-id="4552c-234">You get the same results as before, but now loaded from an F# implementation file.</span></span>  <span data-ttu-id="4552c-235">此處的主要差異是 F # 原始程式檔會編譯成執行 FSI 不只是在任何地方、 組件。</span><span class="sxs-lookup"><span data-stu-id="4552c-235">The major difference here is that F# source files are compiled into assemblies which can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="4552c-236">總結</span><span class="sxs-lookup"><span data-stu-id="4552c-236">Summary</span></span>

<span data-ttu-id="4552c-237">在本文中，您學到：</span><span class="sxs-lookup"><span data-stu-id="4552c-237">In this article, you've learned:</span></span>

1. <span data-ttu-id="4552c-238">如何設定與 Ionide Visual Studio 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4552c-238">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="4552c-239">如何使用 Ionide 建立第一個 F # 專案。</span><span class="sxs-lookup"><span data-stu-id="4552c-239">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="4552c-240">如何使用 F # 指令碼處理 Ionide 中撰寫您的第一個 F # 函式，然後將它執行 FSI 中。</span><span class="sxs-lookup"><span data-stu-id="4552c-240">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="4552c-241">如何將指令碼移轉至 F # 原始程式檔，然後從 FSI 呼叫該程式碼。</span><span class="sxs-lookup"><span data-stu-id="4552c-241">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="4552c-242">您現在要寫入更多 F # 程式碼使用 Visual Studio 程式碼和 Ionide 配備。</span><span class="sxs-lookup"><span data-stu-id="4552c-242">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="4552c-243">疑難排解</span><span class="sxs-lookup"><span data-stu-id="4552c-243">Troubleshooting</span></span>

<span data-ttu-id="4552c-244">以下是您可以疑難排解特定問題，您可能會遇到的幾個方法：</span><span class="sxs-lookup"><span data-stu-id="4552c-244">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="4552c-245">若要取得程式碼編輯 Ionide 的功能，您的 F # 檔案需要儲存到磁碟，然後在 Visual Studio 程式碼工作區中開啟的資料夾內。</span><span class="sxs-lookup"><span data-stu-id="4552c-245">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="4552c-246">如果您變更您的系統或 Ionide 必要條件安裝 Visual Studio 程式碼開啟，請重新啟動 Visual Studio 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4552c-246">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="4552c-247">請檢查您可以使用 F # 編譯器和 F # interactive 從命令列不完整的路徑。</span><span class="sxs-lookup"><span data-stu-id="4552c-247">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span>  <span data-ttu-id="4552c-248">您可以輸入`fsc`對於 F # 編譯器，命令列中和`fsi`或`fsharpi`Visual F # 工具在 Windows 和 Mac/Linux 上的 Mono 上分別。</span><span class="sxs-lookup"><span data-stu-id="4552c-248">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="4552c-249">如果您在專案目錄中有無效的字元，Ionide 可能無法運作。</span><span class="sxs-lookup"><span data-stu-id="4552c-249">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="4552c-250">如果發生這種情況，請重新命名專案目錄。</span><span class="sxs-lookup"><span data-stu-id="4552c-250">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="4552c-251">如果使用無 Ionide 命令，請檢查您[Visual Studio Code 按鍵組合](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)查看如果您要覆寫的它們不小心。</span><span class="sxs-lookup"><span data-stu-id="4552c-251">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="4552c-252">如果您的電腦上中斷 Ionide 上述都無法有固定的問題，請嘗試移除`ionide-fsharp`目錄在電腦上重新安裝外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="4552c-252">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="4552c-253">Ionide 是開放原始碼專案所建立與維護由 F # 社群的成員。</span><span class="sxs-lookup"><span data-stu-id="4552c-253">Ionide is an open source project built and maintained by members of the F# community.</span></span>  <span data-ttu-id="4552c-254">請報告問題，並隨意在參與[Ionide VSCode: FSharp GitHub 儲存機制](https://github.com/ionide/ionide-vscode-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="4552c-254">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="4552c-255">如果您有要報告的問題，請遵循[取得記錄檔使用 回報問題時的指示](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)。</span><span class="sxs-lookup"><span data-stu-id="4552c-255">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="4552c-256">您也可以要求取得進一步的協助從 Ionide 開發人員和 F # 中的社群[Ionide Gitter 通道](https://gitter.im/ionide/ionide-project)。</span><span class="sxs-lookup"><span data-stu-id="4552c-256">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4552c-257">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4552c-257">Next steps</span></span>

<span data-ttu-id="4552c-258">若要深入了解 F # 和語言的功能，請參閱[教學課程的 F #](../tour.md)。</span><span class="sxs-lookup"><span data-stu-id="4552c-258">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4552c-259">請參閱</span><span class="sxs-lookup"><span data-stu-id="4552c-259">See also</span></span>

[<span data-ttu-id="4552c-260">F 的教學課程</span><span class="sxs-lookup"><span data-stu-id="4552c-260">Tour of F#</span></span>](../tour.md)

[<span data-ttu-id="4552c-261">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="4552c-261">F# Language Reference</span></span>](../language-reference/index.md)

[<span data-ttu-id="4552c-262">函式</span><span class="sxs-lookup"><span data-stu-id="4552c-262">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="4552c-263">模組</span><span class="sxs-lookup"><span data-stu-id="4552c-263">Modules</span></span>](../language-reference/modules.md)

[<span data-ttu-id="4552c-264">命名空間</span><span class="sxs-lookup"><span data-stu-id="4552c-264">Namespaces</span></span>](../language-reference/namespaces.md)

[<span data-ttu-id="4552c-265">Ionide VSCode: FSharp</span><span class="sxs-lookup"><span data-stu-id="4552c-265">Ionide-VSCode: FSharp</span></span>](https://github.com/ionide/ionide-vscode-fsharp)
