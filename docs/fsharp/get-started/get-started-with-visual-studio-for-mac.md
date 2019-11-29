---
title: 開始使用F# Visual Studio for Mac
description: 瞭解如何搭配 Visual Studio for Mac F#使用。
ms.date: 07/03/2018
ms.openlocfilehash: cd45ab9c59cef76e4bf85a93f39d8e2ee063d200
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552374"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="998e9-103">開始使用F# Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="998e9-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="998e9-104">F#Visual Studio for Mac IDE 中F#支援和視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="998e9-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="998e9-105">請確定您已[安裝 Visual Studio for Mac](install-fsharp.md#install-f-with-visual-studio-for-mac)。</span><span class="sxs-lookup"><span data-stu-id="998e9-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="998e9-106">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="998e9-106">Creating a console application</span></span>

<span data-ttu-id="998e9-107">Visual Studio for Mac 中最基本的專案之一，就是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="998e9-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="998e9-108">以下為作法。</span><span class="sxs-lookup"><span data-stu-id="998e9-108">Here's how to do it.</span></span>  <span data-ttu-id="998e9-109">開啟 Visual Studio for Mac 之後：</span><span class="sxs-lookup"><span data-stu-id="998e9-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="998e9-110">**在 [檔案**] 功能表上，指向 [**新增方案**]。</span><span class="sxs-lookup"><span data-stu-id="998e9-110">On the **File** menu, point to **New Solution**.</span></span>

2. <span data-ttu-id="998e9-111">在 [新增專案] 對話方塊中，主控台應用程式有2個不同的範本。</span><span class="sxs-lookup"><span data-stu-id="998e9-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="998e9-112">在以 .NET Framework 為目標的其他 > .NET 底下有一個。</span><span class="sxs-lookup"><span data-stu-id="998e9-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="998e9-113">另一個範本位於 .NET Core-以 .NET Core 為目標 > 應用程式底下。</span><span class="sxs-lookup"><span data-stu-id="998e9-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="998e9-114">其中一個範本應適用于本文的目的。</span><span class="sxs-lookup"><span data-stu-id="998e9-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="998e9-115">在 [主控台應用程式C# ] F#下，視需要將變更為。</span><span class="sxs-lookup"><span data-stu-id="998e9-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="998e9-116">選擇 [**下一步]** 按鈕繼續進行！</span><span class="sxs-lookup"><span data-stu-id="998e9-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="998e9-117">指定您的專案名稱，然後選擇您想要用於應用程式的選項。</span><span class="sxs-lookup"><span data-stu-id="998e9-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="998e9-118">請注意，畫面側邊的預覽窗格會顯示將根據選取的選項建立的目錄結構。</span><span class="sxs-lookup"><span data-stu-id="998e9-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="998e9-119">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="998e9-119">Click **Create**.</span></span>  <span data-ttu-id="998e9-120">您現在應該會在F#方案總管中看到專案。</span><span class="sxs-lookup"><span data-stu-id="998e9-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="998e9-121">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="998e9-121">Writing your code</span></span>

<span data-ttu-id="998e9-122">讓我們先從撰寫一些程式碼開始。</span><span class="sxs-lookup"><span data-stu-id="998e9-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="998e9-123">請確定 `Program.fs` 檔案已開啟，然後以下列內容取代其內容：</span><span class="sxs-lookup"><span data-stu-id="998e9-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="998e9-124">在先前的程式碼範例中，已定義函式 `square`，它會接受名為 `x` 的輸入，並將其與本身相乘。</span><span class="sxs-lookup"><span data-stu-id="998e9-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="998e9-125">因為F#使用[型別推斷](../language-reference/type-inference.md)，所以不需要指定 `x` 的類型。</span><span class="sxs-lookup"><span data-stu-id="998e9-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="998e9-126">F#編譯器會瞭解乘法的有效值，並根據呼叫 `square` 的方式，將型別指派給 `x`。</span><span class="sxs-lookup"><span data-stu-id="998e9-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="998e9-127">如果您將滑鼠停留在 `square`上，您應該會看到下列內容：</span><span class="sxs-lookup"><span data-stu-id="998e9-127">If you hover over `square`, you should see the following:</span></span>

```console
val square: x:int -> int
```

<span data-ttu-id="998e9-128">這就是所謂的函式型別簽章。</span><span class="sxs-lookup"><span data-stu-id="998e9-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="998e9-129">它可以讀取如下：「正方形是一個函式，它會採用名為 x 的整數，並產生一個整數」。</span><span class="sxs-lookup"><span data-stu-id="998e9-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="998e9-130">請注意，編譯器現在提供 `square` `int` 類型，這是因為乘法在*所有*類型之間並不是泛型，而是在一組封閉的類型之間是泛型的。</span><span class="sxs-lookup"><span data-stu-id="998e9-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="998e9-131">F#編譯器會在此時挑選 `int`，但如果您使用不同的輸入類型（例如 `float`）來呼叫 `square`，它會調整類型簽章。</span><span class="sxs-lookup"><span data-stu-id="998e9-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="998e9-132">已定義另一個函式 `main`，它會使用 `EntryPoint` 屬性裝飾，告訴編譯器應該F#在該處啟動程式執行。</span><span class="sxs-lookup"><span data-stu-id="998e9-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="998e9-133">其遵循與其他[C 樣式程式語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)相同的慣例，其中命令列引數可傳遞給此函式，並傳回整數代碼（通常 `0`）。</span><span class="sxs-lookup"><span data-stu-id="998e9-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="998e9-134">在這個函式中，我們使用 `12`的引數來呼叫 `square` 函數。</span><span class="sxs-lookup"><span data-stu-id="998e9-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="998e9-135">然後F#編譯器會指派要 `int -> int` 的 `square` 類型（也就是接受 `int` 並產生 `int`的函式）。</span><span class="sxs-lookup"><span data-stu-id="998e9-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="998e9-136">`printfn` 的呼叫是格式化的列印函式，它會使用格式字串，類似于 C 樣式的程式語言、對應于格式字串中所指定的參數，然後列印結果和新行。</span><span class="sxs-lookup"><span data-stu-id="998e9-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="998e9-137">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="998e9-137">Running your code</span></span>

<span data-ttu-id="998e9-138">您可以從最上層功能表按一下 [**執行**] 來執行程式碼並查看結果，然後在不進行檢查的情況**下啟動**。</span><span class="sxs-lookup"><span data-stu-id="998e9-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="998e9-139">這會執行程式而不進行偵測，並可讓您查看結果。</span><span class="sxs-lookup"><span data-stu-id="998e9-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="998e9-140">您現在應該會在主控台視窗中看到下列列印 Visual Studio for Mac：</span><span class="sxs-lookup"><span data-stu-id="998e9-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="998e9-141">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="998e9-141">Congratulations!</span></span>  <span data-ttu-id="998e9-142">您已在 Visual Studio for Mac 中F#建立第一個專案，並F#撰寫一個函式來列印呼叫該函數的結果，然後執行專案以查看一些結果。</span><span class="sxs-lookup"><span data-stu-id="998e9-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="998e9-143">使用F#互動式</span><span class="sxs-lookup"><span data-stu-id="998e9-143">Using F# Interactive</span></span>

<span data-ttu-id="998e9-144">Visual Studio for Mac 中視覺化F#工具的其中一項最佳功能就是F#互動式視窗。</span><span class="sxs-lookup"><span data-stu-id="998e9-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="998e9-145">它可讓您將程式碼傳送至進程，您可以在其中呼叫該程式碼，並以互動方式查看結果。</span><span class="sxs-lookup"><span data-stu-id="998e9-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="998e9-146">若要開始使用，請反白顯示程式碼中所定義的 `square` 函式。</span><span class="sxs-lookup"><span data-stu-id="998e9-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="998e9-147">接下來，按一下最上層功能表中的 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="998e9-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="998e9-148">接下來 **，選取 [ F#將選取範圍傳送至互動式**]。</span><span class="sxs-lookup"><span data-stu-id="998e9-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="998e9-149">這會在F#互動式視窗中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="998e9-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="998e9-150">或者，您也可以在選取範圍上按一下滑鼠右鍵，然後選擇 [**傳送選取專案F#到互動**]。</span><span class="sxs-lookup"><span data-stu-id="998e9-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="998e9-151">您應該會看到F#互動式視窗出現，其中包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="998e9-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```console
>

val square : x:int -> int

>
```

<span data-ttu-id="998e9-152">這會顯示 `square` 函式的相同函式簽章，當您在函式上暫留時，您會看到此功能簽章。</span><span class="sxs-lookup"><span data-stu-id="998e9-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="998e9-153">由於 `square` 現在是在F#互動式進程中定義，因此您可以使用不同的值來呼叫它：</span><span class="sxs-lookup"><span data-stu-id="998e9-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="998e9-154">這會執行函式，將結果系結至 `it`的新名稱，並顯示 `it`的類型和值。</span><span class="sxs-lookup"><span data-stu-id="998e9-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="998e9-155">請注意，您必須使用 `;;`來終止每一行。</span><span class="sxs-lookup"><span data-stu-id="998e9-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="998e9-156">這是互動式F#瞭解函式呼叫完成的方式。</span><span class="sxs-lookup"><span data-stu-id="998e9-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="998e9-157">您也可以在互動中定義F#新的函式：</span><span class="sxs-lookup"><span data-stu-id="998e9-157">You can also define new functions in F# Interactive:</span></span>

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="998e9-158">上述定義了新的函式 `isOdd`，它會接受 `int` 並檢查其是否為奇數！</span><span class="sxs-lookup"><span data-stu-id="998e9-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="998e9-159">您可以呼叫此函式，以查看它以不同的輸入傳回的內容。</span><span class="sxs-lookup"><span data-stu-id="998e9-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="998e9-160">您可以在函式呼叫中呼叫函數：</span><span class="sxs-lookup"><span data-stu-id="998e9-160">You can call functions within function calls:</span></span>

```console
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="998e9-161">您也可以使用「順[向」運算子](../language-reference/symbol-and-operator-reference/index.md)，將值管線至這兩個函數：</span><span class="sxs-lookup"><span data-stu-id="998e9-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="998e9-162">後面的教學課程會涵蓋「管線轉寄」運算子等等。</span><span class="sxs-lookup"><span data-stu-id="998e9-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="998e9-163">這只是深入探討您可以使用F#互動式執行的工作。</span><span class="sxs-lookup"><span data-stu-id="998e9-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="998e9-164">若要深入瞭解，請參閱[使用的F#互動式程式設計](../tutorials/fsharp-interactive/index.md)。</span><span class="sxs-lookup"><span data-stu-id="998e9-164">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="998e9-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="998e9-165">Next steps</span></span>

<span data-ttu-id="998e9-166">如果您還沒有這麼做，請參閱的[導覽F# ](../tour.md)，其中涵蓋了F#語言的一些核心功能。</span><span class="sxs-lookup"><span data-stu-id="998e9-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="998e9-167">它可讓您大致瞭解的某些功能F#，並提供您可以複製到 Visual Studio for Mac 並執行的豐富程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="998e9-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="998e9-168">還有一些您可以使用的絕佳外部資源，請參閱[ F#指南](../index.yml)中的展示。</span><span class="sxs-lookup"><span data-stu-id="998e9-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.yml).</span></span>

## <a name="see-also"></a><span data-ttu-id="998e9-169">請參閱</span><span class="sxs-lookup"><span data-stu-id="998e9-169">See also</span></span>

- [<span data-ttu-id="998e9-170">F#輥</span><span class="sxs-lookup"><span data-stu-id="998e9-170">F# guide</span></span>](../index.yml)
- [<span data-ttu-id="998e9-171">F# 的教學課程</span><span class="sxs-lookup"><span data-stu-id="998e9-171">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="998e9-172">F#語言參考</span><span class="sxs-lookup"><span data-stu-id="998e9-172">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="998e9-173">型別推斷</span><span class="sxs-lookup"><span data-stu-id="998e9-173">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="998e9-174">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="998e9-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
