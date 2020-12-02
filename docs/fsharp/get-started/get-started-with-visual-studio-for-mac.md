---
title: '開始使用 Visual Studio for Mac 中的 F #'
description: '瞭解如何搭配 Visual Studio for Mac 使用 F #。'
ms.date: 07/03/2018
ms.openlocfilehash: d2ad24ad18bb31419b39508f2cf555c82fbe2e0b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437998"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="c2618-103">開始使用 Visual Studio for Mac 中的 F #</span><span class="sxs-lookup"><span data-stu-id="c2618-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="c2618-104">Visual Studio for Mac IDE 支援 F # 和 Visual F# 工具。</span><span class="sxs-lookup"><span data-stu-id="c2618-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="c2618-105">確定您已 [安裝 Visual Studio for Mac](install-fsharp.md#install-f-with-visual-studio-for-mac)。</span><span class="sxs-lookup"><span data-stu-id="c2618-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="c2618-106">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c2618-106">Creating a console application</span></span>

<span data-ttu-id="c2618-107">Visual Studio for Mac 的其中一個最基本的專案是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2618-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="c2618-108">以下說明如何執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="c2618-108">Here's how to do it.</span></span>  <span data-ttu-id="c2618-109">Visual Studio for Mac 開啟之後：</span><span class="sxs-lookup"><span data-stu-id="c2618-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="c2618-110">**在 [檔案**] 功能表上，指向 [**新增方案**]。</span><span class="sxs-lookup"><span data-stu-id="c2618-110">On the **File** menu, point to **New Solution**.</span></span>

2. <span data-ttu-id="c2618-111">在 [新增專案] 對話方塊中，主控台應用程式有2個不同的範本。</span><span class="sxs-lookup"><span data-stu-id="c2618-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="c2618-112">在以 .NET Framework 為目標的其他 > .NET 下會有一個。</span><span class="sxs-lookup"><span data-stu-id="c2618-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="c2618-113">另一個範本是以 .net core 為目標的 > 應用程式，以 .NET Core 為目標。</span><span class="sxs-lookup"><span data-stu-id="c2618-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="c2618-114">這兩個範本都應該適用于本文的目的。</span><span class="sxs-lookup"><span data-stu-id="c2618-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="c2618-115">在 [主控台應用程式] 下，視需要將 c # 變更為 F #。</span><span class="sxs-lookup"><span data-stu-id="c2618-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="c2618-116">選擇 [ **下一步]** 按鈕繼續進行！</span><span class="sxs-lookup"><span data-stu-id="c2618-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="c2618-117">為您的專案命名，並選擇您想要用於應用程式的選項。</span><span class="sxs-lookup"><span data-stu-id="c2618-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="c2618-118">請注意，畫面側邊的 [預覽] 窗格會顯示將根據選取的選項建立的目錄結構。</span><span class="sxs-lookup"><span data-stu-id="c2618-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="c2618-119">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="c2618-119">Click **Create**.</span></span>  <span data-ttu-id="c2618-120">您現在應該會在方案總管中看到 F # 專案。</span><span class="sxs-lookup"><span data-stu-id="c2618-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="c2618-121">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="c2618-121">Writing your code</span></span>

<span data-ttu-id="c2618-122">先撰寫一些程式碼，讓我們開始吧。</span><span class="sxs-lookup"><span data-stu-id="c2618-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="c2618-123">請確定檔案 `Program.fs` 已開啟，然後將其內容取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="c2618-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="c2618-124">在先前的程式碼範例中，已 `square` 定義函式，該函式會接受名為的輸入 `x` ，並將其本身相乘。</span><span class="sxs-lookup"><span data-stu-id="c2618-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="c2618-125">因為 F # 使用 [型別推斷](../language-reference/type-inference.md)，所以 `x` 不需要指定的型別。</span><span class="sxs-lookup"><span data-stu-id="c2618-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="c2618-126">F # 編譯器瞭解乘法有效的型別，而且會根據呼叫方式將型別指派給 `x` `square` 。</span><span class="sxs-lookup"><span data-stu-id="c2618-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="c2618-127">如果您將滑鼠停留在上方 `square` ，您應該會看到下列內容：</span><span class="sxs-lookup"><span data-stu-id="c2618-127">If you hover over `square`, you should see the following:</span></span>

```console
val square: x:int -> int
```

<span data-ttu-id="c2618-128">這就是所謂的函式類型簽章。</span><span class="sxs-lookup"><span data-stu-id="c2618-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="c2618-129">它可以像這樣讀取：「方形是一個函式，它會採用名為 x 的整數，並產生整數」。</span><span class="sxs-lookup"><span data-stu-id="c2618-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="c2618-130">請注意，編譯器 `square` `int` 會提供目前的型別，這是因為在 *所有* 類型中的乘法不是泛型，而是在一組封閉的型別中是泛型。</span><span class="sxs-lookup"><span data-stu-id="c2618-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="c2618-131">此時會挑選 F # 編譯器 `int` ，但如果您 `square` 使用不同的輸入類型（例如）來呼叫，則會調整型別簽章 `float` 。</span><span class="sxs-lookup"><span data-stu-id="c2618-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="c2618-132">另外也定義了另一個函式， `main` 它是以 `EntryPoint` 屬性裝飾，告訴 F # 編譯器，程式執行應該在此開始。</span><span class="sxs-lookup"><span data-stu-id="c2618-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="c2618-133">它會遵循與其他 [C 樣式程式設計語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)相同的慣例，其中命令列引數可傳遞給此函式，而整數程式碼則會傳回 (通常 `0`) 。</span><span class="sxs-lookup"><span data-stu-id="c2618-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="c2618-134">在這個函式中，我們使用的 `square` 引數來呼叫函式 `12` 。</span><span class="sxs-lookup"><span data-stu-id="c2618-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="c2618-135">然後，F # 編譯器會將的型別指派為 `square` `int -> int` (也就是採用 `int` 並產生) 的函式 `int` 。</span><span class="sxs-lookup"><span data-stu-id="c2618-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="c2618-136">的呼叫 `printfn` 是格式化的列印函式，它會使用格式字串，類似于 C 樣式的程式設計語言、與格式字串中指定的參數對應的參數，然後列印結果和新的行。</span><span class="sxs-lookup"><span data-stu-id="c2618-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="c2618-137">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="c2618-137">Running your code</span></span>

<span data-ttu-id="c2618-138">您可以從最上層功能表中按一下 [ **執行** ]，然後在不進行偵錯工具的情況 **下啟動**，來執行程式碼並查看結果。</span><span class="sxs-lookup"><span data-stu-id="c2618-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="c2618-139">這會執行程式而不進行任何偵測，並可讓您查看結果。</span><span class="sxs-lookup"><span data-stu-id="c2618-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="c2618-140">您現在應該會在主控台視窗中看到下列輸出 Visual Studio for Mac 快顯視窗：</span><span class="sxs-lookup"><span data-stu-id="c2618-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="c2618-141">恭喜！</span><span class="sxs-lookup"><span data-stu-id="c2618-141">Congratulations!</span></span>  <span data-ttu-id="c2618-142">您已在 Visual Studio for Mac 中建立您的第一個 F # 專案、撰寫 F # 函式以列印呼叫該函式的結果，並執行專案以查看某些結果。</span><span class="sxs-lookup"><span data-stu-id="c2618-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="c2618-143">使用 F# 互動</span><span class="sxs-lookup"><span data-stu-id="c2618-143">Using F# Interactive</span></span>

<span data-ttu-id="c2618-144">在 Visual Studio for Mac 中，Visual F# 工具的其中一個最佳功能是 F# 互動視窗。</span><span class="sxs-lookup"><span data-stu-id="c2618-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="c2618-145">它可讓您將程式碼傳送至進程，您可以在其中呼叫該程式碼，並以互動方式查看結果。</span><span class="sxs-lookup"><span data-stu-id="c2618-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="c2618-146">若要開始使用，請反白顯示 `square` 您程式碼中所定義的函式。</span><span class="sxs-lookup"><span data-stu-id="c2618-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="c2618-147">接著，按一下最上層功能表中的 [ **編輯** ]。</span><span class="sxs-lookup"><span data-stu-id="c2618-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="c2618-148">接下來選取 [ **傳送選取專案至 F# 互動**]。</span><span class="sxs-lookup"><span data-stu-id="c2618-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="c2618-149">這會在 F# 互動視窗中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2618-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="c2618-150">或者，您也可以在選取專案上按一下滑鼠右鍵，然後選擇 [ **傳送選取專案] F# 互動**。</span><span class="sxs-lookup"><span data-stu-id="c2618-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="c2618-151">您應該會看到 F# 互動視窗顯示如下：</span><span class="sxs-lookup"><span data-stu-id="c2618-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```console
>

val square : x:int -> int

>
```

<span data-ttu-id="c2618-152">這會顯示函式的相同函式簽章，您稍早在此函式上方看到該簽章 `square` 。</span><span class="sxs-lookup"><span data-stu-id="c2618-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="c2618-153">因為 `square` 現在已在 F# 互動進程中定義，所以您可以使用不同的值來呼叫它：</span><span class="sxs-lookup"><span data-stu-id="c2618-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="c2618-154">這會執行函數、將結果系結至新的名稱 `it` ，並顯示的類型和值 `it` 。</span><span class="sxs-lookup"><span data-stu-id="c2618-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="c2618-155">請注意，您必須使用來終止每一行 `;;` 。</span><span class="sxs-lookup"><span data-stu-id="c2618-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="c2618-156">這是在函式呼叫完成時 F# 互動知道的方式。</span><span class="sxs-lookup"><span data-stu-id="c2618-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="c2618-157">您也可以在 F# 互動中定義新函數：</span><span class="sxs-lookup"><span data-stu-id="c2618-157">You can also define new functions in F# Interactive:</span></span>

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="c2618-158">上述定義了新的函 `isOdd` 式，它會取得 `int` 並檢查是否為奇數！</span><span class="sxs-lookup"><span data-stu-id="c2618-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="c2618-159">您可以呼叫此函式，以查看傳回的內容有不同的輸入。</span><span class="sxs-lookup"><span data-stu-id="c2618-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="c2618-160">您可以呼叫函式呼叫內的函數：</span><span class="sxs-lookup"><span data-stu-id="c2618-160">You can call functions within function calls:</span></span>

```console
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="c2618-161">您也可以使用 [管道轉寄運算子](../language-reference/symbol-and-operator-reference/index.md) ，將值管線至兩個函數：</span><span class="sxs-lookup"><span data-stu-id="c2618-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="c2618-162">順向運算子和其他的教學課程將在稍後的教學課程中討論。</span><span class="sxs-lookup"><span data-stu-id="c2618-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="c2618-163">這只是您可以運用 F# 互動的內容。</span><span class="sxs-lookup"><span data-stu-id="c2618-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="c2618-164">若要深入瞭解，請參閱 [使用 F # 的互動式程式設計](../tools/fsharp-interactive/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c2618-164">To learn more, check out [Interactive Programming with F#](../tools/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c2618-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c2618-165">Next steps</span></span>

<span data-ttu-id="c2618-166">如果您尚未這麼做，請查看 [f #](../tour.md)的教學課程，其中包含 f # 語言的一些核心功能。</span><span class="sxs-lookup"><span data-stu-id="c2618-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="c2618-167">它將概述 F # 的一些功能，並提供可複製到 Visual Studio for Mac 並執行的豐富程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="c2618-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="c2618-168">另外還有一些絕佳的外部資源可供您使用，請展示在 [F # 指南](../index.yml)中。</span><span class="sxs-lookup"><span data-stu-id="c2618-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.yml).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2618-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2618-169">See also</span></span>

- [<span data-ttu-id="c2618-170">F# 指南</span><span class="sxs-lookup"><span data-stu-id="c2618-170">F# guide</span></span>](../index.yml)
- [<span data-ttu-id="c2618-171">F# 的教學課程</span><span class="sxs-lookup"><span data-stu-id="c2618-171">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="c2618-172">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="c2618-172">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="c2618-173">型別推斷</span><span class="sxs-lookup"><span data-stu-id="c2618-173">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="c2618-174">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="c2618-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
