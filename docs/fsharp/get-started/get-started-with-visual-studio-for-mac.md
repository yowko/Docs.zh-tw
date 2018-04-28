---
title: '開始使用 F # 在 Visual Studio for Mac'
description: '了解如何使用 F # 與 Visual Studio for mac。'
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 232235952ec43f682dc21de4ef7dde9c1b553364
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="9a98c-103">開始使用 F # 在 Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="9a98c-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="9a98c-104">F # 和 Visual F # 工具支援 Visual Studio for Mac IDE。</span><span class="sxs-lookup"><span data-stu-id="9a98c-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span>  <span data-ttu-id="9a98c-105">若要開始，您應該[下載 Visual Studio for Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)，如果您還沒有這麼做。</span><span class="sxs-lookup"><span data-stu-id="9a98c-105">To begin, you should [download Visual Studio for Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), if you haven't already.</span></span>  <span data-ttu-id="9a98c-106">本文使用 Visual Studio 社群 2017 for Mac，但是您可以使用 F # 與您所選擇的版本。</span><span class="sxs-lookup"><span data-stu-id="9a98c-106">This article uses the Visual Studio Community 2017 for Mac, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="9a98c-107">正在安裝 F #</span><span class="sxs-lookup"><span data-stu-id="9a98c-107">Installing F#</span></span> #

<span data-ttu-id="9a98c-108">下載 Visual Studio for Mac 之後, 就會提示您選擇您想要安裝。</span><span class="sxs-lookup"><span data-stu-id="9a98c-108">After downloading Visual Studio for Mac, it will prompt you to choose what you want to install.</span></span>  <span data-ttu-id="9a98c-109">基於本文的目的，我們會離開預設值。</span><span class="sxs-lookup"><span data-stu-id="9a98c-109">For the purposes of this article we will be leaving the defaults.</span></span>  <span data-ttu-id="9a98c-110">相較於 Visual Studio for Windows，您不需要特別安裝 F # 支援。</span><span class="sxs-lookup"><span data-stu-id="9a98c-110">In contrast to Visual Studio for Windows, you do not need to specifically install F# support.</span></span>  <span data-ttu-id="9a98c-111">請按 [安裝] 以繼續。</span><span class="sxs-lookup"><span data-stu-id="9a98c-111">Press "Install" to proceed.</span></span>

<span data-ttu-id="9a98c-112">安裝完成後，選擇 [啟動 Visual Studio]。</span><span class="sxs-lookup"><span data-stu-id="9a98c-112">After the install completes, choose "Start Visual Studio".</span></span>  <span data-ttu-id="9a98c-113">您也可以啟動它透過搜尋 macOS 上。</span><span class="sxs-lookup"><span data-stu-id="9a98c-113">You can also launch it through Finder on macOS.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="9a98c-114">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="9a98c-114">Creating a console application</span></span>

<span data-ttu-id="9a98c-115">在 Visual Studio for Mac 最基本的專案是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="9a98c-115">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="9a98c-116">以下為作法。</span><span class="sxs-lookup"><span data-stu-id="9a98c-116">Here's how to do it.</span></span>  <span data-ttu-id="9a98c-117">一旦開啟 Visual Studio for Mac:</span><span class="sxs-lookup"><span data-stu-id="9a98c-117">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="9a98c-118">在**檔案**功能表上，指向**新方案**。</span><span class="sxs-lookup"><span data-stu-id="9a98c-118">On the **File** menu, point to **New Solution**.</span></span>

2.  <span data-ttu-id="9a98c-119">在 [新增專案] 對話方塊中，有 2 不同的範本，為主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="9a98c-119">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="9a98c-120">有一個在 其他-> 以.NET Framework 為目標的.NET。</span><span class="sxs-lookup"><span data-stu-id="9a98c-120">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="9a98c-121">.NET core 是其他範本]-> [應用程式為目標的.NET Core。</span><span class="sxs-lookup"><span data-stu-id="9a98c-121">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="9a98c-122">其中一個範本應該針對本文的目的工作。</span><span class="sxs-lookup"><span data-stu-id="9a98c-122">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="9a98c-123">在主控台應用程式中，視需要變更 C# F #。</span><span class="sxs-lookup"><span data-stu-id="9a98c-123">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="9a98c-124">選擇**下一步**向前移動的按鈕 ！</span><span class="sxs-lookup"><span data-stu-id="9a98c-124">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="9a98c-125">為您的專案命名，並選擇您想要的應用程式的選項。</span><span class="sxs-lookup"><span data-stu-id="9a98c-125">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="9a98c-126">請注意，螢幕將會顯示將建立的目錄結構的側邊的 [預覽] 窗格會根據選取的選項。</span><span class="sxs-lookup"><span data-stu-id="9a98c-126">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="9a98c-127">按一下 [建立] 。</span><span class="sxs-lookup"><span data-stu-id="9a98c-127">Click **Create**.</span></span>  <span data-ttu-id="9a98c-128">您現在應該會看到 [方案總管] 中的 F # 專案。</span><span class="sxs-lookup"><span data-stu-id="9a98c-128">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="9a98c-129">撰寫程式碼</span><span class="sxs-lookup"><span data-stu-id="9a98c-129">Writing your code</span></span>

<span data-ttu-id="9a98c-130">讓我們開始吧撰寫一些程式碼第一次。</span><span class="sxs-lookup"><span data-stu-id="9a98c-130">Let's get started by writing some code first.</span></span>  <span data-ttu-id="9a98c-131">請確定`Program.fs`檔案已開啟，而且然後取代為下列內容：</span><span class="sxs-lookup"><span data-stu-id="9a98c-131">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="9a98c-132">在先前程式碼範例中，函式`square`其可接受名為輸入已定義`x`再將它本身。</span><span class="sxs-lookup"><span data-stu-id="9a98c-132">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="9a98c-133">因為 F # 使用[型別推斷](../language-reference/type-inference.md)的型別`x`不需要指定。</span><span class="sxs-lookup"><span data-stu-id="9a98c-133">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="9a98c-134">F # 編譯器瞭解乘法是有效的其中的型別，並將指派到的類型`x`根據`square`呼叫。</span><span class="sxs-lookup"><span data-stu-id="9a98c-134">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="9a98c-135">如果您將滑鼠停留在`square`，您應該會看到下列：</span><span class="sxs-lookup"><span data-stu-id="9a98c-135">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="9a98c-136">這是所謂的函式的類型簽章。</span><span class="sxs-lookup"><span data-stu-id="9a98c-136">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="9a98c-137">它可以讀取如下:"方會採用名為整數的函式 x，並產生整數 」。</span><span class="sxs-lookup"><span data-stu-id="9a98c-137">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="9a98c-138">請注意，編譯器提供`square``int`類型現在-這是因為乘法不是泛型跨*所有*類型、 但而是跨一組已關閉的類型是泛型。</span><span class="sxs-lookup"><span data-stu-id="9a98c-138">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="9a98c-139">F # 編譯器挑選`int`這點，但它會調整的類型簽章如果您呼叫`square`不同輸入類型，例如`float`。</span><span class="sxs-lookup"><span data-stu-id="9a98c-139">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="9a98c-140">另一個函式， `main`，定義，這以裝飾`EntryPoint`告訴 F # 編譯器執行該程式的屬性應該從那裡開始。</span><span class="sxs-lookup"><span data-stu-id="9a98c-140">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="9a98c-141">它會遵循與其他的相同慣例[c-style 程式設計語言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)，然後從中命令列引數可以傳遞至這個函式，並將整數傳回碼 (通常`0`)。</span><span class="sxs-lookup"><span data-stu-id="9a98c-141">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="9a98c-142">它是我們會呼叫這個函式中`square`函式的引數`12`。</span><span class="sxs-lookup"><span data-stu-id="9a98c-142">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="9a98c-143">F # 編譯器然後將指定的型別`square`是`int -> int`(也就是函式會採用`int`並產生`int`)。</span><span class="sxs-lookup"><span data-stu-id="9a98c-143">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="9a98c-144">若要呼叫`printfn`是格式化的列印函式以使用格式字串，類似 c-style 程式設計語言，其對應至格式字串中指定的參數，然後列印結果和新行。</span><span class="sxs-lookup"><span data-stu-id="9a98c-144">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="9a98c-145">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="9a98c-145">Running your code</span></span>

<span data-ttu-id="9a98c-146">您可以執行的程式碼，並查看結果上的 **執行**從最上層功能表，然後**啟動但不偵錯**。</span><span class="sxs-lookup"><span data-stu-id="9a98c-146">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="9a98c-147">這會執行程式，但不偵錯，並可讓您查看結果。</span><span class="sxs-lookup"><span data-stu-id="9a98c-147">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="9a98c-148">您現在應該會看到下列列印到主控台視窗上的 Visual Studio for Mac:</span><span class="sxs-lookup"><span data-stu-id="9a98c-148">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="9a98c-149">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="9a98c-149">Congratulations!</span></span>  <span data-ttu-id="9a98c-150">您在 Visual Studio 中建立第一個 F # 專案，適用於 Mac、 撰寫 F # 函式列印呼叫此函式的結果並執行專案，以查看一些結果。</span><span class="sxs-lookup"><span data-stu-id="9a98c-150">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="9a98c-151">使用 F # Interactive</span><span class="sxs-lookup"><span data-stu-id="9a98c-151">Using F# Interactive</span></span>

<span data-ttu-id="9a98c-152">其中一個最佳功能的 Visual F # 工具在 Visual Studio for Mac 是 F # Interactive 視窗。</span><span class="sxs-lookup"><span data-stu-id="9a98c-152">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="9a98c-153">它可讓您透過的程式碼傳送至處理序，您可以在此呼叫該程式碼，並以互動方式查看結果。</span><span class="sxs-lookup"><span data-stu-id="9a98c-153">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="9a98c-154">若要開始使用它，反白顯示`square`程式碼中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="9a98c-154">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="9a98c-155">接下來，按一下**編輯**從最上層功能表。</span><span class="sxs-lookup"><span data-stu-id="9a98c-155">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="9a98c-156">接下來選取**將選取範圍傳送至 F # Interactive**。</span><span class="sxs-lookup"><span data-stu-id="9a98c-156">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="9a98c-157">這是 F # Interactive 視窗中執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="9a98c-157">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="9a98c-158">或者，您可以在 選取項目上按一下滑鼠右鍵，然後選擇**將選取範圍傳送至 F # Interactive**。</span><span class="sxs-lookup"><span data-stu-id="9a98c-158">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="9a98c-159">您應該會看到 F # 互動式視窗會出現在它為下列：</span><span class="sxs-lookup"><span data-stu-id="9a98c-159">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="9a98c-160">這會顯示為相同的函式簽章`square`函式，當您暫留在進入函式之前看到。</span><span class="sxs-lookup"><span data-stu-id="9a98c-160">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="9a98c-161">因為`square`是定義在 F # 互動式處理序中，現在可以呼叫具有不同值：</span><span class="sxs-lookup"><span data-stu-id="9a98c-161">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="9a98c-162">這會執行函式，請將結果繫結至新的名稱`it`，並顯示類型和值`it`。</span><span class="sxs-lookup"><span data-stu-id="9a98c-162">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="9a98c-163">請注意，您必須終止與每一行`;;`。</span><span class="sxs-lookup"><span data-stu-id="9a98c-163">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="9a98c-164">這是如何 F # Interactive 知道函式呼叫完成時。</span><span class="sxs-lookup"><span data-stu-id="9a98c-164">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="9a98c-165">您也可以定義新的函式 F # Interactive 中：</span><span class="sxs-lookup"><span data-stu-id="9a98c-165">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="9a98c-166">上述定義新的函式， `isOdd`，這個方法會接受`int`和檢查，以查看是否為奇數 ！</span><span class="sxs-lookup"><span data-stu-id="9a98c-166">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="9a98c-167">您可以呼叫此函式，以查看它傳回以不同的輸入。</span><span class="sxs-lookup"><span data-stu-id="9a98c-167">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="9a98c-168">您可以呼叫函式呼叫中的函式：</span><span class="sxs-lookup"><span data-stu-id="9a98c-168">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="9a98c-169">您也可以使用[管道正運算子](../language-reference/symbol-and-operator-reference/index.md)值導入兩個函式：</span><span class="sxs-lookup"><span data-stu-id="9a98c-169">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="9a98c-170">管道正運算子和詳細資訊，之後的教學課程所述。</span><span class="sxs-lookup"><span data-stu-id="9a98c-170">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="9a98c-171">這是一窺成您可以使用 F # Interactive 執行。</span><span class="sxs-lookup"><span data-stu-id="9a98c-171">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="9a98c-172">若要進一步了解，請參閱[使用 F # 互動式程式設計](../tutorials/fsharp-interactive/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9a98c-172">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9a98c-173">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9a98c-173">Next steps</span></span>

<span data-ttu-id="9a98c-174">如果您還沒有這麼做，請參閱[教學課程的 F #](../tour.md)，其中涵蓋了某些 F # 語言的核心功能。</span><span class="sxs-lookup"><span data-stu-id="9a98c-174">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="9a98c-175">它會提供 F # 的功能概觀，並提供豐富的程式碼範例，您可以將複製到 Visual Studio for Mac 並執行。</span><span class="sxs-lookup"><span data-stu-id="9a98c-175">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="9a98c-176">也有一些絕佳的外部資源，您可以使用，在其中顯示[F # 指南](../index.md)。</span><span class="sxs-lookup"><span data-stu-id="9a98c-176">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a98c-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a98c-177">See also</span></span>
 [<span data-ttu-id="9a98c-178">Visual F#</span><span class="sxs-lookup"><span data-stu-id="9a98c-178">Visual F#</span></span>](../index.md)  
 [<span data-ttu-id="9a98c-179">F# 的教學課程</span><span class="sxs-lookup"><span data-stu-id="9a98c-179">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="9a98c-180">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="9a98c-180">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="9a98c-181">類型推斷</span><span class="sxs-lookup"><span data-stu-id="9a98c-181">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="9a98c-182">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="9a98c-182">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
