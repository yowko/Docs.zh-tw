---
title: 開始在 Visual Studio Code 中使用 F#
description: 瞭解如何搭配 Visual Studio Code F#和 Ionide 外掛程式套件使用。
ms.date: 12/23/2018
ms.openlocfilehash: 91265303c2954387df0f500940c9af68b3c97dac
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559660"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="3cf9d-103">開始在 Visual Studio Code 中使用 F#</span><span class="sxs-lookup"><span data-stu-id="3cf9d-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="3cf9d-104">您可以使用F# [Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)來撰寫[Visual Studio Code](https://code.visualstudio.com) ，利用 IntelliSense 和程式碼重構取得絕佳的跨平臺、輕量的整合式開發環境（IDE）體驗。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span></span> <span data-ttu-id="3cf9d-105">若要深入瞭解外掛程式，請造訪[Ionide.io](http://ionide.io) 。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-105">Visit [Ionide.io](http://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="3cf9d-106">若要開始，請確定您已[ F#正確安裝和 Ionide 外掛程式](install-fsharp.md#install-f-with-visual-studio-code)。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="create-your-first-project-with-ionide"></a><span data-ttu-id="3cf9d-107">使用 Ionide 建立您的第一個專案</span><span class="sxs-lookup"><span data-stu-id="3cf9d-107">Create your first project with Ionide</span></span>

<span data-ttu-id="3cf9d-108">若要建立新F#的專案，請開啟命令列，並使用 .NET Core CLI 建立新的專案：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span></span>

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

<span data-ttu-id="3cf9d-109">完成後，請將目錄變更為專案，並開啟 Visual Studio Code：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-109">Once it completes, change directory to the project and open Visual Studio Code:</span></span>

```console
cd FirstIonideProject
code .
```

<span data-ttu-id="3cf9d-110">在 Visual Studio Code 上載入專案之後，您應該會在F#視窗左側看到 [方案總管] 窗格開啟。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span></span> <span data-ttu-id="3cf9d-111">這表示 Ionide 已成功載入您剛建立的專案。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-111">This means Ionide has successfully loaded the project you just created.</span></span> <span data-ttu-id="3cf9d-112">在此時間點之前，您可以在編輯器中撰寫程式碼，但一旦發生這種情況，所有專案都已完成載入。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span></span>

## <a name="configure-f-interactive"></a><span data-ttu-id="3cf9d-113">設定F#互動式</span><span class="sxs-lookup"><span data-stu-id="3cf9d-113">Configure F# interactive</span></span>

<span data-ttu-id="3cf9d-114">首先，請確定 .NET Core 腳本是您的預設腳本環境：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-114">First, ensure that .NET Core scripting is your default scripting environment:</span></span>

1. <span data-ttu-id="3cf9d-115">開啟 [Visual Studio Code 設定] \ （程式**代碼** > **喜好** **設定 > 設定**）。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span></span>
1. <span data-ttu-id="3cf9d-116">搜尋「  **F#腳本**」一詞。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-116">Search for the term **F# Script**.</span></span>
1. <span data-ttu-id="3cf9d-117">按一下顯示 [ **fsharp.core：使用 SDK 腳本**] 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-117">Click the checkbox that says **FSharp: use SDK scripts**.</span></span>

<span data-ttu-id="3cf9d-118">這目前是必要的，因為 .NET Framework 型腳本中的一些舊版行為不適用於 .NET Core 腳本，而 Ionide 目前致力於回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span></span> <span data-ttu-id="3cf9d-119">未來，.NET Core 腳本會成為預設值。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-119">In the future, .NET Core scripting will become the default.</span></span>

### <a name="write-your-first-script"></a><span data-ttu-id="3cf9d-120">撰寫您的第一個指令碼</span><span class="sxs-lookup"><span data-stu-id="3cf9d-120">Write your first script</span></span>

<span data-ttu-id="3cf9d-121">設定 Visual Studio Code 以使用 .NET Core 腳本之後，請流覽至 Visual Studio Code 中的 Explorer 視圖，並建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span></span> <span data-ttu-id="3cf9d-122">將它命名為*MyFirstScript. run.fsx*。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-122">Name it *MyFirstScript.fsx*.</span></span>

<span data-ttu-id="3cf9d-123">現在，在其中新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-123">Now add the following code to it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="3cf9d-124">此函式會將單字轉換成[Pig 拉丁](https://en.wikipedia.org/wiki/Pig_Latin)格式。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="3cf9d-125">下一個步驟是使用F#互動式（fsi.exe）進行評估。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-125">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="3cf9d-126">反白顯示整個函式（應為11行長）。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-126">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="3cf9d-127">反白顯示後，按住**Alt**鍵並按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="3cf9d-128">您會發現畫面底部會出現一個終端機視窗，看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span></span>

![具有 Ionide F#的互動式輸出範例](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="3cf9d-130">這有三件事：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-130">This did three things:</span></span>

1. <span data-ttu-id="3cf9d-131">它已開始 FSI.EXE 程式。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-131">It started the FSI process.</span></span>
2. <span data-ttu-id="3cf9d-132">它會傳送您在 FSI.EXE 流程上反白顯示的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-132">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="3cf9d-133">FSI.EXE 流程會評估您傳送的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-133">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="3cf9d-134">由於您傳送的內容是[函式](../language-reference/functions/index.md), 因此您現在可以使用 fsi.exe 來呼叫該函式!</span><span class="sxs-lookup"><span data-stu-id="3cf9d-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="3cf9d-135">在 [互動式] 視窗中，輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-135">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="3cf9d-136">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-136">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="3cf9d-137">現在，讓我們以母音做為第一個字母來嘗試。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-137">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="3cf9d-138">輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-138">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="3cf9d-139">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-139">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="3cf9d-140">函式看起來如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-140">The function appears to be working as expected.</span></span> <span data-ttu-id="3cf9d-141">恭喜您，您只是在F# Visual Studio Code 中撰寫了第一個函式，並使用 fsi.exe 進行評估！</span><span class="sxs-lookup"><span data-stu-id="3cf9d-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="3cf9d-142">您可能已經注意到，FSI.EXE 中的行會以 `;;`終止。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="3cf9d-143">這是因為 FSI.EXE 可讓您輸入多行。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-143">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="3cf9d-144">結尾的 `;;` 可讓 FSI.EXE 知道程式碼完成的時間。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-144">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="3cf9d-145">說明程式碼</span><span class="sxs-lookup"><span data-stu-id="3cf9d-145">Explaining the code</span></span>

<span data-ttu-id="3cf9d-146">如果您不確定程式碼實際執行的作業，以下是逐步解說。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="3cf9d-147">如您所見，`toPigLatin` 是採用單字作為其輸入的函式，並將它轉換成該單字的 Pig-拉丁標記法。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="3cf9d-148">此動作的規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-148">The rules for this are as follows:</span></span>

<span data-ttu-id="3cf9d-149">如果單字中的第一個字元是以母音開頭，請將 "好耶" 新增至單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="3cf9d-150">如果不是以母音開頭，請將該第一個字元移至單字的結尾，並在其中加上 "ay"。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="3cf9d-151">在 FSI.EXE 中，您可能已注意到下列事項：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-151">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="3cf9d-152">這表示 `toPigLatin` 是接受 `string` 做為輸入（稱為 `word`）的函式，並會傳回另一個 `string`。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="3cf9d-153">這稱為函式的[型](https://fsharpforfunandprofit.com/posts/function-signatures/)別簽章，這是瞭解F# F#程式碼的關鍵。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="3cf9d-154">如果您將滑鼠停留在 Visual Studio Code 的函式上，也會注意到這一點。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-154">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="3cf9d-155">在函式的主體中，您會注意到兩個不同的部分：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-155">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="3cf9d-156">稱為`isVowel`的內部函式, 藉由透過[模式比對](../language-reference/pattern-matching.md)檢查指定的字元 (`c`) 是否符合其中一種提供的模式, 來判斷其是否為母音:</span><span class="sxs-lookup"><span data-stu-id="3cf9d-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="3cf9d-157">一個[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)運算式，可檢查第一個字元是否為母音，並根據第一個字元是否為母音，從輸入字元來建立傳回值：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="3cf9d-158">因此，`toPigLatin` 的流程如下：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-158">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="3cf9d-159">檢查輸入字的第一個字元是否為母音。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-159">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="3cf9d-160">如果是，請將 "好耶" 附加至單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-160">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="3cf9d-161">否則，請將該第一個字元移到單字的結尾，並在其中加上 "ay"。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="3cf9d-162">有一件最後要注意的事項：從函式傳回的明確指示，與其他許多語言不同。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-162">There's one final thing to notice about this: there's no explicit instruction to return from the function, unlike many other languages out there.</span></span> <span data-ttu-id="3cf9d-163">這是因為F#是以運算式為基礎，而函數主體中的最後一個運算式是傳回值。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-163">This is because F# is Expression-based, and the last expression in the body of a function is the return value.</span></span> <span data-ttu-id="3cf9d-164">因為 `if..then..else` 本身就是運算式，所以會根據輸入值傳回 `then` 區塊的主體或 `else` 區塊的主體。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-164">Because `if..then..else` is itself an expression, the body of the `then` block or the body of the `else` block will be returned depending on the input value.</span></span>

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a><span data-ttu-id="3cf9d-165">將主控台應用程式轉換成 Pig 的拉丁產生器</span><span class="sxs-lookup"><span data-stu-id="3cf9d-165">Turn the console app into a Pig Latin generator</span></span>

<span data-ttu-id="3cf9d-166">本文中的先前章節示範了撰寫F#程式碼的常見第一個步驟：撰寫初始函式，並使用 fsi.exe 以互動方式執行它。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="3cf9d-167">這就是所謂的複寫驅動開發, 其中[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)複寫代表「讀取-評估-列印迴圈」。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="3cf9d-168">這是實驗功能的絕佳方式，直到您有一些工作可以運作為止。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-168">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="3cf9d-169">以複寫為導向的開發的下一個步驟是將工作程式碼F#移至執行檔案。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="3cf9d-170">然後編譯器會將它編譯F#成可執行檔元件。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="3cf9d-171">若要開始，請開啟您先前使用 .NET Core CLI 建立的*程式. fs*檔案。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span></span> <span data-ttu-id="3cf9d-172">您會發現有一些程式碼已經在那裡。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-172">You'll notice that some code is already in there.</span></span>

<span data-ttu-id="3cf9d-173">接下來，建立稱為 `PigLatin` 的新[`module`](../language-reference/modules.md) ，並將您稍早建立的 `toPigLatin` 函式複製到其中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

<span data-ttu-id="3cf9d-174">此模組應高於 `main` 函式和 `open System` 宣告底下。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-174">This module should be above the `main` function and below the `open System` declaration.</span></span> <span data-ttu-id="3cf9d-175">宣告的順序很重要F#，因此您必須先定義函式，才能在檔案中呼叫它。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span></span>

<span data-ttu-id="3cf9d-176">現在，在 `main` 函式中，對引數呼叫您的 Pig 拉丁產生器函式：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span></span>

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

<span data-ttu-id="3cf9d-177">現在您可以從命令列執行主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-177">Now you can run your console app from the command line:</span></span>

```dotnetcli
dotnet run apple banana
```

<span data-ttu-id="3cf9d-178">您會發現它會輸出與腳本檔案相同的結果，但這次是執行中的程式！</span><span class="sxs-lookup"><span data-stu-id="3cf9d-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span></span>

## <a name="troubleshooting-ionide"></a><span data-ttu-id="3cf9d-179">疑難排解 Ionide</span><span class="sxs-lookup"><span data-stu-id="3cf9d-179">Troubleshooting Ionide</span></span>

<span data-ttu-id="3cf9d-180">以下幾種方式可讓您針對可能遇到的某些問題進行疑難排解：</span><span class="sxs-lookup"><span data-stu-id="3cf9d-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="3cf9d-181">若要取得 Ionide 的程式碼編輯功能， F#您的檔案必須儲存至磁片，以及在 Visual Studio Code 工作區中開啟的資料夾內。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
1. <span data-ttu-id="3cf9d-182">如果您已對系統進行變更，或已安裝 Ionide 的必要條件 Visual Studio Code 開啟，請重新開機 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
1. <span data-ttu-id="3cf9d-183">如果您的專案目錄中有不正確字元，Ionide 可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-183">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="3cf9d-184">如果是這種情況，請重新命名您的專案目錄。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-184">Rename your project directories if this is the case.</span></span>
1. <span data-ttu-id="3cf9d-185">如果沒有可用的 Ionide 命令，請檢查您[Visual Studio Code 的金鑰](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization)系結，以查看您是否意外覆寫它們。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-185">If none of the Ionide commands are working, check your [Visual Studio Code Key Bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) to see if you're overriding them by accident.</span></span>
1. <span data-ttu-id="3cf9d-186">如果您的電腦上的 Ionide 已中斷，而上述未修正您的問題，請嘗試移除電腦上的 `ionide-fsharp` 目錄，然後重新安裝外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>
1. <span data-ttu-id="3cf9d-187">如果無法載入專案（ F#方案總管將會顯示這種情況），請以滑鼠右鍵按一下該專案，然後按一下 [**查看詳細資料**] 以取得更多診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span></span>

<span data-ttu-id="3cf9d-188">Ionide 是由F#社區成員所建立和維護的開放原始碼專案。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-188">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="3cf9d-189">請在[ionide-vscode-Fsharp.core GitHub 存放庫](https://github.com/ionide/ionide-vscode-fsharp)（英文）中回報問題並歡迎您參與。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="3cf9d-190">您也可以在[Ionide Gitter 頻道](https://gitter.im/ionide/ionide-project)中，向 Ionide 開發F#人員和社區尋求進一步的協助。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3cf9d-191">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3cf9d-191">Next steps</span></span>

<span data-ttu-id="3cf9d-192">若要深入瞭解F#語言的詳細資訊，請參閱[的F#導覽](../tour.md)。</span><span class="sxs-lookup"><span data-stu-id="3cf9d-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
