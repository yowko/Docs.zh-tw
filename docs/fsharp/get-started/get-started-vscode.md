---
title: 開始使用F# Visual Studio Code
description: 瞭解如何搭配 Visual Studio Code F#和 Ionide 外掛程式套件使用。
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082991"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="c31e7-103">開始使用F# Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c31e7-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="c31e7-104">您可以使用F# [Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)來撰寫[Visual Studio Code](https://code.visualstudio.com) ，利用 IntelliSense 和基本程式碼重構取得絕佳的跨平臺、輕量的整合式開發環境（IDE）體驗。</span><span class="sxs-lookup"><span data-stu-id="c31e7-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="c31e7-105">若要深入瞭解外掛程式，請造訪[Ionide.io](http://ionide.io) 。</span><span class="sxs-lookup"><span data-stu-id="c31e7-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="c31e7-106">若要開始，請確定您已[ F#正確安裝和 Ionide 外掛程式](install-fsharp.md#install-f-with-visual-studio-code)。</span><span class="sxs-lookup"><span data-stu-id="c31e7-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

> [!NOTE]
> <span data-ttu-id="c31e7-107">Ionide 會產生 .NET Framework F#專案，而不是 dotnet core，這可能會有跨平臺的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="c31e7-107">Ionide will generate .NET Framework F# projects, not dotnet core, which can have cross-platform compatibility issues.</span></span> <span data-ttu-id="c31e7-108">如果您是在**Linux**或**OSX**上執行，較簡單的入門方式就是使用[命令列工具](get-started-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="c31e7-108">If you are running on **Linux** or **OSX**, a simpler way to get started is to use the [command-line tools](get-started-command-line.md).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="c31e7-109">使用 Ionide 建立您的第一個專案</span><span class="sxs-lookup"><span data-stu-id="c31e7-109">Creating your first project with Ionide</span></span>

<span data-ttu-id="c31e7-110">若要建立新F#的專案，請在新的資料夾中開啟 Visual Studio Code （您可以將它命名為任何您喜歡的名稱）。</span><span class="sxs-lookup"><span data-stu-id="c31e7-110">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="c31e7-111">接下來，開啟命令選擇區（**View > 命令**選擇區），然後輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="c31e7-111">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```console
> F# new project
```

<span data-ttu-id="c31e7-112">這是由[偽造](https://github.com/fsharp-editing/Forge)專案提供技術支援。</span><span class="sxs-lookup"><span data-stu-id="c31e7-112">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
> <span data-ttu-id="c31e7-113">如果您沒有看到範本選項，請在命令選擇區中執行下列命令，以嘗試重新`>F#: Refresh Project Templates`整理範本：。</span><span class="sxs-lookup"><span data-stu-id="c31e7-113">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="c31e7-114">選取 F#：新增專案，按**Enter 鍵**。</span><span class="sxs-lookup"><span data-stu-id="c31e7-114">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="c31e7-115">這會帶您前往下一個步驟，也就是選取專案範本。</span><span class="sxs-lookup"><span data-stu-id="c31e7-115">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="c31e7-116">挑選範本，然後按**Enter 鍵。** `classlib`</span><span class="sxs-lookup"><span data-stu-id="c31e7-116">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="c31e7-117">接下來，選擇要在其中建立專案的目錄。</span><span class="sxs-lookup"><span data-stu-id="c31e7-117">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="c31e7-118">如果您將它保留空白，則會使用目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="c31e7-118">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="c31e7-119">最後，在最後一個步驟中命名您的專案。</span><span class="sxs-lookup"><span data-stu-id="c31e7-119">Finally, name your project in the final step.</span></span> <span data-ttu-id="c31e7-120">F#針對專案名稱使用[Pascal 大小寫](http://c2.com/cgi/wiki?PascalCase)。</span><span class="sxs-lookup"><span data-stu-id="c31e7-120">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="c31e7-121">本文會使用`ClassLibraryDemo`做為名稱。</span><span class="sxs-lookup"><span data-stu-id="c31e7-121">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="c31e7-122">輸入您想要用於專案的名稱之後，按**Enter 鍵**。</span><span class="sxs-lookup"><span data-stu-id="c31e7-122">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="c31e7-123">如果您已遵循上一個步驟，您應該會在左邊看到 [Visual Studio Code] 工作區，以顯示下列內容：</span><span class="sxs-lookup"><span data-stu-id="c31e7-123">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="c31e7-124">F#專案本身，位於`ClassLibraryDemo`資料夾底下。</span><span class="sxs-lookup"><span data-stu-id="c31e7-124">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="c31e7-125">透過新增封裝[`Paket`](https://fsprojects.github.io/Paket/)的正確目錄結構。</span><span class="sxs-lookup"><span data-stu-id="c31e7-125">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="c31e7-126">使用[`FAKE`](https://fsharp.github.io/FAKE/)的跨平臺組建腳本。</span><span class="sxs-lookup"><span data-stu-id="c31e7-126">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="c31e7-127">可以為您提取封裝及解析相依性的可執行檔。`paket.exe`</span><span class="sxs-lookup"><span data-stu-id="c31e7-127">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="c31e7-128">如果`.gitignore`您想要將此專案加入至 Git 型原始檔控制，則為檔案。</span><span class="sxs-lookup"><span data-stu-id="c31e7-128">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="c31e7-129">撰寫一些程式碼</span><span class="sxs-lookup"><span data-stu-id="c31e7-129">Writing some code</span></span>

<span data-ttu-id="c31e7-130">開啟 [ *ClassLibraryDemo* ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c31e7-130">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="c31e7-131">您應該會看到下列檔案：</span><span class="sxs-lookup"><span data-stu-id="c31e7-131">You should see the following files:</span></span>

1. <span data-ttu-id="c31e7-132">`ClassLibraryDemo.fs`，這F#是已定義類別的實作為檔案。</span><span class="sxs-lookup"><span data-stu-id="c31e7-132">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="c31e7-133">`ClassLibraryDemo.fsproj`，這F#是用來建立此專案的專案檔。</span><span class="sxs-lookup"><span data-stu-id="c31e7-133">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="c31e7-134">`Script.fsx`，這F#是載入原始程式檔的腳本檔案。</span><span class="sxs-lookup"><span data-stu-id="c31e7-134">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="c31e7-135">`paket.references`，這是指定專案相依性的 Paket 檔案。</span><span class="sxs-lookup"><span data-stu-id="c31e7-135">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="c31e7-136">開啟`Script.fsx`，並在其結尾處新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="c31e7-136">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="c31e7-137">此函式會將單字轉換成[Pig 拉丁](https://en.wikipedia.org/wiki/Pig_Latin)格式。</span><span class="sxs-lookup"><span data-stu-id="c31e7-137">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="c31e7-138">下一個步驟是使用F#互動式（fsi.exe）進行評估。</span><span class="sxs-lookup"><span data-stu-id="c31e7-138">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="c31e7-139">反白顯示整個函式（應為11行長）。</span><span class="sxs-lookup"><span data-stu-id="c31e7-139">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="c31e7-140">反白顯示後，按住**Alt**鍵並按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c31e7-140">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="c31e7-141">您會注意到下面的視窗快顯，它應該會顯示如下的內容：</span><span class="sxs-lookup"><span data-stu-id="c31e7-141">You'll notice a window pop up below, and it should show something like this:</span></span>

![具有 Ionide F#的互動式輸出範例](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="c31e7-143">這有三件事：</span><span class="sxs-lookup"><span data-stu-id="c31e7-143">This did three things:</span></span>

1. <span data-ttu-id="c31e7-144">它已開始 FSI.EXE 程式。</span><span class="sxs-lookup"><span data-stu-id="c31e7-144">It started the FSI process.</span></span>
2. <span data-ttu-id="c31e7-145">它會傳送您在 FSI.EXE 流程上反白顯示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c31e7-145">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="c31e7-146">FSI.EXE 流程會評估您傳送的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c31e7-146">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="c31e7-147">由於您傳送的內容是[函式](../language-reference/functions/index.md), 因此您現在可以使用 fsi.exe 來呼叫該函式!</span><span class="sxs-lookup"><span data-stu-id="c31e7-147">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="c31e7-148">在 [互動式] 視窗中，輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="c31e7-148">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="c31e7-149">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="c31e7-149">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="c31e7-150">現在，讓我們以母音做為第一個字母來嘗試。</span><span class="sxs-lookup"><span data-stu-id="c31e7-150">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="c31e7-151">輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="c31e7-151">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="c31e7-152">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="c31e7-152">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="c31e7-153">函式看起來如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="c31e7-153">The function appears to be working as expected.</span></span> <span data-ttu-id="c31e7-154">恭喜您，您只是在F# Visual Studio Code 中撰寫了第一個函式，並使用 fsi.exe 進行評估！</span><span class="sxs-lookup"><span data-stu-id="c31e7-154">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="c31e7-155">您可能已經注意到，FSI.EXE 中的行會以`;;`終止。</span><span class="sxs-lookup"><span data-stu-id="c31e7-155">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="c31e7-156">這是因為 FSI.EXE 可讓您輸入多行。</span><span class="sxs-lookup"><span data-stu-id="c31e7-156">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="c31e7-157">結尾`;;`的可讓 fsi.exe 知道程式碼完成的時間。</span><span class="sxs-lookup"><span data-stu-id="c31e7-157">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="c31e7-158">說明程式碼</span><span class="sxs-lookup"><span data-stu-id="c31e7-158">Explaining the code</span></span>

<span data-ttu-id="c31e7-159">如果您不確定程式碼實際執行的作業，以下是逐步解說。</span><span class="sxs-lookup"><span data-stu-id="c31e7-159">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="c31e7-160">如您所見， `toPigLatin`是採用單字做為其輸入的函式，並將它轉換成該單字的 Pig-拉丁標記法。</span><span class="sxs-lookup"><span data-stu-id="c31e7-160">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="c31e7-161">此動作的規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="c31e7-161">The rules for this are as follows:</span></span>

<span data-ttu-id="c31e7-162">如果單字中的第一個字元是以母音開頭，請將 "好耶" 新增至單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="c31e7-162">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="c31e7-163">如果不是以母音開頭，請將該第一個字元移至單字的結尾，並在其中加上 "ay"。</span><span class="sxs-lookup"><span data-stu-id="c31e7-163">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="c31e7-164">在 FSI.EXE 中，您可能已注意到下列事項：</span><span class="sxs-lookup"><span data-stu-id="c31e7-164">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="c31e7-165">這表示`toPigLatin`會`string`將當做輸入（稱為`word`）的函式，並傳回另`string`一個。</span><span class="sxs-lookup"><span data-stu-id="c31e7-165">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="c31e7-166">這稱為函式的[型](https://fsharpforfunandprofit.com/posts/function-signatures/)別簽章，這是瞭解F# F#程式碼的關鍵。</span><span class="sxs-lookup"><span data-stu-id="c31e7-166">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="c31e7-167">如果您將滑鼠停留在 Visual Studio Code 的函式上，也會注意到這一點。</span><span class="sxs-lookup"><span data-stu-id="c31e7-167">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="c31e7-168">在函式的主體中，您會注意到兩個不同的部分：</span><span class="sxs-lookup"><span data-stu-id="c31e7-168">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="c31e7-169">稱為`isVowel`的內部函式, 藉由透過[模式比對](../language-reference/pattern-matching.md)檢查指定的字元 (`c`) 是否符合其中一種提供的模式, 來判斷其是否為母音:</span><span class="sxs-lookup"><span data-stu-id="c31e7-169">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="c31e7-170">一個[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)運算式，可檢查第一個字元是否為母音，並根據第一個字元是否為母音，依據輸入字元來構造傳回值：</span><span class="sxs-lookup"><span data-stu-id="c31e7-170">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="c31e7-171">因此，的`toPigLatin`流程如下：</span><span class="sxs-lookup"><span data-stu-id="c31e7-171">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="c31e7-172">檢查輸入字的第一個字元是否為母音。</span><span class="sxs-lookup"><span data-stu-id="c31e7-172">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="c31e7-173">如果是，請將 "好耶" 附加至單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="c31e7-173">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="c31e7-174">否則，請將該第一個字元移到單字的結尾，並在其中加上 "ay"。</span><span class="sxs-lookup"><span data-stu-id="c31e7-174">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="c31e7-175">有一件最後要注意的事項：從函式傳回的明確指示，與其他許多語言不同。</span><span class="sxs-lookup"><span data-stu-id="c31e7-175">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="c31e7-176">這是因為F#是以運算式為基礎，而函數主體中的最後一個運算式是傳回值。</span><span class="sxs-lookup"><span data-stu-id="c31e7-176">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="c31e7-177">因為`if..then..else`本身就是運算式，所以會根據輸入`then`值傳回區塊的主體`else`或區塊主體。</span><span class="sxs-lookup"><span data-stu-id="c31e7-177">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="c31e7-178">將您的腳本程式碼移至執行檔</span><span class="sxs-lookup"><span data-stu-id="c31e7-178">Moving your script code into the implementation file</span></span>

<span data-ttu-id="c31e7-179">本文中的先前章節示範了撰寫F#程式碼的常見第一個步驟：撰寫初始函式，並使用 fsi.exe 以互動方式執行它。</span><span class="sxs-lookup"><span data-stu-id="c31e7-179">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="c31e7-180">這就是所謂的複寫驅動開發, 其中[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)複寫代表「讀取-評估-列印迴圈」。</span><span class="sxs-lookup"><span data-stu-id="c31e7-180">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="c31e7-181">這是實驗功能的絕佳方式，直到您有一些工作可以運作為止。</span><span class="sxs-lookup"><span data-stu-id="c31e7-181">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="c31e7-182">以複寫為導向的開發的下一個步驟是將工作程式碼F#移至執行檔案。</span><span class="sxs-lookup"><span data-stu-id="c31e7-182">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="c31e7-183">然後編譯器會將它編譯F#成可執行檔元件。</span><span class="sxs-lookup"><span data-stu-id="c31e7-183">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="c31e7-184">若要開始， `ClassLibraryDemo.fs`請開啟。</span><span class="sxs-lookup"><span data-stu-id="c31e7-184">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="c31e7-185">您會發現有一些程式碼已經在那裡。</span><span class="sxs-lookup"><span data-stu-id="c31e7-185">You'll notice that some code is already in there.</span></span> <span data-ttu-id="c31e7-186">請繼續並刪除類別定義，但請務必將宣告保留[`namespace`](../language-reference/namespaces.md)在頂端。</span><span class="sxs-lookup"><span data-stu-id="c31e7-186">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="c31e7-187">接下來，建立名[`module`](../language-reference/modules.md) `PigLatin`為的新， `toPigLatin`並將函式複製到其中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c31e7-187">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="c31e7-188">接下來，再次`Script.fsx`開啟檔案，並刪除整個`toPigLatin`函式，但請務必在檔案中保留下列兩行：</span><span class="sxs-lookup"><span data-stu-id="c31e7-188">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="c31e7-189">選取這兩行文字，然後按 Alt + Enter 鍵，在 FSI.EXE 中執行這些行。</span><span class="sxs-lookup"><span data-stu-id="c31e7-189">Select both lines of text and press Alt+Enter to execute these lines in FSI.</span></span> <span data-ttu-id="c31e7-190">這些會將 Pig 拉丁程式庫的內容載入 fsi.exe 程式和`open` `ClassLibraryDemo`命名空間，讓您可以存取該功能。</span><span class="sxs-lookup"><span data-stu-id="c31e7-190">These will load the contents of the Pig Latin library into the FSI process and `open` the `ClassLibraryDemo` namespace so that you have access to the functionality.</span></span>

<span data-ttu-id="c31e7-191">接下來，在 [fsi.exe] 視窗中，使用您`PigLatin`稍早定義的模組來呼叫函式：</span><span class="sxs-lookup"><span data-stu-id="c31e7-191">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="c31e7-192">成功！</span><span class="sxs-lookup"><span data-stu-id="c31e7-192">Success!</span></span> <span data-ttu-id="c31e7-193">您會得到與之前相同的結果，但現在已F#從執行檔載入。</span><span class="sxs-lookup"><span data-stu-id="c31e7-193">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="c31e7-194">此處的主要差異在於， F#原始程式檔會編譯成可以在任何地方執行的元件，而不只是在 fsi.exe 中。</span><span class="sxs-lookup"><span data-stu-id="c31e7-194">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="c31e7-195">總結</span><span class="sxs-lookup"><span data-stu-id="c31e7-195">Summary</span></span>

<span data-ttu-id="c31e7-196">在本文中，您已瞭解：</span><span class="sxs-lookup"><span data-stu-id="c31e7-196">In this article, you've learned:</span></span>

1. <span data-ttu-id="c31e7-197">如何使用 Ionide 設定 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="c31e7-197">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="c31e7-198">如何使用 Ionide 建立您F#的第一個專案。</span><span class="sxs-lookup"><span data-stu-id="c31e7-198">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="c31e7-199">如何使用F#腳本，在 Ionide 中撰寫F#您的第一個函式，然後在 fsi.exe 中加以執行。</span><span class="sxs-lookup"><span data-stu-id="c31e7-199">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="c31e7-200">如何將您的腳本程式碼F#遷移至來源，然後從 fsi.exe 呼叫該程式碼。</span><span class="sxs-lookup"><span data-stu-id="c31e7-200">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="c31e7-201">您現在已可使用 Visual Studio Code 和 Ionide F#來撰寫更多程式碼。</span><span class="sxs-lookup"><span data-stu-id="c31e7-201">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="c31e7-202">疑難排解</span><span class="sxs-lookup"><span data-stu-id="c31e7-202">Troubleshooting</span></span>

<span data-ttu-id="c31e7-203">以下幾種方式可讓您針對可能遇到的某些問題進行疑難排解：</span><span class="sxs-lookup"><span data-stu-id="c31e7-203">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="c31e7-204">若要取得 Ionide 的程式碼編輯功能， F#您的檔案必須儲存至磁片，以及在 Visual Studio Code 工作區中開啟的資料夾內。</span><span class="sxs-lookup"><span data-stu-id="c31e7-204">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="c31e7-205">如果您已對系統進行變更，或已安裝 Ionide 的必要條件 Visual Studio Code 開啟，請重新開機 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="c31e7-205">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="c31e7-206">檢查您是否可以從命令F#行使用F#編譯器和互動式，而不需要完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c31e7-206">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="c31e7-207">若要這麼做，您`fsc`可以在F#編譯器的命令列中輸入， `fsi`或`fsharpi`分別針對 Windows F#上的視覺效果工具和 Mac/Linux 上的 Mono。</span><span class="sxs-lookup"><span data-stu-id="c31e7-207">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="c31e7-208">如果您的專案目錄中有不正確字元，Ionide 可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="c31e7-208">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="c31e7-209">如果是這種情況，請重新命名您的專案目錄。</span><span class="sxs-lookup"><span data-stu-id="c31e7-209">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="c31e7-210">如果沒有可用的 Ionide 命令，請檢查您的[Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) ，以查看是否不小心覆寫它們。</span><span class="sxs-lookup"><span data-stu-id="c31e7-210">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="c31e7-211">如果您的電腦上的 Ionide 已中斷，而上述未修正您的問題，請嘗試`ionide-fsharp`移除您電腦上的目錄，然後重新安裝外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="c31e7-211">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="c31e7-212">Ionide 是由F#社區成員所建立和維護的開放原始碼專案。</span><span class="sxs-lookup"><span data-stu-id="c31e7-212">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="c31e7-213">請在[Ionide-VSCode 回報問題，並隨意參與：Fsharp.core GitHub 存放](https://github.com/ionide/ionide-vscode-fsharp)庫。</span><span class="sxs-lookup"><span data-stu-id="c31e7-213">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="c31e7-214">如果您有回報的問題，請遵循[指示來取得報告問題時使用的記錄](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)。</span><span class="sxs-lookup"><span data-stu-id="c31e7-214">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="c31e7-215">您也可以在[Ionide Gitter 頻道](https://gitter.im/ionide/ionide-project)中，向 Ionide 開發F#人員和社區尋求進一步的協助。</span><span class="sxs-lookup"><span data-stu-id="c31e7-215">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c31e7-216">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c31e7-216">Next steps</span></span>

<span data-ttu-id="c31e7-217">若要深入瞭解F#語言的詳細資訊，請參閱[的F#導覽](../tour.md)。</span><span class="sxs-lookup"><span data-stu-id="c31e7-217">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
