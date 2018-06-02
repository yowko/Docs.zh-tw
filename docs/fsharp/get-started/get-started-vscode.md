---
title: '開始使用 F # 在 Visual Studio 程式碼'
description: '了解如何使用 F # 與 Visual Studio 程式碼和 Ionide 外掛程式套件。'
ms.date: 05/28/2018
ms.openlocfilehash: e56274caf36be231338876ded5a6d7c7968906b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728624"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="d942e-103">開始使用 F # 在 Visual Studio 程式碼</span><span class="sxs-lookup"><span data-stu-id="d942e-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="d942e-104">您可以撰寫 F # [Visual Studio Code](https://code.visualstudio.com)與[Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)，若要取得跨平台的輕量型整合式開發環境 (IDE) 體驗 IntelliSense 和基本的程式碼重構。</span><span class="sxs-lookup"><span data-stu-id="d942e-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="d942e-105">請瀏覽[Ionide.io](http://ionide.io)若要深入了解外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="d942e-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin suite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d942e-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="d942e-106">Prerequisites</span></span>

<span data-ttu-id="d942e-107">您必須擁有[安裝 git](https://git-scm.com/download)並可使用您的路徑，請使用專案中的範本 Ionide。</span><span class="sxs-lookup"><span data-stu-id="d942e-107">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates in Ionide.</span></span> <span data-ttu-id="d942e-108">您可以確認它已正確安裝輸入`git --version`在命令提示字元並按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="d942e-108">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="d942e-109">macOS</span><span class="sxs-lookup"><span data-stu-id="d942e-109">macOS</span></span>](#tab/macos)

<span data-ttu-id="d942e-110">使用 Ionide [Mono](http://www.mono-project.com)。</span><span class="sxs-lookup"><span data-stu-id="d942e-110">Ionide uses [Mono](http://www.mono-project.com).</span></span> <span data-ttu-id="d942e-111">安裝 Mono macOS 上最簡單的方式是透過 Homebrew。</span><span class="sxs-lookup"><span data-stu-id="d942e-111">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="d942e-112">只要您的終端機中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="d942e-112">Simply type the following into your terminal:</span></span>

```
brew install mono
```

<span data-ttu-id="d942e-113">您也必須安裝[.NET Core SDK](https://www.microsoft.com/net/download)。</span><span class="sxs-lookup"><span data-stu-id="d942e-113">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="d942e-114">Linux</span><span class="sxs-lookup"><span data-stu-id="d942e-114">Linux</span></span>](#tab/linux)

<span data-ttu-id="d942e-115">在 Linux 上 Ionide 也會使用[Mono](https://www.mono-project.com)。</span><span class="sxs-lookup"><span data-stu-id="d942e-115">On Linux, Ionide also uses [Mono](https://www.mono-project.com).</span></span> <span data-ttu-id="d942e-116">如果您是在 Debian 或 Ubuntu 上，您可以使用下列項目：</span><span class="sxs-lookup"><span data-stu-id="d942e-116">If you're on Debian or Ubuntu, you can use the following:</span></span>

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="d942e-117">您也必須安裝[.NET Core SDK](https://www.microsoft.com/net/download)。</span><span class="sxs-lookup"><span data-stu-id="d942e-117">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="d942e-118">Windows</span><span class="sxs-lookup"><span data-stu-id="d942e-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="d942e-119">如果您在 Windows 上，您必須[使用 F # 支援安裝 Visual Studio](get-started-visual-studio.md#installing-f)。</span><span class="sxs-lookup"><span data-stu-id="d942e-119">If you're on Windows, you must [install Visual Studio with F# support](get-started-visual-studio.md#installing-f).</span></span> <span data-ttu-id="d942e-120">這會安裝所有必要的元件，來撰寫、 編譯及執行 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d942e-120">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="d942e-121">您也必須安裝[.NET Core SDK](https://www.microsoft.com/net/download/)。</span><span class="sxs-lookup"><span data-stu-id="d942e-121">You must also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a><span data-ttu-id="d942e-122">安裝 Visual Studio 程式碼和 Ionide 外掛程式</span><span class="sxs-lookup"><span data-stu-id="d942e-122">Installing Visual Studio Code and the Ionide plugin</span></span>

<span data-ttu-id="d942e-123">您可以安裝 Visual Studio 程式碼從[code.visualstudio.com](https://code.visualstudio.com)網站。</span><span class="sxs-lookup"><span data-stu-id="d942e-123">You can install Visual Studio Code from the [code.visualstudio.com](https://code.visualstudio.com) website.</span></span>

<span data-ttu-id="d942e-124">接下來，按一下 擴充功能圖示並搜尋"Ionide 」:</span><span class="sxs-lookup"><span data-stu-id="d942e-124">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="d942e-125">只有 Visual Studio 程式碼中的 F # 支援所需的外掛程式[Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="d942e-125">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="d942e-126">不過，您也可以安裝[Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)取得[偽造](https://fsharp.github.io/FAKE/)支援和[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)取得[Paket](https://fsprojects.github.io/Paket/)支援。</span><span class="sxs-lookup"><span data-stu-id="d942e-126">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="d942e-127">假造而且 Paket 其他 F # 社群工具來建置專案及分別管理的相依性。</span><span class="sxs-lookup"><span data-stu-id="d942e-127">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="d942e-128">使用 Ionide 建立第一個專案</span><span class="sxs-lookup"><span data-stu-id="d942e-128">Creating your first project with Ionide</span></span>

<span data-ttu-id="d942e-129">若要建立新的 F # 專案，請在新的資料夾 （您可以將檔案命名任何您喜歡） 中開啟 Visual Studio 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d942e-129">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="d942e-130">接下來，開啟 命令面板 (**檢視 > 命令調色盤**) 並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="d942e-130">Next, open the command pallette (**View > Command Pallette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="d942e-131">這由[FORGE](https://github.com/fsharp-editing/Forge)專案。</span><span class="sxs-lookup"><span data-stu-id="d942e-131">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
<span data-ttu-id="d942e-132">如果看不到範本選項，請再試一次命令選擇區中執行下列命令，以重新整理範本： `>F#: Refresh Project Templates`。</span><span class="sxs-lookup"><span data-stu-id="d942e-132">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="d942e-133">選取 「 F #:: 新專案 」，請按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="d942e-133">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="d942e-134">這會帶您前往下一個步驟，可用於選取的專案範本。</span><span class="sxs-lookup"><span data-stu-id="d942e-134">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="d942e-135">挑選`classlib`範本，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="d942e-135">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="d942e-136">下一步，挑選要在其中建立專案的目錄。</span><span class="sxs-lookup"><span data-stu-id="d942e-136">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="d942e-137">如果保留空白，它會使用目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="d942e-137">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="d942e-138">最後，命名您的專案中的最後一個步驟。</span><span class="sxs-lookup"><span data-stu-id="d942e-138">Finally, name your project in the final step.</span></span> <span data-ttu-id="d942e-139">F # 使用[Pascal 案例](http://c2.com/cgi/wiki?PascalCase)專案名稱。</span><span class="sxs-lookup"><span data-stu-id="d942e-139">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="d942e-140">本文使用`ClassLibraryDemo`做為名稱。</span><span class="sxs-lookup"><span data-stu-id="d942e-140">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="d942e-141">一旦您輸入您想要為您的專案的名稱，叫用**Enter**。</span><span class="sxs-lookup"><span data-stu-id="d942e-141">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="d942e-142">如果您遵循上述步驟，您應該取得 Visual Studio 程式碼工作區左邊會出現以下列：</span><span class="sxs-lookup"><span data-stu-id="d942e-142">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="d942e-143">F # 專案本身，在底下`ClassLibraryDemo`資料夾。</span><span class="sxs-lookup"><span data-stu-id="d942e-143">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="d942e-144">新增套件透過正確的目錄結構[ `Paket` ](https://fsprojects.github.io/Paket/)。</span><span class="sxs-lookup"><span data-stu-id="d942e-144">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="d942e-145">跨平台建置指令碼[ `FAKE` ](https://fsharp.github.io/FAKE/)。</span><span class="sxs-lookup"><span data-stu-id="d942e-145">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="d942e-146">`paket.exe`可以擷取封裝，並讓您解析的相依性的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="d942e-146">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="d942e-147">A`.gitignore`檔案，如果您想要將這個專案加入 Git 架構的原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="d942e-147">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="d942e-148">撰寫一些程式碼</span><span class="sxs-lookup"><span data-stu-id="d942e-148">Writing some code</span></span>

<span data-ttu-id="d942e-149">開啟*ClassLibraryDemo*資料夾。</span><span class="sxs-lookup"><span data-stu-id="d942e-149">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="d942e-150">您應該會看到下列檔案：</span><span class="sxs-lookup"><span data-stu-id="d942e-150">You should see the following files:</span></span>

1. <span data-ttu-id="d942e-151">`ClassLibraryDemo.fs`定義的類別具有的 F # 實作檔案。</span><span class="sxs-lookup"><span data-stu-id="d942e-151">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="d942e-152">`ClassLibraryDemo.fsproj`F # 專案檔用來建置此專案。</span><span class="sxs-lookup"><span data-stu-id="d942e-152">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="d942e-153">`Script.fsx`F # 指令碼檔，以載入原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="d942e-153">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="d942e-154">`paket.references`可指定專案相依性的 Paket 檔。</span><span class="sxs-lookup"><span data-stu-id="d942e-154">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="d942e-155">開啟`Script.fsx`，並在結尾處加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d942e-155">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="d942e-156">此函式會將文字轉換成一種[Pig 拉丁](https://en.wikipedia.org/wiki/Pig_Latin)。</span><span class="sxs-lookup"><span data-stu-id="d942e-156">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="d942e-157">下一步是評估使用 F # Interactive (FSI)。</span><span class="sxs-lookup"><span data-stu-id="d942e-157">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="d942e-158">反白顯示整個函式 （應為 11 行長度）。</span><span class="sxs-lookup"><span data-stu-id="d942e-158">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="d942e-159">一旦會反白顯示，保存**Alt**金鑰並點擊**Enter**。</span><span class="sxs-lookup"><span data-stu-id="d942e-159">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="d942e-160">您會發現下面顯視窗，它應該會顯示結果類似這樣：</span><span class="sxs-lookup"><span data-stu-id="d942e-160">You'll notice a window pop up below, and it should show something like this:</span></span>

![F # Interactive Ionide 輸出的範例](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="d942e-162">這並未三件事：</span><span class="sxs-lookup"><span data-stu-id="d942e-162">This did three things:</span></span>

1. <span data-ttu-id="d942e-163">它會啟動 FSI 程序。</span><span class="sxs-lookup"><span data-stu-id="d942e-163">It started the FSI process.</span></span>
2. <span data-ttu-id="d942e-164">它透過 FSI 程序傳送您反白顯示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d942e-164">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="d942e-165">FSI 程序會評估您透過傳送的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d942e-165">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="d942e-166">因為您透過傳送[函式](../language-reference/functions/index.md)，您現在可以呼叫該函式與 FSI ！</span><span class="sxs-lookup"><span data-stu-id="d942e-166">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="d942e-167">在互動式視窗中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="d942e-167">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="d942e-168">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="d942e-168">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="d942e-169">現在，讓我們再一次與第一個字母母音。</span><span class="sxs-lookup"><span data-stu-id="d942e-169">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="d942e-170">輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d942e-170">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="d942e-171">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="d942e-171">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="d942e-172">此函式會出現無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="d942e-172">The function appears to be working as expected.</span></span> <span data-ttu-id="d942e-173">恭喜您，只需要在 Visual Studio 程式碼撰寫您的第一個 F # 函式，並評估與 FSI ！</span><span class="sxs-lookup"><span data-stu-id="d942e-173">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="d942e-174">您可能已經注意到，在以結束 FSI 中的線條`;;`。</span><span class="sxs-lookup"><span data-stu-id="d942e-174">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="d942e-175">這是因為 FSI 可讓您輸入多行。</span><span class="sxs-lookup"><span data-stu-id="d942e-175">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="d942e-176">`;;`結尾可讓 FSI 知道完成程式碼。</span><span class="sxs-lookup"><span data-stu-id="d942e-176">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="d942e-177">說明程式碼</span><span class="sxs-lookup"><span data-stu-id="d942e-177">Explaining the code</span></span>

<span data-ttu-id="d942e-178">如果您不確定程式實際上做什麼的程式碼，以下是逐步。</span><span class="sxs-lookup"><span data-stu-id="d942e-178">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="d942e-179">如您所見，`toPigLatin`是函式會採用做為輸入的文字，並將它轉換成該單字的 Pig 拉丁表示法。</span><span class="sxs-lookup"><span data-stu-id="d942e-179">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="d942e-180">這個規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="d942e-180">The rules for this are as follows:</span></span>

<span data-ttu-id="d942e-181">在 word 中的第一個字元開頭母音，"鐘樓"加入文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="d942e-181">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="d942e-182">如果它不會以某個母音開頭，將該第一個字元移至文字的結尾，加入 「 可能 」。</span><span class="sxs-lookup"><span data-stu-id="d942e-182">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="d942e-183">您可能已注意到 FSI 中的下列：</span><span class="sxs-lookup"><span data-stu-id="d942e-183">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="d942e-184">這指出`toPigLatin`是使用中的函式`string`做為輸入 (稱為`word`)，並傳回另一個`string`。</span><span class="sxs-lookup"><span data-stu-id="d942e-184">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="d942e-185">這稱為[函式的類型簽章](https://fsharpforfunandprofit.com/posts/function-signatures/)，F # 是要了解 F # 程式碼索引鍵的基本部分。</span><span class="sxs-lookup"><span data-stu-id="d942e-185">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="d942e-186">您也會發現這如果您將滑鼠停留在 Visual Studio 程式碼中的函式。</span><span class="sxs-lookup"><span data-stu-id="d942e-186">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="d942e-187">在函式的主體中，您會發現兩個不同的部分：</span><span class="sxs-lookup"><span data-stu-id="d942e-187">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="d942e-188">內部的函式，呼叫`isVowel`，決定如果指定的字元 (`c`) 會編碼母音方法是檢查它是否符合其中一個提供的模式透過[模式比對](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="d942e-188">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="d942e-189">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)檢查是否第一個字元會編碼母音，並傳回值的輸入字元超出建構根據 if 的第一個字元的運算式已母音或未驗證：</span><span class="sxs-lookup"><span data-stu-id="d942e-189">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="d942e-190">流程`toPigLatin`因此：</span><span class="sxs-lookup"><span data-stu-id="d942e-190">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="d942e-191">檢查輸入的字組的第一個字元是否為某個母音。</span><span class="sxs-lookup"><span data-stu-id="d942e-191">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="d942e-192">如果是，請將"鐘樓"附加至文字的結尾。</span><span class="sxs-lookup"><span data-stu-id="d942e-192">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="d942e-193">否則，將該第一個字元移至文字的結尾，加入 「 可能 」。</span><span class="sxs-lookup"><span data-stu-id="d942e-193">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="d942e-194">沒有最後一注意到關於此： 沒有任何明確指令來從與許多其他語言有不同的函式傳回。</span><span class="sxs-lookup"><span data-stu-id="d942e-194">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="d942e-195">這是因為 F # 是以運算式為基礎，並在函式主體中的最後一個運算式是傳回的值。</span><span class="sxs-lookup"><span data-stu-id="d942e-195">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="d942e-196">因為`if..then..else`本身是運算式的主體`then`區塊或內文`else`區塊將會傳回輸入值而定。</span><span class="sxs-lookup"><span data-stu-id="d942e-196">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="d942e-197">將您的指令碼移到實作檔</span><span class="sxs-lookup"><span data-stu-id="d942e-197">Moving your script code into the implementation file</span></span>

<span data-ttu-id="d942e-198">這篇文章中的先前各節示範常見的第一個步驟，在撰寫 F # 程式碼： 撰寫初始的函式，然後使用 FSI 以互動方式執行。</span><span class="sxs-lookup"><span data-stu-id="d942e-198">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="d942e-199">這稱為 REPL 導向的開發工作，其中[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)代表 「 讀取評估列印迴圈 」。</span><span class="sxs-lookup"><span data-stu-id="d942e-199">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="d942e-200">它是實驗功能，直到您有工作的好方法。</span><span class="sxs-lookup"><span data-stu-id="d942e-200">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="d942e-201">REPL 導向的開發工作的下一個步驟是將使用中程式碼移至 F # 實作檔。</span><span class="sxs-lookup"><span data-stu-id="d942e-201">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="d942e-202">它可以再編譯 F # 編譯器可執行的組件。</span><span class="sxs-lookup"><span data-stu-id="d942e-202">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="d942e-203">若要開始，請開啟`ClassLibraryDemo.fs`。</span><span class="sxs-lookup"><span data-stu-id="d942e-203">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="d942e-204">您會發現，某些程式碼已在有。</span><span class="sxs-lookup"><span data-stu-id="d942e-204">You'll notice that some code is already in there.</span></span> <span data-ttu-id="d942e-205">請繼續並刪除類別定義中，但請務必保留[ `namespace` ](../language-reference/namespaces.md)頂端的宣告。</span><span class="sxs-lookup"><span data-stu-id="d942e-205">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="d942e-206">接下來，建立新[ `module` ](../language-reference/modules.md)呼叫`PigLatin`並複製`toPigLatin`函式匯入它在這種情況：</span><span class="sxs-lookup"><span data-stu-id="d942e-206">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="d942e-207">接下來，開啟`Script.fsx`檔案一次，並刪除整個`toPigLatin`函式，但務必要保留檔案中的下列兩行：</span><span class="sxs-lookup"><span data-stu-id="d942e-207">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="d942e-208">FSI 以載入指令碼所需的第一行`ClassLibraryDemo.fs`。</span><span class="sxs-lookup"><span data-stu-id="d942e-208">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="d942e-209">第二行在於其便利性： 略過為選擇性，但是您必須輸入`open ClassLibraryDemo`FSI 視窗，如果您想要將`ToPigLatin`模組納入範圍。</span><span class="sxs-lookup"><span data-stu-id="d942e-209">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="d942e-210">接下來，在 FSI 視窗中，呼叫函式`PigLatin`先前定義的模組：</span><span class="sxs-lookup"><span data-stu-id="d942e-210">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="d942e-211">成功！</span><span class="sxs-lookup"><span data-stu-id="d942e-211">Success!</span></span> <span data-ttu-id="d942e-212">取得與之前相同的結果，但現在已從 F # 實作檔案載入。</span><span class="sxs-lookup"><span data-stu-id="d942e-212">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="d942e-213">此處的主要差異是 F # 原始程式檔會編譯成執行 FSI 不只是在任何地方、 組件。</span><span class="sxs-lookup"><span data-stu-id="d942e-213">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="d942e-214">總結</span><span class="sxs-lookup"><span data-stu-id="d942e-214">Summary</span></span>

<span data-ttu-id="d942e-215">在本文中，您學到：</span><span class="sxs-lookup"><span data-stu-id="d942e-215">In this article, you've learned:</span></span>

1. <span data-ttu-id="d942e-216">如何設定與 Ionide Visual Studio 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d942e-216">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="d942e-217">如何使用 Ionide 建立第一個 F # 專案。</span><span class="sxs-lookup"><span data-stu-id="d942e-217">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="d942e-218">如何使用 F # 指令碼處理 Ionide 中撰寫您的第一個 F # 函式，然後將它執行 FSI 中。</span><span class="sxs-lookup"><span data-stu-id="d942e-218">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="d942e-219">如何將指令碼移轉至 F # 原始程式檔，然後從 FSI 呼叫該程式碼。</span><span class="sxs-lookup"><span data-stu-id="d942e-219">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="d942e-220">您現在要寫入更多 F # 程式碼使用 Visual Studio 程式碼和 Ionide 配備。</span><span class="sxs-lookup"><span data-stu-id="d942e-220">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="d942e-221">疑難排解</span><span class="sxs-lookup"><span data-stu-id="d942e-221">Troubleshooting</span></span>

<span data-ttu-id="d942e-222">以下是您可以疑難排解特定問題，您可能會遇到的幾個方法：</span><span class="sxs-lookup"><span data-stu-id="d942e-222">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="d942e-223">若要取得程式碼編輯 Ionide 的功能，您的 F # 檔案需要儲存到磁碟，然後在 Visual Studio 程式碼工作區中開啟的資料夾內。</span><span class="sxs-lookup"><span data-stu-id="d942e-223">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="d942e-224">如果您變更您的系統或 Ionide 必要條件安裝 Visual Studio 程式碼開啟，請重新啟動 Visual Studio 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d942e-224">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="d942e-225">請檢查您可以使用 F # 編譯器和 F # interactive 從命令列不完整的路徑。</span><span class="sxs-lookup"><span data-stu-id="d942e-225">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="d942e-226">您可以輸入`fsc`對於 F # 編譯器，命令列中和`fsi`或`fsharpi`Visual F # 工具在 Windows 和 Mac/Linux 上的 Mono 上分別。</span><span class="sxs-lookup"><span data-stu-id="d942e-226">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="d942e-227">如果您在專案目錄中有無效的字元，Ionide 可能無法運作。</span><span class="sxs-lookup"><span data-stu-id="d942e-227">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="d942e-228">如果發生這種情況，請重新命名專案目錄。</span><span class="sxs-lookup"><span data-stu-id="d942e-228">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="d942e-229">如果使用無 Ionide 命令，請檢查您[Visual Studio Code 按鍵組合](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)查看如果您要覆寫的它們不小心。</span><span class="sxs-lookup"><span data-stu-id="d942e-229">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="d942e-230">如果您的電腦上中斷 Ionide 上述都無法有固定的問題，請嘗試移除`ionide-fsharp`目錄在電腦上重新安裝外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="d942e-230">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="d942e-231">Ionide 是開放原始碼專案所建立與維護由 F # 社群的成員。</span><span class="sxs-lookup"><span data-stu-id="d942e-231">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="d942e-232">請報告問題，並隨意在參與[Ionide VSCode: FSharp GitHub 儲存機制](https://github.com/ionide/ionide-vscode-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="d942e-232">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="d942e-233">如果您有要報告的問題，請遵循[取得記錄檔使用 回報問題時的指示](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)。</span><span class="sxs-lookup"><span data-stu-id="d942e-233">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="d942e-234">您也可以要求取得進一步的協助從 Ionide 開發人員和 F # 中的社群[Ionide Gitter 通道](https://gitter.im/ionide/ionide-project)。</span><span class="sxs-lookup"><span data-stu-id="d942e-234">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d942e-235">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d942e-235">Next steps</span></span>

<span data-ttu-id="d942e-236">若要深入了解 F # 和語言的功能，請參閱[教學課程的 F #](../tour.md)。</span><span class="sxs-lookup"><span data-stu-id="d942e-236">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
