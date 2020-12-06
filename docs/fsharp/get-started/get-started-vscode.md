---
title: 開始在 Visual Studio Code 中使用 F#
description: '瞭解如何使用 F # 搭配 Visual Studio Code 和 Ionide 外掛程式套件。'
ms.date: 12/23/2018
ms.openlocfilehash: 11fb0d443fb7c2b3f270d45bfeaa91102ba28efd
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739798"
---
# <a name="get-started-with-f-in-visual-studio-code"></a><span data-ttu-id="f771c-103">開始在 Visual Studio Code 中使用 F#</span><span class="sxs-lookup"><span data-stu-id="f771c-103">Get Started with F# in Visual Studio Code</span></span>

<span data-ttu-id="f771c-104">您可以使用[Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)來撰寫[Visual Studio Code](https://code.visualstudio.com)的 F #，以取得絕佳的跨平臺、輕量的整合式開發環境， (使用 IntelliSense 和程式碼重構的 IDE) 體驗。</span><span class="sxs-lookup"><span data-stu-id="f771c-104">You can write F# in [Visual Studio Code](https://code.visualstudio.com) with the [Ionide plugin](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) to get a great cross-platform, lightweight Integrated Development Environment (IDE) experience with IntelliSense and code refactorings.</span></span> <span data-ttu-id="f771c-105">造訪 [Ionide.io](https://ionide.io) 以深入瞭解外掛程式。</span><span class="sxs-lookup"><span data-stu-id="f771c-105">Visit [Ionide.io](https://ionide.io) to learn more about the plugin.</span></span>

<span data-ttu-id="f771c-106">若要開始，請確定您已 [正確安裝 F # 和 Ionide 外掛程式](install-fsharp.md#install-f-with-visual-studio-code)。</span><span class="sxs-lookup"><span data-stu-id="f771c-106">To begin, ensure that you have [F# and the Ionide plugin correctly installed](install-fsharp.md#install-f-with-visual-studio-code).</span></span>

## <a name="create-your-first-project-with-ionide"></a><span data-ttu-id="f771c-107">使用 Ionide 建立您的第一個專案</span><span class="sxs-lookup"><span data-stu-id="f771c-107">Create your first project with Ionide</span></span>

<span data-ttu-id="f771c-108">若要建立新的 F # 專案，請開啟命令列，並使用 .NET Core CLI 建立新的專案：</span><span class="sxs-lookup"><span data-stu-id="f771c-108">To create a new F# project, open a command line and create a new project with the .NET Core CLI:</span></span>

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

<span data-ttu-id="f771c-109">完成之後，請將目錄變更為專案，並開啟 Visual Studio Code：</span><span class="sxs-lookup"><span data-stu-id="f771c-109">Once it completes, change directory to the project and open Visual Studio Code:</span></span>

```console
cd FirstIonideProject
code .
```

<span data-ttu-id="f771c-110">專案載入 Visual Studio Code 之後，您應該會在視窗的左側看到 F # 方案總管窗格開啟。</span><span class="sxs-lookup"><span data-stu-id="f771c-110">After the project loads on Visual Studio Code, you should see the F# Solution Explorer pane on the left-hand side of your window open.</span></span> <span data-ttu-id="f771c-111">這表示 Ionide 已成功載入您剛才建立的專案。</span><span class="sxs-lookup"><span data-stu-id="f771c-111">This means Ionide has successfully loaded the project you just created.</span></span> <span data-ttu-id="f771c-112">您可以在此時間點之前在編輯器中撰寫程式碼，但是一旦發生這種情況，所有專案都已完成載入。</span><span class="sxs-lookup"><span data-stu-id="f771c-112">You can write code in the editor before this point in time, but once this happens, everything has finished loading.</span></span>

## <a name="configure-f-interactive"></a><span data-ttu-id="f771c-113">設定 F # interactive</span><span class="sxs-lookup"><span data-stu-id="f771c-113">Configure F# interactive</span></span>

<span data-ttu-id="f771c-114">首先，請確定 .NET Core 腳本是您的預設腳本環境：</span><span class="sxs-lookup"><span data-stu-id="f771c-114">First, ensure that .NET Core scripting is your default scripting environment:</span></span>

1. <span data-ttu-id="f771c-115">開啟 [Visual Studio Code 設定] ([程式 **代碼**  >  **偏好**  >  **設定**]) 。</span><span class="sxs-lookup"><span data-stu-id="f771c-115">Open the Visual Studio Code settings (**Code** > **Preferences** > **Settings**).</span></span>
1. <span data-ttu-id="f771c-116">搜尋「 **F # 腳本**」一詞。</span><span class="sxs-lookup"><span data-stu-id="f771c-116">Search for the term **F# Script**.</span></span>
1. <span data-ttu-id="f771c-117">按一下顯示 [ **fsharp.core：使用 SDK 腳本**] 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f771c-117">Click the checkbox that says **FSharp: use SDK scripts**.</span></span>

<span data-ttu-id="f771c-118">這目前是必要的，因為 .NET Framework 型腳本中的某些舊版行為不適用於 .NET Core 腳本，而 Ionide 目前致力於提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="f771c-118">This is currently necessary due to some legacy behaviors in .NET Framework-based scripting that don't work with .NET Core scripting, and Ionide is currently striving for that backwards compatibility.</span></span> <span data-ttu-id="f771c-119">未來，.NET Core 腳本會成為預設值。</span><span class="sxs-lookup"><span data-stu-id="f771c-119">In the future, .NET Core scripting will become the default.</span></span>

### <a name="write-your-first-script"></a><span data-ttu-id="f771c-120">撰寫您的第一個指令碼</span><span class="sxs-lookup"><span data-stu-id="f771c-120">Write your first script</span></span>

<span data-ttu-id="f771c-121">當您將 Visual Studio Code 設定為使用 .NET Core 腳本之後，請流覽至 Visual Studio Code 中的 Explorer 視圖，然後建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="f771c-121">Once you've configured Visual Studio Code to use .NET Core scripting, navigate to the Explorer view in Visual Studio Code and create a new file.</span></span> <span data-ttu-id="f771c-122">將它命名為 *MyFirstScript. .fsx*。</span><span class="sxs-lookup"><span data-stu-id="f771c-122">Name it *MyFirstScript.fsx*.</span></span>

<span data-ttu-id="f771c-123">現在，在其中新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="f771c-123">Now add the following code to it:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

<span data-ttu-id="f771c-124">此函式會將單字轉換成 [Pig 拉丁](https://en.wikipedia.org/wiki/Pig_Latin)的形式。</span><span class="sxs-lookup"><span data-stu-id="f771c-124">This function converts a word to a form of [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).</span></span> <span data-ttu-id="f771c-125">下一步是使用 F# 互動 (FSI) 來進行評估。</span><span class="sxs-lookup"><span data-stu-id="f771c-125">The next step is to evaluate it using F# Interactive (FSI).</span></span>

<span data-ttu-id="f771c-126">醒目提示整個函數 (應為11行長) 。</span><span class="sxs-lookup"><span data-stu-id="f771c-126">Highlight the entire function (it should be 11 lines long).</span></span> <span data-ttu-id="f771c-127">反白顯示之後，請按住 **Alt** 鍵，然後按 **Enter** 鍵。</span><span class="sxs-lookup"><span data-stu-id="f771c-127">Once it's highlighted, hold the **Alt** key and hit **Enter**.</span></span> <span data-ttu-id="f771c-128">您會注意到畫面底部會出現一個終端機視窗，看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="f771c-128">You'll notice a terminal window pop up on the bottom of the screen, and it should look similar to this:</span></span>

![使用 Ionide F# 互動輸出的範例](./media/getting-started-vscode/vscode-fsi.png)

<span data-ttu-id="f771c-130">這有三個專案：</span><span class="sxs-lookup"><span data-stu-id="f771c-130">This did three things:</span></span>

1. <span data-ttu-id="f771c-131">它已開始 FSI 程式。</span><span class="sxs-lookup"><span data-stu-id="f771c-131">It started the FSI process.</span></span>
2. <span data-ttu-id="f771c-132">它會將您在 FSI 程式上反白顯示的程式碼傳送給您。</span><span class="sxs-lookup"><span data-stu-id="f771c-132">It sent the code you highlighted over the FSI process.</span></span>
3. <span data-ttu-id="f771c-133">FSI 進程會評估您傳送的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f771c-133">The FSI process evaluated the code you sent over.</span></span>

<span data-ttu-id="f771c-134">因為您送出的是函 [式，所以](../language-reference/functions/index.md)您現在可以使用 FSI 來呼叫該函式！</span><span class="sxs-lookup"><span data-stu-id="f771c-134">Because what you sent over was a [function](../language-reference/functions/index.md), you can now call that function with FSI!</span></span> <span data-ttu-id="f771c-135">在互動式視窗中，輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="f771c-135">In the interactive window, type the following:</span></span>

```fsharp
toPigLatin "banana";;
```

<span data-ttu-id="f771c-136">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="f771c-136">You should see the following result:</span></span>

```fsharp
val it : string = "ananabay"
```

<span data-ttu-id="f771c-137">現在，讓我們以母音做為第一個字母來嘗試。</span><span class="sxs-lookup"><span data-stu-id="f771c-137">Now, let's try with a vowel as the first letter.</span></span> <span data-ttu-id="f771c-138">輸入以下資訊：</span><span class="sxs-lookup"><span data-stu-id="f771c-138">Enter the following:</span></span>

```fsharp
toPigLatin "apple";;
```

<span data-ttu-id="f771c-139">您應該會看到下列結果：</span><span class="sxs-lookup"><span data-stu-id="f771c-139">You should see the following result:</span></span>

```fsharp
val it : string = "appleyay"
```

<span data-ttu-id="f771c-140">函數看起來像預期般運作。</span><span class="sxs-lookup"><span data-stu-id="f771c-140">The function appears to be working as expected.</span></span> <span data-ttu-id="f771c-141">恭喜，您只是在 Visual Studio Code 撰寫了第一個 F # 函式，並使用 FSI 進行評估！</span><span class="sxs-lookup"><span data-stu-id="f771c-141">Congratulations, you just wrote your first F# function in Visual Studio Code and evaluated it with FSI!</span></span>

> [!NOTE]
> <span data-ttu-id="f771c-142">您可能已經注意到，FSI 中的行會以終止 `;;` 。</span><span class="sxs-lookup"><span data-stu-id="f771c-142">As you may have noticed, the lines in FSI are terminated with `;;`.</span></span> <span data-ttu-id="f771c-143">這是因為 FSI 可讓您輸入多行。</span><span class="sxs-lookup"><span data-stu-id="f771c-143">This is because FSI allows you to enter multiple lines.</span></span> <span data-ttu-id="f771c-144">`;;`最後讓 FSI 知道程式碼完成的時間。</span><span class="sxs-lookup"><span data-stu-id="f771c-144">The `;;` at the end lets FSI know when the code is finished.</span></span>

## <a name="explaining-the-code"></a><span data-ttu-id="f771c-145">說明程式碼</span><span class="sxs-lookup"><span data-stu-id="f771c-145">Explaining the code</span></span>

<span data-ttu-id="f771c-146">如果您不確定程式碼實際執行的工作，以下是逐步解說。</span><span class="sxs-lookup"><span data-stu-id="f771c-146">If you're not sure about what the code is actually doing, here's a step-by-step.</span></span>

<span data-ttu-id="f771c-147">如您所見，它 `toPigLatin` 是接受單字作為其輸入的函式，並將它轉換成該單字的 Pig-Latin 標記法。</span><span class="sxs-lookup"><span data-stu-id="f771c-147">As you can see, `toPigLatin` is a function that takes a word as its input and converts it to a Pig-Latin representation of that word.</span></span> <span data-ttu-id="f771c-148">其規則如下所示：</span><span class="sxs-lookup"><span data-stu-id="f771c-148">The rules for this are as follows:</span></span>

<span data-ttu-id="f771c-149">如果單字中的第一個字元開頭為母音，請將 "好耶" 新增至單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="f771c-149">If the first character in a word starts with a vowel, add "yay" to the end of the word.</span></span> <span data-ttu-id="f771c-150">如果它不是以母音開頭，請將第一個字元移至單字的結尾，並將 "ay" 新增至其中。</span><span class="sxs-lookup"><span data-stu-id="f771c-150">If it doesn't start with a vowel, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="f771c-151">您可能已注意到 FSI 中的下列事項：</span><span class="sxs-lookup"><span data-stu-id="f771c-151">You may have noticed the following in FSI:</span></span>

```fsharp
val toPigLatin : word:string -> string
```

<span data-ttu-id="f771c-152">這是一種函式 `toPigLatin` ，它會採用 `string` 做為輸入的 (`word` ，稱為) ，並傳回另一個 `string` 。</span><span class="sxs-lookup"><span data-stu-id="f771c-152">This states that `toPigLatin` is a function that takes in a `string` as input (called `word`), and returns another `string`.</span></span> <span data-ttu-id="f771c-153">這就是所謂的函式 [類型](https://fsharpforfunandprofit.com/posts/function-signatures/)簽章，這是 f # 的基本部分，這是瞭解 F # 程式碼的關鍵。</span><span class="sxs-lookup"><span data-stu-id="f771c-153">This is known as the [type signature of the function](https://fsharpforfunandprofit.com/posts/function-signatures/), a fundamental piece of F# that's key to understanding F# code.</span></span> <span data-ttu-id="f771c-154">如果您將滑鼠停留在 Visual Studio Code 的函式上，也會注意到這一點。</span><span class="sxs-lookup"><span data-stu-id="f771c-154">You'll also notice this if you hover over the function in Visual Studio Code.</span></span>

<span data-ttu-id="f771c-155">在函式主體中，您會看到兩個不同的部分：</span><span class="sxs-lookup"><span data-stu-id="f771c-155">In the body of the function, you'll notice two distinct parts:</span></span>

1. <span data-ttu-id="f771c-156">稱為的內部函式， `isVowel` 它 `c` 會藉由檢查是否符合透過 [模式](../language-reference/pattern-matching.md)比對所提供的其中一個模式，來判斷指定的字元 () 是否為母音：</span><span class="sxs-lookup"><span data-stu-id="f771c-156">An inner function, called `isVowel`, that determines if a given character (`c`) is a vowel by checking if it matches one of the provided patterns via [Pattern Matching](../language-reference/pattern-matching.md):</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. <span data-ttu-id="f771c-157">[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)檢查第一個字元是否為母音的運算式，並根據第一個字元是否為母音來根據輸入字元來檢查傳回值：</span><span class="sxs-lookup"><span data-stu-id="f771c-157">An [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) expression that checks if the first character is a vowel, and constructs a return value out of the input characters based on if the first character was a vowel or not:</span></span>

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

<span data-ttu-id="f771c-158">因此的流程 `toPigLatin` 如下：</span><span class="sxs-lookup"><span data-stu-id="f771c-158">The flow of `toPigLatin` is thus:</span></span>

<span data-ttu-id="f771c-159">檢查輸入單字的第一個字元是否為母音。</span><span class="sxs-lookup"><span data-stu-id="f771c-159">Check if the first character of the input word is a vowel.</span></span> <span data-ttu-id="f771c-160">如果是，請將 "好耶" 附加至單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="f771c-160">If it is, attach "yay" to the end of the word.</span></span> <span data-ttu-id="f771c-161">否則，請將第一個字元移至單字的結尾，並將 "ay" 新增至該字元。</span><span class="sxs-lookup"><span data-stu-id="f771c-161">Otherwise, move that first character to the end of the word and add "ay" to it.</span></span>

<span data-ttu-id="f771c-162">有一項最後要注意的事項：在 F # 中，沒有從函式傳回的明確指示。</span><span class="sxs-lookup"><span data-stu-id="f771c-162">There's one final thing to notice about this: in F#, there's no explicit instruction to return from the function.</span></span> <span data-ttu-id="f771c-163">這是因為 F # 是以運算式為基礎，而且在函式主體中評估的最後一個運算式會決定該函數的傳回值。</span><span class="sxs-lookup"><span data-stu-id="f771c-163">This is because F# is expression-based, and the last expression evaluated in the body of a function determines the return value of that function.</span></span> <span data-ttu-id="f771c-164">因為 `if..then..else` 本身是運算式，所以區塊主體或區塊主體的評估會 `then` `else` 決定函數所傳回的值 `toPigLatin` 。</span><span class="sxs-lookup"><span data-stu-id="f771c-164">Because `if..then..else` is itself an expression, evaluation of the body of the `then` block or the body of the `else` block determines the value returned by the `toPigLatin` function.</span></span>

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a><span data-ttu-id="f771c-165">將主控台應用程式轉換成 Pig 的拉丁產生器</span><span class="sxs-lookup"><span data-stu-id="f771c-165">Turn the console app into a Pig Latin generator</span></span>

<span data-ttu-id="f771c-166">本文的前幾節示範了撰寫 F # 程式碼的常見第一個步驟：撰寫初始函式，並以互動方式使用 FSI 來執行它。</span><span class="sxs-lookup"><span data-stu-id="f771c-166">The previous sections in this article demonstrated a common first step in writing F# code: writing an initial function and executing it interactively with FSI.</span></span> <span data-ttu-id="f771c-167">這就是所謂的複寫導向開發，其中的 [複寫代表「](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 讀取-評估-列印迴圈」。</span><span class="sxs-lookup"><span data-stu-id="f771c-167">This is known as REPL-driven development, where [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) stands for "Read-Evaluate-Print Loop".</span></span> <span data-ttu-id="f771c-168">這是實驗功能的絕佳方法，直到您有一些工作。</span><span class="sxs-lookup"><span data-stu-id="f771c-168">It's a great way to experiment with functionality until you have something working.</span></span>

<span data-ttu-id="f771c-169">複寫導向開發的下一步，是將工作程式碼移到 F # 實作為檔案。</span><span class="sxs-lookup"><span data-stu-id="f771c-169">The next step in REPL-driven development is to move working code into an F# implementation file.</span></span> <span data-ttu-id="f771c-170">然後，F # 編譯器會將它編譯成可執行檔元件。</span><span class="sxs-lookup"><span data-stu-id="f771c-170">It can then be compiled by the F# compiler into an assembly that can be executed.</span></span>

<span data-ttu-id="f771c-171">若要開始，請開啟您稍早使用 .NET Core CLI 建立的 *程式. fs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="f771c-171">To begin, open the *Program.fs* file that you created earlier with the .NET Core CLI.</span></span> <span data-ttu-id="f771c-172">您會發現其中已有一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="f771c-172">You'll notice that some code is already in there.</span></span>

<span data-ttu-id="f771c-173">接著，建立名為的新， [`module`](../language-reference/modules.md) `PigLatin` 並將您稍早建立的函式複製 `toPigLatin` 到其中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f771c-173">Next, create a new [`module`](../language-reference/modules.md) called `PigLatin` and copy the `toPigLatin` function you created earlier into it as such:</span></span>

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

<span data-ttu-id="f771c-174">此模組應該在函式 `main` 和宣告下方 `open System` 。</span><span class="sxs-lookup"><span data-stu-id="f771c-174">This module should be above the `main` function and below the `open System` declaration.</span></span> <span data-ttu-id="f771c-175">在 F # 中，宣告的順序很重要，因此您必須先定義函式，才能在檔案中呼叫該函式。</span><span class="sxs-lookup"><span data-stu-id="f771c-175">Order of declarations matters in F#, so you'll need to define the function before you call it in a file.</span></span>

<span data-ttu-id="f771c-176">現在，在函式中 `main` ，呼叫引數上的 Pig 拉丁產生器函式：</span><span class="sxs-lookup"><span data-stu-id="f771c-176">Now, in the `main` function, call your Pig Latin generator function on the arguments:</span></span>

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn %"{name} in Pig Latin is: {newName}"

    0
```

<span data-ttu-id="f771c-177">現在您可以從命令列執行您的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="f771c-177">Now you can run your console app from the command line:</span></span>

```dotnetcli
dotnet run apple banana
```

<span data-ttu-id="f771c-178">您會看到它與腳本檔案輸出的結果相同，但是這次是執行中的程式！</span><span class="sxs-lookup"><span data-stu-id="f771c-178">And you'll see that it outputs the same result as your script file, but this time as a running program!</span></span>

## <a name="troubleshooting-ionide"></a><span data-ttu-id="f771c-179">針對 Ionide 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="f771c-179">Troubleshooting Ionide</span></span>

<span data-ttu-id="f771c-180">以下是一些您可以針對一些可能遇到的問題進行疑難排解的方法：</span><span class="sxs-lookup"><span data-stu-id="f771c-180">Here are a few ways you can troubleshoot certain problems that you might run into:</span></span>

1. <span data-ttu-id="f771c-181">若要取得 Ionide 的程式碼編輯功能，您的 F # 檔案必須儲存到磁片，並放在 Visual Studio Code 工作區中開啟的資料夾內。</span><span class="sxs-lookup"><span data-stu-id="f771c-181">To get the code editing features of Ionide, your F# files need to be saved to disk and inside of a folder that is open in the Visual Studio Code workspace.</span></span>
1. <span data-ttu-id="f771c-182">如果您已對系統進行變更，或已安裝 Visual Studio Code 開啟的 Ionide 必要條件，請重新開機 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="f771c-182">If you've made changes to your system or installed Ionide prerequisites with Visual Studio Code open, restart Visual Studio Code.</span></span>
1. <span data-ttu-id="f771c-183">如果您的專案目錄中有不正確字元，Ionide 可能無法運作。</span><span class="sxs-lookup"><span data-stu-id="f771c-183">If you have invalid characters in your project directories, Ionide might not work.</span></span>  <span data-ttu-id="f771c-184">如果發生這種情況，請重新命名您的專案目錄。</span><span class="sxs-lookup"><span data-stu-id="f771c-184">Rename your project directories if this is the case.</span></span>
1. <span data-ttu-id="f771c-185">如果沒有任何 Ionide 命令可運作，請檢查您的 [Visual Studio Code 機碼](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) 系結，以查看是否意外覆寫這些命令。</span><span class="sxs-lookup"><span data-stu-id="f771c-185">If none of the Ionide commands are working, check your [Visual Studio Code Key Bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) to see if you're overriding them by accident.</span></span>
1. <span data-ttu-id="f771c-186">如果您的電腦上的 Ionide 已中斷，且上述各項都未修正您的問題，請嘗試移除 `ionide-fsharp` 電腦上的目錄，然後重新安裝外掛程式套件。</span><span class="sxs-lookup"><span data-stu-id="f771c-186">If Ionide is broken on your machine and none of the above has fixed your problem, try removing the `ionide-fsharp` directory on your machine and reinstall the plugin suite.</span></span>
1. <span data-ttu-id="f771c-187">如果專案無法載入 (F # 方案總管將會顯示此) ，請在該專案上按一下滑鼠右鍵，然後按一下 [ **查看詳細資料** ] 以取得更多診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="f771c-187">If a project failed to load (the F# Solution Explorer will show this), right-click on that project and click **See details** to get more diagnostic info.</span></span>

<span data-ttu-id="f771c-188">Ionide 是一種開放原始碼專案，由 F # 群體的成員所建立和維護。</span><span class="sxs-lookup"><span data-stu-id="f771c-188">Ionide is an open source project built and maintained by members of the F# community.</span></span> <span data-ttu-id="f771c-189">請在 [ionide-vscode-Fsharp.core GitHub 存放庫](https://github.com/ionide/ionide-vscode-fsharp)中回報問題，並歡迎您參與。</span><span class="sxs-lookup"><span data-stu-id="f771c-189">Please report issues and feel free to contribute at the [ionide-vscode-fsharp GitHub repository](https://github.com/ionide/ionide-vscode-fsharp).</span></span>

<span data-ttu-id="f771c-190">您也可以在 [Ionide Gitter 頻道](https://gitter.im/ionide/ionide-project)中向 Ionide 開發人員和 F # 團體要求進一步的協助。</span><span class="sxs-lookup"><span data-stu-id="f771c-190">You can also ask for further help from the Ionide developers and F# community in the [Ionide Gitter channel](https://gitter.im/ionide/ionide-project).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f771c-191">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f771c-191">Next steps</span></span>

<span data-ttu-id="f771c-192">若要深入瞭解 F # 和語言的功能，請參閱 [f # 導覽](../tour.md)。</span><span class="sxs-lookup"><span data-stu-id="f771c-192">To learn more about F# and the features of the language, check out [Tour of F#](../tour.md).</span></span>
