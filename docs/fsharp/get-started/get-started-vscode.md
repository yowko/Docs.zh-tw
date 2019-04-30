---
title: 開始使用F#Visual Studio Code 中
description: 了解如何使用F#利用 Visual Studio Code 和 ionide 使用者外掛程式套件。
ms.date: 12/23/2018
ms.openlocfilehash: 7c2ecab14b3351d441249e7fc7cb3188a4ee7eba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949538"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="4f2e2-103">開始使用F#Visual Studio Code 中</span><span class="sxs-lookup"><span data-stu-id="4f2e2-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="4f2e2-104">您可以撰寫F#中[Visual Studio Code](https://code.visualstudio.com)具有[Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)若要取得 IntelliSense 與基本的程式碼好跨平台、 輕量級整合式開發環境 (IDE) 體驗重構作業。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="4f2e2-105">請瀏覽[Ionide.io](http://ionide.io)若要深入了解此外掛程式。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="4f2e2-106">若要開始，請確定您已[F#和正確安裝 Ionide 外掛程式](install-fsharp.md#install-f-with-visual-studio-code)。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

> [!NOTE]
> <span data-ttu-id="4f2e2-107">Ionide 使用者將會產生.NET FrameworkF#專案，不 dotnet core，這可能會有跨平台相容性問題。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-107">Ionide will generate .NET Framework F# projects, not dotnet core, which can have cross-platform compatibility issues.</span></span> <span data-ttu-id="4f2e2-108">如果您在上執行**Linux**或是**OSX**，若要開始更簡單的方式是使用[命令列工具](https://docs.microsoft.com/en-us/dotnet/fsharp/get-started/get-started-command-line)。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-108">If you are running on **Linux** or **OSX**, a simpler way to get started is to use the [command line tools](https://docs.microsoft.com/en-us/dotnet/fsharp/get-started/get-started-command-line).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="4f2e2-109">透過 Ionide 建立第一個專案</span><span class="sxs-lookup"><span data-stu-id="4f2e2-109">Creating your first project with Ionide</span></span>

<span data-ttu-id="4f2e2-110">若要建立新的F#專案中，開啟 Visual Studio Code （您可以為它命名您喜歡） 的新資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-110">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="4f2e2-111">接下來，開啟 命令選擇區 (**檢視 > 命令選擇區**) 並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-111">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="4f2e2-112">這由[偽造](https://github.com/fsharp-editing/Forge)專案。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-112">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
> <span data-ttu-id="4f2e2-113">如果看不到範本選項，請嘗試重新整理的範本，藉由在命令選擇區中執行下列命令： `>F#: Refresh Project Templates`。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-113">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="4f2e2-114">選取 「F#:新專案 」 點擊**Enter**。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-114">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="4f2e2-115">這會帶您前往下一個步驟，也就是選取專案範本。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-115">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="4f2e2-116">挑選`classlib`範本，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-116">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="4f2e2-117">接下來，選擇要建立的專案中的目錄。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-117">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="4f2e2-118">如果保留空白，它會使用目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-118">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="4f2e2-119">最後，命名您的專案中的最後一個步驟。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-119">Finally, name your project in the final step.</span></span> <span data-ttu-id="4f2e2-120">F#會使用[Pascal 大小寫慣例](http://c2.com/cgi/wiki?PascalCase)專案名稱。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-120">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="4f2e2-121">本文章使用`ClassLibraryDemo`做為名稱。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-121">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="4f2e2-122">一旦您輸入您想為您的專案的名稱，點擊**Enter**。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-122">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="4f2e2-123">如果您遵循上一個步驟，您應該會看到 Visual Studio 程式碼工作區左手邊顯示與下列：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-123">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="4f2e2-124">F#專案下, 面`ClassLibraryDemo`資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-124">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="4f2e2-125">新增套件透過正確的目錄結構[ `Paket` ](https://fsprojects.github.io/Paket/)。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-125">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="4f2e2-126">跨平台建置指令碼[ `FAKE` ](https://fsharp.github.io/FAKE/)。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-126">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="4f2e2-127">`paket.exe`可以擷取封裝，並為您解決相依性的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-127">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="4f2e2-128">A`.gitignore`檔案，如果您想要將此專案新增至 Git 架構原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-128">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="4f2e2-129">撰寫一些程式碼</span><span class="sxs-lookup"><span data-stu-id="4f2e2-129">Writing some code</span></span>

<span data-ttu-id="4f2e2-130">開啟*ClassLibraryDemo*資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-130">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="4f2e2-131">您應該會看到下列檔案：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-131">You should see the following files:</span></span>

1. <span data-ttu-id="4f2e2-132">`ClassLibraryDemo.fs`F#實作所定義的類別檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-132">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="4f2e2-133">`ClassLibraryDemo.fsproj`F#用來建置此專案的專案檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-133">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="4f2e2-134">`Script.fsx`F#載入原始程式檔的指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-134">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="4f2e2-135">`paket.references`指定專案相依性的 Paket 檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-135">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="4f2e2-136">開啟`Script.fsx`，並在結尾處新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-136">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="4f2e2-137">此函式會將單字轉換成一種[Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-137">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="4f2e2-138">下一步是評估使用F#互動式 (FSI)。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-138">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="4f2e2-139">反白顯示整個函式 （它應該是很長的 11 行）。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-139">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="4f2e2-140">之後它會反白顯示，保存**Alt**鍵並按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-140">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="4f2e2-141">您會發現下面顯示的視窗，並應該會顯示類似如下：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-141">You'll notice a window pop up below, and it should show something like this:</span></span>

![範例中的F#透過 Ionide 輸出的互動](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="4f2e2-143">這會執行三項工作：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-143">This did three things:</span></span>

1. <span data-ttu-id="4f2e2-144">它會啟動 FSI 程序。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-144">It started the FSI process.</span></span>
2. <span data-ttu-id="4f2e2-145">它透過 FSI 程序傳送您反白顯示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-145">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="4f2e2-146">FSI 程序會評估您透過傳送的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-146">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="4f2e2-147">因為您透過傳送[函式](../language-reference/functions/index.md)，您現在可以呼叫該函式與 FSI ！</span><span class="sxs-lookup"><span data-stu-id="4f2e2-147">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="4f2e2-148">在互動式視窗中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-148">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="4f2e2-149">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-149">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="4f2e2-150">現在，讓我們試一次的第一個字母母音的群組。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-150">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="4f2e2-151">輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-151">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="4f2e2-152">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-152">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="4f2e2-153">函式看起來如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-153">The function appears to be working as expected.</span></span> <span data-ttu-id="4f2e2-154">恭喜，您剛撰寫您的第一個F#在 Visual Studio Code 函式，並評估使用 FSI ！</span><span class="sxs-lookup"><span data-stu-id="4f2e2-154">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="4f2e2-155">您可能已經注意到，結尾 FSI 中的行`;;`。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-155">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="4f2e2-156">這是因為 FSI 可讓您輸入多行。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-156">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="4f2e2-157">`;;`結尾可讓 FSI 知道程式碼完成時。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-157">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="4f2e2-158">說明程式碼</span><span class="sxs-lookup"><span data-stu-id="4f2e2-158">Explaining the code</span></span>

<span data-ttu-id="4f2e2-159">如果您不確定程式碼實際上在做什麼，以下是逐步執行精靈。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-159">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="4f2e2-160">如您所見，`toPigLatin`是函式會採用做為輸入的字組，並將它轉換成該單字的 Pig Latin 表示法。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-160">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="4f2e2-161">此規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-161">The rules for this are as follows:</span></span>

<span data-ttu-id="4f2e2-162">如果在 word 中的第一個字元是由某個母音開頭，新增"yay 」 到字尾。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-162">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="4f2e2-163">如果它未啟動與母音的群組，移動該第一個字元到字尾，"ay 」 加入它。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-163">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="4f2e2-164">您可能已經注意到下列 FSI 中：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-164">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="4f2e2-165">這指出`toPigLatin`是函式，接受`string`做為輸入 (稱為`word`)，並傳回另一個`string`。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-165">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="4f2e2-166">這就所謂[函式的型別簽章](https://fsharpforfunandprofit.com/posts/function-signatures/)，基本的一項F#這是要了解索引鍵F#程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-166">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="4f2e2-167">您也會發現這如果您將滑鼠停留在 Visual Studio Code 中的函式。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-167">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="4f2e2-168">在此函式主體中，您會注意到兩個不同的部分：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-168">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="4f2e2-169">內部函式，呼叫`isVowel`，，決定如果指定的字元 (`c`) 檢查是否符合其中一個透過提供的模式是母音的群組[模式比對](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="4f2e2-169">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="4f2e2-170">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)檢查是否第一個字元是母音的群組，並傳回值超出輸入字元的建構基礎 if 的第一個字元的運算式是否母音的群組：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-170">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="4f2e2-171">流程`toPigLatin`因此：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-171">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="4f2e2-172">檢查是否輸入單字的第一個字元是母音的群組。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-172">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="4f2e2-173">如果是，將 「 yay"附加到字尾。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-173">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="4f2e2-174">否則，移動該第一個字元到字尾，而且"ay 」 加入它。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-174">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="4f2e2-175">沒有一個最後的一件事来注意一點： 沒有任何明確指令來從與許多其他語言有不同的函式傳回。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-175">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="4f2e2-176">這是因為F#是以運算式為基礎，並在函式主體中的最後一個運算式是傳回的值。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-176">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="4f2e2-177">因為`if..then..else`本身是運算式的主體`then`區塊或主體`else`區塊將會傳回輸入的值而定。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-177">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="4f2e2-178">將您的指令碼移到實作檔案</span><span class="sxs-lookup"><span data-stu-id="4f2e2-178">Moving your script code into the implementation file</span></span>

<span data-ttu-id="4f2e2-179">在本文中先前各節示範常見的第一個步驟，在撰寫F#程式碼： 撰寫的初始函式和以 FSI 以互動方式執行。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-179">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="4f2e2-180">這也稱為 REPL 為導向的開發，其中[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)代表 「 讀取-評估-列印迴圈 」。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-180">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="4f2e2-181">它是適合用來試驗功能，直到您完全運作。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-181">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="4f2e2-182">REPL 為導向的開發下一個步驟是將工作程式碼插入F#實作檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-182">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="4f2e2-183">它接著要編譯的F#編譯器可以執行的組件。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-183">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="4f2e2-184">若要開始，請開啟`ClassLibraryDemo.fs`。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-184">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="4f2e2-185">您會發現，一些程式碼已經在存在。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-185">You'll notice that some code is already in there.</span></span> <span data-ttu-id="4f2e2-186">請繼續並刪除類別定義，但請務必保留[ `namespace` ](../language-reference/namespaces.md)頂端的宣告。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-186">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="4f2e2-187">接下來，建立新[ `module` ](../language-reference/modules.md)稱為`PigLatin`並複製`toPigLatin`函式匯入它，例如：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-187">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="4f2e2-188">接下來，開啟`Script.fsx`同樣地，檔案，並刪除整個`toPigLatin`函式，但請務必保持檔案中的下列兩行：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-188">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="4f2e2-189">選取這兩個文字行，然後按 Alt + Enter 來執行這幾行 FSI 中。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-189">Select both lines of text and press Alt+Enter to execute these lines in FSI.</span></span> <span data-ttu-id="4f2e2-190">這些會載入 FSI 程序中的 Pig Latin 程式庫的內容及`open``ClassLibraryDemo`命名空間，所以您需要存取的功能。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-190">These will load the contents of the Pig Latin library into the FSI process and `open` the `ClassLibraryDemo` namespace so that you have access to the functionality.</span></span>

<span data-ttu-id="4f2e2-191">接下來，在 FSI 視窗中，呼叫函式搭配`PigLatin`您稍早定義的模組：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-191">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="4f2e2-192">成功！</span><span class="sxs-lookup"><span data-stu-id="4f2e2-192">Success!</span></span> <span data-ttu-id="4f2e2-193">您取得相同的結果之前，但現在從載入F#實作檔案。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-193">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="4f2e2-194">此處的主要差異在於F#原始程式檔編譯成組件可不只是在 FSI 隨處執行。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-194">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="4f2e2-195">總結</span><span class="sxs-lookup"><span data-stu-id="4f2e2-195">Summary</span></span>

<span data-ttu-id="4f2e2-196">在本文中，您已了解：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-196">In this article, you've learned:</span></span>

1. <span data-ttu-id="4f2e2-197">如何設定 Visual Studio Code，透過 Ionide。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-197">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="4f2e2-198">如何建立您的第一個F#透過 Ionide 的專案。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-198">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="4f2e2-199">如何使用F#撰寫您的第一個指令碼處理F#中 Ionide 函式，然後 FSI 中執行它。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-199">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="4f2e2-200">如何移轉指令碼，以F#來源，並接著從 FSI 呼叫該程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-200">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="4f2e2-201">現在您答對了要寫入更多F#使用 Visual Studio Code 和 ionide 使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-201">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="4f2e2-202">疑難排解</span><span class="sxs-lookup"><span data-stu-id="4f2e2-202">Troubleshooting</span></span>

<span data-ttu-id="4f2e2-203">以下是幾種方式，您可以針對某些您可能會遇到的問題進行疑難排解：</span><span class="sxs-lookup"><span data-stu-id="4f2e2-203">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="4f2e2-204">若要取得程式碼編輯功能的 ionide 使用者，您F#檔案必須儲存到磁碟，然後在 Visual Studio Code 工作區中開啟的資料夾內。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-204">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="4f2e2-205">如果您已對您的系統中的變更，或使用開啟的 Visual Studio Code 安裝 Ionide 必要條件，請重新啟動 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-205">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="4f2e2-206">您可以使用的核取F#編譯器和F#互動式命令列，而不需要完整的路徑。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-206">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="4f2e2-207">則可以輸入`fsc`的命令列中F#編譯器，並`fsi`或`fsharpi`視覺效果的F#分別工具在 Windows 和 Mac/Linux 上的 Mono。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-207">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="4f2e2-208">如果您在專案目錄中有無效的字元，ionide 使用者可能無法運作。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-208">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="4f2e2-209">如果發生這種情況，請重新命名您的專案目錄。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-209">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="4f2e2-210">如果使用 none Ionide 命令時，請檢查您[Visual Studio Code 按鍵繫結關係](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)以查看 如果您要覆寫它們意外。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-210">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="4f2e2-211">如果 Ionide 已損毀您的電腦上，並以上皆非已修正您的問題，請嘗試移除`ionide-fsharp`目錄在您的電腦上重新安裝的外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-211">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="4f2e2-212">Ionide 是開放原始碼專案所建立與維護成員的F#社群。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-212">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="4f2e2-213">請回報問題，並歡迎您參與在[Ionide VSCode:FSharp GitHub 存放庫](https://github.com/ionide/ionide-vscode-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-213">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="4f2e2-214">如果您有要報告的問題，請遵循[取得的記錄檔使用時回報問題的指示](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-214">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="4f2e2-215">您也可尋求進一步的協助，Ionide 開發人員和F#中的社群[Ionide Gitter 通道](https://gitter.im/ionide/ionide-project)。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-215">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4f2e2-216">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4f2e2-216">Next steps</span></span>

<span data-ttu-id="4f2e2-217">若要深入了解F#功能的語言，請查閱[概觀F# ](../tour.md)。</span><span class="sxs-lookup"><span data-stu-id="4f2e2-217">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
