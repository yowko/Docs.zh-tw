---
title: 開始使用 Visual Studio Code 中的 F#
description: 了解如何使用 F# 與 Visual Studio Code 和 ionide 使用者外掛程式套件。
ms.date: 05/28/2018
ms.openlocfilehash: e962be2796cf0d6eb90d459730659e492f864716
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "50192664"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="6d5ea-103">開始使用 Visual Studio Code 中的 F#</span><span class="sxs-lookup"><span data-stu-id="6d5ea-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="6d5ea-104">您可以撰寫 F# [Visual Studio Code](https://code.visualstudio.com)具有[Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)若要取得 IntelliSense 與基本的程式碼好跨平台、 輕量級整合式開發環境 (IDE) 體驗重構作業。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and basic code refactorings.</span></span> <span data-ttu-id="6d5ea-105">請瀏覽[Ionide.io](http://ionide.io)若要深入了解此外掛程式。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="6d5ea-106">若要開始，請確定您已[F# 和 ionide 使用者外掛程式安裝正確](install-fsharp.md#install-f-with-visual-studio-code)。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="creating-your-first-project-with-ionide"></a><span data-ttu-id="6d5ea-107">透過 Ionide 建立第一個專案</span><span class="sxs-lookup"><span data-stu-id="6d5ea-107">Creating your first project with Ionide</span></span>

<span data-ttu-id="6d5ea-108">若要建立新的 F# 專案，開啟 Visual Studio Code （您可以為它命名您喜歡） 的新資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-108">To create a new F# project, open Visual Studio Code in a new folder (you can name it whatever you like).</span></span>

<span data-ttu-id="6d5ea-109">接下來，開啟 命令選擇區 (**檢視 > 命令選擇區**) 並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-109">Next, open the command palette (**View > Command Palette**) and type the following:</span></span>

```
> F# new project
```

<span data-ttu-id="6d5ea-110">這由[偽造](https://github.com/fsharp-editing/Forge)專案。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-110">This is powered by the [FORGE](https://github.com/fsharp-editing/Forge) project.</span></span>

> [!NOTE]
<span data-ttu-id="6d5ea-111">如果看不到範本選項，請嘗試重新整理的範本，藉由在命令選擇區中執行下列命令： `>F#: Refresh Project Templates`。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-111">If you don't see template options, try refreshing templates by running the following command in the Command Palette: `>F#: Refresh Project Templates`.</span></span>

<span data-ttu-id="6d5ea-112">選取 [F#:: 新專案] 點擊**Enter**。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-112">Select "F#: New Project" by hitting **Enter**.</span></span> <span data-ttu-id="6d5ea-113">這會帶您前往下一個步驟，也就是選取專案範本。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-113">This takes you to the next step, which is for selecting a project template.</span></span>

<span data-ttu-id="6d5ea-114">挑選`classlib`範本，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-114">Pick the `classlib` template and hit **Enter**.</span></span>

<span data-ttu-id="6d5ea-115">接下來，選擇要建立的專案中的目錄。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-115">Next, pick a directory to create the project in.</span></span> <span data-ttu-id="6d5ea-116">如果保留空白，它會使用目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-116">If you leave it blank, it uses the current directory.</span></span>

<span data-ttu-id="6d5ea-117">最後，命名您的專案中的最後一個步驟。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-117">Finally, name your project in the final step.</span></span> <span data-ttu-id="6d5ea-118">F# 會使用[Pascal 大小寫慣例](http://c2.com/cgi/wiki?PascalCase)專案名稱。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-118">F# uses [Pascal case](http://c2.com/cgi/wiki?PascalCase) for project names.</span></span> <span data-ttu-id="6d5ea-119">本文章使用`ClassLibraryDemo`做為名稱。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-119">This article uses `ClassLibraryDemo` as the name.</span></span> <span data-ttu-id="6d5ea-120">一旦您輸入您想為您的專案的名稱，點擊**Enter**。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-120">Once you've entered the name you want for your project, hit **Enter**.</span></span>

<span data-ttu-id="6d5ea-121">如果您遵循上一個步驟，您應該會看到 Visual Studio 程式碼工作區左手邊顯示與下列：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-121">If you followed the previous step, you should get the Visual Studio Code Workspace on the left-hand side to appear with the following:</span></span>

1. <span data-ttu-id="6d5ea-122">F# 專案下, 面`ClassLibraryDemo`資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-122">The F# project itself, underneath the `ClassLibraryDemo` folder.</span></span>
2. <span data-ttu-id="6d5ea-123">新增套件透過正確的目錄結構[ `Paket` ](https://fsprojects.github.io/Paket/)。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-123">The correct directory structure for adding packages via [`Paket`](https://fsprojects.github.io/Paket/).</span></span>
3. <span data-ttu-id="6d5ea-124">跨平台建置指令碼[ `FAKE` ](https://fsharp.github.io/FAKE/)。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-124">A cross-platform build script with [`FAKE`](https://fsharp.github.io/FAKE/).</span></span>
4. <span data-ttu-id="6d5ea-125">`paket.exe`可以擷取封裝，並為您解決相依性的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-125">The `paket.exe` executable that can fetch packages and resolve dependencies for you.</span></span>
5. <span data-ttu-id="6d5ea-126">A`.gitignore`檔案，如果您想要將此專案新增至 Git 架構原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-126">A `.gitignore` file if you wish to add this project to Git-based source control.</span></span>

## <a name="writing-some-code"></a><span data-ttu-id="6d5ea-127">撰寫一些程式碼</span><span class="sxs-lookup"><span data-stu-id="6d5ea-127">Writing some code</span></span>

<span data-ttu-id="6d5ea-128">開啟*ClassLibraryDemo*資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-128">Open the *ClassLibraryDemo* folder.</span></span>  <span data-ttu-id="6d5ea-129">您應該會看到下列檔案：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-129">You should see the following files:</span></span>

1. <span data-ttu-id="6d5ea-130">`ClassLibraryDemo.fs`定義的類別與 F# 實作檔。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-130">`ClassLibraryDemo.fs`, an F# implementation file with a class defined.</span></span>
2. <span data-ttu-id="6d5ea-131">`ClassLibraryDemo.fsproj`F# 專案檔用來建置此專案。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-131">`ClassLibraryDemo.fsproj`, an F# project file used to build this project.</span></span>
3. <span data-ttu-id="6d5ea-132">`Script.fsx`會載入原始程式檔的 F# 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-132">`Script.fsx`, an F# script file that loads the source file.</span></span>
4. <span data-ttu-id="6d5ea-133">`paket.references`指定專案相依性的 Paket 檔案。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-133">`paket.references`, a Paket file that specifies the project dependencies.</span></span>

<span data-ttu-id="6d5ea-134">開啟`Script.fsx`，並在結尾處新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-134">Open `Script.fsx`, and add the following code at the end of it:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="6d5ea-135">此函式會將單字轉換成一種[Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-135">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="6d5ea-136">下一個步驟是使用 F# Interactive (FSI) 進行評估。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-136">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="6d5ea-137">反白顯示整個函式 （它應該是很長的 11 行）。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-137">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="6d5ea-138">之後它會反白顯示，保存**Alt**鍵並按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-138">Once it is highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="6d5ea-139">您會發現下面顯示的視窗，並應該會顯示類似如下：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-139">You'll notice a window pop up below, and it should show something like this:</span></span>

![透過 Ionide 的 F# Interactive 輸出範例](media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="6d5ea-141">這會執行三項工作：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-141">This did three things:</span></span>

1. <span data-ttu-id="6d5ea-142">它會啟動 FSI 程序。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-142">It started the FSI process.</span></span>
2. <span data-ttu-id="6d5ea-143">它透過 FSI 程序傳送您反白顯示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-143">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="6d5ea-144">FSI 程序會評估您透過傳送的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-144">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="6d5ea-145">因為您透過傳送[函式](../language-reference/functions/index.md)，您現在可以呼叫該函式與 FSI ！</span><span class="sxs-lookup"><span data-stu-id="6d5ea-145">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="6d5ea-146">在互動式視窗中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-146">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="6d5ea-147">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-147">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="6d5ea-148">現在，讓我們試一次的第一個字母母音的群組。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-148">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="6d5ea-149">輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-149">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="6d5ea-150">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-150">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="6d5ea-151">函式看起來如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-151">The function appears to be working as expected.</span></span> <span data-ttu-id="6d5ea-152">恭喜，您剛在 Visual Studio Code 中撰寫您的第一個 F# 函式，並評估使用 FSI ！</span><span class="sxs-lookup"><span data-stu-id="6d5ea-152">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

>[!NOTE]
<span data-ttu-id="6d5ea-153">您可能已經注意到，結尾 FSI 中的行`;;`。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-153">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="6d5ea-154">這是因為 FSI 可讓您輸入多行。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-154">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="6d5ea-155">`;;`結尾可讓 FSI 知道程式碼完成時。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-155">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="6d5ea-156">說明程式碼</span><span class="sxs-lookup"><span data-stu-id="6d5ea-156">Explaining the code</span></span>

<span data-ttu-id="6d5ea-157">如果您不確定程式碼實際上在做什麼，以下是逐步執行精靈。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-157">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="6d5ea-158">如您所見，`toPigLatin`是函式會採用做為輸入的字組，並將它轉換成該單字的 Pig Latin 表示法。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-158">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="6d5ea-159">此規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-159">The rules for this are as follows:</span></span>

<span data-ttu-id="6d5ea-160">如果在 word 中的第一個字元是由某個母音開頭，新增"yay 」 到字尾。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-160">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="6d5ea-161">如果它未啟動與母音的群組，移動該第一個字元到字尾，"ay 」 加入它。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-161">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="6d5ea-162">您可能已經注意到下列 FSI 中：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-162">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="6d5ea-163">這指出`toPigLatin`是函式，接受`string`做為輸入 (稱為`word`)，並傳回另一個`string`。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-163">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="6d5ea-164">這就所謂[函式的型別簽章](https://fsharpforfunandprofit.com/posts/function-signatures/)，基本的一項 F# 是了解 F# 程式碼的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-164">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="6d5ea-165">您也會發現這如果您將滑鼠停留在 Visual Studio Code 中的函式。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-165">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="6d5ea-166">在此函式主體中，您會注意到兩個不同的部分：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-166">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="6d5ea-167">內部函式，呼叫`isVowel`，，決定如果指定的字元 (`c`) 檢查是否符合其中一個透過提供的模式是母音的群組[模式比對](../language-reference/pattern-matching.md):</span><span class="sxs-lookup"><span data-stu-id="6d5ea-167">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="6d5ea-168">[ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)檢查是否第一個字元是母音的群組，並傳回值超出輸入字元的建構基礎 if 的第一個字元的運算式是否母音的群組：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-168">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="6d5ea-169">流程`toPigLatin`因此：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-169">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="6d5ea-170">檢查是否輸入單字的第一個字元是母音的群組。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-170">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="6d5ea-171">如果是，將 「 yay"附加到字尾。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-171">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="6d5ea-172">否則，移動該第一個字元到字尾，而且"ay 」 加入它。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-172">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="6d5ea-173">沒有一個最後的一件事来注意一點： 沒有任何明確指令來從與許多其他語言有不同的函式傳回。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-173">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="6d5ea-174">這是因為 F# 是以運算式為基礎，而且在函式主體中的最後一個運算式傳回的值。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-174">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="6d5ea-175">因為`if..then..else`本身是運算式的主體`then`區塊或主體`else`區塊將會傳回輸入的值而定。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-175">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="moving-your-script-code-into-the-implementation-file"></a><span data-ttu-id="6d5ea-176">將您的指令碼移到實作檔案</span><span class="sxs-lookup"><span data-stu-id="6d5ea-176">Moving your script code into the implementation file</span></span>

<span data-ttu-id="6d5ea-177">在本文中先前各節示範常見的第一個步驟，在撰寫 F# 程式碼： 撰寫的初始函式和以 FSI 以互動方式執行。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-177">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="6d5ea-178">這也稱為 REPL 為導向的開發，其中[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)代表 「 讀取-評估-列印迴圈 」。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-178">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="6d5ea-179">它是適合用來試驗功能，直到您完全運作。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-179">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="6d5ea-180">REPL 導向開發方法的下一個步驟是將工作程式碼移至 F# 實作檔。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-180">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="6d5ea-181">它接著要編譯的 F# 編譯器可以執行的組件。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-181">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="6d5ea-182">若要開始，請開啟`ClassLibraryDemo.fs`。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-182">To begin, open `ClassLibraryDemo.fs`.</span></span>  <span data-ttu-id="6d5ea-183">您會發現，一些程式碼已經在存在。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-183">You'll notice that some code is already in there.</span></span> <span data-ttu-id="6d5ea-184">請繼續並刪除類別定義，但請務必保留[ `namespace` ](../language-reference/namespaces.md)頂端的宣告。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-184">Go ahead and delete the class definition, but make sure to leave the [`namespace`](../language-reference/namespaces.md) declaration at the top.</span></span>

<span data-ttu-id="6d5ea-185">接下來，建立新[ `module` ](../language-reference/modules.md)稱為`PigLatin`並複製`toPigLatin`函式匯入它，例如：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-185">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function into it as such:</span></span>

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

<span data-ttu-id="6d5ea-186">接下來，開啟`Script.fsx`同樣地，檔案，並刪除整個`toPigLatin`函式，但請務必保持檔案中的下列兩行：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-186">Next, open the `Script.fsx` file again, and delete the entire `toPigLatin` function, but make sure to keep the following two lines in the file:</span></span>

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

<span data-ttu-id="6d5ea-187">第一行所需的指令碼載入 FSI `ClassLibraryDemo.fs`。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-187">The first line is needed for FSI scripting to load `ClassLibraryDemo.fs`.</span></span> <span data-ttu-id="6d5ea-188">第二行可讓您輕鬆： 省略它是選擇性的但您必須輸入`open ClassLibraryDemo`FSI 視窗，如果您想要讓`ToPigLatin`進入範圍內的模組。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-188">The second line is a convenience: omitting it is optional, but you will need to type `open ClassLibraryDemo` in an FSI window if you wish to bring the `ToPigLatin` module into scope.</span></span>

<span data-ttu-id="6d5ea-189">接下來，在 FSI 視窗中，呼叫函式搭配`PigLatin`您稍早定義的模組：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-189">Next, in the FSI window, call the function with the `PigLatin` module that you defined earlier:</span></span>

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

<span data-ttu-id="6d5ea-190">成功！</span><span class="sxs-lookup"><span data-stu-id="6d5ea-190">Success!</span></span> <span data-ttu-id="6d5ea-191">取得與之前相同的結果，但現在從 F# 實作檔載入。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-191">You get the same results as before, but now loaded from an F# implementation file.</span></span> <span data-ttu-id="6d5ea-192">此處的主要差異是 F# 原始程式檔會編譯成組件可不只是在 FSI 隨處執行。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-192">The major difference here is that F# source files are compiled into assemblies that can be executed anywhere, not just in FSI.</span></span>

## <a name="summary"></a><span data-ttu-id="6d5ea-193">總結</span><span class="sxs-lookup"><span data-stu-id="6d5ea-193">Summary</span></span>

<span data-ttu-id="6d5ea-194">在本文中，您已了解：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-194">In this article, you've learned:</span></span>

1. <span data-ttu-id="6d5ea-195">如何設定 Visual Studio Code，透過 Ionide。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-195">How to set up Visual Studio Code with Ionide.</span></span>
2. <span data-ttu-id="6d5ea-196">如何透過 Ionide 建立第一個 F# 專案。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-196">How to create your first F# project with Ionide.</span></span>
3. <span data-ttu-id="6d5ea-197">如何使用 ionide 使用者撰寫您的第一個 F# 函式，然後將它執行 FSI 中的 F# 指令碼。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-197">How to use F# Scripting to write your first F# function in Ionide and then execute it in FSI.</span></span>
4. <span data-ttu-id="6d5ea-198">如何將您的指令碼移轉至 F# 原始程式檔，並接著從 FSI 呼叫該程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-198">How to migrate your script code to F# source and then call that code from FSI.</span></span>

<span data-ttu-id="6d5ea-199">您要現在可以撰寫更多 F# 程式碼使用 Visual Studio Code 和 ionide 使用者。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-199">You're now equipped to write much more F# code using Visual Studio Code and Ionide.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="6d5ea-200">疑難排解</span><span class="sxs-lookup"><span data-stu-id="6d5ea-200">Troubleshooting</span></span>

<span data-ttu-id="6d5ea-201">以下是幾種方式，您可以針對某些您可能會遇到的問題進行疑難排解：</span><span class="sxs-lookup"><span data-stu-id="6d5ea-201">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="6d5ea-202">若要取得程式碼編輯 ionide 使用者的功能，您的 F# 檔案必須儲存到磁碟，然後在 Visual Studio Code 工作區中開啟的資料夾內。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-202">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
2. <span data-ttu-id="6d5ea-203">如果您已對您的系統中的變更，或使用開啟的 Visual Studio Code 安裝 Ionide 必要條件，請重新啟動 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-203">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
3. <span data-ttu-id="6d5ea-204">請檢查您可以使用 F# 編譯器和 F# interactive 命令列，而不需要完整的路徑。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-204">Check that you can use the F# compiler and F# interactive from the command line without a fully-qualified path.</span></span> <span data-ttu-id="6d5ea-205">則可以輸入`fsc`F# 編譯器命令列中並`fsi`或`fsharpi`Visual F# 工具在 Windows 和 Mac/Linux 上的 Mono 上分別。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-205">You can do so by typing `fsc` in a command line for the F# compiler, and `fsi` or `fsharpi` for the Visual F# tools on Windows and Mono on Mac/Linux, respectively.</span></span>
4. <span data-ttu-id="6d5ea-206">如果您在專案目錄中有無效的字元，ionide 使用者可能無法運作。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-206">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="6d5ea-207">如果發生這種情況，請重新命名您的專案目錄。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-207">Rename your project directories if this is the case.</span></span>
5. <span data-ttu-id="6d5ea-208">如果使用 none Ionide 命令時，請檢查您[Visual Studio Code 按鍵繫結關係](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)以查看 如果您要覆寫它們意外。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-208">If none of the Ionide commands are working, check your [Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) to see if you're overriding them by accident.</span></span>
6. <span data-ttu-id="6d5ea-209">如果 Ionide 已損毀您的電腦上，並以上皆非已修正您的問題，請嘗試移除`ionide-fsharp`目錄在您的電腦上重新安裝的外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-209">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>

<span data-ttu-id="6d5ea-210">Ionide 是開放原始碼專案所建立與維護的 F# 社群的成員。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-210">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="6d5ea-211">請回報問題，並歡迎您在參與[Ionide VSCode: FSharp GitHub 存放庫](https://github.com/ionide/ionide-vscode-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-211">Please report issues and feel free to contribute at the [Ionide-VSCode: FSharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="6d5ea-212">如果您有要報告的問題，請遵循[取得的記錄檔使用時回報問題的指示](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-212">If you have an issue to report, please follow [the instructions for getting logs to use when reporting an issue](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).</span></span>

<span data-ttu-id="6d5ea-213">您也可以要求取得進一步的協助從 Ionide 開發人員和 F# 社群[Ionide Gitter 通道](https://gitter.im/ionide/ionide-project)。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-213">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6d5ea-214">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6d5ea-214">Next steps</span></span>

<span data-ttu-id="6d5ea-215">若要深入了解 F# 和語言的功能，請參閱[的 F# 教學課程](../tour.md)。</span><span class="sxs-lookup"><span data-stu-id="6d5ea-215">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
